---
title: "Linux ported Game installation please"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by lammergeir on 2008-06-05
Hi there, I´m unsuccessfully trying to install the Linux version of Robin Hood.
I get the following error: Grateful for assistance
-en
Welcome to the Robin Hood installation script

Select the directory where you want to install the game,
the default is [/home/justin/robinhood], press return only if it's ok for you:
/home/justin/robinhd/
-e
Installing to: /home/justin/robinhd/

/media/cdrom0/setup.sh: 41: cannot create robin.kdelnk: Permission denied
/media/cdrom0/setup.sh: 43: cannot create robin.gnome: Permission denied
mv: try to overwrite `/home/justin/.kde/share/applnk/Robin Hood.desktop', overriding mode 0555 (r-xr-xr-x)?

---

### Post by Duck2006 on 2008-06-05
Have you tried doing it as root.

---

### Post by lammergeir on 2008-06-10
Hi there, thks for reply.  Have tried sudo then cd/media/cdrom0 but nothing.  I must familiarise myself more with the root/sudo instructions.
The CDrom opens when inserted and there a setup.sh file which when clicked gives the option to "run in terminal" or "run". 
"Run in terminal" gives the above result.
Cheers.

---

### Post by The Cosmic Hobo on 2008-06-10
How about you open a terminal yourself, change your directory to media/cdrom0 and enter the command sudo setup.sh ? That should, if my out-of-date knowledge works, allow the setup script to run as root.

---

