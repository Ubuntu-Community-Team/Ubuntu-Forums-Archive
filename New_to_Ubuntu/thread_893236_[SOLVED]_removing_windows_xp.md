---
title: "[SOLVED] removing windows xp"
date: 2008-08-18
forum: New to Ubuntu
---

### Post by imgkg on 2008-08-18
hi guys i want to remove windows xp from my system, should i just directly format the partition that contains window xp will this remove the windows xp option from grub menu list

---

### Post by jualin on 2008-08-18
I am pretty sure it will. If not you can always install "startupmanager" using Synaptic to delete the entry. Of course you have to format the XP partition first.

---

### Post by lisati on 2008-08-18
You can delete or format the partition (gparted is good for this), but you will probably have to edit grub's menu list. Feel free to ask for details if you get stuck.

---

### Post by imgkg on 2008-08-18
what about that MBR thing

---

### Post by victor.zamanian on 2008-08-18
> **imgkg said:**
> hi guys i want to remove windows xp from my system, should i just directly format the partition that contains window xp will this remove the windows xp option from grub menu list

Do you have Ubuntu on that same system? I think I did that once and I had both Windows XP and Ubuntu installed, and then I couldn't startup Ubuntu anymore. Be careful and research some more (or wait for more replies) before you proceed!

---

### Post by waspbr on 2008-08-18
Your MBR (grub) should be fine if you just erase the windows partition,  it may still display it after you delete, that's why some people suggested you used startup manager to write it off.

however it is always handy to keep a copy of the supergrub cd ([http://supergrub.forjamari.linex.org/]("http://supergrub.forjamari.linex.org/")) handy, just in case

---

### Post by imgkg on 2008-08-18
yes i do have ubuntu on same system but on different partition i guess

---

### Post by jualin on 2008-08-18
> **waspbr said:**
> Your MBR (grub) should be fine if you just erase the windows partition,  it may still display it after you delete, that's why some people suggested you used startup manager to write it off.

however it is always handy to keep a copy of the supergrub cd ([http://supergrub.forjamari.linex.org/]("http://supergrub.forjamari.linex.org/")) handy, just in case

If you didn't install Ubuntu using the Wubi installer (which installs within Windows) you can format the Windows partition and it will not alter GRUB.

---

### Post by jualin on 2008-08-18
> **imgkg said:**
> yes i do have ubuntu on same system but on different partition i guess

To check if you have it in a different partition please run on the terminal (ubuntu) > sudo fdisk -l and post the results on the forums

---

### Post by imgkg on 2008-08-18
these are the result

```
~$ sudo fdisk -l 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe134e134

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sda2            3825        9729    47431912+   f  W95 Ext'd (LBA)
/dev/sda5            3825        6374    20482843+   7  HPFS/NTFS
/dev/sda6            6375        6773     3204936    7  HPFS/NTFS
/dev/sda7            6774        9601    22715878+  83  Linux
/dev/sda8            9602        9729     1028128+  82  Linux swap / Solaris
~$ 



``` 



so is my windows xp on same partition as ubuntu

---

### Post by jualin on 2008-08-18
> **imgkg said:**
> these are the result

```
~$ sudo fdisk -l 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe134e134

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sda2            3825        9729    47431912+   f  W95 Ext'd (LBA)
/dev/sda5            3825        6374    20482843+   7  HPFS/NTFS
/dev/sda6            6375        6773     3204936    7  HPFS/NTFS
/dev/sda7            6774        9601    22715878+  83  Linux
/dev/sda8            9602        9729     1028128+  82  Linux swap / Solaris
~$ 



``` 



so is my windows xp on same partition as ubuntu

As far as I can see you have Ubuntu on a different partition. The last 2 partitions named "Linux" should be Ubuntu. So you should be okay.

---

### Post by imgkg on 2008-08-18
so i can go ahead with removing xp. thank you

---

### Post by jualin on 2008-08-18
Glad I helped you out. You can use Gparted from Ubuntu to format the XP partition. You can install it using Synaptic.

---

### Post by nicedude on 2008-08-18
Device Boot      Start         End      Blocks   Id  System

THIS IS YOUR XP PARTITION YOU CAN DELETE IT IF YOU WANT
/dev/sda1   *           1        3824    30716248+   7  HPFS/NTFS

THIS MOST LIKELY CONTAINS RECOVERY PARTITIONS TO REINSTALL XP - DO YOU HAVE A DELL?
/dev/sda2            3825        9729    47431912+   f  W95 Ext'd (LBA)

THE NEXT TWO ARE CONTAINED IN SDA2 UNKNOWN BUT ARE NTFS AND PROBABLY JUST DATA PARTITIONS ONE WOULD BE REINSTALL BACKUP & OTHER WOULD BE THE UTIL TO DO THE REINSTALL
/dev/sda5            3825        6374    20482843+   7  HPFS/NTFS
/dev/sda6            6375        6773     3204936    7  HPFS/NTFS

THESE ARE YOUR LINUX PARTITION & SWAP DO NOT DELETE THEM OR NO MORE UBUNTU
/dev/sda7            6774        9601    22715878+  83  Linux
/dev/sda8            9602        9729     1028128+  82  Linux swap / Solaris

So the only things I see that you need for sure are sda7 & sda8 the others could all go bye bye if you wished but sda5 & sda6 look like they are contained within the EXTENDED partition at sda2 and are most likely related to a system restore ( with one being the reinstall data and the other utilities to use it ) manufacturers use this type of setup so they don't have to give you reinstall disks ( CHEAPSKATES ). That is of course unless you created sda2 sda5 sda6 yourself and know what they are ? But I would bet $20 they are system recovery crap. Assuming I am right about all those then you could ditch everything but sda7 & sda8 and then reformat the newly freed space as a nice data storage drive for you to keep stuff on :-)

Also your MBR will be fine it already has grub on it and deleting all those pesky Windows partitions will not change your sda7 & sda8 so they will still be valid to boot from. You will have to edit your /boot/grub/menu.lst file though to remove the XP choice from it I believe.

Hope this helps you out and that is one awesome title for a thread.

---

### Post by imgkg on 2008-08-18
thanks nicedude and everyone for helping out for explaining it all, beer to you all, marking this thread as solved :guitar::lolflag:

---

### Post by jualin on 2008-08-18
Glad to hear it. 
@nicedude. Nice way of expanding on the partition explanation "THESE ARE YOUR LINUX PARTITION & SWAP DO NOT DELETE THEM OR NO MORE UBUNTU" :). And I think that you are probably right about the Recovery partitions.

---

