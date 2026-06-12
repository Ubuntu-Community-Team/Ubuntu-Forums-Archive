---
title: "Source code for shutdown command"
date: 2008-03-11
forum: Programming Talk
---

### Post by ittiam on 2008-03-11
Can anyone let me know where I could i find the source code for the shutdown command?

---

### Post by mssever on 2008-03-11
```
~:$ which shutdown
/sbin/shutdown
~:$ dpkg --search /sbin/shutdown
upstart-compat-sysv: /sbin/shutdown
~:$ apt-cache show upstart-compat-sysv 
Package: upstart-compat-sysv
Priority: required
Section: base
Installed-Size: 260
Maintainer: Scott James Remnant <scott@ubuntu.com>
Architecture: i386
**Source: upstart**
Version: 0.3.8-2
Replaces: upstart (<< 0.3.1-1), sysvinit
Depends: libc6 (>= 2.6-1), upstart (= 0.3.8-2), sysvutils (>= 2.86.ds1-14.1ubuntu11), sysv-rc, initscripts
Filename: pool/main/u/upstart/upstart-compat-sysv_0.3.8-2_i386.deb
Size: 74508
MD5sum: 46d2a6e29a2cbc88647c53dd81827232
SHA1: 659ba7d1d47983d51624dbc14feaa6e8ccd5ddfd
SHA256: a791b224120c1d3b9a2f1a49fbbebab783a052735b0f75ef01833ae7c2a8bfbb
Description: compatibility for System-V-like init
 This package contains compatibility tasks and utilities that emulate
 the behaviour of the original sysvinit package, including runlevels,
 and ensures that the initscripts in /etc/rc*.d are still run.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

``` The answer is in bold (and you can see how I found it).

---

### Post by geraldm on 2008-03-11
In the package sysvinit

Gerald

---

### Post by mssever on 2008-03-11
> **geraldm said:**
> In the package sysvinit
Except for Ubuntu Feisty or later.

---

### Post by ittiam on 2008-03-11
Thanks guys for the reply. One more question that I just posted by creating a new thread...i just want to ask it here

I am trying to compile and have my own kernel appear on the grub menu apart from the current existing kernels...and this what I did

I am following this how to [https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile).

it says after ```
make menuconfig
``` 
and
 ```
make-kpkg --rootcmd fakeroot --initrd --append-to-version=-some-string-here kernel-image kernel-headers
```, 

you would find packages generated in ~/. But i did not find any.

Help on this please?

---

### Post by ittiam on 2008-03-11
> **mssever said:**
> ```
~:$ which shutdown
/sbin/shutdown
~:$ dpkg --search /sbin/shutdown
upstart-compat-sysv: /sbin/shutdown
~:$ apt-cache show upstart-compat-sysv 
Package: upstart-compat-sysv
Priority: required
Section: base
Installed-Size: 260
Maintainer: Scott James Remnant <scott@ubuntu.com>
Architecture: i386
**Source: upstart**
Version: 0.3.8-2
Replaces: upstart (<< 0.3.1-1), sysvinit
Depends: libc6 (>= 2.6-1), upstart (= 0.3.8-2), sysvutils (>= 2.86.ds1-14.1ubuntu11), sysv-rc, initscripts
Filename: pool/main/u/upstart/upstart-compat-sysv_0.3.8-2_i386.deb
Size: 74508
MD5sum: 46d2a6e29a2cbc88647c53dd81827232
SHA1: 659ba7d1d47983d51624dbc14feaa6e8ccd5ddfd
SHA256: a791b224120c1d3b9a2f1a49fbbebab783a052735b0f75ef01833ae7c2a8bfbb
Description: compatibility for System-V-like init
 This package contains compatibility tasks and utilities that emulate
 the behaviour of the original sysvinit package, including runlevels,
 and ensures that the initscripts in /etc/rc*.d are still run.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

``` The answer is in bold (and you can see how I found it).

Err, sorry to bother but still did not get as how i could get the source file after this.

---

### Post by mssever on 2008-03-12
> **ittiam said:**
> Err, sorry to bother but still did not get as how i could get the source file after this.

Sorry. I assumed that you knew how to get source packages. The line in bold shows that the source package is called upstart. So, ```
~:$ mkdir upstart-source
~:$ cd upstart-source/
~/upstart-source:$ apt-get source upstart
```

Of course, you'll need to have the proper deb-src lines in your /etc/apt/sources.list (or enable them from Synaptic).

---

### Post by Whiffle on 2008-03-12
> **ittiam said:**
> Thanks guys for the reply. One more question that I just posted by creating a new thread...i just want to ask it here

I am trying to compile and have my own kernel appear on the grub menu apart from the current existing kernels...and this what I did

I am following this how to [https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile).

it says after ```
make menuconfig
``` 
and
 ```
make-kpkg --rootcmd fakeroot --initrd --append-to-version=-some-string-here kernel-image kernel-headers
```, 

you would find packages generated in ~/. But i did not find any.

Help on this please?

I think that howto might be off, they usually are put in /usr/src

---

### Post by linwhwylb on 2010-09-11
Well! it helps me.

---

