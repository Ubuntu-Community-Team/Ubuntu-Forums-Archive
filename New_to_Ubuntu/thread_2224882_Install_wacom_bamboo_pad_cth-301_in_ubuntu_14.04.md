---
title: "Install wacom bamboo pad cth-301 in ubuntu 14.04"
date: 2014-05-18
forum: New to Ubuntu
---

### Post by bas6 on 2014-05-18
Dear People,

After installing ubuntu as a double boot with windows 8 (took my a whole day...) I would like to get some stuff working in ubuntu.

I am annoyed my bamboo mouse pad isnt working.

[http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Downloads](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Downloads)
Tried to use this. Couldnt get it to work.

With the kernel driver i just can't get beyond ./configure
I have no clue hwo to do the next steps.mboo 
uname -r gt my my kernel version: 3.13.0-24-generic. But there is no folder with the name of my kernel after i run configure so I am stuck.sudo cp ./<kernel version>/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet
sudo cp ./<kernel version>/wacom_w8001.ko /lib/modules/`uname -r`/kernel/drivers/input/touchscreen

My wacom bamboo doesnt even turn on.

Why do thinks have to be so complicated in ubuntu?

Anyway hope anybody can point my in the right direction.

With kind regards

Bas

---

