---
title: "Ubuntu did not install properly?"
date: 2008-10-05
forum: New to Ubuntu
---

### Post by V8VN7V on 2008-10-05
So just when all seemed well apparently Ubuntu did not install properly or something.  I had just got settled in, added some plugins, had to reboot and since I had taken out the boot disk I thought it would just use the HD location.

But then I got something like initramfs (sp) which I assume is like C:\

I had NO CLUE WHAT TO DO ;_;

So I reboot from the disk and ALL THE STUFF I JUST INSTALLED IS GONE!

What did I do wrong?!

---

### Post by germanix on 2008-10-05
Just for clarification.
Did you actualy install Ubuntu on your pc, or were you just using the "live session option".

---

### Post by Mud.Knee.Havoc on 2008-10-05
Instead of installing, select the option to test the disc integrity (check it for errors) to make sure that the CD burned properly.  

If there are errors, you can try re-burning at the slowest speed your burner will allow, or compare md5sums of the downloaded ISO and the one on Ubuntu's server (if this is Greek to you, don't worry - we can help you out).

I usually download the minimal install for Ubuntu.  It's a tiny download, and it installs everything from the net (so I don't have to worry about CD burning errors).

---

### Post by Sef on 2008-10-05
To see what is installed on your hard drive, do this from the LIve CD:

System > Administration > Terminal:

paste or type this code:

```
sudo fdisk -l
``` small L

then paste the information here.

---

### Post by V8VN7V on 2008-10-07
> **Sef said:**
> To see what is installed on your hard drive, do this from the LIve CD:

System > Administration > Terminal:

paste or type this code:

```
sudo fdisk -l
``` small L

then paste the information here.

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x766bcaa8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1274    10233373+  27  Unknown
/dev/sda2   *        1275       10383    73168042+   6  FAT16
/dev/sda3           10384       17192    54693292+   7  HPFS/NTFS
/dev/sda4           18185       19457    10225372+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8d399bc0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60800   488375968+   c  W95 FAT32 (LBA)
ubuntu@ubuntu:~$

---

### Post by V8VN7V on 2008-10-07
> **germanix said:**
> Just for clarification.
Did you actualy install Ubuntu on your pc, or were you just using the "live session option".

I actually started the installation process, but at the end there was an error message that I accidentally just clicked through.  But the OS seemed to be operating smoothly right after installation so I kept using it.  Then at the next reboot, I just get the box and text commands.

---

### Post by V8VN7V on 2008-10-07
> **Mud.Knee.Havoc said:**
> Instead of installing, select the option to test the disc integrity (check it for errors) to make sure that the CD burned properly.  

If there are errors, you can try re-burning at the slowest speed your burner will allow, or compare md5sums of the downloaded ISO and the one on Ubuntu's server (if this is Greek to you, don't worry - we can help you out).

I usually download the minimal install for Ubuntu.  It's a tiny download, and it installs everything from the net (so I don't have to worry about CD burning errors).

Good idea!  I will check. Thanks!

---

