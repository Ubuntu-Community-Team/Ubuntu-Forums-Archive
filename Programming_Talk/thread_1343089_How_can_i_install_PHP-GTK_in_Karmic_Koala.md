---
title: "How can i install PHP-GTK in Karmic Koala"
date: 2009-12-01
forum: Programming Talk
---

### Post by tatw on 2009-12-01
I want to install php5 gtk to my Ubuntu. How can i install ?

i cant find on synaptics

---

### Post by CyberJack on 2009-12-02
I guess you have to compile and install it manually.
You can get the source here: [http://gtk.php.net/download.php](http://gtk.php.net/download.php)

---

### Post by tatw on 2009-12-02
is GTK having any dependencies for work under Ubuntu ? like glade etc..

---

### Post by CyberJack on 2009-12-03
See [http://ubuntuforums.org/showthread.php?t=333616](http://ubuntuforums.org/showthread.php?t=333616) for compile instructions.
According to this compile instructions you need to install php5-cli php5-dev libgtk2.0-dev and libglade2-dev

---

### Post by udayrajb on 2010-02-02
If you are using 64-bit Ubuntu 9.10 then here is a link for you.
Download the deb package and enjoy! :)

[http://martin-fleming.co.uk/2009/10/php-gtk-ubuntu-64bit-deb-package/](http://martin-fleming.co.uk/2009/10/php-gtk-ubuntu-64bit-deb-package/)

---

### Post by wiscalico on 2010-02-18
I've got it compiling an put it in [my PPA]("https://launchpad.net/~jacob-emcken/+archive/ppa/")... for those too lazy to build themselves :)

It is build with the following: --with-extra --with-html --with-libsexy --with-spell --enable-php-gtk --enable-scintilla --with-mozembed

---

