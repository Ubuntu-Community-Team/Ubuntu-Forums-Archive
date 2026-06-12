---
title: "Reformatting External"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by ssharps711 on 2008-06-05
So, I've had it up to here with this external... Let me explain. 

It's a 250gb external 128.8gb free and 104.0gb used. I can't see the files on it though after a crash. I actually found them with Data Recovery Wizard though. Now I can't remove them because I can't see them any other way. 

Anyhow, my question. I need to remove all of these files. Already tried Show Hidden Files. Should I just reformat orrrrr? What I need suggestions. 

I would like to just reformat but I'm clueless as to how I should do that. GParted is taking forever to Scan the Devices. 

I want to completely wipe the crap out of it and reformat.

---

### Post by ssharps711 on 2008-06-05
Bump

---

### Post by ajgreeny on 2008-06-05
No problem.  Just attach it to your main computer, unmount it if it automounts, and use gparted (Partition Manager in the menu) to reformat it to whatever you want.  If it is for both windows and linux use either NTFS or FAT32, but if it's for linux alone go for ext3, which is much better at keeping permissions and owner/group than the windows filesystems.

---

### Post by sam_delta on 2008-06-05
if you want to format, first find out which device is your harddrive by typing ```
fdisk -l
``` (if your in debt, post the ouput here)

 then once you find which device is your hard drive,  to format it to ext3 file system just type ```
sudo mkfs.ext3 /dev/sda1
``` where sda1 is the device partition (you got this from fdisk -l, again, if in dubt, post the ouput of "fdisk -l" here and we will help you)

to format it to fat32, use the following command ```
sudo mkfs.vfat -F 32 /dev/sda1
```  where sda1 is the device partition (you got this from fdisk -l, again, if in dubt, post the ouput of "fdisk -l" here and we will help you)


sam

---

### Post by sam_delta on 2008-06-05
you can also open gparted targetting a specific device,, from my post above, find your device  and then open gparted targetting your speciffic device by typing ```
sudo gparted /dev/sda1
``` where sda1 is your device (usb drive)

sam

---

