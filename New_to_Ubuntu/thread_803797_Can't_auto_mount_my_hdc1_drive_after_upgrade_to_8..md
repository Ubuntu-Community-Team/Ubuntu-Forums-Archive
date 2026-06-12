---
title: "Can't auto mount my hdc1 drive after upgrade to 8.04"
date: 2008-05-22
forum: New to Ubuntu
---

### Post by Ashy72 on 2008-05-22
Hello everyone I upgraded to 8.04LTS today.
I have an ide hard drive HDC1 which I want to automount it was ext3.
I see the drive on boot up in places when I click on it then it mounts. 

I want the drive to automount to media/disk

As there is already a disk there it will now mount to media/disk_

Any ideas?

My /etc/fstab file was preserved but doesn't now seem to work the line i previously used was:-

/dev/hdc1     /media/disk      ext3      defaults   0    0

I would very much appreciate any help from anyone on this..

---

### Post by lswest on 2008-05-22
can you post the output of ```
sudo fdisk -l
ls /media/
``` please? it may be something as simple as the folder being renamed or the drive being re-named.

---

### Post by Ashy72 on 2008-05-22
> **lswest said:**
> can you post the output of ```
sudo fdisk -l
ls /media/
``` please? it may be something as simple as the folder being renamed or the drive being re-named.

I think the drive has been renamed. It now shows 158.6 GB Media
it didn't show as this before.


Disk /dev/sda: 20.0 GB, 20003880960 bytes
255 heads, 63 sectors/track, 2432 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0207f162

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2325    18675531   83  Linux
/dev/sda2            2326        2432      859477+   5  Extended
/dev/sda5            2326        2432      859446   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x10c5defb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19281   154874601   83  Linux
/dev/sdb2           19282       19457     1413720    5  Extended
/dev/sdb5           19282       19457     1413688+  82  Linux swap / Solaris
mark@Black-Widow:~$ ls /media/
cdrom  cdrom0  disk  samba

Why is my disk now showing as /dev/sdb ?

Thanks for your help in advance.

---

### Post by lswest on 2008-05-22
this is because it seems that in hardy they've named most drives sdXX, and so you have to change "hdc1" to whatever the new name is.  Or perhaps it's using a new driver for your hdd, it's possible.

---

### Post by Ashy72 on 2008-05-22
> **lswest said:**
> this is because it seems that in hardy they've named most drives sdXX, and so you have to change "hdc1" to whatever the new name is.  Or perhaps it's using a new driver for your hdd, it's possible.

Many thanks I was already changing it in the fstab file to the new names.
Why can't they just leave things alone I would be listening to my music server by now if they had.

I hope this is the only trouble i will have, if not I can feel a restore to 7.10 coming on I have it on dvd backed up by mondo just in case.

Thankyou for your quick replies.

Mark.

---

### Post by lswest on 2008-05-23
No problem, glad it worked for you.  And who knows, maybe they changed it because there was some issue other people were having?

---

