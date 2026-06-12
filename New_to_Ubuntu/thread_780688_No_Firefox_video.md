---
title: "No Firefox video ?"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by Drakkor on 2008-05-03
Trying to play videos from videojug.com and get this:

---

### Post by CloudFX on 2008-05-03
Do you have Flash Player properly installed?  You will want to install it manually, and if you haven't, then we can provide you with help to do so.  Does Youtube work?

---

### Post by kestrel1 on 2008-05-03
Had a similar problem & found that another plugin was trying to play the videos (sorry cant remember the plugin name) Once that was uninstalled & flashplayer installed manually (as suggested above) every thing was fine.

---

### Post by Drakkor on 2008-05-03
Ok,just tried youtube and it prompted me to search for suitable codecs,which I did,and installed gstreamer,and youtube is playing good now,but videojug is still having problems.

---

### Post by Drakkor on 2008-05-03
Guess that's why I have a dual boot :(

---

### Post by SunnyRabbiera on 2008-05-03
well hold on a sec, if its just flash then installing the flash plugin should help...
let me try it and see what other plugins you need.

yes you just need the flash plugin, what kind of processor do you have though?

---

### Post by Drakkor on 2008-05-04
HA! Just bought the computer yesterday,lol, and its a Intel Duo Core processor, at 2.2 GHZ with 4GB shared Ram,500GB hdd ACER ASPIRE

---

### Post by SunnyRabbiera on 2008-05-04
alright, thought I ask just in case you had a AMD (that sometimes has problems with flash)
what version of ubuntu are you running?

---

### Post by Drakkor on 2008-05-04
8.04 Hardy

---

### Post by SunnyRabbiera on 2008-05-04
are you using the 32 bit version or the 64 bit?
this matters as it can give me insight to your issue.

---

### Post by Drakkor on 2008-05-04
As far as I know it's the standard I386 32bit version that I downloaded and installed.

---

### Post by Drakkor on 2008-05-04
Anyone else got any bright ideas ? ,lol :)

---

### Post by SunnyRabbiera on 2008-05-04
alright, just install flashplayer nonfree and that should solve your problem.
installing flash is easy, go up to system then to administration and into synaptic package manager.
in synaptic go up to settings and then to repositories and make sure everything is checked off on the first tab except the source code repository
and then go to the second tab and make sure everything is checked off there too except the source code repositories.
after that close the repository manager and then click refresh and then search for flashplayer, or just flash
and then from there go down to flashplayer nonfree and MAKE sure that gnash and others are not present, installed packages will have a green box beside them.
on the flashplayer nonfree box, right or left click it and mark it for install, then go up to apply and the rest of the installation process should be pretty straightforward.
All that other stuff I asked was for a reason as I know that the 64 bit version of ubuntu has issues with flash.

---

### Post by Drakkor on 2008-05-04
That's all fine,but I already have the flashplugin non-free installed, I just installed the "ubuntu restricted extras", and still no videos !

---

### Post by Drakkor on 2008-05-04
Found the answer here ,post #6 [http://ubuntuforums.org/showthread.php?t=771423&highlight=firefox+video](http://ubuntuforums.org/showthread.php?t=771423&highlight=firefox+video)
Am watching videos now !! :) Thanks for trying though.

---

