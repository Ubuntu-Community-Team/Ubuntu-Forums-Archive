---
title: "Help booting into windows (I know I know! - Damn Uni)"
date: 2008-10-24
forum: New to Ubuntu
---

### Post by yuffie8 on 2008-10-24
Hey guys, I have been using Ubuntu for a while now - well over a year - but it has been a while since I have booted into Windows (dual boot). Unfortunately I now need to boot in to load some software for University, however when I select Windows XP on the grub the screen goes black and the computer is unresponsive. While I dont have too much of a problem installing windows again, I would rather not have to.

Any ideas ?
Thanks

---

### Post by Crandom on 2008-10-24
Please can you paste the output of this command in this thread:
```
sudo fdisk -l
```
and then copy into this thread the text displayed when you highlight the windows option in grub and press 'e'

---

### Post by yuffie8 on 2008-10-24
Hey, from the fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9bb1edf4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        7140        9729    20804175    7  HPFS/NTFS
/dev/sda2               1        6932    55681258+  83  Linux
/dev/sda3            6933        7139     1662727+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe397e397

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4998    40146403+   b  W95 FAT32





and from pressing 'e' 
root (hd0, 0)
savedefault
makeactive
chainloader


i clearly see the ntfs hmmm

---

### Post by Crandom on 2008-10-24
Ok, i see the problem. Open a terminal and type:
```
gksudo gedit /boot/grub/menu.lst
```
and then change the line towards the end of the file that look like:
```
chainloader
```to```
chainloader +1
```and then save it. I am assuming you didn't leave out the "+1" when copying the data down.

---

### Post by yuffie8 on 2008-10-24
I am a fool, i opened menu.lst and the +1 is already after chainloader!

Sorry ...!

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by Duck2006 on 2008-10-24
Try changing this,

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Microsoft Windows XP Home Edition
root (hd0,0)
savedefault
makeactive
chainloader +1

To this,

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Microsoft Windows XP Home Edition
root (hd0,0)
#savedefault
makeactive
chainloader +1

---

### Post by Crandom on 2008-10-24
If you have your xp disk to hand, you can boot up on that then use the "recovery console" to boot into your local copy of xp. You might not have your disk if windows came pre-installed.

---

### Post by yuffie8 on 2008-10-24
Ok I tried Duck 2006's method and nothing,

Then I got my XP disc to try and boot into it and oddly nothing happened!
The same blank, I have never had a problem booting into Ubuntu and last time I checked windows was working fine (6 months or so ago),
very weird.

Thanks for your efforts guys, any more suggestions ?

---

### Post by Bölvaður on 2008-10-24
due to time limits I couldn't read the thread (which I normally do).
So Im just guessing that you need to use the "super grub disk", look it up on google, download it, burn it, boot it up to see how it works and go through the help, also check on the internet and  then finally you can let the super grub disk repair grub to be able to boot up the OSes that are on there.

---

### Post by Crandom on 2008-10-24
I have to say Super Grub Disk has helped me before when I got locked out of windows: [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

It could be a windows based problem. Have you change partitions recently? You could paste the boot.ini file from your xp partition here, there could be something wrong with that.

---

### Post by Duck2006 on 2008-10-24
If nothing else is working, super grub may be the way to go.

---

