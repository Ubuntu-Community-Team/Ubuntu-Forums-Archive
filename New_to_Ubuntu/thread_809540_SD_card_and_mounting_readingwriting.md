---
title: "SD card and mounting reading/writing"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by natman on 2008-05-27
Hi, I am trying to modify content on sd card write a file to it. But i keep getting the error message 
[HTML]Could not write to /media/disk/..[/HTML]
I then tried
[HTML]natman@natman-laptop:~$ sudo chmod 775 /media/disk
chmod: changing permissions of `/media/disk': Read-only file system
natman@natman-laptop:~$
[/HTML]
That did nothing for me, the i tried using the little lock on the SD card both ways - no difference. If it means anything im using KDE3.5.9

---

### Post by sayakb on 2008-05-27
At a terminal:
```
sudo mkdir /media/disk
sudo mount -t /dev/mmcblk0p /media/disk
gksudo dolphin
```But first, do ```
sudo fdisk -l
``` (Doesn't always need sudo)
And check your MMC's device link and replace /dev/mmcblk0p with that one.
Plus work only with the root dolphin window while writing to the MMC card.

---

### Post by KingTermite on 2008-05-27
If you find the "settings" media like that (used to be STORAGE tab for "removable drives and media" or whatever that app is called) in 8.04, let me know where it is.

I have a thread about asking for it, but no answers.
[http://ubuntuforums.org/showthread.php?t=808107](http://ubuntuforums.org/showthread.php?t=808107)

---

### Post by natman on 2008-05-27
No that dint do anything for me

---

### Post by sayakb on 2008-05-27
> **natman said:**
> No that dint do anything for me
What didn't do anything? :confused:
Did you follow the exact procedure? And remember using dolphin as root for writing on the MMC..

---

### Post by natman on 2008-05-27
> At a terminal:
Code:

sudo mkdir /media/disk
sudo mount -t /dev/mmcblk0p /media/disk
gksudo dolphin

But first, do
Code:

sudo fdisk -l

(Doesn't always need sudo)
And check your MMC's device link and replace /dev/mmcblk0p with that one.
Plus work only with the root dolphin window while writing to the MMC card.
__________________
did not help, i then tried
> sudo mv afile /media/disk
and got the following
> natman@natman-laptop:~/Videos/Lost$ sudo mv Lost401_the_begining_of_the_end.avi
mv: cannot create regular file `/media/disk/Lost401_the_begining_of_the_end.avi'
natman@natman-laptop:~/Videos/Lost$  

---

### Post by sayakb on 2008-05-27
Have you checked your card's integrity? Backup its data and format it using gparted. Then try again.

---

