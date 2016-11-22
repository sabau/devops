FROM php:5.6-fpm
ENV PHANTOM_JS_VERSION 2.1.1-linux-x86_64

RUN apt-get update && apt-get install -y \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libmcrypt-dev \
        libsnmp-dev \
        snmp \
        snmpd \
        libpng12-dev \
        libpq-dev \
        libxml2-dev \
        libfontconfig \
        libssl-dev \
        libfontconfig1-dev \
        libfreetype6 \
        curl \
        bzip2 \
        libicu-dev \
        g++ \
        zlib1g-dev \
        ssmtp \
    #&& docker-php-ext-install iconv \
    && docker-php-ext-install mcrypt \
    && docker-php-ext-install snmp \
    && docker-php-ext-install pdo \
    && docker-php-ext-install pdo_mysql \
    && docker-php-ext-install pdo_pgsql \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install gd \
    && docker-php-ext-configure intl \
    && docker-php-ext-install intl \
    && docker-php-ext-install soap \
    && mkdir /tmp/phantomjs \
    && curl -L https://bitbucket.org/ariya/phantomjs/downloads/phantomjs-$PHANTOM_JS_VERSION.tar.bz2 \
            | tar -xj --strip-components=1 -C /tmp/phantomjs \
    && mv /tmp/phantomjs/bin/phantomjs /usr/local/bin \
    && echo "FromLineOverride=YES" >> /etc/ssmtp/ssmtp.conf \
    && echo 'sendmail_path = "/usr/sbin/ssmtp -t"' > /usr/local/etc/php/conf.d/mail.ini

COPY ./php.ini /usr/local/etc/php/conf.d/php.ini

#RUN curl -sSL https://bitbucket.org/ariya/phantomjs/downloads/phantomjs-$PHANTOM_JS_VERSION.tar.bz2 | tar xjC /
#RUN ln -s phantomjs-$PHANTOM_JS_VERSION /bin/phantomjs
