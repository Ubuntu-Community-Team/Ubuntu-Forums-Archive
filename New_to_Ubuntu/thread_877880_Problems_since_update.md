---
title: "Problems since update"
date: 2008-08-02
forum: New to Ubuntu
---

### Post by ooblyboo on 2008-08-02
I'm pretty new to Linux so not really aware of what I am doing, but I am having problems since I tried automatically installing updates a couple of days ago. There were about 165 updates. I chose to download and install. The download went fine but a problem occurred during the installation. 

Since then I get a message on start up that my graphics card (Palit GeForce 7600GT) is disabled. I can't seem to reinstall the driver, despite having no problems first time round. 

Also, the update installer tells me I still have 105 updates to install, but when I try to install them, I get this error message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


I've tried to do as instructed in the terminal but am told I need 'superuser' status. Bit stumped. Any ideas?

---

### Post by bumanie on 2008-08-02
In terminal > sudo dpkg --configure -aThis should download the remaining packages that didn't finish. Once they have finished, try the graphics driver again.

---

### Post by overdrank on 2008-08-02
> **ooblyboo said:**
> I'm pretty new to Linux so not really aware of what I am doing, but I am having problems since I tried automatically installing updates a couple of days ago. There were about 165 updates. I chose to download and install. The download went fine but a problem occurred during the installation. 

Since then I get a message on start up that my graphics card (Palit GeForce 7600GT) is disabled. I can't seem to reinstall the driver, despite having no problems first time round. 

Also, the update installer tells me I still have 105 updates to install, but when I try to install them, I get this error message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


I've tried to do as instructed in the terminal but am told I need 'superuser' status. Bit stumped. Any ideas?

Hi and welcome, that command would be ```
sudo dpkg --configure -a
```
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by UbuntuNerd on 2008-08-02
I guess I was to slow!!!


sudo dpkg --configure -a

---

### Post by ooblyboo on 2008-08-02
Many thanks to all of you for that suggestion - it sorted everything out. Didn't need to reinstall graphics card driver.

---

