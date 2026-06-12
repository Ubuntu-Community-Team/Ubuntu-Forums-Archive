---
title: "Installing ndiswrapper and linux-2.6.17 on Ubuntu"
date: 2006-08-29
forum: Packaging and Compiling Programs
---

### Post by JulietBravo on 2006-08-29
:confused: Installing ndiswrapper and linux-2.6.17 on Ubuntu ]:confused: 

--------------------------------------------------------------------------------

I am trying to install ndiwrapper and the linux-2.6.17 kernel, but I have encountered some errors. 

Firstly, my current kernel is vmlinuz-2.6.15-26-386.  I need some help in completely removing this kernel and installing linux-2.6.17.  Is this posible and if so how do I go about achieving it.

Secondly, while installing ndiswrapper to enabe wireless access, although I have executed all th codes successfully(with no errors), when I get to the point where I run "modprobe ndiswrapper" I get the following error:

FATAL: Could not open '/lib/modules/2.6.15-26-386/misc/ndiswrapper.ko': No such file or directory

I believe this is because I built the link to the kernel header to point to the linux-2.6.17 kernel instead of the vmlinuz-2.6.15.386 kernel that already existed a follows:
ln -s /usr/src/linux-2.6.17 /lib/modules/2.6.17/build

I am not sure I am making sense here because I am new too all this.  Hence the reason why I am asking for help on how to completely remove the vmlinuz-2.6.15.386 kernel and replace it with linux-2.6.17.  Also how do I remove a link such as the one I have built above. 

Can someone please please please HELP me out here ](*,) . Many thanks :D .

---

### Post by mlind on 2006-08-30
To install 2.6.17 kernel for Dapper, you need to compile it manually. Dapper is "freezed" to use 2.6.15 kernel's (which means that codebase stays 2.6.15, but necessary fixes may be backported from newer upsteam kernels).

If you really need a 2.6.17 kernel (if there's a good reason for it), then search HOWTO forums. There's at least 3 good threads which explain how to compile a vanilla (custom) kernel for your taste.

To compile a ndiswrapper for 2.6.17 kernel, you need to have its headers installed (see the kernel threads on HOWTO forums). You can modprobe (include modules to running kernel) only from the kernel you are currently running.

Don't remove earlier kernel unless you're absolutely sure that newer one works..

---

