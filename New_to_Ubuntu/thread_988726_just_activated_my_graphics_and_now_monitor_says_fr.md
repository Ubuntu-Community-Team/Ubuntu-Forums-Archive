---
title: "just activated my graphics and now monitor says: frenquency out of range!!!"
date: 2008-11-20
forum: New to Ubuntu
---

### Post by thekylehome@gmail.com on 2008-11-20
I've been running Ubuntu for a year or so now and I just decided to check out and install Kubuntu... after a clean install I activated both my wireless and graphic drivers, then restarted. after restart, I got to the login page, logged in and then, BOOM! as soon as it logged in onto the desktop, my monitor went black and then a box came up that says: "frequency out of range." What do I do now? I can't do anything. How do I change the frequency?

YIKES! Help!!!

---

### Post by SuperSonic4 on 2008-11-20
If I recall correctly you boot into a low resolution using F4 at the boot menu and then change your xorg.conf to change to the monitor res

---

### Post by thekylehome@gmail.com on 2008-11-20
k, I'll try it out!

---

### Post by thekylehome@gmail.com on 2008-11-20
Ho! Just tried the F4 trick... but it did not work!

---

### Post by thekylehome@gmail.com on 2008-11-20
Help! What I am left to... reinstalling??? oooohhhh... there's got to be some way!

---

### Post by doas777 on 2008-11-20
I had a similar problem when I upgraded my kernel last. in the end, I found out that the problem was that nvidia-settings did not match the settings in the ubuntu screen resolution tools settings,and they we're fighting with each other. i was able to fix it by setting both apps to the same res, and loading nvidia-settings at login. 

unfourtunatly the only way i was able to do it was via my TV monitor. ultimatly i replaced the vid card, which solved several other problems I was having as well. I guess geforce 8500s just don't work too good with ubuntu. 

good luck,
franklin

---

### Post by tvtech on 2008-11-20
a frequency out of range typifies the following problem.  in the united states the frequency of the electrical system is 60hz in most of the rest of the world it is 50hz most modern monitors with switching power supplies can take a range of voltage from 110 to 220  and a range of frequencies from 40-60hz.  

it would seem that your default graphics card mode is set to a frequency output that is incompatible with your monitor.  if you can boot into safe graphics mode and change your frequency in System>Preferences>Screen resolution, or your video cards config settings this may save you.        otherwise 

boot up to a terminal and try the following  
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

this will reconfigure your xserver and your xorg file to default using the standard vesa driver and give you a shot at redoing this without a full re-install.

---

### Post by tvtech on 2008-11-20
and seriously this is one of the best lines to remember if you are having video card problems it will save your butt.  I had a video card that ubuntu didn't like a few years ago and it took A LOT of configuration to get it happy. but I finally got it after I reset xorg.conf about a million times

---

### Post by thekylehome@gmail.com on 2008-11-20
Thanks guys! I'm going to try it out... I'll let you know what I get.


The wierd thing is that ubuntu has never done this to me...

---

### Post by thekylehome@gmail.com on 2008-11-20
> **tvtech said:**
> it would seem that your default graphics card mode is set to a frequency output that is incompatible with your monitor.  if you can boot into safe graphics mode and change your frequency in System>Preferences>Screen resolution...

how do I boot into safe graphics mode???

---

### Post by thekylehome@gmail.com on 2008-11-20
Man! I did the "sudo dpkg-reconfigure -phigh xserver-xorg" and it reset it so that I could see the os again but it set it back to 800x600 again (looking very funky) and it unactivated my nvidia graphic driver. so I reactivated the driver but alas! back to where I was! before I reactivated the driver I went in and set the frequency to "auto" thinking that might help, but apparently when I reactivated the driver (which requires a restart) it must have not payed attention to that. 
Hmmmmm...

---

### Post by thekylehome@gmail.com on 2008-11-21
I have been trying all kinds of things to change the frequency, but alas! nothing has worked for me! 

I really don't want to re-install! Help!

---

### Post by thekylehome@gmail.com on 2008-11-21
Okay guys, seems like I'm not going to get this resolved. BUT, my question is, how do I know if a reinstall is going to fix this problem??? Because it is after I activate the graphic driver that everything goes belly-up!

What am I left to?

---

