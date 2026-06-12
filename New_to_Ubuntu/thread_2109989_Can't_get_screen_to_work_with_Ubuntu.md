---
title: "Can't get screen to work with Ubuntu"
date: 2013-01-29
forum: New to Ubuntu
---

### Post by Csharp94 on 2013-01-29
Hello, 

this is a question I'm sure has been answered before but I have had trouble finding a solution, that and I'm scared to try to many things incase I mess up my system and have to format. 

Basically I've used ubuntu for a while now along side windows 8. 
From my computer I use an HDMI to a 32inch HDTV (as the main monitor) this works find with windows, I can get audio and sound from the HDMI cable,

However when I boot ubuntu I have to use a VGA to VGA cable to even get signal. That doesn't bother me too much. It is still annoying having to switch cables... 

(I connect both of these through the ports on my graphics card) 

From reading online I think it has something to do with the Nvida card not being compadible with Ubuntu(I'm using 12.10) because with windows I have no problem running at 1080*1920, although Ubuntu limits me to a max of 800*600. 

Also everything is very fuzzy and hard to see. 

My graphics card is : GeForce gtx 560 ti. 
My Mobo is intel. 
Not sure what other information I would need to give.

---

### Post by omeomi on 2013-01-29
Did you install Nvidia drivers instead of the default nouveau driver? You can do this in Software Sources -> Additional Drivers. Your best bet would be to select nvidia-current first to see if that works.

---

### Post by Alcidious on 2013-01-30
I'm trying to troubleshoot getting my second monitor working so I can have a dual monitor setup. During my search I noticed, because I have an AMD grahpics card, that amd quit supporting a line of slightly aged drivers. 

Perhaps your ubuntu distro. considers your nvidia drivers as legacy ones?

---

