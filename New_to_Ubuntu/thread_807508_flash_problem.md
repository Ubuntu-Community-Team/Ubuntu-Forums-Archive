---
title: "flash problem"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by shayvasa on 2008-05-25
hi, i have a problem with firefox and flash player, i have the firefox flash player and macromedia flash player. so heres what happenes, sometimes, not all the time, when i enter a page that has flash, a lot of flash, like youtube, gamespot, etc.. firefox closes. its really annoying.
how can i fix this?

---

### Post by ubuntu-freak on 2008-05-25
I've added instructions for both 32/64-bit users on manually installing Flash v10 beta in Ubuntu to Part 1 of my [Multimedia & Video How-to](http://ubuntuforums.org/showthread.php?t=766683).
 
Nathan

---

### Post by shayvasa on 2008-05-26
it didint work :(

---

### Post by philinux on 2008-05-26
> **reassuringlyoffensive said:**
> 
 
P.S. If any 64-bit Ubuntu users are reading this, you need to execute one more command:
 
**sudo nspluginwrapper -i /usr/lib/firefox/plugins/libflashplayer.so**

Interesting Nathan I just copied the file in earlier today without that command and it worked fine. Also this version has fixed the losing flash problem that needed a firefox restart.

---

### Post by shayvasa on 2008-05-26
but my firefox still restarts.
how can i check if it worked?

---

### Post by philinux on 2008-05-26
You could try this.

In a terminal type

firefox -safe-mode

It could be one of many addons.

---

### Post by shayvasa on 2008-05-26
so every time i enter firefox i need to write that?

---

### Post by philinux on 2008-05-26
> **shayvasa said:**
> so every time i enter firefox i need to write that?

No this is just a one-off diagnostic mode. Some addons can cause firefox to crash. They are all 3rd party remember. If in safe mode firefox does not crash and flash works then try running firefox normally and try disabling all addons then enable them one by one and test logically.

---

### Post by shayvasa on 2008-05-26
ok thanx

---

### Post by ubuntu-freak on 2008-05-26
> **philinux said:**
> Interesting Nathan I just copied the file in earlier today without that command and it worked fine. Also this version has fixed the losing flash problem that needed a firefox restart.

 
Yeah, libflashsupport causes the crashing, but there is no sound, or choppy sound in Flash 9 + PulseAudio without libflashsupport. Flash 10 actually supports/recognises PusleAudio.
 
So, the plugin works on your 64-bit Ubuntu without it being wrapped?
 
Nathan

---

### Post by shayvasa on 2008-05-26
are you asking me? lol, i have a 32 bit btw. and i only have 1 ad on in firefox, i disabled it and so far so good. ill let you know if it crashes again

---

### Post by thegekko on 2008-05-27
I had this problem.  I found the problem to be the flash blocker ( 1.3.9a ) add-on.  I disabled the add on and everything was fine.
Do you have flash blocker installed?

---

### Post by shayvasa on 2008-05-27
no idea, but i think i fixed it, i disabled flash and just left the flash of firefox and i think its working fine, any differences between the 2?

---

### Post by steveneddy on 2008-05-27
> **reassuringlyoffensive said:**
> You might want to try Flash 10 beta. First of all, copy and paste this command into the terminal:
 
**sudo apt-get purge flashplugin-nonfree libflashsupport** 
 
Next, [download Flash 10 beta](http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_install_linux_051508.tar.gz) and move the file named "libflashplayer.so" to your desktop, then execute this command:
 
**sudo mv ~/Desktop/libflashplayer.so /usr/lib/firefox/plugins**
 
Restart Firefox.
 
Nathan 
 
P.S. If any 64-bit Ubuntu users are reading this, you need to execute one more command:
 
**sudo nspluginwrapper -i /usr/lib/firefox/plugins/libflashplayer.so**

Does 10 beta work better with drop down menus?

---

### Post by ubuntu-freak on 2008-05-27
> **steveneddy said:**
> Does 10 beta work better with drop down menus?

 
That bug still persists. 
 
Flash playback is accelerated now though, but they mistakingly disable it when composite is enabled. If you pause a YouTube vid with effects off, then switch effects on, the playback will still be accelerated. Shame the Adobe devs don't understand the elementry workings of composite. 
 
At least it supports PulseAudio now, no more crashes due to libflashsupport.
 
Nathan

---

