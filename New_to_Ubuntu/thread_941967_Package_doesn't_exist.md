---
title: "Package doesn't exist"
date: 2008-10-08
forum: New to Ubuntu
---

### Post by johanang on 2008-10-08
I am on the server addition and i am trying to install the Flux box however, no matter what i do and from what posting thread etc i try it says package missing.. This is after logging in to the command line.

I have tried this from the user account and root account why are these packages missing...


Have i done something wrong? Tried this:

###Installing GUI Interface###
sudo apt-get install fluxbox x-window-system-core xdm

This would install the default GNOME desktop that comes with Ubuntu Desktop version.

sudo apt-get install ubuntu-desktop
sudo apt-get install gdm
sudo /etc/init.d/gdm start
sudo dpkg-reconfigure xserver-xorg

---

### Post by talsemgeest on 2008-10-08
Can you post your /etc/aot/sources.list file?

---

