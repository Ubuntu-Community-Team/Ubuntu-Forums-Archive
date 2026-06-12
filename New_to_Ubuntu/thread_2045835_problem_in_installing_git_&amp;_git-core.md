---
title: "problem in installing git &amp; git-core"
date: 2012-08-22
forum: New to Ubuntu
---

### Post by nawaz1 on 2012-08-22
i am using xubuntu 7.04 on vmware

i try to install git and git-core ad get following error msgs plz solve it

nawaz@nawaz-desktop:~$ **sudo apt-get install git**

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package git

nawaz@nawaz-desktop:~$ **sudo apt-get install git-core**

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package git-core is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package git-core has no installation candidate

---

### Post by spjackson on 2012-08-22
7.04 is very old. Don't you have the possibility to upgrade? It's so old that the packages are not even browseable in the normal way via [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

Git was first released in the wild at the end of 2005, so there's a fair chance that there was a 7.04 package, but it's difficult to tell now. Needless to say, if it exists then it will be an old version of git.

---

### Post by nawaz1 on 2012-08-22
HOW To update it

---

### Post by Zvezdica27 on 2012-08-22
well... as said, 7.04 is way too old for 2012.

But... if you want, just add the proper PPA and after that packages should be available to apt-get

So, first find the PPA name, add it (sudo apt-add-repository ppa_name_here)

then update and upgrade

then try installing git.

I have no idea if it will work on so old a system, but you can try. If it fails, remove the ppa and that's it.

zz

---

### Post by holycow131415 on 2012-08-22
Download xubuntu 12.04, burn it to a disk. backup your data. pop the disk into your computer, restart the computer and choose to boot off it to start the install process.

---

