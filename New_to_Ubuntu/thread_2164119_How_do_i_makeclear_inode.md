---
title: "How do i make/clear inode?"
date: 2013-07-30
forum: New to Ubuntu
---

### Post by X8YnhwA on 2013-07-30
When i was trying to fix my bricked tablet (Voyo A15), i ran into this problem. I have no experience with programming whatsoever, so i am basically following steps as on the internet. 

```
sudo dd if=F18-arndale-201305210148-xfce-uboot-buildin.img of=/dev/sdc1 ;sync
[sudo] password for ramjali: 
dd: writing to `/dev/sdc1 ': No space left on device
8055265+0 records in
8055264+0 records out
4124295168 bytes (4.1 GB) copied, 39.1395 s, 105 MB/s
```

The above states I have no space on my micro SD card. So i followed some pointers on the internet and got the following.

```
ramjali@ramjali-desktop:~$ df
Filesystem     1K-blocks    Used Available Use% Mounted on
/dev/sdb5       24808568 7034316  16514016  30% /
udev             4027632       4   4027628   1% /dev
tmpfs            1627984    1000   1626984   1% /run
none                5120       0      5120   0% /run/lock
none             4069952     156   4069796   1% /run/shm
/dev/sdc1        7738080       4   7738076   1% /media/USB1

ramjali@ramjali-desktop:~$ df -i
Filesystem      Inodes  IUsed   IFree IUse% Mounted on
/dev/sdb5      1577968 201536 1376432   13% /
udev           1006908    604 1006304    1% /dev
tmpfs          1017488    525 1016963    1% /run
none           1017488      3 1017485    1% /run/lock
none           1017488      7 1017481    1% /run/shm
/dev/sdc1            0      0       0     - /media/USB1
```

My micro SD card is the sdc1. As you can see i have used less than 1% of the total space but however I have 0 inodes which i think is the problem. 
How do i go about fixing this problem, so i can write the tablet img file to the micro SD?
Even doing a complete format in Win7 does not seem to work
I have no prior knowledge with linux so please give me commands which i can copy and paste in the terminal.

---

### Post by Cheesemill on 2013-07-30
Try running this command to write the image...
```
sudo dd if=F18-arndale-201305210148-xfce-uboot-buildin.img of=/dev/sdc ;sync
```

Note that you should be writing it to /dev/sdc not /dev/sdc1.

---

### Post by papibe on 2013-07-30
Hi X8YnhwA.

What filesystem is it?

Have you try formating it using Gparted?

Regards.

---

### Post by mcduck on 2013-07-31
Since its's a microSD card it's probably using FAT filesystem rather than a native Linux filesystem, in which case it doesn't use any inodes (FAT has it's own way of storing file information).

Also dd doesn't operate on filesystem level, it simply handles the raw data on the drive directly, so it couldn't care less about the fielsystem the drive currently has or if there are free inodes or anything like that. So inodes sure aren't the casue of your problem...

---

### Post by X8YnhwA on 2013-08-04
Yup, solved my problem. I didn't know that I should be writing to the partion, not the root.
Although still couldn't un-brick my tablet, thank you.

---

