---
title: "GRUB2 doesn't list other OS"
date: 2012-05-04
forum: New to Ubuntu
---

### Post by cshin9 on 2012-05-04
I reinstalled Ubuntu for reason I won't explain here. When I reinstalled  it, I had a separate /boot partition which was formatted. Now, GRUB2  detects Ubuntu fine, but it doesn't list LMDE, which I have on a  separate partition. When I run update-grub2, it detects LMDE, but when I  reboot, GRUB2 still doesn't list it.

---

### Post by papibe on 2012-05-04
Hi cshin9.

By any chance do you have several HD?

Could you post the result of this command?
```
sudo fdisk -l
```

Regards.

---

### Post by cshin9 on 2012-05-04
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5b9914f7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048     1050623      524288   83  Linux
/dev/sda2         1052670   976771071   487859201    5  Extended
/dev/sda5         1052672    34607103    16777216   83  Linux
/dev/sda6        34609152   168826879    67108864   83  Linux
/dev/sda7       168828928   185606143     8388608   82  Linux swap / Solaris
/dev/sda8       968382464   976771071     4194304   82  Linux swap / Solaris
/dev/sda9       185608192   252717055    33554432   83  Linux
/dev/sda10      252719104   968380415   357830656   83  Linux

Partition table entries are not in disk order

```Ubuntu is installed on sda9 (/) and sda10(/home). LMDE is installed on sda5(/) and sda6 (/home). sda1 is /boot.

---

### Post by oldfred on 2012-05-04
If menu is not updated, either there is corruption in the creation process on the menu (I had typo in 40_custom) or you are booting one version but changing another.

To see all the details post the link to Boot-Info.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or Create BootInfo report & post the link to a run of boot info script so we can see your exact configuration.

---

### Post by cshin9 on 2012-05-04
> **oldfred said:**
> If menu is not updated, either there is corruption in the creation process on the menu (I had typo in 40_custom) or you are booting one version but changing another.

To see all the details post the link to Boot-Info.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or Create BootInfo report & post the link to a run of boot info script so we can see your exact configuration.
The recommended option for Boot Repair didn't work. It still doesn't list LMDE. If I'm supposed to fiddle with the advanced options, someone will have to walk me through them.

---

### Post by oldfred on 2012-05-04
Run the boot info part from Boot_repair. That will provide a link to a report detailing your system.

---

### Post by cshin9 on 2012-05-05
Eh, I reinstalled the / partition without specifying a separate /boot partition. It now recognizes LMDE. Is it not possible to have a single dedicated /boot partition for multiple OSs?

---

### Post by oldfred on 2012-05-05
Ok that was the problem. No you cannot have one /boot for multiple systems. Each interferes with the other. 

There may be exceptions where with some effort you might make it work if they are so different they use totally different files & folders.

---

### Post by cshin9 on 2012-05-18
Okay, I reinstalled Ubuntu without sharing the /boot partition. Now it's fine. What's the point of having a separate /boot partition anyway if you can't share them?

---

### Post by oldfred on 2012-05-18
There isn't for most desktops. 

Some old systems needed it to boot from the first 137GB, some use file formats that grub does not support or you may have RAID or LVM, but now grub2 even supports most of those issues directly.

Herman on advantages/disadvantages of separate system partitions post#3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)

---

