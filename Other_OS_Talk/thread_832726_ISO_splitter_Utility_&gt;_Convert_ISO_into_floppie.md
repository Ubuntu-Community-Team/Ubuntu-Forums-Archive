---
title: "ISO splitter Utility? &gt; Convert ISO into floppies ?"
date: 2008-06-18
forum: Other OS Talk
---

### Post by Midwest-Linux on 2008-06-18
ISO splitter > Convert ISO into floppies ?

 I have two ways to approach this. I want to install a light weight distro onto a laptop that only takes floppies. How would I go about taking a Linux ISO, splitting it down into 1.44 MB segments so that I can install it on the laptop using floppies? (I have a lot a floppies) Is there some kind of Utility available in Windows or Linux?
Thanks

---

### Post by saulgoode on 2008-06-18
You need a bootable floppy which should be created separately from the rest of your installation; and will most likely need a second disk to provide more functionality (a single floppy is barely sufficient to hold the kernel+shell).

A typical arrangement is to have the boot floppy prompt for a second floppy holding the /usr tree, which gets loaded into a ramdisk. Once you have this system up and running, you can load the rest of your system from floppies.

If your entire system is in one .iso file, you can use the GNU 'split' command to split this up into floppy-sized parts:

***split -b 1440000 filename.iso PREFIX***

Each of the individual files saved ('PREFIXaa', 'PREFIXab', etc) can be written to a floppy and loaded on your target machine. Once loaded, you can join them back together using the 'cat' command:

***cat PREFIX* >filename.iso***

You would then mount this .iso as a loop for further installation.

---

### Post by wormser on 2008-06-18
It would be easier to use a Net Install.  You create one floppy and download the rest.  
[http://archive.ubuntu.com/ubuntu/dists/hardy/main/installer-i386/current/images](http://archive.ubuntu.com/ubuntu/dists/hardy/main/installer-i386/current/images) /netboot/

---

### Post by mips on 2008-06-18
> **wormser said:**
> It would be easier to use a Net Install.  You create one floppy and download the rest.  
[http://archive.ubuntu.com/ubuntu/dists/hardy/main/installer-i386/current/images](http://archive.ubuntu.com/ubuntu/dists/hardy/main/installer-i386/current/images) /netboot/

That would be ideal assuming he has a network adapter.

---

### Post by Midwest-Linux on 2008-06-18
> **mips said:**
> That would be ideal assuming he has a network adapter.


 The problem is that in the bios there are two ways to boot from, either Floppy or Hard drive. One can do a net install without having other options? There is no OS on the hard drive either. So I need to partition the hard drive first.

---

### Post by wormser on 2008-06-18
> **Midwest-Linux said:**
> The problem is that in the bios there are two ways to boot from, either Floppy or Hard drive. One can do a net install without having other options? There is no OS on the hard drive either. So I need to partition the hard drive first.

With a Net Install you use a floppy to boot from.  Then select the packages you want.  My first Linux install was a Debian Net Install.  The following link is for a CD but if you look around you can find one for a floppy or use the technique you were asking about here.  That way would use less floppys. 

[http://www.debian.org/CD/netinst/](http://www.debian.org/CD/netinst/)

---

### Post by jrusso2 on 2008-06-19
I still remember when all Linux installs were off floppys.  It was a royal pain.

Net Install is the way to go if you can find or make a network boot floppy.

---

### Post by zmjjmz on 2008-06-19
In the same situation as you, what I'm doing is taking a Zip drive (The laptop currently has the 2 floppy BasicLinux on it) and loading the DSL image onto another partition, then booting from that using the DSL boot floppy, and installing to the main partition.

---

### Post by mips on 2008-06-20
> **Midwest-Linux said:**
> The problem is that in the bios there are two ways to boot from, either Floppy or Hard drive. One can do a net install without having other options? There is no OS on the hard drive either. So I need to partition the hard drive first.

You can do a net install off a bootable floppy.

---

### Post by maybeway36 on 2008-06-21
You could partition it with FDISK and put FreeDOS on there, if that helps.

---

### Post by atomkarinca on 2008-06-21
The new [Acetoneiso2]("http://www.acetoneiso.netsons.org/") can now split images. You can try that.

---

