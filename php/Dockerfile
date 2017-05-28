FROM php:7.1-fpm
RUN apt-get update && \
  DEBIAN_FRONTEND=noninteractive apt-get install -y apt-utils nano sudo && \
  rm -r /var/lib/apt/lists/*
RUN pear upgrade --force --alldeps
RUN apt-get update && \
  DEBIAN_FRONTEND=noninteractive apt-get install -y libmcrypt-dev && \
  docker-php-ext-install -j$(nproc) mcrypt && \
  rm -r /var/lib/apt/lists/*
RUN docker-php-ext-install pdo_mysql
RUN apt-get update && \
  DEBIAN_FRONTEND=noninteractive apt-get install -y libicu-dev && \
  docker-php-ext-install intl  && \
  rm -r /var/lib/apt/lists/*
RUN apt-get update && \
  DEBIAN_FRONTEND=noninteractive apt-get install -y libxslt-dev && \
  docker-php-ext-install xsl && \
  rm -r /var/lib/apt/lists/*
RUN apt-get update && \
  DEBIAN_FRONTEND=noninteractive apt-get install -y libfreetype6-dev libjpeg62-turbo-dev libpng12-dev && \
  docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ && \
  docker-php-ext-install -j$(nproc) gd && \
  rm -r /var/lib/apt/lists/*
RUN docker-php-ext-install zip
RUN docker-php-ext-install exif
RUN apt-get update && \
  DEBIAN_FRONTEND=noninteractive apt-get install -y libmagickwand-dev --no-install-recommends && \
  pecl install imagick && \
  docker-php-ext-enable imagick && \
  rm -r /var/lib/apt/lists/*
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer && \
  composer --version
