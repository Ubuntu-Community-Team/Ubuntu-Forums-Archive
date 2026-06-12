---
title: "slave drive"
date: 2008-11-26
forum: New to Ubuntu
---

### Post by fossil112 on 2008-11-26
When I startup my machine, my slave drive doesn't automatically "show up".  I have to click Places>DRV2_VOL1.  Then my custom wallpaper picture will load along with my music files for Amarok.  I would think there's a way to automatically mount this drive.  Any suggestions?

---

### Post by Paqman on 2008-11-26
> **fossil112 said:**
> I would think there's a way to automatically mount this drive.

There sure is.

First, what filesystem is the drive? NTFS? EXT3? Something else?

---

### Post by cdtech on 2008-11-26
That makes no sense. If its under places it is mounted. :popcorn:

```
sudo fdisk -l
```
will tell what filesystem it is

---

### Post by fossil112 on 2008-11-26
> **cdtech said:**
> That makes no sense. If its under places it is mounted. :popcorn:

```
sudo fdisk -l
```
will tell what filesystem it is

It doesn't show on my desktop until i click it under places.  why wouldn't it automatically load all necessary files?  (wallpaper, music files, etc)

---

### Post by fossil112 on 2008-11-26
> **paqman said:**
> there sure is.

First, what filesystem is the drive? Ntfs? Ext3? Something else?

ntfs (3.1)

---

### Post by cdtech on 2008-11-26
I'm guessing an "/etc/fstab" issue. Could you post the output of:
```
cat /etc/fstab
```
and:
```
sudo fdisk -l
```
Maybe it has no label, media directories are mounted by label, I don't know without seeing the information.

---

### Post by fossil112 on 2008-11-26
> **cdtech said:**
> I'm guessing an "/etc/fstab" issue. Could you post the output of:
```
cat /etc/fstab
```
and:
```
sudo fdisk -l
```
Maybe it has no label, media directories are mounted by label, I don't know without seeing the information.

Thanks for your help.  Here's the terminal output from each code you've directed me to use:

```
vince@Vince:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=edc50513-bed1-405e-9026-13f28f764d42 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=17ee1064-5c4c-4f5f-ad52-d9b762e155b0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0


```

and


```
Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x83de83de

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4660    37431418+  83  Linux
/dev/sda2            4661        4865     1646662+   5  Extended
/dev/sda5            4661        4865     1646631   82  Linux swap / Solaris

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0156a026

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       24792   199141708+   7  HPFS/NTFS


```

---

### Post by cdtech on 2008-11-26
Try this:
```
sudo mkdir /media/share
```
then:
```
sudo gedit /etc/fstab
**add this line**
# Entry for /dev/sdb1 :
/dev/sdb1 /media/share ntfs defaults,umask=007,gid=46 0 0

```
Then just do a "ctrl + alt + backspace" and log back in. See if it shows on your desktop.

---

### Post by fossil112 on 2008-11-26
thanks so much for your help!  that worked perfectly!  i'll have to go back and retrace the steps and figure out exactly what the coding means.  thanks again!

---

### Post by cdtech on 2008-11-26
Your welcome....

Good luck.

---

### Post by Paqman on 2008-11-26
I'll translate for you if you like:

> 
sudo mkdir /media/share


Makes a directory (mkdir) at /media/share. Since all locations outside /home are owned by root, we need to use sudo to make this happen.

> 
sudo gedit /etc/fstab


Use the application Gedit (a text editor) to open the file at /etc/fstab, we need root priviledges to be able to change the file's contents. Actually, this command should be: gksu gedit /etc/fstab, since we should use gksu for graphical apps and sudo only for command-line ones.

> 
/dev/sdb1 /media/share ntfs defaults,umask=007,gid=46 0 0


/etc/fstab is the File System Table. It contains instructions for which devices to mount and how to do it. In this case:

/dev/sdb = Device: hard drive b
/media/share = the mount point (ie: where this device will show up in the file hierarchy). Stuff in /media pops up on the desktop.
ntfs = the drive's NTFS filesystem
defaults = use default options
umask=007 = this sets some permissions for the files
gid=46 = another permissions thing, this sets a group for the files

> 
Then just do a "ctrl + alt + backspace" and log back in. See if it shows on your desktop.

Ctrl-alt-backspace trashes your session and lets you log in from scratch without having to sit through a whole reboot.

A quicker thing to do have been:
```

sudo mount -a

```

This just tells the system to mount everything in /etc/fstab, including your new line.

---

### Post by cdtech on 2008-11-26
Thank you Paqman, nice explanation.

---

### Post by fossil112 on 2008-11-26
That was a great explanation, Paqman.  Thank you very much.  I learned a lot from your post.

---

### Post by Paqman on 2008-11-26
No problem. There are man pages available for every command, but they're pretty dry, and sometimes it helps to have some real-world practical examples broken down.

Actually Wikipedia has pages for a lot of the more common commands, and they're written in much more useful English than the man pages.

---

