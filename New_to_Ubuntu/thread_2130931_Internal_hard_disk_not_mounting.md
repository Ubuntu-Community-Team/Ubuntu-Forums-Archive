---
title: "Internal hard disk not mounting"
date: 2013-03-31
forum: New to Ubuntu
---

### Post by drpudhi on 2013-03-31
Hi,
          I installed Ubuntu 12.10 through DVD. Previously i had Win 7 with 500 GB internal HDD. It had 4 partitions. When installing Ubuntu, i had given the option of replace win 7 with Ubuntu. The installation has been complete. But the problem is, the computer section in Ubuntu shows 500 GB hard disk in the list. But, when i try to open the hard disk it shows error message as unable to mount. Please help.

---

### Post by carl4926 on 2013-03-31
Thee 500GB is the entire HD
Which has been carved up in to partitions by the installer.

You will probably now have 

swap
extended
ext4 /

Open a terminal and post result of

```
sudo parted -l
```

---

### Post by drpudhi on 2013-03-31
> **carl4926 said:**
> Thee 500GB is the entire HD
Which has been carved up in to partitions by the installer.

You will probably now have 

swap
extended
ext4 /

Open a terminal and post result of

```
sudo parted -l
```

Hi, this is what i got...

Model: ATA TOSHIBA MK5075GS (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type      File system  Flags
 1      1049kB  256MB  255MB  primary   ext2         boot
 2      257MB   500GB  500GB  extended
 5      257MB   500GB  500GB  logical                lvm


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu-root: 496GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End    Size   File system  Flags
 1      0.00B  496GB  496GB  ext4


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu-swap_1: 4236MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system     Flags
 1      0.00B  4236MB  4236MB  linux-swap(v1)

[ATTACH=CONFIG]240773[/ATTACH]

---

### Post by carl4926 on 2013-03-31
Oh OK
It used LVM. It's OK. I just never use LVM myself. I prefer standard partitioning.

I'm guessing your confusion comes from the Icon showing the complete HD.
Ignore it.
All your personal files are in /home/username* (*whatever your username is) 
When you open the file browser it should open there: Documents, Music, Pictures.....

---

### Post by drpudhi on 2013-03-31
Yes...Is there a way i can partition the HDD as it used to show in my previous windows? thanks for the help.

---

### Post by carl4926 on 2013-03-31
> **drpudhi said:**
> Yes...Is there a way i can partition the HDD as it used to show in my previous windows? thanks for the help.

Not sure what you mean exactly.
Linux (Ubuntu) is not windows. It uses a completely different file system and set of principles.

However. If it had been me. I would have used Parted Magic to create my partitions. I would have created a standard DOS MBR Partition Table and done:
swap 2GB or 2xRAM
ext4 for /   30GB
ext4 for /home  all the remaining space

Then you install and go this way: [https://dl.dropbox.com/u/10573557/Ubuntu/12.10_tips/12.10_advanced.png](https://dl.dropbox.com/u/10573557/Ubuntu/12.10_tips/12.10_advanced.png)
Then set the mount points as required: [https://dl.dropbox.com/u/10573557/Ubuntu/12.10_tips/12.10_set_root_home.png](https://dl.dropbox.com/u/10573557/Ubuntu/12.10_tips/12.10_set_root_home.png)


Having said that. What you have will work just fine. I'm not sure what it is you feel is missing?

---

### Post by drpudhi on 2013-03-31
> **carl4926 said:**
> Not sure what you mean exactly.
Linux (Ubuntu) is not windows. It uses a completely different file system and set of principles.

However. If it had been me. I would have used Parted Magic to create my partitions. I would have created a standard DOS MBR Partition Table and done:
swap 2GB or 2xRAM
ext4 for /   30GB
ext4 for /home  all the remaining space

Then you install and go this way: [https://dl.dropbox.com/u/10573557/Ubuntu/12.10_tips/12.10_advanced.png](https://dl.dropbox.com/u/10573557/Ubuntu/12.10_tips/12.10_advanced.png)
Then set the mount points as required: [https://dl.dropbox.com/u/10573557/Ubuntu/12.10_tips/12.10_set_root_home.png](https://dl.dropbox.com/u/10573557/Ubuntu/12.10_tips/12.10_set_root_home.png)


Having said that. What you have will work just fine. I'm not sure what it is you feel is missing?

Thanks a lot...Actually what i was expecting was that in win 7 i had four partitions, C:/, E:/, F:/ for my various set of files and OS. Was expecting something of that sort. There even if i re installed the win OS, the files in other partitions other than C:/ will be intact without need for backing up.

---

### Post by carl4926 on 2013-03-31
> **drpudhi said:**
> Thanks a lot...Actually what i was expecting was that in win 7 i had four partitions, C:/, E:/, F:/ for my various set of files and OS. Was expecting something of that sort. There even if i re installed the win OS, the files in other partitions other than C:/ will be intact without need for backing up.


That's why I create /home on a separate partition

Typically Ubuntu doesn't do that, which annoys me

This is what my eeepc looks like
[https://docs.google.com/file/d/0B3e0lLG3OdqEWkJMelpROVUtaFE/edit?usp=sharing](https://docs.google.com/file/d/0B3e0lLG3OdqEWkJMelpROVUtaFE/edit?usp=sharing)

Ignore the SUSE labels. Currently it has Mint and Ubuntu

I use sda9 as a sandbox (Testing)

I have root partitions of about 20GB and /home of 65+GB

So when it comes to a OS upgrade I format / but keep /home as is

---

