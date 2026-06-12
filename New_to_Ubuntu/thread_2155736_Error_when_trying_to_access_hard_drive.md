---
title: "Error when trying to access hard drive"
date: 2013-06-19
forum: New to Ubuntu
---

### Post by doddie on 2013-06-19
Hi, I am new to Ubuntu and this is my first post!
I installed 13.04 alongside windows 8 on a 250 GB HD. Left partitioning to Ubuntu but selected 50/50 share. 32 bit.
Generally OK but a few problems which include this message when I select "250 GB volume" in Devices:

Error mounting /dev/sda2 at/media/bill/583242D33242B5B2: Command-line `mount -t "ntfs"-o"uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,dmask=0077,fmask=0177""/dev/sda2" "/media/bill/583242D33242B5B2"'exited with non-zero exit status 14: Windows is hibernated, refusedto mount. 
Failed to mount '/dev/sda2': Operationnot permitted 
The NTFS partition is in an unsafestate. Please resume and shutdown 
Windows fully (no hibernation or fastrestarting), or mount the volume 
read-only with the 'ro' mount option.  

As far as I can tell Windows is fully shutdown (used " Shutdown /s /t/0").

Any advice on what I should do, please.

doddie

---

### Post by Mark Phelps on 2013-06-19
>  Left partitioning to Ubuntu That's a bad thing to do, as that can lead to filesystem corruption in Win7 and Win8.

What you will need to do now is run CHKDSK on your Win8 partitions -- but you can't do that from Linux, only from Windows.

Since you will need then to boot from disk media to do that, you need a bootable Windows disk to use.  Had you come her first and ASKED about installing with Win8, we could have told you how to make a "Recovery Drive" (which is actually a disk, not a drive) that you could now use to repair this problem.

Instead, you can go to the site linked and download the ISO needed to make the disk.  You will then have to "burn" that ISO to a DVD: [http://windowsreinstall.com/win8/windows_8_recovery_disk_download.htm#.UcGvntjw-a5]("http://windowsreinstall.com/win8/windows_8_recovery_disk_download.htm#.UcGvntjw-a5")

---

### Post by doddie on 2013-06-19
Thanks Mark - I am working on it! Backing up etc.

---

### Post by doddie on 2013-06-20
I have run CHKDSK and no faults found! Any thoughts on where I go now?

---

