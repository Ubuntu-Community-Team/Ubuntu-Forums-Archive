---
title: "[SOLVED] no wifi interface,no internet icon??"
date: 2008-07-29
forum: New to Ubuntu
---

### Post by rixtr66 on 2008-07-29
i just installed ubuntu studio onto an external hard drive and it boots up
fine but theres no icon for the internet,no interface,how do i get the inter face up and running??i know its there somewhere i used this distro 
before and it had one,is there an apt-get or dpkg i hve to use??
rick:confused:

---

### Post by bobnutfield on 2008-07-29
Is this a wired or wireless connection you are trying to achieve?  Open a terminal and type:

> sudo ifconfig -a

This will tell you what interfaces are available, whether they are working or not.

Bob

---

### Post by rixtr66 on 2008-07-29
it is a wireless connection im trying to get.
rick

---

### Post by bobnutfield on 2008-07-29
OK, what was the output of the ifconfig -a command?  Is your wireless card listed?  If not, what is the wireless card?  If you are using Windows and booting Ubuntu from the external drive, does the wireless work in Windows?

---

### Post by rixtr66 on 2008-07-29
icant show you the output,but it did say i had ethernet0,and lo but no
wlan???it shows up fine in ubuntu i  have to use an ndis wrapper.
the thing is i had wireless on studio before.is there a way to get
studio to see my wireless card its an atheros somthing.

---

### Post by bobnutfield on 2008-07-29
Whatever method you used to get it working in Ubuntu should also work in Studio, and if you used ndiswrapper in Ubuntu, the same will be required in Studio.  Type:

> lspci

in terminal to make sure it is being recognized in the hardware, and then just set it up the way you did in Ubuntu.

Bob

---

### Post by rixtr66 on 2008-07-29
well it worked kinda i had to go through the network settings,thanks
rick

---

### Post by bobnutfield on 2008-07-29
Glad you got going.

---

