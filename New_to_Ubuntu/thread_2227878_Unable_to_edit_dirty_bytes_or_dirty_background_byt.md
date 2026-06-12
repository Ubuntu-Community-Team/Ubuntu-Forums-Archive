---
title: "Unable to edit dirty_bytes or dirty_background_bytes"
date: 2014-06-04
forum: New to Ubuntu
---

### Post by abcdfv on 2014-06-04
I've been having issues with my USB devices stalling, and after doing some research and coming across: [http://lwn.net/Articles/572911/](http://lwn.net/Articles/572911/) it would seem that editing these two files is a possible solution.

However, even as root gedit won't let me overwrite the files and I'm at a loss for what to do. I also tried vim thinking it may be just a gedit problem, but that didnt help either. If i try to change the permissions for the files in a root nautilus window, they just instantly revert as soon as the permissions window is closed.

I'll try to provide anymore information I can, but my main problem is the USB stalling.

---

### Post by oldrocker99 on 2014-06-04
There is already a great little console editor, nano.

```
sudo nano nameoffile
```

All the commands you need are right at the bottom.

---

### Post by abcdfv on 2014-06-04
Fantastic, for whatever reason it was able to overwrite the original files with no problem, and after playing with the numbers a bit I've now got full speed USB working with no stalls. I set it to both files to 1.5GB for my 8GB RAM system and everything seems flawless now.

---

