---
title: "XAMPP Apache + php_xmlrpc"
date: 2011-05-20
forum: Programming Talk
---

### Post by MaloKorrigan on 2011-05-20
Hi everyone,

I'm having a slight problem with starting the Apache service ever since I downloaded and installed the php_xmlrpc bundle to get Moodle to work.

Info:

Installed the newest version of XAMPP 1.7.4 to my Ubuntu 11.04 (fully updated).

Began the install for Moodle, but half way through it requested the 'php_xmlrpc' files which I downloaded from the following link -> [http://docs.moodle.org/en/admin/environ](http://docs.moodle.org/en/admin/environ) ... ion/xmlrpc

Now, before I started downloading and installing 'php_xmlrpc' I stopped all the XAMPP services. After installing the 'php_xmlrpc' successfully, I attempted to start the XAMPP services but was prompted with the following:

Starting XAMPP for Linux 1.7.4...
XAMPP: Another web server daemon is already running.
XAMPP: Starting MySQL...
XAMPP: Starting ProFTPD...
XAMPP for Linux started.

I'm not sure how to proceed, so any assistance would be greatly appreciated!

Thanks in advance,

Malo
:)

---

### Post by roccivic on 2011-05-22
You installed XAMMP from a tarball, right? Maybe you have another copy that you obtained through apt? If so:
[HTML]sudo apt-get remove apache2[/HTML]

---

