---
title: "Startup freezes after GRUB selection"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by Shlonster on 2008-08-28
So I've only been running Ubuntu about a week, but when I installed it I completely destroyed my XP install. I didn't care, at the time.  Right now, I'm trying to dual-boot XP and Hardy 8.04, and I am a little bit stuck.

When I turn on the computer, the GRUB menu comes up, and it lists like 3 different Ubuntu kernels (a memtest, a sort of safe mode one, and the regular one) and it also shows my XP install -- which I can boot to. However, when I select the normal Ubuntu kernel, GRUB disappears, it says to me "Starting... Please wait..." and nothing ever happens.  It seems like GRUB is looking to boot Ubuntu in the wrong place, but I dunno how to fix that if that is the case...

I have ubuntu and XP installed on separate IDE drives, both of which are 40 gigs and both of which work.  I know it would be helpful if I could post the device.map, the /boot/grub/menu.lst, and sudo fdisk -l, but I can't get on that computer right now.  I will post them here as soon as I can, but I thought I'd post this in case someone magically knows the answer.  Thanks in advance.

EDIT -------

Device.map

(hd0)   /dev/sda
(hd1)   /dev/sdb

(I don't know how to embed this menu.lst, so I'm just leaving out the commented out parts...)

/boot/grub/menu.lst

## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=1c3c6c38-ba43-4eda-bcff-f5a5c4ab6f70 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=1c3c6c38-ba43-4eda-bcff-f5a5c4ab6f70 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

title		Windows XP
root 		(hd0,0)
makeactive
chainloader +1


### END DEBIAN AUTOMAGIC KERNELS LIST

and lastly,

sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4a634a62

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4862    39053983+   7  HPFS/NTFS
/dev/sda2            4863        4863        8032+   5  Extended
/dev/sda5            4863        4863        8001   82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x583dff13

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4678    37576003+  83  Linux
/dev/sdb2            4679        4865     1502077+   5  Extended
/dev/sdb5            4679        4865     1502046   82  Linux swap / Solaris

---

### Post by Crafty Kisses on 2008-08-28
Can you boot into recovery mode?

---

### Post by Shlonster on 2008-08-28
I haven't actually tried --- kind of a bonehead move, I suppose, but I didn't really care because I have just been using the LiveCD to edit files.  What is the difference, in terms of what I can do? Also, I will be getting on that computer shortly and I can post all the things I talked about earlier.


Edit:

No, I cannot boot into recovery mode.  A lot of input is shown on the screen, and I get this long error at the end --

fsck.ext3: Bad magic number in super-block while trying to open /dev/sda1
dev/sda1: The superblock could not be read or does not describe a correct ext2 filesystem.  If the device is valid and it really conatins an ext2 filesystem (and not swap or ufs or something else), then the superblock is corrupt, and you might try running e2fsck with an alternate superblock: e2fsck -b 8193 <device>

fsck died with exit status 8

*File system check failed

-----------

So there it is... my ubuntu partition is installed on /dev/sdb, not /dev/sda - is that the problem? I don't know what superblocks are, and there are no ext2 partitions on either of my drives. What now?

EDIT 2:

I hit ctrl+D to exit that screen, and it pops me into the recovery menu, giving me several options - resume normal boot, repair broken packages, drop to root shell prompt, or try to fix X server. I hit resume normal boot, and it works. I'm now in my ubuntu install... I still don't know why it wont do the normal boot though?

---

### Post by Shlonster on 2008-08-28
Just putting it out there that I think I've got it figured out... since I reformatted my /dev/sda to NTFS instead of ext3, I had to change that in my fstab (I actually just removed the entry from my fstab), and now it boots up just fine.... 

Hopefully that helps someone.

---

