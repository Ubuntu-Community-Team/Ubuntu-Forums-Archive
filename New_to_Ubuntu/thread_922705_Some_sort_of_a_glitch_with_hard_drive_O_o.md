---
title: "Some sort of a glitch with hard drive? O_o"
date: 2008-09-17
forum: New to Ubuntu
---

### Post by zloygame on 2008-09-17
I have 3 partions on a  hard drive (one for windows (c), another for files (d), and the third one for ubuntu (u). 
So I made some shortcuts etc for the first and second partitions, and I chose my partition for files in a torrent client as a folder for my downloads. So here is the thing - everytime I restart my computer all those shortcuts are gone and when I open my torrent client it says that there is no such folder as "d". So I need to put all those shortcuts and look for those partitions on my computer etc. 
Why? Is there smth wrong with my computer or it is smth with ubuntu?

---

### Post by Titan8990 on 2008-09-17
Your post is a bit confusing. You mention drive letters yet Linux does not have the drive lettering scheme that Windows has. I would say this is a misconfiguration and not a bug with Ubuntu.

You should be specifying the mount point of a drive as drives can not be accessed directly in Linux (atleast not in the same way as you do in Windows).

---

### Post by zerhacke on 2008-09-17
Which OS are the icons disappearing from?

And what is a smth?

---

### Post by zloygame on 2008-09-17
to access those partitions from ubuntu I have to go /media and there I have a folder "disk" (its a partition with windows) and "disk-1" (a partition with files)

PS smth = something 
lol

---

### Post by kansasnoob on 2008-09-17
If this shared partition is ntfs try adding ntfs-config to Ubuntu.

```
sudo apt-get install ntfs-config
```

Otherwise a screenshot of Gparted would really help.

---

### Post by karlr42 on 2008-09-17
> **zloygame said:**
> to access those partitions from ubuntu I have to go /media and there I have a folder "disk" (its a partition with windows) and "disk-1" (a partition with files)
I think your problem is that in My Computer in Windows you see three partitions, C:/, D:/ and U:/, so in Ubuntu you use those names to set shortcuts. That won't work, **only Windows is calling then C D and U., Ubuntu calls them /, /media/disk and /media/disk-1.**
Change the shortcuts to /media/disk and /media/disk-1. The drive letters you have and see in Windows don't apply in linux. Ubuntu calls the partition /media/disk, Windows calls it D:/ So in Ubuntu, make sure you refer to them properly

---

### Post by zloygame on 2008-09-17
I refer to them properly, cuz when I was making shortcuts etc I was selecting the folders from the media folder =\
I was using names c d and u only to make it more clear here, cuz if I was calling it first second and third partition it would be more confusing. 

> Otherwise a screenshot of Gparted would really help.

What do u mean? I didnt understand that (sorry, its just that I'm new to ubuntu)

---

### Post by karlr42 on 2008-09-17
Sorry about that, then! 
So, when you do a fresh reboot of Ubuntu, can you see your partitions? Are they in Places(top right of the desktop)?

---

### Post by skymera on 2008-09-17
Wrong topic :(

Please delete

---

### Post by PocketDog on 2008-09-17
Your torrent client won't see the Windows partition - or the files partition if it's NTFS - until you mount it/them, which you do when you access them through Nautilus. Search these forums for automounting NTFS partitions

---

### Post by zloygame on 2008-09-17
when I do a fresh boot of Ubuntu I can perfectly use them from my Places tab, but for example if I put a shortcut "Torrents" to the Places tab to access a folder with my torrents that is on a partition with files, and then restart ubuntu - this shortcut will be gone=\

> Wrong topic

Please delete

What? Why?

---

### Post by karlr42 on 2008-09-17
OK, sorry for all the questions, just trying to rule things out. Try navigating to whereever this Torrents folder is, then selecting Bookmarks->Add Bookmark. That should create a permanent link on the Places menu.

---

### Post by zloygame on 2008-09-17
right now im tryin to do the automatic mounting of the drives =)

---

### Post by karlr42 on 2008-09-17
Then see my post [here](http://ubuntuforums.org/showthread.php?t=922653). When it says permenant, it means the drive is auto-mounted at boot. Use ```
sudo fdisk -l
``` to see a list of hard drives and partitions. You'll know which sda1, sda2 or whatever are Windows since they will be NTFS type

---

### Post by PocketDog on 2008-09-17
Until you get auto-mounting sorted, which can seem a little daunting at first, all you need to do is access the drive through 'places' before running your torrent client. Just accessing them mounts them automatically, and your client will be able to access them. Until you do that, it can't.

---

