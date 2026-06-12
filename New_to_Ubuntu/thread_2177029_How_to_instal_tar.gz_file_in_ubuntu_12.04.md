---
title: "How to instal tar.gz file in ubuntu 12.04"
date: 2013-09-26
forum: New to Ubuntu
---

### Post by allan6 on 2013-09-26
Hi guyz. I am requesting if anyone could please help me on how to install .tar.gz file in ubuntu 12.04  I bought a zte mf667 modem and it comes with a tar.gz file for linux. It also has a Readme.txt which reads "extract  the PCL_BATAFR.tar.gz file with achive manager to desktop. There would be two folders Airtel_internet and install.sh  change the current directory to "PCL_BATAFR.tar.gz"  open terminal and make sure you have root priviledges. Run shell command ./instal.sh or use sudo" Please Help. I have tried to google but stil no help. Thanks

---

### Post by Kanuckies on 2013-09-27
See if this helps:
[http://www.makeuseof.com/tag/compile-install-tar-gz-tar-bz2-files-ubuntu-linux/](http://www.makeuseof.com/tag/compile-install-tar-gz-tar-bz2-files-ubuntu-linux/)

---

### Post by sanderj on 2013-09-27
> **allan6 said:**
> Hi guyz. I am requesting if anyone could please help me on how to install .tar.gz file in ubuntu 12.04  I bought a zte mf667 modem and it comes with a tar.gz file for linux. It also has a Readme.txt which reads "extract  the PCL_BATAFR.tar.gz file with achive manager to desktop. There would be two folders Airtel_internet and install.sh  change the current directory to "PCL_BATAFR.tar.gz"  open terminal and make sure you have root priviledges. Run shell command ./instal.sh or use sudo" Please Help. I have tried to google but stil no help. Thanks

I would first try to get the mf667 modem working from the plain Ubuntu linux kernel. So: plug it in, check what appears in your screen and in dmesg. And post the output of the relevant line in "lsusb" with the modem plugged in.

---

### Post by chamuco107 on 2013-09-27
> **Kanuckies said:**
> See if this helps:
[http://www.makeuseof.com/tag/compile-install-tar-gz-tar-bz2-files-ubuntu-linux/](http://www.makeuseof.com/tag/compile-install-tar-gz-tar-bz2-files-ubuntu-linux/)

This is a great page to learn the basics of extracting and installing  tarballs. If you come across any dependency issues during the build,  apt-file is definitely a huge help. If you come across any error  messages look for what file was not found or needs to be upgraded to a  newer version. You might have to run ./configure a couple times until  all dependencies have been met.

thanks Kanuckies for posting this link. Came across this article and found it extremely useful for the noob that I am.

---

### Post by su:bhatta on 2013-09-27
This Ubuntu Help page is a good guide: [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

 Also, as pointed out by Sanderj, first try out if open source divers does the work.

---

### Post by Impavidus on 2013-09-27
Letting Ubuntu find the right drivers automatically is indeed the preferred option, as sanderj indicates, but sometimes unavailable. If so, do exactly what the readme tells you – which says nothing about compiling, BTW, but may do so automatically.

Assuming the file is on your desktop, open a terminal (ctrl-t or alt-t or something like that, or click the button) and give these commands:```

#Go to the right directory
cd Desktop
#Unpack the archive. This can also be done by double-clicking the archive and selecting "extract"
tar -xvzf PCL_BATAFR.tar.gz
#This shows the files and directories it creates. If it creates a parent directory with everything in it,
#enter this directory with
cd directory
#Next run the installer
sudo ./instal.sh
```
In case you haven't used sudo before, it won't give you any feedback on the password you're typing, not even ***. This is normal.

---

