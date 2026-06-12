---
title: "Recovering data using live cd?  Logging in w/ root priveleges?"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by speirint on 2008-06-04
I ran into fsck error #4 [I'm using a dual boot of MSXP and Gutsy Gibbon by the way, and the computer was set to conserve energy (hibernate?) after about 15 minutes of non-use... this led to strange things happening and then a forced check thought the drive was corrupt], and before I do anything to try fixing it, I would like to back up some more of my data.  This error prevents me from using ubuntu and logging in, as well as starting up the x.  However, if I use a live cd, I found that I can mount my drives and copy things out onto the desktop.

Is there a way to modify the data that's in the drives (copy, paste, etc.) while using the live CD?  I used to think it was because I wasn't logged in as root, but when I right clicked a folder to view its properties, the information that is shown says I don't own the computer, and therefore I cannot modify any of the files.  


Is there a way to persuade my computer that I am the owner of it?

Here are threads (where questions are still unresolved for me) that I posted in previously which may be of use for providing more background to the fsck exit status 4, and why my external hard drive is having a hard time working on Ubuntu:

fsck died with exit status 4:
[http://ubuntuforums.org/showthread.php?t=367644&page=6](http://ubuntuforums.org/showthread.php?t=367644&page=6)

acomdata hard drive issues:
[http://ubuntuforums.org/showthread.php?t=386836&page=2](http://ubuntuforums.org/showthread.php?t=386836&page=2)

---

### Post by dracayr on 2008-06-04
open a terminal and type
```
gksudo nautilus &
```


dracayr

---

### Post by Duck2006 on 2008-06-04
This is Knoppix, it may help getting your data back.

[http://www.shockfamily.net/cedric/knoppix/](http://www.shockfamily.net/cedric/knoppix/)

---

