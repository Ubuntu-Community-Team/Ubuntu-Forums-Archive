---
title: "[SOLVED] is_audio_device.txt Forgot exactly what it is called."
date: 2008-11-28
forum: New to Ubuntu
---

### Post by barbedsaber on 2008-11-28
Am in a hurry.
I have an mp3 player that is not recognized by HAL, and in the past I have placed an empty txt file on it. I do not remember the name of the empty txt file that I put there, and am turning up blanks with google.
Am in a hurry, please help.

(It has worked in the past, but I don't remeber if it was underscores, hypehnes, and if it was is audio device, or player)
I get a fail in google.

---

### Post by ajgreeny on 2008-11-28
Is the player found if you run ```
sudo fdisk -l
``` in terminal?  If it is you may be able to mount the player manually using the mount command, and then copy the files you find.

---

### Post by barbedsaber on 2008-11-28
it mounts, just not as an mp3 player.
I have to copy the files on manualy, and can't see it in banshee.

---

### Post by ajgreeny on 2008-11-28
> it mounts, just not as an mp3 player.
I have to copy the files on manualy, and can't see it in banshee. 	So what did you expect?  Sorry, but I don't see what your problem is exactly.  Banshee will not see or display an empty txt file, it is a music player.  What do you want to do with the file(s) on the player?  If you simply want to move, copy, or delete them you can do that in nautilus after mounting the player.

---

### Post by barbedsaber on 2008-12-01
In the past, I have made a blank text file, with a name which I now forget. This convinced HAL (I assume) that my mp3 player is infact an mp3 player, and not a usb thumb drive.
This allowed banhee to recognize it as such. 
Found the page
[http://wiki.banshee-project.org/Guide/DAPs/MassStorageDevices](http://wiki.banshee-project.org/Guide/DAPs/MassStorageDevices)
this is what I ment, so never mind.

---

