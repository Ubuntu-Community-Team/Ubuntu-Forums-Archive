---
title: "Partition problem while installing UBUNTU"
date: 2008-09-08
forum: New to Ubuntu
---

### Post by abdelrazzac10 on 2008-09-08
Hi all,

I'm trying to install Ubuntu 8.04 on my DELL inspiron 6400 laptop. first I used "Acronis Disk Director Suit" program under windows to make two partitions, U: (to install ubuntu,4 GB) and L: (Linux swap 1 GB), I made them EXT3 (I read that it's better for Linux).

after successfully making these partitions, I'm rebooting the computer with the Ubuntu 8.04 inside to install UBUNTU... the problem raises at the 4rth step of the installation. Ubuntu doesn't see any partitions on my hard disk!!! when it tells me to choose the partition, and when I choose to do it manually it shows me my hard disk as: "dev/sda" but no C:, D:, or the new U: and L: !!! any idea???

I have windows XP installed previously... is it something special for DELL laptops???

thanks...

---

### Post by tangibleorange on 2008-09-08
> **abdelrazzac10 said:**
> Hi all,

I'm trying to install Ubuntu 8.04 on my DELL inspiron 6400 laptop. first I used "Acronis Disk Director Suit" program under windows to make two partitions, U: (to install ubuntu,4 GB) and L: (Linux swap 1 GB), I made them EXT3 (I read that it's better for Linux).

after successfully making these partitions, I'm rebooting the computer with the Ubuntu 8.04 inside to install UBUNTU... the problem raises at the 4rth step of the installation. Ubuntu doesn't see any partitions on my hard disk!!! when it tells me to choose the partition, and when I choose to do it manually it shows me my hard disk as: "dev/sda" but no C:, D:, or the new U: and L: !!! any idea???

I have windows XP installed previously... is it something special for DELL laptops???

thanks...

in the live CD, before starting the installation, could you go to a terminal (Applications -> Accessories -> Terminal) and type:

```
sudo fdisk -l
```

then post the output.

---

### Post by abdelrazzac10 on 2008-09-08
here is the output:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 78.5 GB, 78518522880 bytes
255 heads, 63 sectors/track, 9546 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x86b7a0a0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          10       80293+  de  Dell Utility
/dev/sda2   *          11        4548    36451485    7  HPFS/NTFS
/dev/sda3            4549        9546    40146435    5  Extended
/dev/sda4            8502        8893     3148740   db  CP/M / CTOS / ...
/dev/sda5            4549        8501    31752439    7  HPFS/NTFS
/dev/sda6            8894        9546     5245191    7  HPFS/NTFS
ubuntu@ubuntu:~$ 


which means that ubuntu is seeing the partitions! but while installing Linux it sees them as one partition (only sda). moreover, while using ubuntu from the cd, I could see my disks C: and D: and U: and I was able to see, open and use their contents!

thanks for your quick reply

---

### Post by tangibleorange on 2008-09-08
ah I see. try opening up Gparted and seeing if it can see the partitions then:

Alt+f2 -> gksu gparted

---

### Post by abdelrazzac10 on 2008-09-09
Excuse me...
but I couldnt understand your post... should I make a new partition called G? and write "Alt+f2 -> gksu gparted " in the terminal of Ubuntu?:redface:

---

### Post by t0p on 2008-09-09
> **abdelrazzac10 said:**
> Excuse me...
but I couldnt understand your post... should I make a new partition called G? and write "Alt+f2 -> gksu gparted " in the terminal of Ubuntu?:redface:

1. Press the **Alt+F2** keys together

2. In the Run box that appears, type **gksu gparted** and press **Enter**

3.  Type in your password when prompted and press **Enter**

---

### Post by abdelrazzac10 on 2008-09-09
thanks for your fast reply...

well.. I think that Ubuntu doesnt see my partitions; the output of "Alt+f2 -> gksu gparted " was "unallocated    73GB" which is almost all the hard disk, so my hard disk is seen as one partition by Ubuntu. But if I look inside my computer using Ubuntu, I can see all the partitions with all my DATA available, as I have mentioned before. what should I do to make a safe paetition and install Ubuntu on? is FORMAT the only solution? I hope NOT.

---

### Post by tangibleorange on 2008-09-09
> **abdelrazzac10 said:**
> thanks for your fast reply...

well.. I think that Ubuntu doesnt see my partitions; the output of "Alt+f2 -> gksu gparted " was "unallocated    73GB" which is almost all the hard disk, so my hard disk is seen as one partition by Ubuntu. But if I look inside my computer using Ubuntu, I can see all the partitions with all my DATA available, as I have mentioned before. what should I do to make a safe paetition and install Ubuntu on? is FORMAT the only solution? I hope NOT.

hmm i really don't understand it. fdisk can see the partitions, so why can't gparted. I'm out of suggestions i'm afraid... :(

you could try using the alternate CD and partitioning from in there. it has better support for all types of partitioning.

---

### Post by abdelrazzac10 on 2008-09-09
thanks bro... I will try "partition magic" to make the U: partition n try...

---

### Post by Gonz_91 on 2008-09-09
I suffered from partitioning problems as well. So what I did was the following:
Using Parted Magic, I shrunk my existing partitions in order to leave unallocated space for ubuntu, then when installing ubuntu, told it to use the biggest contiguous free space.

Hope it helps ;)

---

### Post by poisonpanik on 2008-10-17
I had the same problem when I tried to install Ubuntu the other day.  I am starting with a CLEAN 120GB IDE HDD.  I will preface this with the fact that I am a LINUX newbie.  I understand a few things and am fairly "windows savy" but I've never used LINUX before.

I downloaded the current version yesterday and attempted to install.  When I get to step 4 the partition manager sees NOTHING and all the buttons are greyed out.  Strange thing is I installed Freespire 2.0 which is based on Ubuntu 7 with no problems at all. Gparted sees and was able to partition the drive when ran from the Freespire 2.0 LiveCD. 

I originally wanted to install a few different distros on my HDD but decided to make things simple to start and do 1 at a time.

I won't be giving up my windows box any time soon but I thought it'd be fun to play around with LINUX a bit.  So far its been a pain in the butt :-(

Thanks for any advice/help!

---

