---
title: "Scripting tips"
date: 2011-10-20
forum: Programming Talk
---

### Post by CptSnork on 2011-10-20
Hello!

I would really like to get more into scripting and I have a problem that I'm trying to solve. 

I am not familiar enough with all the apt packages that are out there to make this any easier but this is what I'm trying to do. 


[LIST=1]
[*]Insert usb drive and have it formatted to FAT
[*]Copy X folder onto the drive (this is optional > and then "safely eject")
[/LIST]

My biggest problem is the mounting and formatting the appropriate devices. It would be nice if I could use 3 usb sticks at a time... I just don't know where to begin :(. Do I just use a Bash script or something else?

---

### Post by gsmanners on 2011-10-20
Bash script would be the way to go, I guess:

```
mkdosfs -n DRIVE01 /dev/sdf9
mount -t vfat /dev/sdf9 /mnt/x
cp -r /path/to/xfolder /mnt/x
umount /mnt/x
eject /dev/sdf9
```

I'm not too sure the above will work, and you'd have to run as root, make the mnt directory before running, etc.

---

