---
title: "Minimal CD with local site repository"
date: 2009-10-15
forum: Repositories &amp; Backports
---

### Post by sunliwei on 2009-10-15
Hi, I am try to install ubuntu 9.04 with minimal CD([https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)). I already have a ubuntu 9.04 desktop CD in hand and I want to use it as the repository for the minimal CD installation. I've tried use APTonCD, but failed. And I tried to copy all the contents from desktop cd to /var/www/ubunt and setup a apache web server for it , but I failed again(yes, I use the directory name right). 
 
Could anyone help me out? I can't access internet when I use the minimal cd image, and the desktop CD is the only thing I've got. please help....

---

### Post by prshah on 2009-10-15
> **sunliwei said:**
> I can't access internet when I use the minimal cd image, and the desktop CD is the only thing I've got.

From the terminal (duh!) give the command```
sudo apt-cdrom add
```, insert the CD when prompted, and press enter.

It will read the CD and add it to your local repository.

Use ```
sudo apt-get update
``` to make package names available for installation.
 
Then use sudo apt-get install ...(whatever).

---

### Post by sunliwei on 2009-10-15
> **prshah said:**
> From the terminal (duh!) give the command```
sudo apt-cdrom add
```, insert the CD when prompted, and press enter.

It will read the CD and add it to your local repository.

Use ```
sudo apt-get update
``` to make package names available for installation.
 
Then use sudo apt-get install ...(whatever).


I mean I need to install the Ubuntu  minimal CD on a machine which doesn't have the CD-ROM  and only have a network card.

---

### Post by prshah on 2009-10-15
> **sunliwei said:**
> need to install the Ubuntu  minimal CD on a machine which doesn't have the CD-ROM  and only have a network card.

Can it boot off USB? In that case look at the community documentation on how to [install from USB]("https://help.ubuntu.com/community/Installation/FromUSBStick"), specifically [isotostick.sh]("#isotostick.sh%20(Command-line%20shell%20script,%20runs%20from%20Linux)")

This will be better than a network install, but if your computer cannot handle booting from USB devices, then you need [Installation from local net]("https://help.ubuntu.com/community/Installation/LocalNet")

---

### Post by sunliwei on 2009-10-17
thank you. problem solved.

---

