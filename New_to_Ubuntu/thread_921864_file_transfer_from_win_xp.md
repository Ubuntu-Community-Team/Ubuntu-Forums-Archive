---
title: "file transfer from win xp"
date: 2008-09-16
forum: New to Ubuntu
---

### Post by stonecoldjha on 2008-09-16
i have installed windows xp with virtualbox in ubuntu hardy.it comes to me of use in running programs like gtalk,JLC internet TV,etc.But how do i transfer the files from this guest xp to host ubuntu.for example,if i procured a file from one of my buddies in gtalk,it would remain in the virtual xp installation.how do i transfer it out of the virtual hard drive partition that xp makes use of to one which ubuntu uses.what is the exact location of c:/ of xp,i mean how do i navigate to that using nautilus.

---

### Post by AndyCooll on 2008-09-16
You know that Pidgin supports GTalk don't you?

Anyway for your Vrtualbox XP image, on the details tab there is a "Shared Folders" section. You need to set that up. I believe to use the facility you need "Guest Additions" installing (I don't use this facility myself so I can't tell you for sure).

:cool:

---

### Post by forger on 2008-09-16
Read the manual on network sharing:
[http://download.virtualbox.org/virtualbox/2.0.2/UserManual.pdf](http://download.virtualbox.org/virtualbox/2.0.2/UserManual.pdf)

It covers up the steps you have to do :)

---

### Post by OffAxis on 2008-09-16
[https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)

Look for the section labeled "Sharing Folders Between Host and Guest"

---

### Post by Peter Frank on 2008-09-16
You need to set up a shared folder. In Virtual Box, right-click the virtual machine, choose "settings", and in the setting window you'll see a section "Shared Folders", and add a folder of your choice. To access the folder, go to "My Computer" in XP and right-click "My Network Places", choose "explore". Then under "Entire Network", you'll find "VirtualBox Shared Folders" which is what you want.

Of course you need to install the VBox Guest Addition in the Virtual Windows for this to work.

---

### Post by Pro-reason on 2008-09-16
You have to set up Shared folders.  Samba is also a possibility.  Read the [user manual]("http://www.virtualbox.org/wiki/Downloads") ([PDF]("http://download.virtualbox.org/virtualbox/2.0.2/UserManual.pdf")).

---

