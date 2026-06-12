---
title: "delete all empty conf files"
date: 2014-01-22
forum: New to Ubuntu
---

### Post by rburkartjo on 2014-01-22
is there a command or a program that will let me delete all empty config files in the home folder at once. been looking and cant find. tks

---

### Post by Dennis N on 2014-01-22
```
find ~/ -size 0c -type f -name "*.conf" -exec rm {} \;
```

would find files with extension .conf and size=0 bytes and delete them. For trial run, change rm to echo to see what would be deleted, since there are no do-overs. Change .conf to other extensions that you want to check.

---

### Post by rburkartjo on 2014-01-22
den tks ran it. however there are still config files there. i saw a post a few years ago and how to do but must of deleted my bookmark

---

### Post by Dennis N on 2014-01-22
If (and only if) the file meets **all** these conditions it will be deleted. Guaranteed. Check the suspect files carefully to find which condition(s) were not met.

1) The file is in your **home folder** (including subfolders)
2) The file is **0 bytes** in size.
3) The file name ends with **.conf**
4) The file is a regular file (not a directory, symlink, or something else).
5) You need permission to delete the file (write permission) for the **rm** part to work.

[890]

---

### Post by rburkartjo on 2014-01-22
my bad guys. i am also trying to delete all folders in  /home/ray/.config that are empty(the application is no longer installed) and those files dont end with .conf example the folder brasero still lives on in /home/ray/config even though i have long since deleted the app.

---

### Post by steeldriver on 2014-01-22
You could use the find -empty test (matches zero length plain files and empty directories) e.g.

[COLOR=#ff0000]**WARNING! THIS WILL SHOW ABSOLUTELY NO MERCY! THERE IS NO BACKOUT SO MAKE SURE YOU REALLY MEAN IT!**[/COLOR]
```
find /home/ray/.config -empty -print -delete
```
(the -print is only there to give a record of what you've done - you can remove it if you really don't care). Somewhat safer would be
```
find /home/ray/.config -depth -empty -exec rm -ri {} \;
```
which will prompt you for confirmation of each removal.

---

### Post by rburkartjo on 2014-01-23
steel tks that was what i was looking for. much appreciated

---

