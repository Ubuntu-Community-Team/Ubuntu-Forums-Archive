---
title: "Initramfs"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by gandalf2000 on 2008-05-07
Hi all.  I am trying to install 8.04 on my laptop but keep running up against  this:-  (initramfs) .
I installed 8.04 on my hard drive in a 15 gig partition (I hope) but when I boot Ubuntu the above appears and I can't find out what to do about it.  There is plenty of material on the web but nothing that helps me.   What commands do I need to input here?

---

### Post by spiderbatdad on 2008-05-07
```
man update-initramfs
```

---

### Post by PinkFloyd102489 on 2008-05-07
Does it say something about BusyBox?

---

### Post by gandalf2000 on 2008-05-07
Thanks for the reply spider.  The message I get is this:-

 /bin/sh: man: not found
(initramfs)

---

### Post by gandalf2000 on 2008-05-07
Hi Pink.  It does have a line above the (initramfs) like this:-

 BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter 'help' for a list of built-in commands

---

### Post by gandalf2000 on 2008-05-07
After two days of searching I finally found the answer.  All I had to do was shut down and boot Windows up then shut down Windows properly.  After the install from Windows, Windows hung so I killed it with the power button.  Apparently doing this creates a problem with the install.  Anyway,  it appears to be working properly.  Thanks to those who tried to help.  Here is a link to the thread:- [http://ubuntuforums.org/showthread.php?t=768933](http://ubuntuforums.org/showthread.php?t=768933)

---

