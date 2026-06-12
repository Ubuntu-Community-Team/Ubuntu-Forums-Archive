---
title: "How to compile and use php5 on Ubuntu 6.04 Server?"
date: 2007-11-27
forum: Packaging and Compiling Programs
---

### Post by burzum on 2007-11-27
I need to install php 5.2.5 because its required for my current project. 

I've downloaded the sources and it looks like it compiles correct, no errors. I've did the make and make install, restarted apache2 but php info still shows me php 5.1.2.

How can i get it running? :( Is there anything else to do? I thought it's going to configure it automatic based on my environment variables.

```
root@Wotan:/data/projekte/php-5.2.5# make install
Installing PHP SAPI module:       cgi
Installing PHP CGI binary: /usr/local/bin/
Installing PHP CLI binary:        /usr/local/bin/
Installing PHP CLI man page:      /usr/local/man/man1/
Installing build environment:     /usr/local/lib/php/build/
Installing header files:          /usr/local/include/php/
Installing helper programs:       /usr/local/bin/
  program: phpize
  program: php-config
Installing man pages:             /usr/local/man/man1/
  page: phpize.1
  page: php-config.1
Installing PEAR environment:      /usr/local/lib/php/
[PEAR] Console_Getopt - already installed: 1.2.3
[PEAR] Archive_Tar    - already installed: 1.3.2
[PEAR] Structures_Graph- already installed: 1.0.2
[PEAR] PEAR           - already installed: 1.6.1
Wrote PEAR system config file at: /usr/local/etc/pear.conf
You may want to add: /usr/local/lib/php to your php.ini include_path
Installing PDO headers:          /usr/local/include/php/ext/pdo/
root@Wotan:/data/projekte/php-5.2.5#

```

---

### Post by maddog39 on 2007-11-27
Try running the following commands:
```

sudo apt-get remove --purge php5

```
That will completely remove Ubuntu's version of PHP5 and purge it from your system. Then you will want to rerun the make install command from the PHP 5.2.5 sources directory to reinstall anything apt-get might have removed accidentily thinking it was part of its own package. See if that works.

---

