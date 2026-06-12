---
title: "[SOLVED] HD Deleted"
date: 2008-07-05
forum: New to Ubuntu
---

### Post by adobrakic on 2008-07-05
My computer was working fine until I restarted it, then I was getting an error that said, something about a disk read error or something. I can restart to get the exact message. I had to boot into live-cd to get on the website.

I went into GParted, and it only shows an unallocated part, and nothing else.

---

### Post by adobrakic on 2008-07-05
I just checked "places" and i can still mount my windows and linux partition. I went to check the grub menu, and nothing's there. is there a default file i can just copy into it?

---

### Post by DGortze380 on 2008-07-05
need a little more information. how long ago did you install?? What were you doing yesterday? today right before you restarted? is data recovery a priority?

sounds like maybe you were running off a live cd all along? hard drive definitely didn't delete itself, so you must have done something to delete the partition?

---

### Post by adobrakic on 2008-07-05
I installed winxp dual boot with ubuntu already installed. I wasn't home yesterday, my sister was and she said she didn't do anything with the computer. Yeah, it is a priority because I don't feel like re-doing everything.

And no, I haven't been running off the live-cd, that'd be a big thing to miss. It seems as if something happened to grub menu.

---

### Post by cariboo on 2008-07-05
If you installed win XP after installing Ubuntu you are going to have to setup grub again, it is probably a lot easier if you run in a terminal:

```
sudo aptitude reinstall grub
```

Also have a look at this thread:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Jim

---

### Post by adobrakic on 2008-07-06
Okay, well my HD isn't deleted, I overreacted. :D
I get the following error when I try to boot up my computer:

```

non-system or disk error,
replace and strike any key

```

The only way I can boot up is by getting into the live-cd and going to "boot from hard disk" or whatever the last option says.

I tried:

```

sudo aptitude reinstall grub

```

but it still gives me that error. 

My 'sudo fdisk -l' gives me:

```

Disk /dev/sda: 60.0 GB, 60060155904 bytes
255 heads, 63 sectors/track, 7301 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfcb1ec06

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        4884    39230698+  83  Linux
/dev/sda2   *        5654        7031    11068785    7  HPFS/NTFS
/dev/sda3            7032        7301     2168775    5  Extended
/dev/sda4            4885        5653     6176992+   7  HPFS/NTFS
/dev/sda5            7032        7301     2168743+  82  Linux swap / Solaris

Partition table entries are not in disk order

```

and when i try 'cat /boot/grub/menu.lst', i get:
```

cat: /boot/grub/menu.lst: No such file or directory

```

---

### Post by cariboo on 2008-07-06
There probably isn't that particular file on  the live cd you have to mount your linux partition:

```
sudo mount /dev/sda1 /mnt
```

then try:

```
cat /mnt/boot/grub/menu.lst
```

Jim

---

### Post by Fixman on 2008-07-06
Are you booting from the hard disk? Maybe theres a floppy disk on your computer.

---

### Post by adobrakic on 2008-07-06
> **cariboo907 said:**
> There probably isn't that particular file on  the live cd you have to mount your linux partition:

```
sudo mount /dev/sda1 /mnt
```

then try:

```
cat /mnt/boot/grub/menu.lst
```

Jim

Well, I can get on my normal ubuntu, I just have to go through live-cd first. Should I get on live-cd and do those commands, or normal ubuntu?


> 
Are you booting from the hard disk? Maybe theres a floppy disk on your computer. 


Nah, i haven't even seen floppies in like 4 years. :lolflag:

----edit (omfg)----

Wow, just wow. You were completely right. My sister left a floppy disk in the floppy disk..thingy, and it was trying to boot up at the beginning. If i could delete this topic, i so would right now. :x

*walks to the hall of shame..*

:p!!

---

### Post by Fixman on 2008-07-07
Don't worry, that happens all the time.

---

