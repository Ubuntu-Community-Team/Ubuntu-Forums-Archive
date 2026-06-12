---
title: "php5 PECL Fileinfo HOWTO (hardy alpha)"
date: 2008-03-12
forum: Outdated Tutorials &amp; Tips
---

### Post by Brazilian Joe on 2008-03-12
I have travelled the rocky road of figuring out how to install the PECL package Fileinfo (latest stable at the time of this writing is 1.0.4), so I am documenting in case I need it again :)
Fileinfo's most obvious use is if you want to identify the mimetype of an uploaded file in your website.

I have installed it on Gutsy and Hardy, and it works beautifully.

You will have to have at least the following packages (I may have forgotten some):

build-essential
apache2
php5
php5-dev
php5-pear
libmagic-dev (on Gutsy I believe this file is called libmagic1-dev)
libmagic1

You will have to compile/install Fileinfo, since at the time of this writing there is no *Ubuntu package for it.

Commands in a nutshell:

```
sudo pear channel-update pear.php.net
sudo pecl install Fileinfo
```

you should add the extension to your php5 setup (/etc/php5/apache2/php.ini, and /etc/php5/cli/php.ini if you also have the command line version)

```

extension=fileinfo.so
```Still, this is not enough. you have to replace /etc/magic and probably /etc/magic.mime too.

```

sudo cp /usr/share/file/magic.mime /etc/magic
sudo cp /usr/share/file/magic.mime /etc/magic.mime
```With this you SHOULD be able to use Fileinfo without problems. if this guide does not work for you, please let me know!
Good luck to you all!

---

### Post by murjam on 2009-01-19
Thanks!

As there is still no Ubuntu package out, this thread was really helpful.

I would just add that you should also restart your web server when you've done everything mentioned above.
```
sudo apache2ctl restart
```

Also, wouldn't it be cleaner to make symlinks to those mime files instead of copying them?

---

### Post by kim-day on 2010-01-12
Thanks for writing up these steps! I just did this on my 8.04 server and it worked!

Question: It's been a year since the last post here - is there still no Ubuntu package for this? I've still got a lot to learn and don't know how to check the repository and answer my own question.

---

### Post by samwilsonau on 2010-08-23
If anyone is getting this error with PHP 5.3 CLI (e.g. [FONT=Courier New]php -version[/FONT]):

```

PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20090626+lfs/fileinfo.so' - /usr/lib/php5/20090626+lfs/fileinfo.so: cannot open shared object file: No such file or directory in Unknown on line 0

```

It can be solved by getting rid of the fileinfo.so extension (i.e. delete or comment out /etc/php5/cli/conf.d/fileinfo.ini) because this is [now in PHP core]("http://php.net/manual/en/fileinfo.installation.php").  The Pecl extension can be removed too, with [FONT=Courier New]sudo pecl uninstall Fileinfo[/FONT].

---

