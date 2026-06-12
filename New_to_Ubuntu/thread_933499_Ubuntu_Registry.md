---
title: "Ubuntu Registry?"
date: 2008-09-29
forum: New to Ubuntu
---

### Post by JBA2337 on 2008-09-29
Does Ubuntu have a Registry, similar to Windows, or anything like that?

If not, how does Ubuntu keep up with where various programs and files are located?

JBA2337

---

### Post by ronnielsen1 on 2008-09-29
No registry
>  The first thing that most new users shifting from Windows will find
confusing is navigating the Linux filesystem. The Linux filesystem 
does things a lot more differently than the Windows filesystem.
This article explains the differences and takes you through the 
layout of the Linux filesystem.  For starters, there is only a single hierarchal directory structure.
Everything starts from the root directory, represented by '/', and then
expands into sub-directories. Where DOS/Windows had various partitions and
then directories under those partitions, Linux places all the partitions
under the root directory by 'mounting' them under specific directories.
Closest to root under Windows would be c:.
Under Windows, the various partitions are detected at boot and assigned a
drive letter. Under Linux, unless you mount a partition or a device, the
system does not know of the existence of that partition or device. This
might not seem to be the easiest way to provide access to your partitions
or devices but it offers great flexibility.
This kind of layout, known as the unified filesystem, does offer several
advantages over the approach that Windows uses. Let's take the example of
the /usr directory. This directory off the root directory contains most of
the system executables. With the Linux filesystem, you can choose to mount
it off another partition or even off another machine over the network. The
underlying system will not know the difference because /usr appears to be
a local directory that is part of the local directory structure! How many
times have you wished to move around executables and data under Windows,
only to run into registry and system errors? Try moving c:windowssystem
to another partition or drive.


[http://www.freeos.com/articles/3102/](http://www.freeos.com/articles/3102/)

---

### Post by LowSky on 2008-09-29
[http://www.linuxforums.org/forum/misc/34185-linux-equivalent-windows-registry.html](http://www.linuxforums.org/forum/misc/34185-linux-equivalent-windows-registry.html)

---

### Post by t0p on 2008-09-29
Ubuntu does not have a registry.  Linux is utterly unlike windows in this respect.  Most applications are in the directories /usr/bin and /usr/sbin.  Configuration files are located in the /etc directory and in the user's home directory.

---

### Post by jonobr on 2008-09-29
Hello


Recommend becoming fmailiar with the Linux/Ubuntu file structure.
There is nothing similar to the windows operating system registry \



[http://www.ubuntugeek.com/linux-or-ubuntu-directory-structure.html](http://www.ubuntugeek.com/linux-or-ubuntu-directory-structure.html)

---

### Post by DrMega on 2008-09-29
> **JBA2337 said:**
> Does Ubuntu have a Registry, similar to Windows, or anything like that?

If not, how does Ubuntu keep up with where various programs and files are located?

JBA2337

It manages fine in much the same way as all OS's did before Windows 95 came along and lumped all your system data into one huge ever growing badly organised unreadable mess:)

---

