---
title: "cannot write on a portable hard drive from another computer"
date: 2013-07-16
forum: New to Ubuntu
---

### Post by yaoyueer on 2013-07-16
i started using my new portable hard drive on this ubuntu 13.04 machine. from another machine, i cannot create new folders, due to the permission problem. i can only read the files that exist. i try to go back to ubuntu to change the file permission. i try to do it from "Properties", to provide "others" the access to "create and delete files". it simply flashes back to "none". can somebody tell what the problem is and how to fix it? i would like to use my hard drive from other computers.

thank you!

---

### Post by yaoyueer on 2013-07-16
if it's relevant, i should mention that it's a WD My Book hard drive.

---

### Post by Bashing-om on 2013-07-16
yaoyueer; Hi ! Welcome to the forum.

Your issue is tough to deal with, with out any info;
Let us see what you are working with:
with the hard drive plugged into the ubuntu system,
Post the output - between code tags (#) - top of post --of terminal codes:
```

sudo fdisk -lu 
sudo parted -l
sudo parted /dev/sda unit s print
lsblk -f

```
Once the file systems are determined, we can advise further.
Ubuntu can read/write Windows, Windows can not see ubuntu file system.

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

