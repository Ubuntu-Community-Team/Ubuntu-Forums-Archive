---
title: "cant access windows partition..."
date: 2008-08-16
forum: New to Ubuntu
---

### Post by waggingwabbit on 2008-08-16
I can't get into my windows partition. windows gets to the windows logo, then it hangs in a blank screen. safe mode doesn't work either. and I can't repair windows. I've already tried it with the disk, and it gets stuck for hours on searching for a copy of windows thats already installed or something like that. I want to try to access my files through ubuntu before nuking it so I could actually reinstall again. but i cant access the partition because it says i didn't shut down windows properly the last time i was in it. I can't get back and and get out properly...is there any way around this?

---

### Post by Rolcol on 2008-08-16
You can force mount the partition.  If you try mounting it using the GUI, click on the details arrow and it should give you a command to mount the partition forcefully.  It should be something like:```
sudo mount -t ntfs-3g -o force /dev/sdXX mountpoint
```

---

### Post by dodle on 2008-08-16
Is your computer a Dell laptop by any chance?  Your problem sounds identical to an issue my brother-in-law had with his.  It turned out to be hardware related.

---

