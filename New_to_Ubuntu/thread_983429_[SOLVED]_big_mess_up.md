---
title: "[SOLVED] big mess up"
date: 2008-11-15
forum: New to Ubuntu
---

### Post by Techarmy on 2008-11-15
i aca dent ly messed up 1 of my harddrives and now when i try to acses it it says


The volume uses the sbd file system which is not supported by your system. i need to mack it so ubuntu can use it as xtra space but now i cant plz help

---

### Post by Patrick793 on 2008-11-15
What did you do to cause this.

Or, what happened recently before this happened?

---

### Post by Techarmy on 2008-11-15
um all i know is that i clicke properdies and i went to a tab witch idk the name and it had like mount opitans and now i dont see that tab any more i mean its only a 20 gb that i got 4 free but it has 7200 rpm so im not that mad

---

### Post by cdtech on 2008-11-15
Can you post the output of:
```
sudo fdisk -l
```
And which drive are you trying to access?

---

### Post by Techarmy on 2008-11-15
Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x021e021d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4678    37576003+  83  Linux
/dev/sda2            4679        4865     1502077+   5  Extended
/dev/sda5            4679        4865     1502046   82  Linux swap / Solaris

Disk /dev/sdb: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2327    18691596   83  Linux
/dev/sdb2            2328        2434      859477+   5  Extended
/dev/sdb5            2328        2434      859446   82  Linux swap / Solaris
macgyver@macgyver-desktop:~$ Disk /dev/sda: 40.0 GB, 40020664320 bytes
Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 bash: Disk: command not found
macgyver@macgyver-desktop:~$ 255 Disk /dev/sda: 40.0 GB, 40020664320 bytes
bash: 255: command not found


and i need to accsess the 20 gb 1 the 40 is my main

---

### Post by cdtech on 2008-11-15
You should be able to mount the paritions using:
```
sudo mkdir /mnt/sdb1
sudo mount /dev/sdb1 /mnt/sdb1
```
I see no reason why you cannot do this. The structure looks ok from the command you provided.

---

### Post by cdtech on 2008-11-15
I also see that you may be using the wrong command:
> The volume uses the sbd
Which should be **[COLOR="DarkRed"]sdb[/COLOR]**

---

