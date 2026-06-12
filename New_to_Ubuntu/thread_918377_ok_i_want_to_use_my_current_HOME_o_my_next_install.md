---
title: "ok i want to use my current HOME o my next install"
date: 2008-09-12
forum: New to Ubuntu
---

### Post by Kedster on 2008-09-12
ok I am want to try linux mint (so i backed upp my personal stuff) and then i downloaded the live CD and ran it then i went to install, and i got to the part where it asks for to partition i got to "manual" then i went and i selected my home partition and clicked EDIT and i changed "do not use" to "ext 2" (that what file system it says it is) and then i set the mount point to "/home" and unselected the format check box and then clicked ok

when i looked at the menu art the format check box was selected how can i make it not format that partition

---

### Post by Jack M. on 2008-09-12
I *think* that it's "Do not use" in the file system box, but "/home" in the "mount as..." column. I could be wrong, though, so make sure first, of course.

---

### Post by Kedster on 2008-09-12
it wont let u select a mount point unless u set its file system i think 
 right now i cant check but i will in like an hour

---

### Post by Locutus_of_Borg on 2008-09-12
you can only use that /home if it is on its own partition

in which case install normally leaving that partition alone, then point your /etc/fstab to mount that partition as /home

if /home is not currently on its own partition, you cannot use the same folder in a new partition, you can replicate your current folder on the new partition though

---

### Post by Kedster on 2008-09-12
Ok so How would i go about > in which case install normally leaving that partition alone, then point your /etc/fstab to mount that partition as /home and umm will my ubuntu home mess around with mint

---

### Post by Locutus_of_Borg on 2008-09-12
just install linux mint onto whatever free space you have at mount point /

boot into mint and set up your account with the same name as what your /home/ directory is

once all set-up is finished and you are logged in normally, open a terminal and enter 'sudo nano /etc/fstab' and enter the location of your /home/ partition and mount it at /home

something like this:

/dev/sda#   /home  ext3  defaults,noatime 0 0


would work fine as long as you change # to what your partition is

now reboot and as long as you are using the same account name all will be fine

---

### Post by doas777 on 2008-09-12
the way i would do it, is to copy your home to disk or network share before performing your install.

then boot into the live CD, and use gparted to delete the existing partitions. then create a partition that will become your home partition. copy your data back to it. be sure to note the device associated (/dev/sda1 or whatever).

then when you install ubuntu select manual partitioning. create an ext2 partition and set it to mount as / . then edit the partiton you created a moment ago to /home. then create one last partition for your swap drive.

if you do this, once the install is done, ubuntu shoudl automatically mount your existing home dir. I personally was suprised how many settings are retained just by saving a home.

good luck,
frank

ps: no idea about mint

---

### Post by Kedster on 2008-09-12
how would i find out what drive and then what command do i use t do it

---

### Post by doas777 on 2008-09-13
> **Kedster said:**
> how would i find out what drive and then what command do i use t do it

you would see it in gparted after you had created the home partition.

to run gparted from a livecd, open a terminal and enter:
```
sudo gparted
```

it's a little like diskmgr in windows or partition magic.

---

### Post by Kedster on 2008-09-13
so my home partition is sda2 and here isthe output to that comand 
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=609ed07a-54a7-414a-9b15-5917439032ad /               ext3    relatime,erro$
# /dev/sda1
UUID=85a07073-a273-47d6-8bdc-b1ccb501705c none            swap    sw           $
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

but i dont no how to do what needs to be done

---

### Post by Kedster on 2008-09-13
umm how can i do this
iv installed mint now and want to get my home do i need to do stuff with the live cd or what

---

### Post by Kedster on 2008-09-14
Ok so like i dont get it what do i need to d to get my home back

---

### Post by C.S.Cameron on 2008-09-14
You can always copy your old home to dvd, reformat your HDD and install ubuntu then merge your old home back into your new home folder.
When you merge do not overwrite any of the files in the new home folder.
You may have to use chown to get permissions.

---

### Post by Kedster on 2008-09-14
tiss 12 gigs 
that 4 dvds 
like i dont mind doin a reinstall but i want to use that partition as my home and id rather have the stuf/setting that are there
is there a way to ghange th mount point of a partition cuz that al i really need to do right

---

### Post by Kedster on 2008-09-14
ok imm gunna start a new tread with a more appropriate name and hopfully get better resualts.

---

### Post by doas777 on 2008-09-17
Sorry man, i've been without power for the last 4 days and couldn't get back to ya.

so your algorithm is to backup your home to DVD or Network. if you can't do that then you are most likely sunk (unless you resize with a liveCD. there's a few good threads on that). then you need to wipe your harddrive and create a new partition (for your home, don;'t use the whole disk)on your nicely slicked hdd. then copy your home files to that partition (the root should contain a folder named for your user). then install your new OS, telling it that you want to partition manually. create your system and swap partitions, and set the mount points for the home partit.
you should be ready to go after that. 

when installing ubuntu you have an option to partition the drive manually. if you select it, you can create several partitions (sys, home, swap) and assign mount points to them. just make your mount point on the home partit, '/home' and it should work fine.

---

