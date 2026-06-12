---
title: "[SOLVED] Copy /home to another partition"
date: 2008-10-21
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2008-10-21
I read

Copy /home to another partition

at: [http://www.funnestra.org/ubuntu/hardy/](http://www.funnestra.org/ubuntu/hardy/)

[COLOR="DarkOrange"]... What is /home? The /home directory contains a sub-directory for each desktop user (e.g., /home/john, /home/paul, etc.). Each desktop user's files (documents, music, pictures, desktop folder, user-specific desktop- and application-settings, etc.) all go into his or her sub-directory. Thus, if the /home directory resides on a partition different from the one that Ubuntu is installed in, you can re-install the operating system without worrying about blowing away your users' files so long as you don't touch the partition on which /home resides. This is why, if the /home directory currently resides on the sane partition as the operating system, it is wise to migrate it to another partition. In order to perform such a migration, you must first copy the /home directory to the new partition, and then you must switch to the /home directory on that partition.

   1. Copy your /home directory to the desired partition.

      sudo cp -pr /home/* /media/$PARTITION/
--------------------------------------------------------------
where

  * $PARTITION is name of the partition containing the /home directory that you want to switch to.[/COLOR]

I'm copying /home to an external usb harddrive. It is partitioned, into one partition (80 gig). My question is the desktop icon name of this drive is "**80.0 GM Media**" But in /media it shows as:

drwxrwxr-x  3 mark mark  4096 2008-10-21 09:14 disk

Is this disk set up properly? Usually devices for the "end user" don't have so many permissions. (I'm guessing)

What letters to I put into where the cp command wants to see the operand $PARTITION?

How do I make the space between the .0 G and the M M? And even better:

How can I rename the drive to something that has no spaces in the name and still have the OS happy?

Also, will using gksudo nautilus to change the permsssions of this drive last permanently, or only for this session? I need to change the permissions permanently.

---

### Post by stephanvaningen on 2008-10-21
Ok, '1' big question ;-) I'll try:
A: I think usb devices are specifically set up like that in order to have easy write-erpmissions to memory-sticks etc..
B: If your mount is going to /media/disk, you can just use /media/disk in the cp-command: why not?
C:See B: which would not need you to try to 'encode' the "80 M"... in any way, if you would have to encode a name with spaces, you can 'escape' it with a preceding backslash: [start]80 M[end] would be [start]80\ M[end] in a terminal. Example:
```
stephan@living-vib:/media$ sudo mkdir test\ this
[sudo] password for stephan: 
stephan@living-vib:/media$ ls -al
total 28
drwxr-xr-x  7 root root 4096 2008-10-21 19:27 .
drwxr-xr-x 21 root root 4096 2008-10-21 18:48 ..
drwxr-xr-x  2 root root 4096 2008-08-23 23:48 backupdisk
lrwxrwxrwx  1 root root    6 2008-05-05 22:25 cdrom -> cdrom0
drwxr-xr-x  2 root root 4096 2008-05-05 22:25 cdrom0
drwxr-xr-x  2 root root 4096 2008-08-23 23:39 disk
drwxr-xr-x  2 root root 4096 2008-05-05 22:48 ext
-rw-r--r--  1 root root    0 2008-10-21 18:48 .hal-mtab
drwxr-xr-x  2 root root 4096 2008-10-21 19:27 test this
stephan@living-vib:/media$
```  
D: You can mount one external file system more than once on different file system locations. So if you have a device /dev/sdc1 mounted to /media/disk-1, you can re-mount it on /home/user/mymemorysticky and again on /home/user/Desktop/backup using the mount command (sudo-rights needed for that)
E:I think if you want to do that you need to specifically add an fs-tab entry ... hmmmm, not sure, I'll have to investigate that to give more precise information


> **Mark_in_Hollywood said:**
> I read...

[COLOR="red"]A:[/COLOR] Is this disk set up properly? Usually devices for the "end user" don't have so many permissions. (I'm guessing)

[COLOR="red"]B:[/COLOR] What letters to I put into where the cp command wants to see the operand $PARTITION?

[COLOR="red"]C:[/COLOR] How do I make the space between the .0 G and the M M? And even better:

[COLOR="red"]D:[/COLOR] How can I rename the drive to something that has no spaces in the name and still have the OS happy?

[COLOR="red"]E:[/COLOR] Also, will using gksudo nautilus to change the permsssions of this drive last permanently, or only for this session? I need to change the permissions permanently.

---

### Post by jerome1232 on 2008-10-21
What filesystem on is that drive? If you put a partition label it'll start mounting as /media/paritionlabel

The filesystem is important because if it's ntfs or fat it won't retain your posix style permissions and we'll have to copy it a different way to retain permissions.

edit: and btw you would copy everything like this (assuming that drive is ext3 or someother linux file system)

```
sudo cp -pr /home /media/disk
```

---

### Post by Duck2006 on 2008-10-21
You can change the name of the device at the mount point and it will show up as that name.

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by Crandom on 2008-10-21
The name of the usb drive is simply "disk", so it is found at /media/disk . Ubuntu names an unnamed usb drive as "disk" as default, but calls it something obscure in nautilus (the file browsing window). Trust me, this is the command you want:

sudo cp -pr /home/* /media/disk/homebackup

where "homebackup" is a folder. A note: if you are copying to a non-native linux filesystem like FAT, FAT16, FAT32, exFAT or NTFS, all your permissions will be lost. You cannot just copy the files in the backup back to a /home in a new install, as there won't be any permissions on the files. Instead, you would have to use the dd command. Don't use the dd command without instruction or risk breaking your computer.

---

### Post by Duck2006 on 2008-10-21
> Instead, you would have to use the dd command. Don't use the dd command without instruction or risk breaking your computer.

dd commands are very good but, if you not to sure as to how to use them don't use them. Use part image to do the back-up.

[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

[http://www.brunolinux.com/02-The_Terminal/The_dd_command.html](http://www.brunolinux.com/02-The_Terminal/The_dd_command.html)

---

### Post by Mark_in_Hollywood on 2008-10-21
> **jerome1232 said:**
> What filesystem on is that drive? If you put a partition label it'll start mounting as /media/paritionlabel

The filesystem is important because if it's ntfs or fat it won't retain your posix style permissions and we'll have to copy it a different way to retain permissions.

edit: and btw you would copy everything like this (assuming that drive is ext3 or someother linux file system)

```
sudo cp -pr /home /media/disk
```

This disk was formatted ext3 under GParted. It's an msdos disk label.

---

### Post by jerome1232 on 2008-10-21
In that case cp should work fine with the -p flag.


If you want to re-label the partition (has nothing to do with that msdos label you are talking about**don't change that**)

To figure out what's it /dev path is use this command, if your not sure post the output and we should be able to help determine which one is the usb drive.
```
sudo fdisk -l
```

This is how you change the label
```
sudo e2label /dev/path-to-device newlabel
```

---

### Post by Mark_in_Hollywood on 2008-10-21
Relevant part:

Disk /dev/sdd: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000cdf5f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1        9729    78148161   83  Linux

yet, when I look in /dev, there is no usb or 80.0 GB Media names, there are a bunch of "devices" and one is named:

usbdev1.1_ep81

which is one of twenty-four similarly named devices. So yes, a little more help from you, please.

and

mark@Lexington-19:~$ sudo e2label /dev/sdd mp-usb
e2label: Bad magic number in super-block while trying to open /dev/sdd
Couldn't find valid filesystem superblock.

---

### Post by jerome1232 on 2008-10-21
you only need to worry about this if you want to change the label name.

If you look at that output from fdisk, it's /dev/sdd1 so to change the label name:

edit: Are you sure that wasn't sdb1? you have alot of disks if you have a sdd :)

```
sudo e2label /dev/sdd1 newlabelname
```

---

### Post by Mark_in_Hollywood on 2008-10-21
I have one primary master 320 gig drive. It's the only hard drive "on the motherboard"

I have 2 usb memory devices. One is a 1 gig stick and the other is 256 meg. 

The only other device is the external usb 2.0 80 gig drive.

---

