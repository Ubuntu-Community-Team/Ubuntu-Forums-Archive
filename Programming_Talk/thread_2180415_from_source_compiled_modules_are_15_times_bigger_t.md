---
title: "from source compiled modules are 15 times bigger then the installed modules"
date: 2013-10-12
forum: Programming Talk
---

### Post by Sidoney on 2013-10-12
I could compile load and unload modules, but the modules installed vom apt are about 15 times smaller:

>ls -ilaF
2643532 -rw-r--r--  1 root root   50764 2013-09-10 22:30:16 rt73usb.2013-10-082229
2643542 -rw-r--r--  1 root root  713048 2013-10-08 22:24:20 rt73usb.2013-10-090851

With file i see no difference; both modules are  ELF 64-bit LSB relocatable, x86-64, version 1 (SYSV) and not stripped.
But why is the module i compiled, via "make modules", so much bigger? :confused:

---

### Post by tgalati4 on 2013-10-12
If you look in the make configuration file, there will be several build settings.  The larger module is probably statically built--with all of the dependencies built into it so that it does not rely on any shared libraries on the system.  You can use the *modinfo* command on both to see if there are different parameters that can be set.  Perhaps one has more advanced features than the prebuilt one.

tgalati4@Mint14-Extensa ~ $ modinfo rt73usb
filename:       /lib/modules/3.5.0-39-generic/kernel/drivers/net/wireless/rt2x00/rt73usb.ko
license:        GPL
firmware:       rt73.bin
description:    Ralink RT73 USB Wireless LAN driver.
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     0B02148AE34D1BB9A181FC5
alias:          usb:v0586p3415d*dc*dsc*dp*ic*isc*ip*
.
.
.
alias:          usb:v07B8pB21Bd*dc*dsc*dp*ic*isc*ip*
**depends:        rt2x00lib,rt2x00usb,crc-itu-t**
intree:         Y
vermagic:       3.5.0-39-generic SMP mod_unload modversions 
parm:           nohwcrypt:Disable hardware encryption. (bool)

---

### Post by Sidoney on 2013-10-13
> **tgalati4 said:**
> If you look in the make configuration file, there will be several build settings.


Yes, but i made the kernel config with

yes "" | make oldconfig

So the settings should be the same.


  > **tgalati4 said:**
> 
You can use the *modinfo* command on both to see if there are different parameters that can be set.  Perhaps one has more advanced features than the prebuilt one.


I used modinfo and diff but there are no great changes:

< srcversion:     B68330971444C000132AEFA
---
> srcversion:     A4A99640D66C4F4ED571A55

< vermagic:       3.8.0-31-generic SMP mod_unload modversions 
---
> vermagic:       3.8.13.8 SMP mod_unload modversions 

It's confusing that vegmagig shows 3.8.13.8 because the current kernel is 3.8.0-31-generic and i patched linux_3.8.0.orig.tar.gz (unpacked) with linux_3.8.0-31.46.diff.gz.

---

### Post by Sidoney on 2013-10-13
I also checked the files with strings and diff and could see that the main difference are f=-lines:

> f=p0txf=q0trf=
> 0tlf=
> f=R3t\f=
> 3tVf=r5tPf=
> f=r(
> f=p0
> f=q0
> f=r5
> f=R3
> f=p0
> f=p0
> f=q0
> f=r5
> f=p0L
> f=R3
> f=r5
> f=p0
> f=p0L
> f=p0
> t"f=q0t
> f=q0
> f=p0
> [A\A]A^]
> f=q0
> f=p0
> f=q0t
> f=q0t
> f=p0
> [A\A]A^]
> f=p0
> f=r(
> AVAUATSH
178,206d206
< AWAVAUATSH
< f=p0tyf=q0tsf=
< 0tmf=
< f=R3t]f=
< 3tWf=r5tQf=
< f=r(
< f=p0
< f=q0
< f=r5
< f=R3
< f=p0
< f=p0
< f=q0
< f=r5
< f=p0L
< f=R3
< f=r5
< f=p0
< f=p0L
< f=p0
< f=q0t
< f=q0
< f=p0
< [A\A]A^A_]
< f=q0
< f=p0
< f=q0t
< f=q0t
< f=p0
210,212c210
< f=p0
< f=r(

But i have no idea what this means.

---

### Post by tgalati4 on 2013-10-14
What are the combined sizes of these dependencies?   rt2x00lib,rt2x00usb,crc-itu-t

If the larger module is statically compiled, then it might contain the code of these modules as well.  

As far as the < f=r( stuff, it looks like [Klingon]("http://en.wikipedia.org/wiki/Klingon_language#Phonology").

---

### Post by Sidoney on 2013-10-15
> **tgalati4 said:**
> What are the combined sizes of these dependencies?   rt2x00lib,rt2x00usb,crc-itu-t

If the larger module is statically compiled, then it might contain the code of these modules as well.  


As i posted modinfo and diff shows that the dependencies are the same.
But by googling with the right words i found the answer:  readelf -S rt2800lib.ko
shows that the new module has debug sections!
The reason is that in .config CONFIG_DEBUG_INFO is set to Y although i used
make oldconfig!
I can strip the module via strip --strip-debug *.ko.

---

### Post by tgalati4 on 2013-10-15
I was going to suggest debug symbols, but as you said, using the same configuration should lead to the same build.  However for debug builds there is a separate configuration file!  Good catch.

---

