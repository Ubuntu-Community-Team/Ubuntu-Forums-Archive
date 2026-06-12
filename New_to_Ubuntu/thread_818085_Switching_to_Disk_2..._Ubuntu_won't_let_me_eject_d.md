---
title: "Switching to Disk 2... Ubuntu won't let me eject disk"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by giordun on 2008-06-04
So I'm installing NBA Live 06 onto Ubuntu right now (not sure if it works so giving it a try) and the installation has 2 disks. I have finished installing on disk 1 and the installer needs me to use disk 2, but Ubuntu won't let me eject the disk. Anyone got a way I can like force eject the disk?

---

### Post by sayakb on 2008-06-04
```
sudo umount /media/cdrom
```
or
```
sudo umount /media/cdrom0
```

---

### Post by giordun on 2008-06-04
jdan@jdan-desktop:~$ sudo umount /media/cdrom
[sudo] password for jdan: 
umount: /media/cdrom: not mounted
jdan@jdan-desktop:~$ sudo umount /media/cdrom0
umount: /media/cdrom0: not mounted

But like it's mounted.

---

### Post by giordun on 2008-06-04
I tried it with the filename instead of cdrom/cdrom0 and this is what I got.

jdan@jdan-desktop:~$ sudo umount /media/NBALIVE06_1
umount: /media/NBALIVE06_1: device is busy
umount: /media/NBALIVE06_1: device is busy

And I'm stuck on installation. Maybe there just isn't a way to do it?

---

### Post by SunnyRabbiera on 2008-06-04
do you have mounted icons on the desktop?
try right clicking them.

---

### Post by imbjr on 2008-06-04
The trick with this is to run the installation file from the CD-ROM using the command winefile.

winefile will start up a Windows-looking File Manager. Navigate to the CD-ROM's installation file and double-click it. Installation should proceed as if you were doing it in Windows i.e. no messing around with unmount.

---

### Post by The Cog on 2008-06-04
You could try 
```
sudo umount -l /media/NBALIVE06_1
```

---

