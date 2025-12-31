ARG PHP_IMAGE_TAG=8.3-apache
FROM php:${PHP_IMAGE_TAG}

# Apache modules (Laravelで必要になりがち)
RUN a2enmod rewrite headers

# Packages + PHP extensions
RUN apt-get update && apt-get install -y --no-install-recommends \
    git unzip libzip-dev libpng-dev libonig-dev libicu-dev \
  && docker-php-ext-install pdo_mysql mbstring zip intl \
  && rm -rf /var/lib/apt/lists/*

# Composer
COPY --from=composer:2 /usr/bin/composer /usr/bin/composer

# PHP settings
COPY docker/php/php.ini /usr/local/etc/php/php.ini

WORKDIR /var/www
