---
title: "[SOLVED] Boot error after installing dual boot"
date: 2008-11-20
forum: New to Ubuntu
---

### Post by TripitakaUK on 2008-11-20
I kinda hijacked another thread :-\" so I'll start my own.

I have 5 drives in my system and want to dual-boot Windows and Hardy.

Hardy is going on an empty drive - sdb
Windows is on sdd1

All went well but I told the install to put the boot loader on sdd rather than sdd1 and now when I boot I just get GRUB GRUB GRUB filling the screen and scrolling.

How can I fix the error? I *think* that I need to move the boot loader to sdd1 from sdd but I don't know how to do that. I guess I could reinstall but there must be a tool or something that does it.

Mark.

---

### Post by wolfen69 on 2008-11-20
try [this]("http://maketecheasier.com/how-to-restore-grub-in-ubuntu/2008/04/11").

---

### Post by philinux on 2008-11-20
Post the results of

```
sudo fdisk -l
```

---

### Post by caljohnsmith on 2008-11-20
Can you change your BIOS to boot your Ubuntu sdb drive on start up? If so, you could install Grub to the MBR of your sdb drive to make it bootable, and once you have it booting OK, you can simply add an entry to your Grub's menu.lst to boot Windows. 

To install Grub to the MBR of your Ubuntu drive, just do the following from a terminal (Applications > Accessories > Terminal):
```
sudo grub
grub> find /boot/grub/stage1
grub> find /grub/stage1
```
One of the above commands should return your main Ubuntu partition (or /boot partition if you have one) in the form of (hdX,Y) where X and Y are numbers, for example (hd1,0), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
Then if you set your BIOS to boot the sdb drive, you should at least get a Grub menu on start up, but booting Ubuntu from the menu might not work just yet. See if you can get this far and we can work from here if you want.

---

### Post by TripitakaUK on 2008-11-20
wolfen69:
Thanks - that seemed to get rid of the GRUB screen and I now get the bootloader menu. However...

caljohnsmith:
You are quite right - it works but will not boot into either ubuntu or windows. I have a mix of sata and pata drives in the system which were a real pain to get booting in the right order so I'm reluctant to jiggle those unless it is absolutely necessary.

philinux:
results to follow in next post.

---

### Post by TripitakaUK on 2008-11-20
Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x045f045f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30515   245111706    7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x368b12aa

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3824    30716248+  83  Linux
/dev/sdb2           29266       30401     9124920    5  Extended
/dev/sdb3            3825       29265   204354832+  83  Linux
/dev/sdb5           29266       30401     9124888+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x63d69b05

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       38913   312568641    7  HPFS/NTFS

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x10ba10b9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1        5099    40957686    7  HPFS/NTFS
/dev/sdd2            5100       60801   447426315    7  HPFS/NTFS

Disk /dev/sde: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x94c0dc61

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       48641   390708801   42  SFS
ubuntu@ubuntu:~$

---

### Post by caljohnsmith on 2008-11-20
So are you booting the Ubuntu sdb drive on start up? If so, how about when you get the Grub menu on start up, select the first Ubuntu entry, press "e" to edit it, select the line that says "root (hdX,Y)" where X and Y are numbers, press "e" to edit it, change it to "root (hd0,Y)", press return to save the change, then press "b" to boot. If you are booting the sdb drive, that should most likely be all it takes to boot Ubuntu. Note that the above change is not permanent, so you'll need to modify your menu.lst to make it permanent.

So if it works, when you get into Ubuntu, just do:
```
gksudo gedit /boot/grub/menu.lst
```
And change the line that says "#groot=(hdX,Y)" to use the (hd0,Y) that worked to boot Ubuntu. Also, to boot Windows, add the following entries in your menu.lst:
```
title	   Windows XP (hd1)
root       (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

title	   Windows XP (hd2)
root       (hd2,0)
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader +1

title	   Windows XP (hd3)
root       (hd3,0)
map        (hd0) (hd3)
map        (hd3) (hd0)
chainloader +1

title	   Windows XP (hd4)
root       (hd4,0)
map        (hd0) (hd4)
map        (hd4) (hd0)
chainloader +1
```
Save, quit gedit, then run:
```
sudo update-grub
```
And let me know how it goes as far as booting Windows; if none of the above entries work, let me know exactly what happens when you try each from the Grub menu.

---

### Post by TripitakaUK on 2008-11-21
How do I find out what disks/partitions the (hdx,y) relates to? I've looked in GParted but that info isn't there?

I can't edit the boot loader until I know this I guess?

Lovin' this Linux thing - as a M$ user for two decades, it is a breath of fresh air but I'm lovin' these forums the most.

---

### Post by TripitakaUK on 2008-11-21
Seems I found the answer here:

[http://ubuntuforums.org/archive/index.php/t-160035.html](http://ubuntuforums.org/archive/index.php/t-160035.html)

Off to play with that theory now.

---

### Post by TripitakaUK on 2008-11-21
Using the link above, the post that refers to the sdxn linking to the (hdx,y) was a little misleading but the thread corrects that later.

Using root (<tab> I could find my drive numbers then using cat (hd<tab> I found some of the partitions, one of which was my ubuntu install. Now got that booting OK.

I'm going to have a stab at finding the windows partition now.

---

### Post by TripitakaUK on 2008-11-21
Ta-daaa!

That works a treat AND I have learnt some more stuff.

I'm only a week in and the curve has been steep but I'm suprised at how easy it is beginning to feel - every day I discover stuff in Ubuntu where I think "Oh yes - I like that!". It's shocking how brainwashed you become when using windows and accept cr*p as the norm.

Many thanks caljohnsmith - you :guitar:

---

### Post by caljohnsmith on 2008-11-21
That's great news you have it working; cheers and have fun with Ubuntu. :)


:popcorn:

---

