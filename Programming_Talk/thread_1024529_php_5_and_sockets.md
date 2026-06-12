---
title: "php 5 and sockets"
date: 2008-12-29
forum: Programming Talk
---

### Post by jent on 2008-12-29
Hey,

So i have pretty much spent the last 48 hours trying to setup everything, but for the last few hours, i have been stuck on trying to configure php5 and sockets.

Every tutorial i read online, it teaches you how to install a LAMP environment with Ubuntu, but nowhere does it tell you how to have you own php extensions.

I found one post where the writer downloaded the php source, and pretty much ./configured it, but when i did it, it failed.

Anyone have a solution for recompiling php so I can enable php sockets? (compile with --enable-sockets)

Thanks in advance

---

### Post by Reiger on 2008-12-29
You'll require: php5-dev (DEB package from the Ubuntu/Debian APT repositories).

If it's a PECL extension you want it's as easy as:
```

sudo aptitude install php5-dev php-pear apache2-dev
sudo pear update-channels
sudo pecl install XXX

```
Where XXX is the name of your PECL extension (say: apc).
PHP5-dev is required for building PHP5 modules, PEAR is the PHP Package tool, PECL is the PHP build tool (for building & linking modules), Apache2 dev is required if you run Apache2 -- it is needed for some auto-magic configuration which needs be done compile/build time.

At the end of installing say APC you'll see something like:
```

Build process completed successfully
Installing '/usr/lib/php5/20060613+lfs/apc.so'
install ok: channel://pecl.php.net/APC-3.0.19
configuration option "php_ini" is not set to php.ini location
You should add "extension=apc.so" to php.ini

```

So then do a:
```

echo "extension=apc.so" | sudo tee -a /etc/php5/apache2/php.ini

```
And then that's done too.

---

### Post by catchmeifyoutry on 2008-12-29
what are you trying to do with sockets? This stuff: [http://nl2.php.net/sockets](http://nl2.php.net/sockets) ?
Example code works for me without extra configuration, that is, the socket functions are available in php5.
My installed php stuff:
[PHP]
i A libapache2-mod-php5             - server-side, HTML-embedded scripting langu
i   php5                            - server-side, HTML-embedded scripting langu
i   php5-cli                        - command-line interpreter for the php5 scri
i A php5-common                     - Common files for packages built from the p
i A php5-gd                         - GD module for php5                        
i   php5-imagick                    - ImageMagick module for php5               
i A php5-mcrypt                     - MCrypt module for php5                    
i   php5-mysql                      - MySQL module for php5                     
i   php5-xdebug                     - Xdebug Module for PHP 5                   
i   phpmyadmin                      - MySQL web administration tool             
[/PHP]

Otherwise, can you be a bit more specific about what you want to achieve?
Cheers

---

