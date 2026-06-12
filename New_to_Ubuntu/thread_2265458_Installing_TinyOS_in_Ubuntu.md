---
title: "Installing TinyOS in Ubuntu"
date: 2015-02-15
forum: New to Ubuntu
---

### Post by remmas-sido on 2015-02-15
I mean, can I just type tinyos in Ubuntu Software Center and installed just like I install VLC,Chromium ,or it requires a lot of terminal commands line just like the 12.04 version?
Thank you

---

### Post by oldos2er on 2015-02-15
```
apt-cache seach tinyos
``` reveals two tinyos-related packages. You can also check for packages online at packages.ubuntu.com

---

### Post by remmas-sido on 2015-02-17
Hi guys
Does tiny os included by defaut in ubuntu 14.04 repositories? is it hard to install? I mean will there be a lot of terminal command lines or just one or two? I have already post a thread it just I didn't get a precise answer like yes/no answer.
Thank You

---

### Post by Holger_Gehrke on 2015-02-17
The only tinyOS I can find is an operating system for micro controllers. It's a development toolchain consisting of cross compilers, libraries, the OS and so on. It is in the repositories (tinyos-tools + gcc-avr and / or gcc-msp430 and tinyos-source ), but in a rather old version (1.4.2, current is 2.1.2). The installation is just an 'apt-get install' (or two or three), but you'll have to get very comfortable with the command line to actually use it to develop applications for micro controllers.

---

### Post by lisati on 2015-02-17
Threads merged.

Having multiple threads for the same topic can get confusing, and it dilutes the community's ability to help.

---

### Post by grahammechanical on 2015-02-17
[http://tinyos.stanford.edu/tinyos-wiki/index.php/TinyOS_Overview](http://tinyos.stanford.edu/tinyos-wiki/index.php/TinyOS_Overview)

[http://tinyos.stanford.edu/tinyos-wiki/index.php/Automatic_installation](http://tinyos.stanford.edu/tinyos-wiki/index.php/Automatic_installation)

Decide for yourself.

Regards.

---

