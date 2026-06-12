---
title: "Using the Terminal to Copy Files when Having Issues"
date: 2011-12-15
forum: New to Ubuntu
---

### Post by py3ak on 2011-12-15
I need to get some files off my desktop onto a thumb drive.  Problem is, I can't get into the GUI.  I can boot into a terminal window, and that's it.

So how do I:

1. Find out the path for the thumb drive
2. Get the terminal to copy a whole directory to that thumb drive

Alternatively, if I could start Dropbox from the terminal, I could simply get my files out from there.

Thanks!

---

### Post by py3ak on 2011-12-15
Actually a way to start Dropbox from the terminal would be my best bet to make sure I lose nothing too valuable.  Sadly Dropbox did not start automatically.:-\"

---

### Post by wolfen69 on 2011-12-15
Have a live cd handy? You can get the files that way.

---

### Post by idoitprone on 2011-12-15
[https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)
[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)
[http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide)

the first two links will give you the basics to mounting an usb and using the terminal

---

### Post by bodhi.zazen on 2011-12-15
Can you recover your data with a live CD. That would give you a desktop.

---

### Post by py3ak on 2011-12-15
I have the ISO CD I used to install it in the first place, but that's all.

---

### Post by wolfen69 on 2011-12-15
> **py3ak said:**
> I have the ISO CD I used to install it in the first place, but that's all.

Was it the desktop cd or alternate cd? If you installed with a gui, it is a live cd.

---

### Post by py3ak on 2011-12-15
It's the desktop CD but from 2009 - I think the 8.04 release.

---

### Post by py3ak on 2011-12-15
OK, that almost worked.  I am in, and I located my files.  But it says I don't have permission to read them, and of course not to copy them either.  My dropbox and downloads folders have little "unreadable" icons on them.

---

### Post by wolfen69 on 2011-12-15
Do:
```
sudo su
```
then
```
nautilus
```
and you should be able to copy then.

---

### Post by gbrowning on 2011-12-15
Watching this thread.  I am trying to manipulate some files using a live CD (burned yesterday) but am also finding "permission denied" and "operation not permitted"

---

### Post by py3ak on 2011-12-15
It looks like it's working.  Thank you, thank you!

---

### Post by py3ak on 2011-12-15
> **gbrowning said:**
> Watching this thread.  I am trying to manipulate some files using a live CD (burned yesterday) but am also finding "permission denied" and "operation not permitted"

First I got an error message - but when I tried to copy from the window that the nautilus command pulled up it started to work (the windows that I had up before were still a bust).  Now I'm halfway there.

---

### Post by gbrowning on 2011-12-15
Wolfen:  thank you... the sudo su         and then Nautilus will put me on the road to recovery here.

---

