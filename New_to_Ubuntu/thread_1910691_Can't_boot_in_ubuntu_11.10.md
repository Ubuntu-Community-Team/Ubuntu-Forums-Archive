---
title: "Can't boot in ubuntu 11.10"
date: 2012-01-17
forum: New to Ubuntu
---

### Post by b_andries on 2012-01-17
Hi!

I have a problem i can't fix :) A couple days ago i reinstalled ubuntu 11.10 because i did something wrong ,I decided to reinstall ubuntu again . I also have windows 7 and it was installed as a dual boot. But the problem now is when i boot my system there isn't any boot menu where i can choose between Windows 7 and ubuntu. It only boots automatically in windows 7. So i searched for a solution and found that it could be fixed using boot repair to fix my Grub menu(via a live CD). So I did this but still when i reboot there still isn't a boot menu. I don't know how to solve this problem. Can anyone help me with this please?

Thanks in advance!
Greets

---

### Post by Double.J on 2012-01-17
Hi there! Welcome to the forums!

Was ubuntu on a different hard drive to Windows? Did you also reinstall windows?

When you ran boot repair - did you set the grub location as a drive- for example /dev/sda or a partition eg /dev/sda3? in your case, you'd want it installed to the sart of the drive, so /dev/sda most likely.

Either way, if you've followed boot repair and still got nowhere, best have a look at the drive - make sure everything is as it should be - boot up the live disk and copy/paste this into the terminal
```

sudo fdisk -l

```

---

### Post by b_andries on 2012-01-17
thanks!
Ubuntu was on the same hard drive. I didnt reinstall windows. I made a  new partition in windows in drive letter g:/ and reinstalled ubuntu in  that partition. 
I didnt set a grub location as a drive in boot repair, I did the recommended repair in "boot repair".
When i type sudo fdisk -l in terminal i get :

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xf1cc70a9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63        2047         992+  42  SFS
Partition 1 does not start on physical sector boundary.
/dev/sda2   *        2048      409599      203776   42  SFS
/dev/sda3          409600  1224964095   612277248   42  SFS
/dev/sda4      1224964096  1465147119   120091512   42  SFS


I have no idea what it means :-)

---

### Post by Double.J on 2012-01-17
Hi there - is this a wubi install by any chance?

---

### Post by b_andries on 2012-01-17
> **gnu/mirow said:**
> Hi there - is this a wubi install by any chance?

yes it is

---

### Post by Double.J on 2012-01-17
Ah right, that's a bit clearer! Wubi is a bit special, it doesn't use grub, so no boot repair to worry about. Have a look at this ehow on reinstalling

[ehow.com guide]("http://www.ehow.com/how_7465639_uninstall-reinstall-wubi.html")

Ofcourse if you've experienced enough to want to try out a full install you could always head over to the [main downloads page]("http://www.ubuntu.com/download/ubuntu/download")? You'll find lots of info and help on the forums if you did :)

---

### Post by b_andries on 2012-01-18
Thanks for your help i found the solution :)

---

