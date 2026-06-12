---
title: "screen resolution"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by mkeithcloud on 2008-04-22
I recently installed Ubuntu 7.10 on my laptop and the graphics card was labeled a "restricted driver". It installed fine and the screen resolution is fine on the desktop but at the logon screen, the resolution is set to something lower like 640x480 or something. Is there any way to change this?

---

### Post by Jammy4041 on 2008-04-22
Can you still see the panel? If you can, go System...> Preferences...>Screen Resolution. If it's not under that, try under Screens and Graphics (again under System > Preferences)

I think...

---

### Post by wolfen69 on 2008-04-22
open terminal and:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by mkeithcloud on 2008-04-22
I tried the sudo command and it let me pick a graphics card model and resolution for that config file. After I reboot to test it, Ubuntu will not load the GUI. I tried to log in from the command line and run startx but it comes back with:

fatal server error
no screens found
X10: fatal IO error 104 (Connection reset by peer) on X server ":0:0" after 0 requests (0 known processed) with 0 events remaining.

Any ideas????

---

### Post by jaytek13 on 2008-04-22
Oh my... Unfortunately I cannot suggest anything, but this should be a lesson for some posters here. While you may be trying to help, sometime your methods can be detrimental. Preferably we should all be following the 'kiss' procedure. There was no reason to reconfigure the entire x server just to change the resolution.

---

### Post by banished_one on 2008-04-22
<Ctrl><Left-Alt><F1> to change to a virtual terminal

to back up the settings kinda file use 
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

if anything goes wrong use this to replace 
sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf

use this to change the settings 
sudo dpkg-reconfigure xserver-xorg

---

