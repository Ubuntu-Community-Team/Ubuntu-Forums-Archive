---
title: "Install packages offline"
date: 2012-09-23
forum: New to Ubuntu
---

### Post by kmegamind on 2012-09-23
I have downloaded a package with .tar.gz extension 
now I need to install the package. 
Of course apt-get install won work directly as it can't locate the package. 
Should i put the package in a certain directory before executing the command ?, Or what should i do?

---

### Post by NikTh on 2012-09-23
Hi , 

First you must uncompress the file with tar command 
```
tar -xvzf packagename.tar.gz
```then you must connect to the folder with cd command 
```
cd foldername
```and then read any README file inside that folder for instructions on how to install. 

Thanks

---

### Post by Peripheral Visionary on 2012-09-23
It's always, always better to download a .deb from Ubuntu's repositories than to go to some web site and trust that their "tarball" will work in Ubuntu.

Installing a tarball is pretty simple and there have been numerous threads here with step-by-step directions. Just a quick search of the forums should take you to one of the many how-to threads on the subject.

---

### Post by kmegamind on 2012-09-24
Thanks both for the help :)

---

