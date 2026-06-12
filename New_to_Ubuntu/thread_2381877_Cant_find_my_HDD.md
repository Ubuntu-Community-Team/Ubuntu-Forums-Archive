---
title: "Cant find my HDD"
date: 2018-01-06
forum: New to Ubuntu
---

### Post by mac187 on 2018-01-06
Hi, i just installed clean windows, then i made partition and installed Ubuntu. This two partition is one HDD, i have another HDD in my laptop where i store all my stuffs.

Problem is..

I can acsess my HDD from unity launcher, i can make write and read, but in terminal i cant find my hdd where i store all my stuff in /media or /mnt , nothing there, how to solve this? thank you

---

### Post by Holger_Gehrke on 2018-01-06
After opening the drive in the file manager it should be accessible from the terminal,too. But if you don't want to use the file manager just for that, you can do the mounting from the command line too. Use the command ```
lsblk -f
``` to get a list of all block devices including the file systems on them, their labels, their UUIDs and their mount points (don't assume the device names are constant; they can change from one boot to the next; if I forget to unplug a specific USB-hard-disk from my machine before booting, it will be sda on boot instead of my internal hd). There should be at least one partition with a fs-type and a UUID (and possibly, if you've given it one, a label) which does not have a mount point listed. Mount this one with the command 
```
udisksctl mount --block-device /dev/XXXX
``` replacing XXXX with the name of the device from the output of lsblk, probably something like 'sdb1'. udisksctl will print out the path for accessing the drive on successfully mounting it or print out an error-messsage, To unmount the file system after you're done with it, the command is ```
udisksctl unmount --block-device /dev/XXXX
```

Holger

---

