---
title: "general linux question about distro/kernel"
date: 2007-10-14
forum: Programming Talk
---

### Post by skunkrecords on 2007-10-14
Lately I've been looking into linux. While researching the linux kernel, I had a tough time finding the relationship between the kernel and the distro itself. Does the distro use the kernel as an API after it boots? Is there an actual function in the kernel that loads the distro?
I understand the basic function of the kernel and how it interacts with the hardware, but where exactly the distro and its gui come in, im confused
If you could point me to some good resources that address this issue, that would be great. Thanks for the help in advance!

-Ruddy

---

### Post by NotRoot:-) on 2007-10-14
[http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)  is the Master Kernel Thread.  I followed its steps today to compile a customized Linux Kernel.  I am using Ubuntu Release 7.04 with the  latest stable version of the Linux kernel is:  	2.6.23.1
[http://kernel.org/](http://kernel.org/)
uname -a
Linux YRUHere 2.6.23.1 #1 SMP Sun Oct 14 17:28:13 MDT 2007 i686 GNU/Linux

[http://distrowatch.com/table.php?distribution=ubuntu](http://distrowatch.com/table.php?distribution=ubuntu)  will show you the default applications and kernel with each Ubuntu release.

The cool thing about open source software is  you can do whatever you want to.   Today was my first day compiling a kernel.  This forum and its contributors made that easy.

---

### Post by CptPicard on 2007-10-14
The "distribution" is just a big bunch of applications bundled together that all run on top of the kernel, while the kernel manages the system's resources in general and works as the general traffic cop that keeps processes from stepping on each others' toes.

Yes, the kernel does have an API for userspace applications to call -- those are the system calls. The ones you'll meet first while programming are the IO ones that print to and read from console and files.

As to what happens during boot... first the kernel gets loaded. Then it starts an initial process that then spawns all the rest of the processes during boot, finally giving you the shell, your GUI, etc...

---

### Post by pmasiar on 2007-10-15
maybe you confuse "Desktop" and "distribution". As CptPicard said, distro is just bunch of programs. Or, to better visualize, it is bunch of developers who picked specific version of user programs, package manager, kernel, libraries, desktop, graphics, icons, documentation etc (to make sure that kernel, libraries and programs work together), for some specific goal. 

Most distros have special goal, try to select only part of available programs with some goal, like: distro for company servers (Redhat/Fedora, Novel/SUSE, Mepis), distro for schools (Edubuntu), for people who want to compile everything (gentoo: to tweak setting and squeeze little more performance out of hardware, or for fun), distro for old hardware (xubuntu, DamnSmallLinux), distro for sysadmins to rescue borked PCs (SystemRescue), Kubuntu is ubuntu with KDE instead of Gnome desktop, etc. Check distrowatch website for links to hundreds of distros.

Distro developers possibly change some settings, and maintain this all over time, upgrading **in sync** all versions (kernel, libraries, apps and docs). It means also security patches, backporting features from new versions of software to versions they settled for, creating original graphic themes, helping to users in forums and mailing lists, etc.

Distro is more social organization than piece of code. The code which paint what you see on the screen in "Desktop". Which distro do you use?

---

