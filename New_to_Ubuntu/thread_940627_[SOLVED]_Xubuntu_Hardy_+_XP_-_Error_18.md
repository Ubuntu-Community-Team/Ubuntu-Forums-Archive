---
title: "[SOLVED] Xubuntu Hardy + XP - Error 18"
date: 2008-10-07
forum: New to Ubuntu
---

### Post by jma79 on 2008-10-07
Hi there

I installed ubuntu on my laptop to try it and a few days later was eliminating all traces of windows presence on it. :)
I decided to do the same thing on my good old desktop but, since it is a low spec machine, the distro of choice was xubuntu from what i have read.
The intention was to keep a partition with XP and to have a dual boot. I did the alternate install and everything was ok until i rebooted. That's when the following appeared:

GRUB Loading stage1.5.

GRUB loading, please wait...
Error 18

These are the computer's specs:
PIII 550
192 MB RAM
2 Hard Drives - one with XP (aprox 8.5 GB) and other one with 160 GB, containing the xubuntu partition and 4 other partitions.

From what i've learned the error results from old bios working with recent big hard drives. It can be fixed by putting the xubuntu partition right in the beginning of the drive. But how do i do that using gparted or another software.

I'm fairly new to this world but liking it.
All help will be appreciated since i can't do much in the pc right now.
Sorry for the long post and thanks in advance.

Cheers

---

### Post by handydan918 on 2008-10-07
See [this link]("http://wiki.linuxquestions.org/wiki/GRUB#Error_18") for how to handle this error.

---

### Post by caljohnsmith on 2008-10-07
> **jma79 said:**
> 
From what i've learned the error results from old bios working with recent big hard drives. It can be fixed by putting the xubuntu partition right in the beginning of the drive. But how do i do that using gparted or another software.

I'm fairly new to this world but liking it.
All help will be appreciated since i can't do much in the pc right now.
Sorry for the long post and thanks in advance.

Cheers
Most likely you're right about that older BIOS not being able to see your entire HDD, and that's why you are getting the Grub error 18 right now; and you're absolutely right that moving the Xubuntu partition to the front of the drive will usually solve the problem. So can you run gparted on that machine? You could use the [gparted Live CD]("http://gparted.sourceforge.net/livecd.php"). If I understand you correctly, you all ready have Windows on that HDD? You could use gparted to move the entire Windows partition to make room for Xubuntu at the beginning, or you could shrink the Windows partition from the beginning by about ~200 MB and use that space as your /boot partition for Xubuntu. 

If you want more help with any of this, it would be helpful if you could first post:
```
sudo fdisk -lu
```
And we can work from there.

---

### Post by jma79 on 2008-10-07
handydan918:
I had already checked that link but was unsure of what to do next.

caljohnsmith:
Here goes the result of fdisk

Disk /dev/hda: 9115 MB, 911536280 bytes
255 heads, 63 sectors/track, 1108 cylinders, total 17803440 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x04470446

   Device Boot         Start           End        Blocks    Id   System
/dev/hda1   *             63      17783954       8891946     7   HPFS/NTFS

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0c75247b

   Device Boot      Start           End        Blocks    Id   System
/dev/hdb1              63      78525719      39262828+    7   HPFS/NTFS
/dev/hdb2        78525720     312576704     117025492+    f   W95 Ext'd (LBA)
/dev/hdb5        78525783     156039344      38756781     7   HPFS/NTFS
/dev/hdb6       156039408     234018854      38989723+    7   HPFS/NTFS
/dev/hdb7       234018918     268430084      17205583+    7   HPFS/NTFS
/dev/hdb8       268430148     311468219      21519036    83   Linux
/dev/hdb9       311468283     312576704        554211    82   Linux swap / Solaris


I have windows and xubuntu on separate drives.
Thx

---

### Post by jma79 on 2008-10-07
handydan918:
I had already checked that link but was unsure of what to do next.

caljohnsmith:
Here goes the result of fdisk

Disk /dev/hda: 9115 MB, 911536280 bytes
255 heads, 63 sectors/track, 1108 cylinders, total 17803440 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x04470446

   Device Boot         Start           End        Blocks    Id   System
/dev/hda1   *             63      17783954       8891946     7   HPFS/NTFS

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0c75247b

   Device Boot      Start           End        Blocks    Id   System
/dev/hdb1              63      78525719      39262828+    7   HPFS/NTFS
/dev/hdb2        78525720     312576704     117025492+    f   W95 Ext'd (LBA)
/dev/hdb5        78525783     156039344      38756781     7   HPFS/NTFS
/dev/hdb6       156039408     234018854      38989723+    7   HPFS/NTFS
/dev/hdb7       234018918     268430084      17205583+    7   HPFS/NTFS
/dev/hdb8       268430148     311468219      21519036    83   Linux
/dev/hdb9       311468283     312576704        554211    82   Linux swap / Solaris


I was able to use fdisk on the terminal in gparted but wasn't able to copy it to a device, so i had to copy it to the reply. It looks a bit scrambled. Sorry about that. Any tips welcome
Thx

---

### Post by caljohnsmith on 2008-10-07
Given your setup, I would shrink your hdb1 NTFS partition at the beginning by 200 MB, create a primary partition formatted to ext3 in that space, then reinstall Xubuntu and tell the Xubuntu installer to use that partition as the /boot mount point. If for some reason you don't want to shrink the hdb1 partition by that much, you could shrink it instead by 10-20 MB and create a super dinky 10 MB partition at the beginning of your disk; then you could use that partition as a dedicated Grub partition instead of a full /boot partition. I would recommend just making a /boot partition though--is this an option you can try?

---

### Post by jma79 on 2008-10-07
I can try that. I'll just have to move some of the data to other partition.
If i understand correctly, during the reinstallation i would create 3 partitions, one with aprox 200 megs for boot, one for xubuntu and another one for swap area. Or would it be enough just one for the boot?

---

### Post by caljohnsmith on 2008-10-07
> **jma79 said:**
> I can try that. I'll just have to move some of the data to other partition.
If i understand correctly, during the reinstallation i would create 3 partitions, one with aprox 200 megs for boot, one for xubuntu and another one for swap area. Or would it be enough just one for the boot?
Yes, you would use the new 200 MB partition at the beginning of your drive for /boot, and then use your previous hdb8 for the root / mount point (the Xubuntu main install), and hdb9 for swap. :)

---

### Post by jma79 on 2008-10-09
That partition did the trick. Now it's working. :)
Thx for your time and patience.

---

### Post by caljohnsmith on 2008-10-09
That's great you can boot it now, and I'm glad I could help out. Cheers and have fun. :)

---

