---
title: "How to Install USB WIRELESS adapter??Atheros chip based"
date: 2008-03-29
forum: Outdated Tutorials &amp; Tips
---

### Post by chilskater on 2008-03-29
Well, i almost done with installation...

here steps i have followed:

lsusb
ndiswrapper -i net5523.inf
ndiswrapper -m
ndiswrapper -l
(net5523 : driver installed
                device (0cf3:0002) present


however when i goto Adm->network, i can only see WIRED and MODEM connection...please help..i just install UBUNTU 5 minute ago..

---

### Post by alan34 on 2008-03-29
You need after installing ndiswrapper have to done the following commands in a terminal (Application - Accessories - Terminal)
copy and paste

sudo depmod -a
sudo modprobe ndiswrapper
sudo ndiswrapper -m

See ndiswrapper when you do?

lsmod

To load ndiswrapper when you boot

sudo gedit /etc/modules

and add on a line on its own at the end of the file

ndiswrapper

Reboot and your wireless card should be recognised

Good luck

---

### Post by chilskater on 2008-03-30
so it suppose to be like this? I am very noob..thanks

lsusb
ndiswrapper -i net5523.inf
ndiswrapper -m
ndiswrapper -l
(net5523 : driver installed
device (0cf3:0002) present

sudo depmod -a
sudo modprobe ndiswrapper
sudo ndiswrapper -m

See ndiswrapper when you do?

lsmod

To load ndiswrapper when you boot

sudo gedit /etc/modules

and add on a line on its own at the end of the file

ndiswrapper

Reboot

---

### Post by alan34 on 2008-03-30
Look like your windows driver is installed correctly. These commands will insert the ndiswrapper into the kernel.

sudo depmod -a
sudo modprobe ndiswrapper
sudo ndiswrapper -m


This command checks that that ndiswrapper is loaded. A load of text will be listed and you should see ndiswrapper somewhere in that list.

lsmod


Adding ndiswrapper to /etc/modules makes sure ndiswrapper is loaded when the machine boots up. 
Hope that sort of explains what is going on well to the best of my ability anyway.

Good luck

---

### Post by chilskater on 2008-04-04
it worked like magic..i have update my UBUNTU..thanks bro!!:guitar:

---

### Post by Niels_ on 2009-03-15
Everything turns out fine by now, thanks for that. But I absolutely have no idea of how to connect to my wireless router now..! :S

---

