---
title: "External Drive Problem"
date: 2014-01-01
forum: New to Ubuntu
---

### Post by kotsosman on 2014-01-01
Hello Ubuntu community

So i intalled ubuntu today in order to back up my files from my W7 pc because windows crashed and i willl reistall them.So i installed ubuntu 13.10 desktop to my flash drive and booted my pc from it.Everything was working great i can see my old files but ubuntu does not "see" my drive, the one i want to back up to.

My drive is a Maxtor 3200.

Any help?How can i make ubuntu see my external drive?

I tried using the driver from another W7 pc but i cant use it either. I get only you could not start the device (code 10)

Thanks in advance and sorry for my bad english

---

### Post by sudodus on 2014-01-01
Welcome to the Ubuntu Forums :-)

We are many people here who are not native English speakers, so don't worry about the English, it is good enough.

Anyway, how did you try to see the external drive? How is it connected (USB, eSATA)?

If you cannot see it in the file browser, I suggest that you try some terminal window commands. Have you tried that before? In Ubuntu you can use the hotkey combination ***ctrl + alt + t***.

Type the command and press the Enter key to run the command. You will get output to the same window, and you can copy and paste it into the editing window of a reply. 'Go Advanced' mark the text and click on the # icon at the top of the editing window to surround it with code tags.

Start with these commands one each time and copy/paste the output. It will make it easier to help.

```

sudo fdisk -lu
sudo parted -l
df

```

---

### Post by kotsosman on 2014-01-01
[FONT=comic sans ms][FONT=arial][/FONT][/FONT]Thanks for taking the time to answer

My drive is connected with a USB cable

Here are the answer to the commands



sudo fdisk -lu.I think these two are my hard drive and the flash drive that i booted from```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
224 heads, 19 sectors/track, 459004 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xdff15214

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848  1953521663   976657408    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 4051 MB, 4051697664 bytes
151 heads, 42 sectors/track, 1247 cylinders, total 7913472 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2968     7913471     3955252    b  W95 FAT32
```

sudo parted -l```
ubuntu@ubuntu:~$ sudo parted -l
Model: ATA ST31000528AS (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  106MB   105MB   primary  ntfs         boot
 2      106MB   1000GB  1000GB  primary  ntfs


Model: JetFlash Transcend 4GB (scsi)
Disk /dev/sdb: 4052MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1520kB  4052MB  4050MB  primary  fat32        boot


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label                                  


```

df ```
ubuntu@ubuntu:~$ df
Filesystem     1K-blocks    Used Available Use% Mounted on
/cow             1551356   67416   1483940   5% /
udev             1541688       4   1541684   1% /dev
tmpfs             310272    1236    309036   1% /run
/dev/sdb1        3947060 2259456   1687604  58% /cdrom
/dev/loop0        881792  881792         0 100% /rofs
none                   4       0         4   0% /sys/fs/cgroup
tmpfs            1551356      16   1551340   1% /tmp
none                5120       4      5116   1% /run/lock
none             1551356      80   1551276   1% /run/shm
none              102400      60    102340   1% /run/user
/dev/sr0         3827190 3827190         0 100% /media/ubuntu/UDF Volume
ubuntu@ubuntu:~$ 

```

---

### Post by sudodus on 2014-01-01
This is a 1 TB disk.

```
Model: ATA ST31000528AS (scsi)
Disk /dev/sda: 1000GB
```

Do you want to connect to it? In that case you can 'always' mount it's partitions with command lines.

Make directories
```
sudo mkdir /mnt/sda1
sudo mkdir /mnt/sda2
```
Mount
```
sudo mount /dev/sda1 /mnt/sda1
sudo mount /dev/sda1 /mnt/sda2
```

And you should be able to see files and directories in the partitions. You could do that with command line tools too, but also with the*** file browser***. Just browse to **[FONT=courier new]/mnt/sda1[/FONT]** and **[FONT=courier new]/mnt/sda2[/FONT]** and continue from there.

You can check with ```
df
``` that the mount works.

---

