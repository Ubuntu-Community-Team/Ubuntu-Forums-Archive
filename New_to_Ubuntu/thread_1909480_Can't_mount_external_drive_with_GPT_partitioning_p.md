---
title: "Can't mount external drive with GPT partitioning properly"
date: 2012-01-15
forum: New to Ubuntu
---

### Post by Anakunda on 2012-01-15
Hello, I have problem to view external drive with GPT architecture properly.
I automount it via fstab, the drive is mounted properly as /media/sdd1 and I can access the content of root dir fine. As soon as I change to any directoy on iit, I get the following error:

```
Anakunda@ASUS-UBUNTU:~$ cd /media/sdd1
Anakunda@ASUS-UBUNTU:/media/sdd1$ ls
archive  games  music  $RECYCLE.BIN  seedbox  System Volume Information  video
Anakunda@ASUS-UBUNTU:/media/sdd1$ cd seedbox
Anakunda@ASUS-UBUNTU:/media/sdd1/seedbox$ ls -l
ls: reading directory .: Input/output error
total 0
Anakunda@ASUS-UBUNTU:/media/sdd1/seedbox$ 

```Is there a chance to view this drive properly , using Ubuntu 11.10 amd64


More info:

Anakunda@ASUS-UBUNTU:~$ sudo blkid /dev/sdd1
/dev/sdd1: LABEL="DATA 3" UUID="9800D43400D41AD8" TYPE="ntfs" 

What doesnot work properly:

sudo mount -t ntfs-3g /dev/sdd1 /media/sdd1
sudo mount -t ntfs /dev/sdd1 /media/sdd1
sudo mount /dev/sdd1 /media/sdd1

All of these mount the drive without error but I can't access anything bore but root directory.

When I created I think I was using Paragon Hard Disk manager to create that partition, how do I know what NTFS version exactly is there?
Weir that when I create some dir on that drive in Ubuntu, than put some content into it, the content is accessible fine in Ubuntu, but in WIndows chkdsk identifies the file structure corrupted, then repairs it and the files created there in Ubuntu are reported as damaged fs entries. Gparted however identifies that partition still as ntfs:

[img]http://img834.imageshack.us/img834/6428/gpartedr.png[/img]

---

### Post by Double.J on 2012-01-15
When I was having problems with GPT, running parted picked up a couple of errors and was able to fix them?

In terms of your specific problem, I'm still a little confused, is the problem with windows or ubuntu?

---

### Post by CharlesA on 2012-01-15
It looks like a Windows partition. I would suggest running chkdsk on it to make sure there are no errors on it.

Input/Output error usually means that the OS is having problems reading that part of the drive.

---

### Post by Anakunda on 2012-01-15
Yep. Its a Windows partition, I was also thinking about performing check with gparted but afraid it will find some errors and "repair" them that way the disk content will be lost for Windows usage, the same way like Win checkdisk "repaired" the Linux entries on that drive by deleting them

---

