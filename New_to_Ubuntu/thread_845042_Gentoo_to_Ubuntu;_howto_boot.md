---
title: "Gentoo to Ubuntu; howto boot?"
date: 2008-06-30
forum: New to Ubuntu
---

### Post by lugong on 2008-06-30
Hello, I am an inexperienced opensource end-user.  After having repeated problems with Gentoo, I decided to install Ubuntu, from a live CD, in a partition on a separate harddrive from my Gentoo install.  As far as I can tell the installation went well, however it is not recognised by Grub upon startup.  :KS

Could I please be directed to relevant docs?
I have had a look at threads on Grub, but there is no problem - apart from a gap in my knowledge - keeping me from getting this right.
I don't know how to remove Gentoo from my system in order to replace it with Ubuntu.

If anyone can help,
Thankyou.

---

### Post by jw5801 on 2008-06-30
Use the installer to completely wipe the hard drive and install Ubuntu, it'll automatically configure and install grub.

---

### Post by lugong on 2008-06-30
Sorry, that is too dramatic, I would lose a lot of data (that I am unable to shuffle).
I thought perhaps there would be a way to clean a harddrive of an operating system, especially if I had another operating system, already installed, to take its place.

As I said earlier, this is less of a technical problem then it is a request for information regarding grub, gentoo, and ubuntu.

---

### Post by jw5801 on 2008-06-30
If you've installed Ubuntu to a different hard drive, then either tell your bios to boot from that harddrive (Ubuntu will have installed it's grub to the mbr of that harddrive, it should have automagically included an entry for your Gentoo install as well), or else you'll need to add an entry for Ubuntu to /boot/grub/grub.conf (which is synonymous to /boot/grub/menu.lst in Debian based systems). For that I point you to the [Gentoo Handbook](http://www.gentoo.org/doc/en/handbook/handbook-amd64.xml?part=1&chap=10). You'll need an entry that points to the second harddrive, and the partition Ubuntu is installed to, so (hd1,0) or similar. Then you'll need to point to it's kernel and initramdisk. Alternatively, mount the Ubuntu filesystem and copy the stanza it uses to boot.

---

### Post by louieb on 2008-06-30
>  I don't know how to remove Gentoo from my system in order to replace it with Ubuntu.
Time to learn about GRUB. 
Reboot the computer and when you get the GRUB menu **press c** to get to the **grub>** prompt and issue the following command.
```
find /boot/grub/menu.lst 
```

Its going to return something like** (hd0,0) **it may return a couple of them one for Ubuntu and one for Gentoo.  
Figure out which one points to Ubuntu. then run the command
```
root (hd#,#)
```
where **#,# **are the numbers corresponding to you Ubuntu partition.
Then run```
 setup (hd0)
```
and ```
quit
``` 

If you have done it right reboot the computer and  the Ubuntu menu should come up.   

Everything I ever needed to know about GRUB can be found here [IDBS GRUB Page]("http://users.bigpond.net.au/hermanzone/p15.htm")

---

