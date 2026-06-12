---
title: "To enable extensions, verify that they are enabled in those .ini fileswiki:/var/www/m"
date: 2017-09-14
forum: New to Ubuntu
---

### Post by armando.ca on 2017-09-14
New to ubuntu, can some help this issue. Thanks.


adminrock@rwiki:/var/www/mediawiki$ composer install --no-dev
> ComposerHookHandler:OnPreUpdate
Loading composer repositories with package information
Updating dependencies
Your requirements could not be resolved to an installable set of packages.

  Problem 1
    - The requested PHP extension ext-mbstring * is missing from your system. Install or enable PHP's mbstring extension.
  Problem 2
    - The requested PHP extension ext-xml * is missing from your system. Install or enable PHP's xml extension.
  Problem 3
    - Installation request for wikimedia/html-formatter 1.0.1 -> satisfiable by wikimedia/html-formatter[1.0.1].
    - wikimedia/html-formatter 1.0.1 requires ext-mbstring * -> the requested PHP extension mbstring is missing from your system.
  Problem 4
    - Installation request for wikimedia/remex-html 1.0.1 -> satisfiable by wikimedia/remex-html[1.0.1].
    - wikimedia/remex-html 1.0.1 requires ext-mbstring * -> the requested PHP extension mbstring is missing from your system.

  To enable extensions, verify that they are enabled in those .ini files:
    - /etc/php/7.0/cli/php.ini
    - /etc/php/7.0/cli/conf.d/10-mysqlnd.ini
    - /etc/php/7.0/cli/conf.d/10-opcache.ini
    - /etc/php/7.0/cli/conf.d/10-pdo.ini
    - /etc/php/7.0/cli/conf.d/20-calendar.ini
    - /etc/php/7.0/cli/conf.d/20-ctype.ini
    - /etc/php/7.0/cli/conf.d/20-curl.ini
    - /etc/php/7.0/cli/conf.d/20-exif.ini
    - /etc/php/7.0/cli/conf.d/20-fileinfo.ini
    - /etc/php/7.0/cli/conf.d/20-ftp.ini
    - /etc/php/7.0/cli/conf.d/20-gd.ini
    - /etc/php/7.0/cli/conf.d/20-gettext.ini
    - /etc/php/7.0/cli/conf.d/20-iconv.ini
    - /etc/php/7.0/cli/conf.d/20-json.ini
    - /etc/php/7.0/cli/conf.d/20-mysqli.ini
    - /etc/php/7.0/cli/conf.d/20-pdo_mysql.ini
    - /etc/php/7.0/cli/conf.d/20-phar.ini
    - /etc/php/7.0/cli/conf.d/20-posix.ini
    - /etc/php/7.0/cli/conf.d/20-readline.ini
    - /etc/php/7.0/cli/conf.d/20-shmop.ini
    - /etc/php/7.0/cli/conf.d/20-sockets.ini
    - /etc/php/7.0/cli/conf.d/20-sysvmsg.ini
    - /etc/php/7.0/cli/conf.d/20-sysvsem.ini
    - /etc/php/7.0/cli/conf.d/20-sysvshm.ini
    - /etc/php/7.0/cli/conf.d/20-tokenizer.ini
  You can also run `php --ini` inside terminal to see which files are used by PHP in CLI mode.
adminrock@To enable extensions, verify that they are enabled in those .ini fileswiki:/var/www/mediawiki$

---

