---
title: "is there any repository for installing OpenOffice 3 into Ubuntu?"
date: 2008-10-27
forum: New to Ubuntu
---

### Post by legolas_w on 2008-10-27
Hi
Thank you for reading my post
Is there any repository for installing OpenOffice 3.0 into Ubuntu 8.04 properly?
I download the deb packages from OO site and install it, I looked into many tutorials for installing it properly with no lock. 
I explained my problem at [http://ubuntuforums.org/showthread.php?t=951890](http://ubuntuforums.org/showthread.php?t=951890)

Please let me know if there is any repo for installing OO 3 into ubuntu 8.04.

---

### Post by drakeman007 on 2008-10-27
Mmm you uninstall the 2.4 version first? cause i have my openoffice 3 installed and i downloaded it from the website openoffice.org but first u have to uninstall the 2.4 version!... you already do that?

---

### Post by roger_1960 on 2008-10-27
Hi

Read this:

[http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/](http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/)

---

### Post by LowSky on 2008-10-27
First go into synaptic and remove openoffice 2.4

Then install the DEBs using the command (make sure you are in the desktop directory in terminal)
```
sudo dpkg -i *.deb 
```

---

### Post by ajgreeny on 2008-10-27
I have both OOo 2.4 and OOo 3 on one of my partitions with Mint 5 without any problems at all, as far as I can see.  I am not sure therefore, if it is really necessary to uninstall OOo 2.4 before adding OOo 3, but it may be that it will avoid any conflicts of the configs, though the configurations are in differently named hidden folders in my /home/username on the Mint 5 install.

---

