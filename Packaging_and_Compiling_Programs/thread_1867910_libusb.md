---
title: "libusb"
date: 2011-10-23
forum: Packaging and Compiling Programs
---

### Post by sepoto on 2011-10-23
I recently installed the library libusb by doing this:

sudo apt-get install libusb-1.0-0-dev

I have a directory with examples that looks like this:


penguin@penguin-Satellite-A505:~/Downloads/libusb-1.0.0/examples$ ls -la
total 124
drwxrwxrwx 3 penguin penguin  4096 2011-10-23 11:38 .
drwxrwxrwx 5 penguin penguin  4096 2011-10-23 11:38 ..
drwxrwxr-x 2 penguin penguin  4096 2011-10-23 11:38 .deps
-rw-r--r-- 1 penguin penguin 10781 2008-08-22 22:57 dpfp.c
-rw-r--r-- 1 penguin penguin 11644 2008-06-24 21:00 dpfp_threaded.c
-rw-r--r-- 1 penguin penguin  1643 2008-11-03 15:13 lsusb.c
-rw-rw-r-- 1 penguin penguin 15923 2011-10-23 11:38 Makefile
-rw-r--r-- 1 penguin penguin   356 2008-11-20 08:24 Makefile.am
-rw-r--r-- 1 penguin penguin 16380 2008-12-13 12:07 Makefile.in
penguin@penguin-Satellite-A505:~/Downloads/libusb-1.0.0/examples$ 



I am trying to compile lsusb.c. Would anyone know how to do it? My OS is Ubuntu 11.1.

Thank You!

---

### Post by Bachstelze on 2011-10-25
There's a makefile, have you tried [font=monospace]make[/font]?

---

