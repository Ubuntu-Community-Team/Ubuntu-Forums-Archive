---
title: "Daemon"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by maheshjr2000 on 2008-11-28
Hello! :D I am having a HUGE problem trying to mount ISO's Cue's and other image files. Is there an application like daemon? I have heard of fstab but I do not think fstab.h is the solution to my problem. the mount command does not seem to work for me and the archive mounter does not read the data correctly. Extracting the files using the archive extractor does not seem to work either.

---

### Post by marshall.robert on 2008-11-28
look for a program called something like gmount in add/remove, that may help you.

---

### Post by hyper_ch on 2008-11-28
```

mkdir /media/MOUNTPOINT
sudo mount -o loop -t iso9660 /path/to/file.iso /media/MOUNTPOINT

```

replace MOUNTPOINT with anything you like.

---

### Post by tarps87 on 2008-11-28
> **marshall.robert said:**
> look for a program called something like gmount in add/remove, that may help you.

I believe the package is called gmountiso so
```
sudo apt-get install gmountiso
```
should install it.
I is a GUI that basically does the same as hyper_ch's suggestion but using buttons

---

### Post by maheshjr2000 on 2008-11-28
This only works on ISOS right? What about .cue or other image files?

---

### Post by hyper_ch on 2008-11-28
if you have a .cue file, just mount the according image with it and not the .cue file... same goes for about any other image.

---

### Post by tarps87 on 2008-11-28
For .cue this thread may help
[http://ubuntuforums.org/showthread.php?t=125482](http://ubuntuforums.org/showthread.php?t=125482)
Or you can convert them to .iso's

---

