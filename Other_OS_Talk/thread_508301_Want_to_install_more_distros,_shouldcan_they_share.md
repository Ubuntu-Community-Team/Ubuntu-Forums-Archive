---
title: "Want to install more distros, should/can they share /boot?"
date: 2007-07-24
forum: Other OS Talk
---

### Post by Laplace's Daemon on 2007-07-24
So I've found myself in the situation of having way more hard drive space than I know what to do with, so I want to put it to good use by trying out different distros (other than using Red Hat at work, Ubuntu is my first Linux).  My concern before I start (other than finding a good way to make my data accessible to all the distros, but there are lots of threads about that) is how to make them play nice during bootup.  Will new installs completely erase my menu.lst, or will they add on to it automatically?  Are there ways to keep GRUB from overwritting the MBR on my second hard drive (where I plan to put the test distros)?

---

### Post by tommcd on 2007-07-24
I think most distros give you a choice of where to install grub (or lilo). For example, on my laptop I boot ubuntu, zenwalk, and debian. Ubuntu's grub is on the MBR. For zenwalk I chose not to install lilo (I'm clueless about lilo, but I know grub pretty well) and I just added zenwalk to ubuntu's grub. For debian I chose to install debian's grub to it's root partition, and I added a configfile boot entry to ubuntu's grub to boot debian like this:
[http://users.bigpond.net.au/hermanzone/p15.htm#1._Configfile](http://users.bigpond.net.au/hermanzone/p15.htm#1._Configfile)
I don't have a separate /boot partition though. You should have the option to not overwrite the MBR when you install a new distro.

---

### Post by pistcivet on 2007-07-24
I let the first distro I install place grub on the MBR,
and direct each subsequent distro to install grub (or lilo) on the boot sector of their partition.
Then I just chainload whichever distro I want to boot. So the end of my menu.lst look like this:

title	chainload hda6
root	(hd0,5)
chainloader	+1

title	chainload hda9
root	(hd0,8)
chainloader	+1

title	chainload hdb1
root	(hd1,0)
chainloader	+1

I have Ubuntu 7.04, Foresight 1.3.1, Absolute 12 and Dreamlinux 2.2 MMGL

"title" can be anything you want of course.
This method is also outlined in tommcd's excellent link provided above.

---

