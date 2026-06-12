---
title: "Nvidia 9600M GT 250GB 7200 RPM + glxgears results weird?"
date: 2008-09-13
forum: New to Ubuntu
---

### Post by Servet on 2008-09-13
so I found some threads about the glxgears :'D 

and I saw some results of 7200 GT cards, and wanted to try myself, but surprisingly my specs are much, *much*lower.. Can anyone tell me why, and if so, [SIZE="6"]a solution?[/SIZE]

Btw it's on my laptop that I executed the command 
> 14272 frames in 5.0 seconds = 2854.236 FPS
14110 frames in 5.0 seconds = 2821.802 FPS
14353 frames in 5.0 seconds = 2870.430 FPS
14250 frames in 5.0 seconds = 2849.921 FPS
14195 frames in 5.0 seconds = 2838.901 FPS
11407 frames in 5.0 seconds = 2281.347 FPS

Running on Ubuntu .

Thx for a crazy a**kicking community [SIZE="7"]<3[/SIZE]

---

### Post by ChanServ on 2008-09-13
first check to make sure you have the proper driver and that it is installed correctly, if in dought try useing envyng

also remember that some people use highly configured drivers, so there card may be outperforming your just due to their settings

---

### Post by Servet on 2008-09-13
I checked, and it says that the latest nvidia is enabled. I installed driver with EnvyNG. .. 


btw how do I uninstall Envy, it said something about deleting it after installing driver, in case of upgrade, because it would do something bad or sumthin' : D

---

### Post by ChanServ on 2008-09-13
sudo apt-get remove envyng-gtk (or envyng-qt if you used the QT version )

---

### Post by Servet on 2008-09-13
thanks again, I have deleted the EnvyNG-Core, but I still don't understand how I'm gonna update drivers, I can't do it through Nvidia sites, and 2800 fps is too low me thinks.. ?

---

