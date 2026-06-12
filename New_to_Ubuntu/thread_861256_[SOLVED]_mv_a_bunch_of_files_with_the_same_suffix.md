---
title: "[SOLVED] mv a bunch of files with the same suffix"
date: 2008-07-16
forum: New to Ubuntu
---

### Post by raymondvillain on 2008-07-16
How does one move (mv from a terminal window) a group of files that have unique names but have the same ending?

I know how to use mv, and I know Unix allows the wildcard character *, so I was hoping I could use "mv *.something newdirectory" or something similar, like I used to in a DOS window on the other OS.

Right now I'm using ls -l | grep something > temporaryfilename and then using that text file to laboriously mv each file, one at a time.

Thanks in advance.

---

### Post by dracayr on 2008-07-16
you can actually use *.something (Tadaaa)

dracayr

---

### Post by nothingspecial on 2008-07-16
Say you had a load of jpg files in your pictures folder and you wanted to move them to a folder called "photos" on a hard drive called "disk"

```
mv ~/Pictures/*jpg /media/disk/photos
```

---

