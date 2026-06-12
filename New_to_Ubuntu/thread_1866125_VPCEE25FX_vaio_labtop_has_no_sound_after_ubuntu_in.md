---
title: "VPCEE25FX vaio labtop has no sound after ubuntu install"
date: 2011-10-21
forum: New to Ubuntu
---

### Post by a73u on 2011-10-21
I am new to ubuntu and know very little. After installing ubuntu 10.04 LTS I have no sound. I tried to mess with the sound preference which didn't work and I messed with the alsamixer which didn't work. I have no idea what to do or how to help you help me. I would gladly give you information from the terminal but I don't know what to get or how to get it. I've looked up solutions for this problem and copied several different codes into my terminal, nothing worked which confuses me because it worked for other people. 

Model: VPCEE25FX 
sony vaio labtop

---

### Post by Iang123 on 2011-10-21
Hiya mate, 

You can try what I tried to get sound, not promising it will work though. Here's what I did 

Remove pulse audio 

sudo apt-get purge pulseaudio

Reboot Machine 

Install alsamixer GUI from software centre. 

Have a mess around with the settings in there, and see if you can get any to work for you.

---

### Post by a73u on 2011-10-21
> **Iang123 said:**
> Hiya mate, 

You can try what I tried to get sound, not promising it will work though. Here's what I did 

Remove pulse audio 

sudo apt-get purge pulseaudio

Reboot Machine 

Install alsamixer GUI from software centre. 

Have a mess around with the settings in there, and see if you can get any to work for you.

I removed the pulse audio, rebooted, and installed the alsamixer GUI. There is still no sound.:confused:

---

### Post by Iang123 on 2011-10-21
Can you get sound when you plug headphones in?

---

### Post by Iang123 on 2011-10-21
Do a screen shot of the Alsa mixer GUI

---

### Post by a73u on 2011-10-21
> **Iang123 said:**
> Can you get sound when you plug headphones in?

I tried that and still no sound.

> **Iang123 said:**
> Do a screen shot of the Alsa mixer GUI

---

### Post by a73u on 2011-10-22
> **Iang123 said:**
> Hiya mate, 

You can try what I tried to get sound, not promising it will work though. Here's what I did 

Remove pulse audio 

sudo apt-get purge pulseaudio

Reboot Machine 

Install alsamixer GUI from software centre. 

Have a mess around with the settings in there, and see if you can get any to work for you.

I think removing the pulse audio may have removed my sound system. I get this when I try and go to my sound preferences. Attached file

---

### Post by yazifeather on 2011-10-22
I can't say for sure, but if neither pulseaudio or alsamixer is working, then you probably have a missing sound driver. Try searching around for the model of your computer and see if you can find any information on people installing Linux having problems with the sound and, if so, whether there is a driver that you need to install. I have needed to do this on multiple occasions with my laptop to get the wireless card working. Let us know if you find anything. 

Good luck. I hope this doesn't cause you too much trouble and angst.

ETA: By the way, what version of Ubuntu are you running? From those screenshots it looks like you're running gnome 2.x. I'm pretty sure that Unity has been default since 11.04.

ETA (again): Restricting a Google search to just your model won't turn up anything, but if you search for sound problems for Sony Vaio it turns up a bunch. Here is one that looks promising: [http://ubuntuforums.org/showthread.php?t=1588575](http://ubuntuforums.org/showthread.php?t=1588575)

---

### Post by mglennpooh on 2011-10-22
Click the silver Ubuntu 11.10 Button top left, then, type " t "to bring up & select Terminal, then, type " alsamixer ", then, press <ENTER> to bring up alsamixer, then, tap your Up arrow until the master volumn is maxed. 

There's also a button top right (next to the shutdown button) which normally is used for volumn but you'll feel like you're going deaf if the alsamixer is set too low (default).

---

### Post by a73u on 2011-10-22
:D All I had to do was upgrade ubuntu from 10.04 LTS to 11.10. I don't know what the problem was, but now it's fixed and I'm glad. Wish I could've had it solved so that others with the same problem could stay with 10.04 LTS if they so choose. By the way, thanks for all your inputs. Now, do I mark this as solved?

---

