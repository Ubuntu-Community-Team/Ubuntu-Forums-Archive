---
title: "New user trying to extract data from laptop hard drive to external drive"
date: 2015-01-05
forum: New to Ubuntu
---

### Post by ericu93 on 2015-01-05
I am having issues using Ubuntu to gain access to my laptop's internal drive. I am not able to access anything through windows 7 which is installed on the laptop. THe hard drive is recognized in the BIOS and also when i access GParted in Ubuntu, but I can't get it to show in the "devices" column. I have been looking around on the internet, but have not been able to figure out how to gain access to the drive. I am using Ubuntu 14.04.1 booting it from a CD.

Thanks in advance for helping.

---

### Post by yancek on 2015-01-05
I'm not sure what the problem is.  Are you not able to boot windows 7?  Are you trying to get data off the windows 7 using Ubuntu?  Did you look in the /media directory when you boot Ubuntu to see if the windows drive is listed there by UUID?

---

### Post by ericu93 on 2015-01-05
hi, 

Yes i am unable to boot windows 7, it will not load safe modes, and keeps trying to do startup repair which does not end up working. I am trying to get the data off of the internal hard drive for my laptop. 

I am still fairly new to Ubuntu so bear with me. How do i look into the media directory? I can see it when i use fdisk -l, or when i open up GParted(shows a UUID in here). Before i was not able to mount it, but i found a command line that allowed me to mount, but the internal hard drive would not show up in the devices area

---

### Post by oldfred on 2015-01-05
If it is hibernated or needs chkdsk which it sounds like it does if it wants repairs, the Linux NTFS driver will not auto mount it to prevent further damage that your chkdsk may not then be able to fix.

You may be able to manually mount in read only mode with a force command.

       sudo mkdir /media/windows
sudo mount ntfs-3g -o rw /dev/<device-name> /media/windows
if you get a message regarding Windows not being shutdown properly, then run the following command to force the mount
But better to run chkdsk from a Windows repair CD first, only use this if you have to copy data.
sudo mount ntfs-3g -o force,rw /dev/<device-name> /media/windows


/dev/<device-name>  is /dev/sda1 or /dev/sda2 or whatever your NTFS partition is. Note space between device & mount point.

---

### Post by ericu93 on 2015-01-05
thank you for the instructions, while i have not run a checkdisk(dont have a recovery CD), i have selected last known good configuration which seems to have helped a bit. My main goal ATM is to recover the data, so i think i will try those commands

---

### Post by ericu93 on 2015-01-05
I tried using the commands above and it says special device ntfs-3g does not exist

---

### Post by oldfred on 2015-01-05
Are you running that from the live installer?

man ntfs-3g
       ntfs-3g - Third Generation Read/Write NTFS Driver

---

### Post by Holger_Gehrke on 2015-01-06
> **ericu93 said:**
> I tried using the commands above and it says special device ntfs-3g does not exist

There's on option missing in the command.
It should be:
```

sudo mount **-t** ntfs-3g -o force,rw /dev/<device-name> /media/windows

```
(ntfs-3g is a **t**ype of file system)
if you're just trying to read data of this disk, you might also want to replace the 'rw' (read and write) in the command with 'ro' (read only), just to be on the safe side.

---

### Post by oldfred on 2015-01-06
@Holger_Gehrke
Thanks for the correction. I have also updated my notes & reread the man page.

---

### Post by coldraven on 2015-01-06
Run the file manager, Nautilus, it's the folder icon second down in the launcher. If you see your drive in the left panel then click it to mount. You should then see your files. You probably have to quit gparted first for this to work.

---

