---
title: "[ubuntu]hard drive naming in ubuntu"
date: 2015-02-18
forum: New to Ubuntu
---

### Post by manas_mangaonkar on 2015-02-18
so i am new to ubuntu and was learning shell,so how does hard drive naming work in ubuntu .... since i couldn't change directories

---

### Post by nerdtron on 2015-02-18
> since i couldn't change directories 

What do you mean you can't change directories? Are you navigating on the command line? What is the error? Do you have any spaces on your file path?

To get a picture of your hard drive naming and layout you try the following from the terminal:
```
lsblk
df -h 
```

Or you can use the GUI tool Disk to see your partitions and their names.
Drives are probably /dev/sda, while partitions are /dev/sda1 and so on.


Also, you don't navigate directly on the hard drive like you are used to in windows.
For example, if your hard drive is /dev/sda3, you don't go directly to /dev/sda3. You will instead go to directory on which the partition is mounted like for example /media/username/SeagateDrive.

---

### Post by ajgreeny on 2015-02-18
Separate physical hard drives are given a totally different naming convention in Linux to that in Windows, so you can forget all about the C drive and D drive as they will get you completely confused, and in windows what are shown as drives are most often just separate partitions on a single hard drive.  In Linux we use /dev/sda for the first hard drive, /dev/sdb for the second hard drive, and so on.  Partitions on those drives are /dev/sda1, /dev/sda2, and so on; all very simple when you know the system.

You don't name or label hard drives; you name or label the partitions on it if you want to, which can be done with gparted.  In cli I presume you can also do it with parted, though I can't find out how after searhing in the **man parted** manual.

For any Linux filesystem partitions, eg ext4, you can add labels to partitions with ```
sudo tune2fs -L [COLOR=#ff0000]*labelname*[/COLOR] /dev/[COLOR=#ff0000]*sdx#*[/COLOR]
```change labelname and sdx# to your situation, obviously.

---

