---
title: "xscreensaver does not start on reboot"
date: 2012-07-16
forum: New to Ubuntu
---

### Post by mystmaiden on 2012-07-16
I'm running Precise, classic no tweaks and using xscreensaver. Every time I reboot though, xscreensaver does not start itself and I get a system error message. I have to go to  applications/system tools/preferences/screensaver and start it manually. Xscreensaver does show on the startup list though.

Anyone know how I can fix this?

thanks,

mystmaiden

---

### Post by Laiquendi on 2012-07-16
What is that error message?

---

### Post by mystmaiden on 2012-07-19
It just says there is a system problem and asks if I wish to report it.

---

### Post by NikTh on 2012-07-19
Hi , 
if you installed xscreensaver , you must remove gnome-screensaver . So open a terminal and 
```
sudo apt-get remove gnome-screensaver
```Then open startup applications and add xscreensaver there , manually. 
At the command field write 
```
xscreensaver -nosplash
``` at description and comment you can write anything you want.

Reboot to see if xscreensaver work on startup.
Thanks

---

### Post by mystmaiden on 2012-07-19
Thank you  for the reply.

I have already removed gnome screensaver and created the startup. (I  double checked both just now to be sure). I hit the save button on the  startup addition anyway and rebooted. Unfortunately, xscreensaver still did not start. I had to start it  manually.

---

### Post by NikTh on 2012-07-20
Hi , 
try to purge xscreensaver and remove the startup application entry. 
Then repeat the install.

```
sudo apt-get purge xscreensaver 
sudo apt-get install xscreensaver xscreensaver-gl-extra xscreensaver-data-extra xscreensaver-screensaver-bsod
```Then add again the startup application entry 

```
xscreensaver -nosplash
``` 

Thanks

---

### Post by hypnot0ad on 2012-07-21
NikTh:

I'm trying this right now.

(edit)
It still doesn't work on start up.

---

### Post by mystmaiden on 2012-07-26
Thanks for the replies.

I'm still not having any luck getting xscreensaver to start on reboot. When I originally loaded it the instructions had me create a file and save it. I am wondering now if there was an issue with that. I can not remember where the file was though to check it but I believe it was just a command line to add it to start up.

mystmaiden

---

### Post by NikTh on 2012-07-26
Hi , 
please try this 
```
gksudo gedit /etc/xdg/autostart/xscreensaver.desktop
``` 

copy paste these lines in there 
```
[Desktop Entry]
Type=Application
Encoding=UTF-8
Name=XScreensaver
TryExec=xscreensaver
Exec=xscreensaver -nosplash
``` 
save the document and restart PC. 

Thanks

---

