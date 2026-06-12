---
title: "Noob needs help with wireless Broadcom 4328"
date: 2008-04-21
forum: New to Ubuntu
---

### Post by amir1979 on 2008-04-21
hello all im new to the linux systems iv used windows my whole life... im trying to learn all the shell codes and how it works, so im sry if i might not understand or as repetive style questions....

i have a dell xps m1330  with a broadcom 4328 wireless n 
i have just installed ubuntu 7.10 amd64  but shows up 7.10 (gutsy)  


ive read and followed many instructions through various forums on here and other sites i have installed the drivers or tweaked it a bit for the system to kinda pick it up...  i have a wireless option now but i cant pick up any signals...   can someone possibly help me with trying to pick up a signal or setting up the wireless?   my ethernet worked fine without any issues from install.

thank you

---

### Post by amir1979 on 2008-04-21
NOTICE TO EVERYONE  i have fixed and resolved this issue thank you for your help and time :)

---

### Post by amir1979 on 2008-04-22
lol ok so i got the signal to work and im able to connect to my wireless network  but i cant seem to get it to function it appears that i didnt get an ip address assigned all the ip and dns settings are 000.00.00 etc.   is there a way to have it automatically get the settings?

---

### Post by amir1979 on 2008-04-22
im just bumping this...   please if anyone can help...   i have the drivers installed and i am able to pick up wifi signals, but when i connect or attempt to connect it fails or i dont get an ip address....

---

### Post by enli on 2008-09-18
> **amir1979 said:**
> im just bumping this...   please if anyone can help...   i have the drivers installed and i am able to pick up wifi signals, but when i connect or attempt to connect it fails or i dont get an ip address....

I didnt mean to hyjack the thread, but i was going to post in a new thread and found this 1. I too have the same problem. I can scan for networks and connect via nm-applet clicking on AP. The only problem is that i m not getting assigned an ip address. And as the amir told, i too have other fields such as IP, dns etc fields 0.

Long story short : Me and my friend purchased Inspiron 1525 which came with BCM4328 (Rev v.3). He has some other card and we both installed the ndiswrapper from fiesty tutorial (i dont have a link right now). It worked (i was able to access the internet for around 30 mins) but it suddenly stopped working. After that i was never able to connect it.

Cheers
EnLi

---

### Post by Sealbhach on 2008-09-18
Try

```
sudo dhclient wlan0
```


.

---

