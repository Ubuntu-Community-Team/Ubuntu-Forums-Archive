---
title: "[SOLVED] drives not mounting under Hardy Heron"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by corkscrew on 2008-06-01
I have just upgraded to Hardy Heron (clean install). My laptop hdd is dual boot with XP. One of my xp partitions is where i store my data, under gutsy gibbon this drive mounted automatically when i started GG. Under HH this does not happen. I have to go to places 1st select computer, or select the drive itself from the menu it will then mount the drive ok.

Is there anyway to make it mount automatically under Hardy Heron the same as in Gutsy Gibbon?

---

### Post by primky on 2008-06-01
1.)
> sudo fdisk -l
And you'll get back every partitions/disks.
Let's say you want to automount sda1.

2.)
> sudo mkdir /media/ntfs1

3.)
> sudo gedit /etc/fstab

add this at the end:
/dev/sda1       /media/ntfs1 ntfs-3g silent,umask=0,locale=en_US.utf8 0 0



Repeat this for other disks.

---

### Post by Hozza on 2008-06-01
If all else fails, you may have to reinstall ubuntu

---

### Post by groeswenphil on 2008-06-01
I Picked up on that thread . I tried following that.....this is what I got:-

sudo fdisk -l 


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2e892e89

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9585    76991481    7  HPFS/NTFS
/dev/sda2            9586       10801     9767520   83  Linux
/dev/sda3           10802       19190    67384642+  83  Linux
/dev/sda4           19191       19457     2144677+  82  Linux swap / Solaris
THEN$ sudo mkdir /media/ntfs1 
THEN~$ sudo gedit /etc/fstab/dev/sda1 /media/ntfs1 ntfs-3g silent,umask=0,locale=en_US.utf8 0 0

** (gedit:6050): WARNING **: Hit unhandled case 19 (Not a directory) in gedit_io_loading_error_message_area_new.

Where did I go wrong?
Phil

---

### Post by corkscrew on 2008-06-01
hmm tried that and it wont mount at all could it be because the patition has label ACERDATA this what shows up in the places menu

---

### Post by ajgreeny on 2008-06-01
Interestingly, when I installed Gutsy, six months ago, it auto mounted my XP partition and I edited fstab to stop that happening as I like to keep things totally separate.  A few weeks ago when I installed Hardy, the XP partition was not auto mounted,so it was just as I like it to be.

Has the default changed with this version or was it just a glitch (in my favour this time) in the installation of Hardy?

EDIT  Just seen primky's post.  He meant to add that line to the end of your fstab file, not to the end of the command you gave in the terminal.```
 sudo gedit /etc/fstab
``` (it should actually be **gksudo**, not **sudo**)  simply opens the fstab file with admin priveleges so you can edit and then save it.  Try again, adding
/dev/sda1       /media/ntfs1 ntfs-3g silent,umask=0,locale=en_US.utf8 0 0
to the end of fstab.

All this assumes that sda1 is your ntfs XP partition.  If not, change it as appropriate; your fdisk -l output will give you a clue what to use.

---

### Post by corkscrew on 2008-06-01
I have found the solution here
[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

works perfectly

---

