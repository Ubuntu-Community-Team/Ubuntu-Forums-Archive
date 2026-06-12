---
title: "Awesome with Kde"
date: 2013-01-13
forum: New to Ubuntu
---

### Post by kabukiM0n0 on 2013-01-13
Evening. 

I'm currently trying to install Awesome from this guide [http://ubuntuforums.org/showthread.php?t=675292](http://ubuntuforums.org/showthread.php?t=675292) but am held up on point 3. When I try to save the file as awesome.desktop in /usr/share/xsessions it tells me this: ```
 The document could not be saved, as it was not possible to write to /usr/share/xsessions/awesome.desktop.

Check that you have write access to this file or that enough disk space is available.
``` 

How do I give myself the permissions to save in /root files?

Thank you!! 

K.m

---

### Post by oldos2er on 2013-01-13
Give your user root privileges with "sudo" or "gksudo": [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

