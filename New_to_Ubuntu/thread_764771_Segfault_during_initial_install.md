---
title: "Segfault during initial install"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by black.rabbit.object on 2008-04-24
Hiya.

I have an old IBM 733Mhz machine that I want to use as a firewall between my DSL router and my wireless Router.  I only have 32Mb of memory in it unfortunately and have stripped every non essential component out of the box it at the moment has 1 20Gb HDD an Ethernet adapter and a CDROM drive in which I have the release candidate -server- CD, the video is onboard.  I had planned to just to a basic install however just after I set up my locale and keyboard it the installer runs through getting some packages off the CD and I get a Segmentation Fault it dumps some page memory to the syslog screen and everything starts flashing.  I can still run through the process list on the busybox linux installer and issue commands and recurse through the structure but the installer itself is completely zombified.  Is there a minimalist install proceedure just to get the basic framework setup, the disk fdisked and partitioned and a bootable device defined?

---

### Post by Cadmus on 2008-04-24
For what is nearly an emedded application you may be better off with another distro, Ubuntu is marvellous but I'm prety sure 32MB is just not enough.

I'd take a look at _[Damn Small Linux]("http://www.damnsmalllinux.org/")_ in your position.

---

