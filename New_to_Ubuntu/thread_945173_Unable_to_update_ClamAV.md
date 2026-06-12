---
title: "Unable to update ClamAV"
date: 2008-10-12
forum: New to Ubuntu
---

### Post by CompSciSTL on 2008-10-12
I finally took the plunge and installed Kubuntu 8.04 64-bit on my laptop as a dual-boot.  I installed ClamAV from the package manager and when I open the program for the first time it mentioned that I need to update the permissions of two files before I can update the definitions of the program.  Unfortunately I didn't write down the names of the two particular files and I'm a bit stuck not being able to update ClamAV.  

If anyone would happen to know which files to update and what I might need to modify in those files, I would greatly appreciate it.

---

### Post by quibbler on 2008-10-14
This post will probably help you.
[http://ubuntuforums.org/showthread.php?t=924469](http://ubuntuforums.org/showthread.php?t=924469)

Regards quibbler

---

### Post by iaculallad on 2008-10-14
On your terminal:

```
sudo apt-get install freshclam
sudo freshclam
```

---

