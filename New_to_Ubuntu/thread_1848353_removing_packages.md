---
title: "removing packages"
date: 2011-09-22
forum: New to Ubuntu
---

### Post by vishant on 2011-09-22
I want to install a old version of a package and install a newer one but i don't know how to uninstall it .Plz help me out.

---

### Post by Linux_junkie on 2011-09-22
How have you installed it?  You didn't download the source file from some rogue web site did you?  If it hasn't be compiled then just locate its directory (folder) and delete it.  If you've installed it from the software centre or apt-get then just use software centre to un-install it. or apt-get remove <appname>

---

### Post by kireeti on 2011-09-22
> **vishant said:**
> I tried to install a package but it is giving me errors during compilation so i tried to uninstalling it but i don't know how uninstall it.
did u try :
sudo apt-get remove package_name .

---

### Post by wildmanne39 on 2011-09-22
Hi, if you compiled it like you say, then do this please:

Change into the directory of the file and run these two commands one at a time.
```
sudo su
make clean
```
Thank you

---

