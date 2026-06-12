---
title: "How do i create a blacklist file?"
date: 2008-09-29
forum: New to Ubuntu
---

### Post by ludu900 on 2008-09-29
I am trying to get my bcm4328 network card to work and in the sticky regarding that topic the first step is to create a blacklist file. What is a blacklist file and how do i create one???

---

### Post by anewguy on 2008-09-29
The file already exists - you just need to add to it:

in a terminal window:

cd /etc/modprobe.d

sudo gedit blacklist

Go to the end of the file and add a new line with the following:

blacklist bcm43xx

Then save the file, exit the editor and reboot.

If you are using ndiswrapper to do all of this, remember to put in /etc/modules so it loads at boot:

in a terminal window

cd /etc
 
sudo gedit modules

Go to the end of the file and add a new line with the following:

ndiswrapper

Then save the file and exit.

Dave :)

---

