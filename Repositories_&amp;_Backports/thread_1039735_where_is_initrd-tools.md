---
title: "where is initrd-tools"
date: 2009-01-14
forum: Repositories &amp; Backports
---

### Post by 999alfred on 2009-01-14
tried to run mkinitrd and it was not found, so I tried to install the initrd-tools package and here is what happenes:
$ sudo apt-get install initrd-tools
[sudo] password for wufo:
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package initrd-tools

Where is the package?
Ubuntu 8.04

tj

---

### Post by jpkotta on 2009-01-16
Ubuntu uses mkinitramfs, which is in....
```
dpkg -S $(which mkinitramfs)
```
```
initramfs-tools: /usr/sbin/mkinitramfs
```

This site may be useful in the future: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

