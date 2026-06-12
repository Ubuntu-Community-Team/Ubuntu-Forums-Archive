---
title: "How to auto mount partition in 8.04?"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by tandkzy on 2008-04-28
Yes, I have some problem on this. 
I have 3 hard disk. One is IDE, others are SATA. The problem is when I reboot, the disk will be in different place. Sorry for my bad english. It's just look like this.
Yesterday, my IDE disk 
  /dev/sdc1
Today, my IDE disk
  /dev/sda1
Anotherday, my IDE disk
  /dev/sdb1

I hadn't saw this problem in version 7.10. So, can someone help me?

---

### Post by DezSP on 2008-04-28
That's funky. Which disk are you using to boot from?

---

### Post by gaffurabi on 2008-04-28
Before you do this, unmount your NTFS partition if you have mounted it manually.

1. Get the name of your NTFS partition
```
sudo fdisk -l
```
* I assume /dev/sda2 as the NTFS partition
	
2. Make folder where your NTFS partition will be mounted
```
sudo mkdir /media/Windows
```

3. Edit	FSTAB to mount the partition at boot
```
gksudo gedit /etc/fstab
```

4. Add this line to the end of the file
```
/dev/sda2 /media/Windows ntfs-3g defaults 0 0
```
Save and Exit.

5. Test it
```
sudo mount -a
```

If all goes well, you should see a desktop shortcut to the partition and should auto-mount next time you reboot. 

if you want to mount more than one drive create more directories such as windows2,windows3 etc.

---

### Post by alienexplorers on 2008-04-28
Can you please open terminal and enter:
> cat /etc/fstab
and post the results here.

---

### Post by tandkzy on 2008-04-28
> **DezSP said:**
> That's funky. Which disk are you using to boot from?

I install my ubuntu 8.04 in one of the SATA disks, and this disk changes too!!

I know how to edit the /etc/fstab file. 
In this file, you must specify one dev to mount, and the dev change every time when I reboot!

---

### Post by vanadium on 2008-04-28
That is exactly why today, UUIDs are used to mount drives rather than device names. With today's hardware, there is no certainty that the same drive gets assigned the same device name on each boot. UUIDS in contrast uniquely identify a partition.

---

### Post by santaslittlehelper on 2008-04-28
```
ls -lF /dev/disk/by-uuid/
```
This will give you the UUIDs.

---

### Post by Klab0 on 2008-04-28
Thanks for the help guys. I also had some problem with Ubuntu not mounting partitions automatically, so this should do the trick!

I also have a 'problem' that the wallpaper won't stay between reboots  (they are located on a non-automatically mounted partition thus far). Do you think that this will solve that problem as well, or should I keep looking for solutions on that one?

Thx //Klab0

---

### Post by tandkzy on 2008-04-28
Thanks everyone, I solved this problem by useing UUID.

---

### Post by Klab0 on 2008-05-06
Hmm.. I'm not following to a 100% here. If i would like to use the uuid instead of device name, should I then type:
> /dev/6C5C69065C68CD00 /media/Windows ntfs-3g defaults 0 0

Instead of:
> /dev/sda1 /media/Windows ntfs-3g defaults 0 0

in the fstab?

My disk's uuid displays as:
> klab0@klab0-desktop:~$ ls -lF /dev/disk/by-uuid/
totalt 0
lrwxrwxrwx 1 root root 10 2008-05-06 14:21 22D420A6D4207E63 -> ../../sdb1
lrwxrwxrwx 1 root root 10 2008-05-06 14:21 6C5C69065C68CD00 -> ../../sda1
lrwxrwxrwx 1 root root 10 2008-05-06 14:21 94357289-c552-4c11-b5d8-441b2d8418aa -> ../../sda5
lrwxrwxrwx 1 root root 10 2008-05-06 14:21 A880E70580E6D8B8 -> ../../sdb2
lrwxrwxrwx 1 root root 10 2008-05-06 14:21 FC944C5C944C1B90 -> ../../sdc1


One more thing. When I do the *sudo fdisk -l* I get this result:
> Disk /dev/sda: 37,0 GB, 37019566080 byte
255 huvuden, 63 sektorer/spår, 4500 cylindrar
Enheter = cylindrar av 16065 · 512 = 8225280 byte
Diskidentifierare: 0x14a314a2

    Enhet Start     Början        Slut     Block    Id  System
/dev/sda1   *           1        3187    25599546    7  HPFS/NTFS
/dev/sda2            3188        4500    10546672+   5  Utökad
/dev/sda5            3188        4500    10546641   83  Linux

Disk /dev/sdb: 500,1 GB, 500107862016 byte
255 huvuden, 63 sektorer/spår, 60801 cylindrar
Enheter = cylindrar av 16065 · 512 = 8225280 byte
Diskidentifierare: 0x53a67d32

    Enhet Start     Början        Slut     Block    Id  System
/dev/sdb1               1       60801   488384001   42  SFS

Disk /dev/sdc: 200,0 GB, 200049647616 byte
255 huvuden, 63 sektorer/spår, 24321 cylindrar
Enheter = cylindrar av 16065 · 512 = 8225280 byte
Diskidentifierare: 0x14d814d7

    Enhet Start     Början        Slut     Block    Id  System
/dev/sdc1               1       24320   195350368+   7  HPFS/NTFS

This is in swedish, but what I'm getting at is the filetables. Should SFS and "Utökad" (extended) be handled differently when editing the fstab?

:confused:


Never mind. I've sorted it out now =)

---

