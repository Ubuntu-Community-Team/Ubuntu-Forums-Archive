---
title: "where is the kernel source?"
date: 2005-01-22
forum: Repositories &amp; Backports
---

### Post by jerome bettis on 2005-01-22
i'm running 2.6.8.1-4-386 and apt-cache search kernel-source doesn't find anything for that version.  any ideas where it is?

oh and any help on how to compile it would be appreciated as well.

i tried it a few days ago and something went terribly wrong.  i'm blaming either a) I used the wrong version, b) i deleted something necessary in the config, c) i can't follow directions.

i'd like to try it again, but i need to be sure i'm getting the correct source before i get started.

thanks

---

### Post by poofyhairguy on 2005-01-22
[QUOTE=jerome bettis]i'm running 2.6.8.1-4-386 and apt-cache search kernel-source doesn't find anything for that version.  any ideas where it is?

oh and any help on how to compile it would be appreciated as well.

i tried it a few days ago and something went terribly wrong.  i'm blaming either a) I used the wrong version, b) i deleted something necessary in the config, c) i can't follow directions.

i'd like to try it again, but i need to be sure i'm getting the correct source before i get started.

thanks[/QUOTE]

It might not be there. Look in synaptic and see if it is installed.

---

### Post by Randabis on 2005-01-22
The kernel source package is not specific to any of the linux kernel images (correct me if I'm wrong). When you install a kernel source package, it places the source in your /usr/src directory as a tar.bz2 file. You'll have to extract this file before you'll be able to get started configuring and compiling your kernel.

Here's a guide to compiling debian kernels.
[http://www.desktop-linux.net/debkernel.htm](http://www.desktop-linux.net/debkernel.htm)

---

### Post by jerome bettis on 2005-01-22
[QUOTE=Randabis]The kernel source package is not specific to any of the linux kernel images (correct me if I'm wrong). When you install a kernel source package, it places the source in your /usr/src directory as a tar.bz2 file. You'll have to extract this file before you'll be able to get started configuring and compiling your kernel.

Here's a guide to compiling debian kernels.
[http://www.desktop-linux.net/debkernel.htm](http://www.desktop-linux.net/debkernel.htm)[/QUOTE]
 it HAS to be there.  but searching apt-cache for kernel-source (what it is when i had debian) this is what i get:

kernel-source-2.2.25 - Linux kernel source for version 2.2.25
kernel-source-2.4.24 - Linux kernel source for version 2.4.24 with Debian patches
kernel-source-2.4.25 - Linux kernel source for version 2.4.25 with Debian patches
kernel-source-2.4.26 - Linux kernel source for version 2.4.26 with Debian patches
kernel-source-2.6.5 - Linux kernel source for version 2.6.5 with Debian patches
kernel-source-2.6.6 - Linux kernel source for version 2.6.6 with Debian patches
kernel-source-2.6.7 - Linux kernel source for version 2.6.7 with Debian patches

i'm using a 2.6.8 right now - where is the source for the kernel that comes with ubuntu???  i guess i could downgrade to 2.6.7 but there's no way i should have to do that.  why isn't the source for this kernel i'm using now in the repository?  weird ...  i run apt-get update & upgrade & dist-upgrade daily.

i extracted the tar.bz2 file and ran the commands in the readme file when i installed the source for the 2.6.7 version last time and i got a kernel panic.  i did delete a bunch of "useless" stuff ... maybe i got a little excited.

the only part that kinda confused me was at the very end when it was done.  the file it said to add to grub's menu.lst file for the kernel didn't exist.  but there was one in a different directory.  i put that in the boot file and got a kernel panic.

thanks for that link.

---

### Post by daniels on 2005-01-22
linux-source-2.6.8.1

---

### Post by jerome bettis on 2005-01-22
[QUOTE=daniels]linux-source-2.6.8.1[/QUOTE]


THANK YOU 8-)

---

