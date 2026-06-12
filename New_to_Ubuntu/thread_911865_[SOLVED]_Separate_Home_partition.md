---
title: "[SOLVED] Separate /Home partition"
date: 2008-09-06
forum: New to Ubuntu
---

### Post by NaF on 2008-09-06
Kinda embarrassing really, but made a "complete removal" of something in synaptics that i thought i didn't need - which kinda uninstalled everything related to gnome. The .deb packagde installer was gone, the network-manager and so on and so on were gone - I couldn't figure out howto recover. So I partitioned my harddrive and moved /home to sda3. 

But I really can't seem to figure out how to reinstall and set that partition as my /home. 
If some kind soul would be a doll and guide me through. I'm in the live cd as of this writing.

---

### Post by Elfy on 2008-09-06
When install reaches partitioner chhose manual.

Pick partition you wish to use as /home - edit partition
  Use as drop down menu - use as ext3
  Mountpoint dropdown menu - pick /home

Close window, follow same for / partition - same as /home but use mountpoint of /

Swap will be recognised, once both partitions are setup proceed to next part.

---

### Post by NaF on 2008-09-06
> **forestpixie said:**
> When install reaches partitioner chhose manual.

Pick partition you wish to use as /home - edit partition
  Use as drop down menu - use as ext3
  Mountpoint dropdown menu - pick /home

Close window, follow same for / partition - same as /home but use mountpoint of /

Swap will be recognised, once both partitions are setup proceed to next part.

That's about how far i got on my own, except i couldn't choose ext3 but rather ext3 journaling, don't know what difference that makes tho. But when I've installed that way, grub just comes up with error 15 - which if i'm nothing mistaken is file not found. Is there any way I could've set up the partitions wrongly - or?

---

### Post by Elfy on 2008-09-06
ext3 is a journaling filesystem

so you have at the moment got an installed ubuntu but error 15 on boot?

If that is the case and you are in the livecd can you run 

```
sudo fdisk -l
```

---

### Post by NaF on 2008-09-06
Aight, don't know what that means, but aight ;)

```
  
Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc7a7c7a7

Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        5099    40957686   83  Linux
/dev/sda2           47885       48641     6080602+   5  Extended
/dev/sda3            5100       30782   206298697+  83  Linux
/dev/sda5           47885       48641     6080571   82  Linux swap / Solaris

Partition table entries are not in disk order

```

---

### Post by NaF on 2008-09-06
No idea?

---

### Post by Bölvaður on 2008-09-06
This looks alright, you got your / and /home there.

All you need to do is when you are installing, is to label the / as the / and chose to format it (should be set to ext3, and no worries if it says ext3 journaling), do the same with /home BUT DO NOT FORMAT IT... unless if you want to lose all your data.

if your computer has any troubles with this, please explain what, and preferably post your errors here, and more detailed explanation on what happened.

---

### Post by NaF on 2008-09-06
I usually just went into the live mode and installed after fiddeling with gparted. tho I noticed after the install bar was out, it didn't tell me to reboot - just closed and went back to the live environment. Didn't pay much attention to that. But when I chose the "Install Ubuntu" option from the live menu, it gave me 
```
Internal error, Failed to initialize HAL!
``` when it had completed the install, and still Grub error 15 when i try and boot into it.

---

### Post by NaF on 2008-09-06
Gah, i hate this. I really wanna be able to fiddle with Linux,i know this obviously can be done - but have no way of knowing where to start. So I'll just have to transfer all my **** to 9 different disks and format everything again.

---

### Post by Elfy on 2008-09-06
I want to see what you're menu list looks like so assuming that the partitions are the same and you haven't changed anything can you do these - 1 should not return anything and should tell you there is no such thing.

```
sudo mkdir /mnt/recovery
sudo mkdir /mnt/recovery1
sudo mount -t ext3 /dev/sda1 /mnt/recovery
sudo mount -t ext3 /dev/sda3 /mnt/recovery1
cat /mnt/recovery/boot/grub/menu.lst
cat /mnt/recovery1/boot/grub/menu.lst
```

Not sure about the hal issue, lets deal with error 15 for the moment.

---

