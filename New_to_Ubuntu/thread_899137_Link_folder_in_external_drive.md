---
title: "Link folder in external drive"
date: 2008-08-24
forum: New to Ubuntu
---

### Post by einstein2001 on 2008-08-24
This is my first post in a forum. I am a noob to Linux and I love it. It defiantly takes more effort but is so much more rewarding.

Ok, I am trying to link a folder located in my external hard drive to my HOME folder.
The folder I want to link is /media/BLACKBERRY/music
BLACKBERRY is the drive and music the folder.
When I right click>make link i get "Error making symbolic link: Operation not permitted"
When I right click the folder properties>permissions and set the file acess to read&write it just reverts back to --.

Any suggestions?

---

### Post by aloshbennett on 2008-08-24
Could you try it from the command prompt?

Go to the folder where you want the link to be created
> cd /home/einstein/music

and create a softlink from there to the blackberry drive
> ln -s /media/BLACKBERRY/music blackberry

---

### Post by einstein2001 on 2008-08-24
Wow, it was just that easy. Worked perfectly.
So I take it "ln" is the link command. What does the "-s" denote?

---

### Post by bab1 on 2008-08-24
It sounds like you have not mounted BLACKBERRY/music to /media via fstab (hard mount).  Symlinks are not allowed on vfs(soft (GUI)) mounts.

---

### Post by eightmillion on 2008-08-24
The -s option tell it to make a symbolic link. It's analogous to a shortcut on windows. [This link]("http://www.linuxclues.com/articles/17.htm") is a good primer on the differences between symbolic and hard links.

---

### Post by einstein2001 on 2008-08-24
I have attempted to "hard mount" my blackberry via fstab with no sucsess.
Could you show me how via commandline?

---

### Post by eightmillion on 2008-08-24
Could you post the output of these two commands please?
```

sudo fdisk -l
mount
```

---

### Post by einstein2001 on 2008-08-24
eightmillion here are the results of those commands:

einstein2001@planet-Earth:~$ sudo fdisk -l
[sudo] password for einstein2001: 

Disk /dev/sda: 6448 MB, 6448619520 bytes
255 heads, 63 sectors/track, 784 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xea1aa9c7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         784     6297448+  83  Linux

Disk /dev/sdb: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdc64ad79

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         127     1020096   82  Linux swap / Solaris
/dev/sdb2             128       12161    96663105   83  Linux

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       38913   312568641    c  W95 FAT32 (LBA)

Disk /dev/sdd: 2032 MB, 2032664576 bytes
37 heads, 31 sectors/track, 3461 cylinders
Units = cylinders of 1147 * 512 = 587264 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1              14        3462     1977090+   6  FAT16

---

### Post by eightmillion on 2008-08-24
Could I get the output of **sudo blkid** also please?

---

### Post by einstein2001 on 2008-08-24
Ah ha. I was wondering what the BLACKBERRY was recognized as in linux. Looks like the sdd. I'll try to mount that instead of "BLACKBERRY".

---

### Post by einstein2001 on 2008-08-24
einstein2001@planet-Earth:~$ sudo blkid 
/dev/sda1: UUID="a27d2ed1-285a-483e-8954-a04ec188a3d1" TYPE="ext3" 
/dev/sdb1: TYPE="swap" UUID="d105bd97-9129-4223-8f80-50d381c54ec4" 
/dev/sdb2: UUID="f1887f51-e959-4950-a240-cf58943b09f4" TYPE="ext3" 
/dev/sdc1: LABEL="340GBIATCH" UUID="153B-BB9C" TYPE="vfat" 
/dev/sdd1: SEC_TYPE="msdos" LABEL="BLACKBERRY" UUID="0118-15AF" TYPE="vfat"

---

### Post by eightmillion on 2008-08-24
You're going to need to add this line to your fstab file by running **gksudo gedit /etc/fstab** and pasting the line and saving the file.

```
UUID=0118-15AF /media/BLACKBERRY vfat user,auto,rw 0 0
```
Then unmount your blackberry manually with ```
sudo umount /media/BLACKBERRY
```
Then you can run this command and check whether it mounts alright and you don't get any errors:
```
sudo mount -a
```

---

### Post by aloshbennett on 2008-08-24
When you right click and create a link, the link is created in the same folder.
Here, you are trying to create a link on the BLACKBERRY file system, which I believe will not work.

---

