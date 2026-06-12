---
title: "Nvidia black screen"
date: 2008-09-11
forum: New to Ubuntu
---

### Post by UltraRos on 2008-09-11
Hello people, 
 
After installing my 8.04 i installed the nvidia driver Ubuntu displayed as an available update. After a reboot it booted but i got a black screen. I was able to log in blind and heard drums again. When i pres ctrl+alt+f1 i get a shell. 
 
What should i do to get graphics back? 
 
I read on forums what to do but nothing solved it. I noticed to late that Ubuntu doesnt like nvidia.
 
Reinstalling takes over 3 days with my connection so i hope that won't be needed

---

### Post by Nepherte on 2008-09-11
How did you exactly install the nvidia driver? If you can't get it to work through restricted hardware, you could try envy:
```
sudo apt-get install envyng-gtk
```

Then run it in console mode:
```
envyng-gtk -t
```
Uninstall the old driver, then install the new driver.

---

### Post by ntbutler on 2008-09-11
Hi there.
Yeah, 8.04 seems to be having a huge issue with nvidia cards, i am still trying to diagnose the issue, but so far i have found that it is linked directly with the installation of the nvidia driver (my system crashes once it is installed instead of getting a black screen).
For the moment, try booting the computer in recovery mode. Once you get to the menu, choose xFix, ehich will reset your Xorg.conf file (basically disabling the nvidia driver).
This should give you graphics back again, and you can try to have a look at what is happening.

It may be good before you run xFix, if you log in to tty1 like you did before, then run "more /etc/X11/xorg.conf" to read the configuration file or "sudo cp /etc/X11/xorg.conf /home/<USERNAME>/Desktop/xorg.conf" to copy it to your desktop so you can have a look at what the nvidia driver has changed around with your settings and see if there is anything conflicting.

I hope that helps buddy, let us know how it goes :)

---

### Post by UltraRos on 2008-09-11
Doing xfix and than resume normal reboot doesnt work.
 
And it says /etc/x11/xorg.conf : on such file or directory. 
 
The suggestion above i need to be connected. I need to use wvdial to connect and i don't know how to get another shell tab in save mode (sorry if i use wrong terms)

---

### Post by ntbutler on 2008-09-11
make sure when you type in the command that the X in etc/_X_11 is a capital, that will make a difference.

As for getting other shells, when you press ctrl+alt+F1, that takes you to a separate terminal/shell. You should also be able to use ctrl+alt+F2-F6 to get another 5 shells (use any one you like). (I hope that helps, i wasn't really sure what you were needing, so i hope that is what you are looking for.)

---

### Post by nbayiha on 2008-09-11
Follow this thread.

[http://ubuntuforums.org/showthread.php?t=880787&highlight=install+nvidia+driver+hardy](http://ubuntuforums.org/showthread.php?t=880787&highlight=install+nvidia+driver+hardy)

---

### Post by UltraRos on 2008-09-11
```
Sudo cp /etc/X11/xorg.conf
``` gives me
'cp: cannot create regular file '/home/Joop/Desktop/xorg.conf' no such file or directory
 
```
More /etc/X11/xorg.conf
``` works. 
 
With ```
Envyng-gtk -t
``` after install i get 'gtk-warning **: cannot open display:

---

### Post by Nepherte on 2008-09-11
My apologies. It's:
```
envyng -t
```

---

### Post by UltraRos on 2008-09-11
Ok done that i've still the same issue accept that a blue screen about the xserver appears very short that it doesn't start

---

### Post by UltraRos on 2008-09-11
Ok i will reinstall Ubuntu an never touch nvidia again

---

