---
title: "Ok, I want to install multiple distros.  A few questions..."
date: 2007-10-05
forum: Other OS Talk
---

### Post by rudeboyskunk on 2007-10-05
Ok, I am running Feisty Fawn right now.  I had to do a clean install because I accidentally formatted the entire hard drive yesterday.  I have two hard drives, one is 80GB (hda), the other is 14GB (hdb).

Feisty is installed on a 26GB partition on hda1.  I have my swap on hda2 (1GB).  I want to install Solaris 10 on an hda3 and Fedora 8 (when it comes out) on hda4.  I want to install Gentoo Linux on hdb.

How do I install these other operating systems without them all installing their own version of GRUB and overwriting the GRUB file on Ubuntu?  Is there some way they might just automatically add themselves to /boot/grub/menu.lst?  Or is that impossible?  Will they install their own GRUB file but automatically read that I have Ubuntu already installed, and therefore add it to /boot/grub/menu.lst?  I've been using Linux for four years now, but I still don't understand how to edit GRUB or anything to do with the MBR.

I realize installing Gentoo will be easy, because I will just tell it to install to hdb (and point swap at hda2).  Fedora should be easy, because I can just tell it that swap is hda2 and give it its own 26GB partition.  Solaris is the tricky one.  I know I should be able to stick it on its own partition, but I'm afraid it will try to format all of hda.  Also, can Solaris use the same swap as the Linux systems?

Any answers to any of these questions would be helpful.  Other posts on the forum and answers on the internet are sometimes confusing and not specific to my problem.

---

### Post by rsambuca on 2007-10-05
The easiest way to install the distros and keep your original Ubuntu grubloader is by chainloading the grubs.  Basically, you point the grub stage 1 to the Ubuntu menu.lst, and then you can select your OS's from there.  For the other distros, you chainload to the next distro's menu.lst.  The benefit of this system is that when a distro updates its kernel and grub menu.lst, you don't ever have to manually edit the grub loaders (except the initial setup).  The minor downside is that to get to a distro other than Ubuntu, you go from one grub to another.

To set this up, you would install Ubuntu as normal, and have the grub installed to the mbr.  When you install the next distro, the key is to instruct grub to install to the /boot partition of the current distro, and not to the mbr.  Then you add a chainloader to the bottom of your first grub eg:

title  gentoo
root (hd1,1)
chainloader +1

---

### Post by rsambuca on 2007-10-05
Here is my /boot/grub/menu.lst as an example (I omitted the top stuff).  As you will see, I have Ubuntu as my main distro, and then I have chainloaders for 32bit Ubuntu, Windows Vista/XP, gentoo, debian, and sabayon```
## ## End Default Options ##

title           Ubuntu, kernel 2.6.20-16-generic
root            (hd2,4)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=024af315-92dd-48fa-9495-7d3d359459f6 ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

#title          Ubuntu, kernel 2.6.20-16-generic (recovery mode)
#root           (hd2,4)
#kernel         /boot/vmlinuz-2.6.20-16-generic root=UUID=024af315-92dd-48fa-9495-7d3d359459f6 ro single
#initrd         /boot/initrd.img-2.6.20-16-generic

#title          Ubuntu, memtest86+
#root           (hd2,4)
#kernel         /boot/memtest86+.bin
#quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Windows Vista/Longhorn (loader)
root            (hd0,0)
makeactive
chainloader     +1

title           Ubuntu 32-bit
root            (hd2,5)
chainloader     +1


title           Gentoo
# kernel path-to-kernel root=rootdevice kernelarguments
root            (hd2,6)
chainloader     +1


title           Debian
root            (hd2,7)
chainloader     +1

title           Sabayon Linux
root            (hd2,8)
chainloader     +1

```

---

### Post by maybeway36 on 2007-10-05
Just install GRUB in the other distros to the partition instead of the MBR. For example, if you had Debian on hda2, you would add:
```
title Debian
chainloader (hd0,1)+1
boot
```or something similar.

---

### Post by rsambuca on 2007-10-05
> **maybeway36 said:**
> Just install GRUB in the other distros to the partition instead of the MBR. For example, if you had Debian on hda2, you would add:
```
title Debian
chainloader (hd0,1)+1
boot
```or something similar.

I have never seen that format.  Have you actually tried it, or are you guessing?

---

### Post by RAV TUX on 2007-10-05
> **rudeboyskunk said:**
> Ok, I am running Feisty Fawn right now.  I had to do a clean install because I accidentally formatted the entire hard drive yesterday.  I have two hard drives, one is 80GB (hda), the other is 14GB (hdb).

Feisty is installed on a 26GB partition on hda1.  I have my swap on hda2 (1GB).  I want to install Solaris 10 on an hda3 and Fedora 8 (when it comes out) on hda4.  I want to install Gentoo Linux on hdb.

How do I install these other operating systems without them all installing their own version of GRUB and overwriting the GRUB file on Ubuntu?  Is there some way they might just automatically add themselves to /boot/grub/menu.lst?  Or is that impossible?  Will they install their own GRUB file but automatically read that I have Ubuntu already installed, and therefore add it to /boot/grub/menu.lst?  I've been using Linux for four years now, but I still don't understand how to edit GRUB or anything to do with the MBR.

I realize installing Gentoo will be easy, because I will just tell it to install to hdb (and point swap at hda2).  Fedora should be easy, because I can just tell it that swap is hda2 and give it its own 26GB partition.  Solaris is the tricky one.  I know I should be able to stick it on its own partition, but I'm afraid it will try to format all of hda.  Also, can Solaris use the same swap as the Linux systems?

Any answers to any of these questions would be helpful.  Other posts on the forum and answers on the internet are sometimes confusing and not specific to my problem.

you should make a partition for Haiku and install that also.

---

### Post by rudeboyskunk on 2007-10-05
Ok, I first want to thank yall for the help.

But, I always read that, "install GRUB to the MBR" or "when installing the other distros just install GRUB to the Ubuntu partition."  How?  Whenever I install an OS, I don't ever recall it ever asking where to install GRUB.  Or does it and I just go through it without thinking?

---

### Post by rudeboyskunk on 2007-10-05
Or is there a simpler way?  Can I just, say, install Fedora and then on the Fedora menu.lst write in an entry for Ubuntu?

---

### Post by RAV TUX on 2007-10-05
> **rudeboyskunk said:**
> Ok, I first want to thank yall for the help.

But, I always read that, "install GRUB to the MBR" or "when installing the other distros just install GRUB to the Ubuntu partition."  How?  Whenever I install an OS, I don't ever recall it ever asking where to install GRUB.  Or does it and I just go through it without thinking?
depends on the OS. I know Elive will ask you.

---

### Post by rsambuca on 2007-10-05
> **rudeboyskunk said:**
> Ok, I first want to thank yall for the help.

But, I always read that, "install GRUB to the MBR" or "when installing the other distros just install GRUB to the Ubuntu partition."  How?  Whenever I install an OS, I don't ever recall it ever asking where to install GRUB.  Or does it and I just go through it without thinking?

Ubuntu asks, Gentoo I did manually, and I can't speak for the others you will be installing.  Even if you make a mistake and accidentally install one of the latter to the mbr, it is a very easy fix, so don't worry about it.

---

### Post by rsambuca on 2007-10-05
> **rudeboyskunk said:**
> Or is there a simpler way?  Can I just, say, install Fedora and then on the Fedora menu.lst write in an entry for Ubuntu?

I honestly think the method I suggested is the easiest.  You only modify the grub menu.lst once.  If you do it manually like you suggest, then you will have to do it manually everytime one of the distro's patches its kernel.

---

### Post by kellemes on 2007-10-05
Another method of booting another distro is using the following line in menu.lst

```
# Debian
title Debian
configfile   (hd*,*)/grub/menu.lst
```

This way you simply point to the menu.lst of the other distro, you can make nested bootmenu's like this.. Works great.
When Debian edits it's menu.lst for whatever reason I'll be fine, never have to edit it, unless I'm having my own reasons to do so.

You just need to think from what distro you want to manage your bootloader.. I always have Windows and 2 distro's, and I manage Grub from dist-1 and use this way of pointing to the menu.lst of dist-2.. or if dist-2 uses LILO I'll install it in the root-partition of dist-2 and chainload like so..

```
# Zenwalk
title Zenwalk
root (hd*,*)
chainloader +1
```

---

### Post by rudeboyskunk on 2007-10-05
> **rsambuca said:**
> The easiest way to install the distros and keep your original Ubuntu grubloader is by chainloading the grubs.  Basically, you point the grub stage 1 to the Ubuntu menu.lst, and then you can select your OS's from there.  For the other distros, you chainload to the next distro's menu.lst.  The benefit of this system is that when a distro updates its kernel and grub menu.lst, you don't ever have to manually edit the grub loaders (except the initial setup).  The minor downside is that to get to a distro other than Ubuntu, you go from one grub to another.

To set this up, you would install Ubuntu as normal, and have the grub installed to the mbr.  When you install the next distro, the key is to instruct grub to install to the /boot partition of the current distro, and not to the mbr.  Then you add a chainloader to the bottom of your first grub eg:

title  gentoo
root (hd1,1)
chainloader +1


Okay, then I guess the question I have is:  Is GRUB already installed on the MBR?  I know that sounds like a dumb question, but my menu.lst is located in Ubuntu's /boot/grub.  And how will I know if one is (hd2,5) or (hd3,4) or something like that?

---

### Post by rsambuca on 2007-10-05
> **rudeboyskunk said:**
> Okay, then I guess the question I have is:  Is GRUB already installed on the MBR?  I know that sounds like a dumb question, but my menu.lst is located in Ubuntu's /boot/grub.  And how will I know if one is (hd2,5) or (hd3,4) or something like that?

If you turn on your machine and you get the grub menu, then yes, it is installed to the mbr.  As far as the numbering system goes, the hd#,# - the first number is the hard drive number (starting at 0 instead of 1), and the second number is the partition (again starting at 0).  Thus if you have two drives, the first partition on the second drive would be hd1,0

---

### Post by rudeboyskunk on 2007-10-05
Ok, I want to again thank everybody.  Four years after I began using Linux, and I learned more today about GRUB and the MBR than I have in those four years.

If anybody is interested in doing a dual-boot with Solaris and Ubuntu (or Solaris and any other Linux distro), this thread worked great: [http://ubuntuforums.org/showthread.php?t=113743](http://ubuntuforums.org/showthread.php?t=113743).  The link in the second post was very helpful as well.

---

