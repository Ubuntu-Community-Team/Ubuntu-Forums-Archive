---
title: "How To Access The Windows Partition"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by Ninelivez on 2008-05-19
Heyz, I am trying to access my Windows Partition to transfer my music from Windows to Ubuntu, but when I try to access it under the Places tab, it says:

"Cannot Mount Volume: Unable To Mount Volume"

Any ideas what I need to do in order to access my Windows Partition and transfer my music?

Thanks!

---

### Post by Ninelivez on 2008-05-19
bump? :)

---

### Post by vitorgatti on 2008-05-19
Can you click in DETAILS to see the cause of the error?
Try to turn off your Windows correctly to have a clean shutdown, so Linux can mount NTFS partitions in the right way.

---

### Post by Ninelivez on 2008-05-19
Ah ok, the details says it indicates an unclean shutdown. So your saying I need to boot into windows and properly shutdown, then go back into Ubuntu and it should work fine?

---

### Post by rockerphil on 2008-05-19
if that doesn't work would you please open up a terminal and post the output of this colde?

sudo fdisk -l

---

### Post by vitorgatti on 2008-05-19
oh yes
that's the way NTFS works :/

---

### Post by amd-64 on 2008-05-19
You will need to shutdown windows if you want to mount the drive in read-write mode. You can always mount the hibernated drive in read-only mode, which means you will not be copying or moving files to that drive. 

I mount mine like this 

```

sudo mkdir /media/hda1
sudo mount -o ro /dev/hda1 /media/hda1

```

In this case, I mount hda1 device to the /media/hda1 empty folder. You may have to use a different device name or target name depending on your configuration.

---

### Post by Ninelivez on 2008-05-19
Hrm that didn't work, heres that output of that terminal code:

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa045a045

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19451   156240126    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x21779a92

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       18700   150207718+  83  Linux
/dev/sdb2           18701       19457     6080602+   5  Extended
/dev/sdb5           18701       19457     6080571   82  Linux swap / Solaris
ben@Hades:~$


EDIT:

Wait, I tried AMD's terminal code, changing it with my NTFS HD name and it worked! I am transfering the music to my Ubuntu Partition! I'll test the songs when it finishes and edit this post again.

Thanks!

EDIT 2:

Yup, worked perfectly. Thanks guys!

---

### Post by amd-64 on 2008-05-20
If it works, you can make it permanent in your /etc/fstab file,
find the line for the ntfs drive and change rw to ro

---

