---
title: "wireless card not working on dell 1525"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by konsta82 on 2008-07-27
I just installed 8.04 version but I can't get to the internet.In hardware drivers wireless device is enabled but not in use.How can I turn it on and where to find drivers for dell inspirin 1525 ? Please help @

---

### Post by Pioneer5000 on 2008-07-27
Try this you need to have connection to net so connect through Ethernet or USB just to do this. I got this from a post from another user on these forums:

```


sudo aptitude purge b43-fwcutter
sudo aptitude update
sudo aptitude install b43-fwcutter

```
After completing the above code in terminal, restart computer then click on connection icon in top right corner of screen and it should detect your wireless connection.

Full credit to sam_delta

---

### Post by ajmorris on 2008-07-27
what wireless card are you using? (post the output of sudo lspci)

AJ

---

### Post by konsta82 on 2008-07-27
my wireless card is broadband corporation BCM4310

---

### Post by ingeva on 2008-07-27
> **konsta82 said:**
> I just installed 8.04 version but I can't get to the internet.In hardware drivers wireless device is enabled but not in use.How can I turn it on and where to find drivers for dell inspirin 1525 ? Please help @

Maybe you have tried this, but after disconnecting the ethernet cable and restarting, all I had to do was enter the correct WPA security code, and then it worked instantly.
It's important that there's no other live connection available.
I'm also a noobie, and with Ubuntu 7.10 I could never make the wireless work. With 8.04 it was a snap.
My computer is a Vostro 400.

---

### Post by Immolatus on 2008-07-27
What you've probably got is the "dell wireless card" lesser known as the Broadcom 4315 card. What you need is to download and install ndiswrapper from the repos and go to the dell site and download the driver for your machines wireless card. IMPORTENT: Download the XP driver as the vista driver will not work with ndiswrapper. Just put the driver in a folder called wireless or some crap in your home folder (make sure you extract it there) then go to System--> Administration-->Windows Wireless Drivers (it'll be right at the bottom of the list) and brows for it from there. Then reboot and that little blue light should finally be on.

If this doesn't work, post back we may have to cross some t's and dot some I's.:popcorn:

---

### Post by Ryadt on 2008-07-27
Have a look at this tutorial
[http://ubuntuforums.org/showthread.php?t=297092&highlight=Dell+Inspiron+E1505+Wireless](http://ubuntuforums.org/showthread.php?t=297092&highlight=Dell+Inspiron+E1505+Wireless)
Hope it helps.

---

### Post by Pioneer5000 on 2008-07-27
Did you try what i posted?

---

### Post by graben3 on 2008-07-27
I have a dell inspiron 1501 laptop which comes with a small variant of your card (mine is 4311 yours is 4310 I think) ... Im pretty sure it should work as mine mostly. 

On Ubuntu Feisty, ndiswrapper was the only way I could get it to work (and it was painful to find the right download to make this work) but under 8.04 fwcutter is working out of the box (and I never been able to make ndiswrapper work on 8.04). All you have to do is go into 

System -> Administration -> Hardware Drivers

You should see a B43 driver which is not in use. Check the box to enable it... it will install some restricted drivers and the wireless card should work after a reboot.

You said yours is not in use.... but enabled ...so try de-enabling it them reboot and re-enable it maybe it will help. 
If it does not work, try opening a terminal and remove references to b43 in the blacklist file (i think maybe your driver is blacklisted, therefore not in use):

sudo gedit /etc/modprobe.d/blacklist

You should see some lines like this :

blacklist b43
blacklist ssb

Remove all those lines (the ones having ssb or b43). Do not remove lines like this :

blacklist bcm43xx

Then reboot !
Hope it helps !

---

### Post by konsta82 on 2008-07-27
I dont have another internet on dell.I downloaded ndiswrapper from old one but I can't install it.There is "open files" menu here but there is no files listed

---

### Post by konsta82 on 2008-07-27
I'm sending this from ubuntu,ndiswrapper and xp driver solved problem.this forum is cool ! thanks all of you

---

### Post by Immolatus on 2008-07-28
great! you might want to mark this thread as "solved", cause it might help someone else K?

---

