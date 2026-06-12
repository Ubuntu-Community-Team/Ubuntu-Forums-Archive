---
title: "Reformat Partition"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by Worp8d on 2008-04-29
Hi,

Sorry if this has been posted a million times before but I just can't find the answer.

I have two ext3 partitions on my HDD, one for 8.04 and the other for 7.10.  I want to reformat the 7.10 partition as NTFS so I can share on my (lame) flatmate's network.  How do I do this?  I don't want to re-install anything but there's no command to just let me do this.

Also, once this is done how do I remove the 7.10 options from the boot menu?

(P.S. 8.04 is freakin' awesome)

---

### Post by marufaberlin on 2008-04-29
1. Get gparted.
2. edit /boot/grub/menu.lst

---

### Post by Michael.Godawski on 2008-04-29
If you have a Live CD boot into the Live session. There you can use Gparted to resize or delete or whatever you want to do with the existing partitions.

---

### Post by jeffimperial on 2008-04-29
> **marufaberlin said:**
> 1. Get gparted.
2. edit /boot/grub/menu.lst
> 2. edit /boot/grub/menu.lst

Probably a stupid question, but how exactly should one go about this?

I have the exact same "problem" as Worp8d.

I've been able to do this much, though:
1. Got GParted, installed and working.
2. I created two tasks for GParted
     First, move the previously installed 7.10 to the very end of the bar.
       "Move /dev/sdb1 to the right and shrink it from 38.28 GiB to 12.20 GiB
     Second, I created a new partition for the unallocated space it left.
       "Create Primary Partition #1 (fat32, 26.08 GiB to 26.08 GiB) on /dev/sdb

---

### Post by Boyohazard on 2008-04-29
```
gksudo gedit /boot/grub/menu.lst
```
I think is the command you are looking for.

Then locate the entries you no longer need and comment them out (place # at beginning of line)

---

### Post by jeffimperial on 2008-04-29
Do I still need to do this if I intend to install Windows XP on that Fat32 partition?

Alternatively, my menu.list has the following presently:
> 
title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=dcb1608d-1a5a-4183-8cc9-cc4b0c43c0de ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=dcb1608d-1a5a-4183-8cc9-cc4b0c43c0de ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 7.10, kernel 2.6.22-14-generic (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=b4d832e7-3339-4a2a-bd58-24eb969fa323 ro quiet splash 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode) (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=b4d832e7-3339-4a2a-bd58-24eb969fa323 ro single 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 7.10, memtest86+ (on /dev/sdb1)
root		(hd1,0)
kernel		/boot/memtest86+.bin  
savedefault
boot


Should I just insert the following at the end of menu.list, much like adding repositories on that other file (which I can no longer name off-hand at this moment)?

> # title		Windows XP
# root		(hd[COLOR="Red"]1[/COLOR],0)
# makeactive
# chainloader	+1
#
# title		[COLOR="Red"]Windows[/COLOR]
# root		(hd[COLOR="Red"]1[/COLOR],[COLOR="Red"]0[/COLOR])
# kernel	/vmlinuz root=/dev/hda2 ro
#

I'm really sorry for being such a simian..

---

### Post by marufaberlin on 2008-04-30
No, that's not what you should insert. First of all, everything that begins with a # is a comment and is ignored (well, there are some exceptions). The, the windows kernel doesn't need to be loaded using "kernel". Then, as I don't know your hard disk config, I can't really tell if the hard drive is at (hd0,1)

---

### Post by jeffimperial on 2008-04-30
> everything that begins with a # is a comment
Oh, much like PHP. Anyways, I'll try again withour the comments.

Here's what I did.
1. In the beginning, I had two HDs, no partitions on each whatsoever. In the first HD, I had clean-installed Hardy. On the second, I had Gutsy.
2. I removed the Hardy HD and set the Gutsy HD as Master.
3. I clean-installed Windows XP on that HD (2nd HD set now as primary)
4. I set the Hardy back in as Master, the 2nd HD (With XP now) as slave. Again, no partitions whatsoever (except the defaults that Hardy puts in, ie swap, filesys, etc?)
5. When I booted up, grub was still the boot manager, but no XP.

> I can't really tell if the hard drive is at (hd0,1)
Should that answer your question?

---

### Post by marufaberlin on 2008-05-05
have a look at this:

[http://ubuntuforums.org/showthread.php?t=761319](http://ubuntuforums.org/showthread.php?t=761319)

---

