---
title: "How do I get to see the other drive?"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by mark.tj on 2008-08-11
Just installed Ubuntu Server 8.04 onto a system with 2 identical ATA hard drives. From my Windows workstations I can only see the one drive 270gb (it is a 300gb drive but I assume Ubuntu takes up some of the room) But cannot see the other 300gb???

I have tried re-installing 4-5 times with different options but all with the same result. Is my Windows system lying to me? (wouldn't be the first time) or am I doing something stupid? The install process sees both drives as does Ubuntu now, so how can I use the extra space from the workstation, I want it to store Video so need all the room I can get.

Really pulling my hair out with this one so any help would be very much appreciated.

---

### Post by halitech on 2008-08-11
when you installed, did you tell Ubuntu to use 1 complete drive?

---

### Post by ntu on 2008-08-11
In my Feisty I go Places>Computer and all the partition icons are sitting there.

---

### Post by mark.tj on 2008-08-12
I tried all options when installing including one complete drive, the current install was done manually for each drive using the auto option to decide the partition sizing. 
As for viewing the drive in something like "My Computer", I have no GUI in the server version so I am using WIndows from another machine to view the server and it can only see 270mb which is what is confusing me.

---

### Post by hyper_ch on 2008-08-12
Post the output of:
```

sudo fdisk -l

```

---

### Post by mark.tj on 2008-08-12
Just looked at /etc/fstab and it only mentions one of the drives, reads as follows;

proc /proc proc defaults 0 0

;/dev/sdb1
UUID= 296b9e21-84e7-4396-95ad-ce3cb711f156/ ext3 relatime erro$
;/dev/sdb5
UUID= eccd537f-d324-4187-b685-969ef0d4de99 none swap sw $

My drive ID's are /dev/sda and /dev/sdb

Anyone know how /etc/fstb should read? and would simply changing this work, the drive should already be formatted for the system to be able to see it.

---

### Post by mark.tj on 2008-08-12
OK fdisk -l dump as follows, (have to hand key as this is all on another machine so I missed out the stuff about the disk sizes etc)

/dev/sda

device    boot    start       end     blocks      id    system
/dev/sda1  *      1          36296   291547588+  83   linux
     sda2      36297       36483   1502077+    5    extended
     sda5     36297       36483   1502046     82 linuxswap/ solaris

/dev/sdb

device    boot    start       end     blocks      id    system
/dev/sdb1         1          36296   291547588+  83   linux
     sdb2      36297       36483   1502077+    5    extended
     sdb5     36297       36483   1502046     82 linuxswap/ solaris

Is this enough info?

---

### Post by hyper_ch on 2008-08-12
it helps very much to the readability if you enclose terminal output and file contents in [noparse]```

```[/noparse] brackets.

---

### Post by dentharg on 2008-08-12
Everything looks pretty good. You see 270GB since the /dev/sda1 is ca. 270GB (291547588 / (1024 * 1024) = 278.xxxx).

If you have mounted partitions of just one drive how would you like to see the other? Mount them and share via samba or so.

---

### Post by mark.tj on 2008-08-12
```
/dev/sda

device boot start end blocks id system
/dev/sda1 * 1 36296 291547588+ 83 linux
sda2 36297 36483 1502077+ 5 extended
sda5 36297 36483 1502046 82 linuxswap/ solaris

/dev/sdb

device boot start end blocks id system
/dev/sdb1 1 36296 291547588+ 83 linux
sdb2 36297 36483 1502077+ 5 extended
sdb5 36297 36483 1502046 82 linuxswap/ solaris
```

---

### Post by hyper_ch on 2008-08-12
well, taking the previous posting and putting it in code tags does not add to the readability as the multiple spaces / tabs have already been filtered.

---

### Post by mark.tj on 2008-08-12
Thanks for that, should I use /etc/fstab to mount the drive tho?

Sorry about the code but I am having to re-key not cut and paste

---

### Post by hyper_ch on 2008-08-12
> **mark.tj said:**
> Sorry about the code but I am having to re-key not cut and paste
Just telling you that because you need to "help" people that try to "help" you ;)

---

### Post by mark.tj on 2008-08-12
Thanks I am very enthusiastic but very much an amateur in this area so any help is very much appreciated.

---

### Post by dentharg on 2008-08-12
First: how do you browse drives on Windows? Samba?

Mount the drive by hand first (mount -t auto /dev/sda1 /mnt/some_dir) and share the some_dir in Samba.

---

### Post by mark.tj on 2008-08-12
Thanks for helping me, I just use Windows explorer to browse files on the server as it is only used like an external hard drive at the moment although I hope to expand its use so I can access over the Internet later. My main computer is Vista we also have a number of XP systems in the house (2 teenage kids, laptops etc)

Tried the command mount -t auto /dev/sda1 /mnt/some_dir
but get the response "mount point /mnt/some_dir does not exist" DO I need to create something in samba first?

Sorry but I really am a newbie here and may not get something that is obvious to everyone else

---

### Post by hyper_ch on 2008-08-12
first you have to create the directory into which you want to mount something:
```

sudo mkdir /mnt/some_dir

```

---

### Post by mark.tj on 2008-08-12
Directory created and mounted but not sure how to share in samba

---

### Post by hyper_ch on 2008-08-12
open nautilius, then right-click the folder and then you should be able to share it... (I think)... not done gui-sharing for a long time. Also make sure that you have permissions on that folder to share it.

---

### Post by mark.tj on 2008-08-12
All sorted and sussed thanks

---

