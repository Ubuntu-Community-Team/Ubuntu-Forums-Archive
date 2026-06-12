---
title: "Kernel build + ndiswrapper version problem"
date: 2006-07-15
forum: Repositories &amp; Backports
---

### Post by SoftGround on 2006-07-15
I have built the standard linux-source (2.6.15-26.44) kernel and also the ndiswrapper-source (1.8-0ubuntu4).
When I came to install the compiled ndiswrapper module (after the kernel) I got the following error.

```
root@Ubuntu:/usr/src# dpkg -i ndiswrapper-modules-2.6.15.7-ubuntu1-khz_1.8-0ubuntu2+10.00.Custom_i386.deb
Selecting previously deselected package ndiswrapper-modules-2.6.15.7-ubuntu1-khz.
(Reading database ... 143031 files and directories currently installed.)
Unpacking ndiswrapper-modules-2.6.15.7-ubuntu1-khz (from ndiswrapper-modules-2.6.15.7-ubuntu1-khz_1.8-0ubuntu2+10.00.Custom_i386.deb) ...
dpkg: dependency problems prevent configuration of ndiswrapper-modules-2.6.15.7-ubuntu1-khz:
 ndiswrapper-modules-2.6.15.7-ubuntu1-khz depends on ndiswrapper-utils (>= 1.8-1); however:
  Version of ndiswrapper-utils on system is 1.8-0ubuntu2.
dpkg: error processing ndiswrapper-modules-2.6.15.7-ubuntu1-khz (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ndiswrapper-modules-2.6.15.7-ubuntu1-khz

```

I have the latest version available of ndiswrapper-utils installed 1.8-0 and I cannot find a later version.

Surely the 1.8-0 source shouldnt need a 1.8-1 utils?

What should I do now?

---

### Post by mikearthur on 2006-08-02
I just manually edited the control* files in the debian subdirectory to -0 from -1 and it all worked fine :D

---

### Post by Steogede on 2006-08-07
> **mikearthur said:**
> I just manually edited the control* files in the debian subdirectory to -0 from -1 and it all worked fine :D

control* files in the debian subdirectory of what?  ](*,)

---

### Post by Steogede on 2006-08-07
> **Steogede said:**
> control* files in the debian subdirectory of what?  ](*,)

'/usr/src/modules/ndiswrapper/debian/control*' it seems.

I also had to remove the .deb from /usr/src and the ndiswrapper-source.tar.bz2

After that I, cd'd to /usr/src and ran 
  tar cjvf ndiswrapper-source.tar.bz2 modules/ndiswrapper/*

Finally I was then able to run 
  module-assistant auto-install ndiswrapper 
without any problems.

---

### Post by Charles Hand on 2006-09-29
> **Steogede said:**
> 

I also had to remove the .deb from /usr/src and the ndiswrapper-source.tar.bz2

After that I, cd'd to /usr/src and ran 
  tar cjvf ndiswrapper-source.tar.bz2 modules/ndiswrapper/*



That doesn't make any sense. You delete ndiswrapper-source.tar.bz2 and then you unpack it.

---

