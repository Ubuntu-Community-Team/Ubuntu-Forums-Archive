---
title: "trying to get grub to load my Winxp"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by Shadowmeph on 2008-11-13
I am having a bit of a problem trying to get my Windows operating system to load from Grub, 
this is what my grub menu.lst looks like```
## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		de5c74d8-eaf1-4cad-a6f1-cec9a86d70af
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=de5c74d8-eaf1-4cad-a6f1-cec9a86d70af ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		de5c74d8-eaf1-4cad-a6f1-cec9a86d70af
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=de5c74d8-eaf1-4cad-a6f1-cec9a86d70af ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		de5c74d8-eaf1-4cad-a6f1-cec9a86d70af
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP (loader)
root		(hd1,0) **( I just changed this from hd0,0)**
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb2
title		Windows NT/2000/XP
root		(hd1,0)
savedefault
makeactive
chainloader	+1

```
and this command here ( which I found on a different post) shows this
 sudo fdisk -l

```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
240 heads, 63 sectors/track, 41345 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x00091c4d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       41344   312560608+  83  Linux

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f8000b1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9727    78132096    7  HPFS/NTFS
/dev/sdb2            9728       38670   232484647+   7  HPFS/NTFS
shadowfire@shadowfire-desktop:~$ sudo kate //boot/grub/menu.lst
```

---

### Post by Duck2006 on 2008-11-13
Change this,

title		Windows NT/2000/XP
root		(hd1,0)
#savedefault
makeactive
chainloader	+1

To this,

title		Windows NT/2000/XP
root		(hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
#savedefault
makeactive
chainloader	+1

---

### Post by terdon on 2008-11-13
Hi, your problem may be that windows is on the 2nd hard drive. I assume you just got a new drive, set it up and installed linux on it? 

Windows needs to be on the first partition of the first hard drive (C:/ in windows, /dev/sda1 in Linux). If you are comfortable rummaging around in your computer you could try switching the cable positions of your disks. Make the windows disk the primary master (let me know if you need more info on this) and the linux drive the primary slave or secondary master.

After you do this, the windows drive will be /dev/sda and linux will be /dev/sdb which means you will have to change your /boot/grub/menu.lst file accordingly before changing the disks. 

You need to be careful with this as it can result in a broken installation. Let me know if you want to try and I can walk you through it.

EDIT: just saw the previous post. I don't know if that would work (if windows can in fact work from a partition other than hda1) but it is definitely worth a try and safer than what I suggest.

---

### Post by Shadowmeph on 2008-11-13
> **Duck2006 said:**
> Change this,

title		Windows NT/2000/XP
root		(hd1,0)
#savedefault
makeactive
chainloader	+1

To this,

title		Windows NT/2000/XP
root		(hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
#savedefault
makeactive
chainloader	+1

Thats it :lolflag: looks to easy but I will try it  
Oh and Thank you for replying to my thread:)
> Hi, your problem may be that windows is on the 2nd hard drive. I assume you just got a new drive, set it up and installed linux on it? 
 
 Windows needs to be on the first partition of the first hard drive (C:/ in windows, /dev/sda1 in Linux). If you are comfortable rummaging around in your computer you could try switching the cable positions of your disks. Make the windows disk the primary master (let me know if you need more info on this) and the linux drive the primary slave or secondary master.
 
 After you do this, the windows drive will be /dev/sda and linux will be /dev/sdb which means you will have to change your /boot/grub/menu.lst file accordingly before changing the disks. 
 
 You need to be careful with this as it can result in a broken installation. Let me know if you want to try and I can walk you through it.
I just posted and seen that you also replied
well originally I had two drives and windows was installed on both the first drive and the second drive . what I did was I formated the first drive and installed Kubuntu onto it.

---

### Post by Duck2006 on 2008-11-13
> I don't know if that would work 

Some info on grub.

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by candtalan on 2008-11-13
afaik, your lines

# on /dev/sda1
title		Windows NT/2000/XP (loader)
root		(hd1,0) ( I just changed this from hd0,0)

are inconsistent because if true, sda1 is the first hard drive and its first partition. In grub speak this would correspond to (h0,0) which by your edit - by implication does not work.

The second entry, again, if true,

# on /dev/sdb2
title		Windows NT/2000/XP
root		(hd1,0)

suggests that sdb2 which is the second hard drive and its second partition, is what grub should use. In which case, grub speak for this would be (hd1,1)

hth?

---

### Post by Shadowmeph on 2008-11-14
Well thanks to everyone here for your replyies.
I ended up getting mad and just reinstalling everything from scratch
now for some reason the Kubuntu install sticks at 82% :lolflag:
I am going to start a new post to try and get some help for that
Thank you all again:)

---

