---
title: "Question about /var/cache/apt/archives"
date: 2011-10-19
forum: New to Ubuntu
---

### Post by Ymurti on 2011-10-19
I can not paste a file .deb to /var/cache/apt/archives Is there a way that I can do that?  Please help

---

### Post by Paqman on 2011-10-19
That folder is owned by root, so you need to move it as root.

Terminal version:
```
sudo mv /path/to/file /var/cache/apt/archives
```
GUI version:

Hit Alt-F2 and type:
```
gksudo nautilus
```
then just cut and paste like normal. Make sure you close this window when you're done.

---

### Post by Ymurti on 2011-10-19
> **Paqman said:**
> That folder is owned by root, so you need to move it as root.

Terminal version:
```
sudo mv /path/to/file /var/cache/apt/archives
```
GUI version:

Hit Alt-F2 and type:
```
gksudo nautilus
```
then just cut and paste like normal. Make sure you close this window when you're done.
Dear Paqman,

Thank You a lot. I upgraded from 11.04 to 11.10 in my laptop and I saved all .deb files from my  /var/cache/apt/archives. 
Now I have copied then and pasted in the  /var/cache/apt/archives of a friend's laptop with Ubuntu 11.04 Can you tell me now what are the next steps so my friend can upgrade from 11.04 to 11.10 as he has all the files on his  /var/cache/apt/archives?

---

### Post by Paqman on 2011-10-19
No problem. Open up the Update Manager and it should show that a new version is available at the top. Click on this and let it do the upgrade.

You may still need an internet connection to download new versions of any packages he has on his system that you don't, but having the packages in the APT cache already should save a fair bit of downloading.

---

