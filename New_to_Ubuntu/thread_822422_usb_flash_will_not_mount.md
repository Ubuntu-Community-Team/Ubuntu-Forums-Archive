---
title: "usb flash will not mount"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by inter-m on 2008-06-08
my usb flash stopped automatically mounting for some reason... when i do a fdisk -l i see it there... but i cant access it... also when i use the same flash on win xp it works fine... i used two other flashes on my ubuntu and they worked fine... im really confused...
:confused:

---

### Post by bumanie on 2008-06-08
Did you remove it from windows via the 'safe removal' routine? If not go back to xp and shutdown the device correctly. Incorrect removal from windows is often a cause of such devices not mounting in linux. Post the exact error message, even a screenshot if possible.

---

### Post by inter-m on 2008-06-08
thats the strange thing i did the 'safe removal' routine... and still its not mounting...

---

### Post by bumanie on 2008-06-08
As you can see it in fdisk -l, when it's plugged in, try sudo mount /dev/sdc1 (substitute the correct device name if it's not sdc1)

---

### Post by inter-m on 2008-06-08
> **bumanie said:**
> As you can see it in fdisk -l, when it's plugged in, try sudo mount /dev/sdc1 (substitute the correct device name if it's not sdc1)

this is the result of the fdisk -l
```
:~$ fdisk -l

Disk /dev/sdb: 33.5 GB, 33554432000 bytes
249 heads, 63 sectors/track, 4177 cylinders
Units = cylinders of 15687 * 512 = 8031744 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4178    32767937    c  W95 FAT32 (LBA)

```
this is what i did next
```
sudo mount /dev/sdb1
mount: can't find /dev/sdb1 in /etc/fstab or /etc/mtab

```
i hope this clears it more... :)

---

### Post by inter-m on 2008-06-08
i have a problem trying to explain what im facing... so plz ask me specific questions so i can be more precise...

---

### Post by MrWES on 2008-06-08
first type

sudo mkdir /media/MyFlash

then

sudo mount -t fat32 /dev/sdb1 /media/MyFlash

---

### Post by inter-m on 2008-06-08
> **MrWES said:**
> first type

sudo mkdir /media/MyFlash

then

sudo mount -t fat32 /dev/sdb1 /media/MyFlash

i tried it and and this is what i got
```
:~$ sudo mount -t fat32 /dev/sdb1 /media/MyFlash
mount: unknown filesystem type 'fat32'

```

---

### Post by cariboo on 2008-06-08
Substitute vfat for fat32 and you should be ok.

Jim

---

### Post by vlaklak on 2008-06-08
I had the same problem before.  Use another usb flash, it will recognize it i think.  Also if you have an Windows Access, use your USB Flsh in it and unmount the usb flash while using Windows.

---

### Post by inter-m on 2008-06-08
> **cariboo907 said:**
> Substitute vfat for fat32 and you should be ok.

Jim
thanx thats what i was looking for its working now...
but i was wondering why was it not automatically mounting like my other flash???

---

