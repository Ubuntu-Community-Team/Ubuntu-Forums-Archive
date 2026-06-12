---
title: "Problem switching to onboard graphics"
date: 2011-11-15
forum: New to Ubuntu
---

### Post by jockyburns on 2011-11-15
The graphics card on my computer has packed up. I have taken it out (GE Force 8400GS) Was running the additional drivers for this card, but have plugged into the onboard graphics of the mobo (AS Rock G31M-S R2.0. When I started up again, (Ubuntu 11.04 Natty)seems to load as normal but there's absolutely no display at all. I think Ubuntu might be trying to use the graphics settings as though I still had the graphics card installed. No desktop, nothing, just a blank screen (although when it starts up initially I do get the set up screen and can access setup and bios before Ubuntu starts, but after that it's totally blank. If I force a shutdown the Ubuntu shutdown screen appears though (the one with ubuntu in white letters against a purple background with the red dots counting down) 
Any bright people out there can help me??
Thanks in advance  
JB

---

### Post by r_mano on 2011-11-15
Try ctrl-alt-F1 and see if the system is alive --- you should have a text terminal for it. 

My guess would be to delete all the proprietary drivers. If I am not wrong, you had a NVIDIA card before, and an Intel one now. So you should remove the nvidia non-free drivers.

Try to see if you can boot in safe mode (ESC when Linux is starting, then choose safe mode). 

I found something here, but I do not know if it's appropiate: [https://wiki.ubuntu.com/X/Troubleshooting/NvidiaDriverSwitching](https://wiki.ubuntu.com/X/Troubleshooting/NvidiaDriverSwitching) , use at your own risk ;-)

---

### Post by jockyburns on 2011-11-15
I have managed to start it in recovery mode and have selected fix broken packages. It's downloading stuff as I type here on G/F's computer so hopefully (fingers crossed) should be running again soon. If not I'll certainly give your suggestions a try (I'm no expert though) and will follow your links and have a look. Cheers

JB

---

### Post by r_mano on 2011-11-15
OK. If you have some graphic interface, try to select system settings (from the user menu) and then "additional driver", and deselect all the NVIDIA graphics drivers. 

HTH --- and have luck!

---

### Post by jockyburns on 2011-11-15
Thanks to all for the replies. Tried the recovery mode, but for some reason there were certain files it wouldn't load (whilst loading files it kept getting into a loop about pixel???? and when it stopped and then finished, asking for a restart, I just got the black screen of doom. So I have downloaded 11.04 on to a USB stick and have re-installed it right from scratch (haven't lost too much though as I've only been using Ubuntu for a few months) Just re-installing other things like Chrome, Winetricks and a few games, but still have to update everything, so looks like a few sleepless hours re-doing it so'd it's just so. Grrrrrrrr, I know it's an old graphic card (4 yrs old) but NVidea should hang their heads in shame :):):):) Nah , must have been ready for a new one anyway:):)

Just glad to be back on though.:)

PS only took a few minutes to set up my email account...... Amazing memory I have for a 55yr old. :D

---

### Post by mörgæs on 2011-11-15
Changed the title to a more descriptive one.

If the reinstall solved the problem, please mark the thread so.

---

### Post by r_mano on 2011-11-16
Hmmm... by reading the thread I had the impression his problem was that he *removed* the GE Force card, and that Ubuntu failed to switch to the Intel on-board device. 

Unfortunately I do not know how to start a complete X reconfigure (maybe an apt-get purge nvidia\* and dpkg-reconfigure xserver-xorg would do?). I am a very old Linux user (1989, Slackware, 0.99plsomething kernel), but it's at least 10 years without touching a xorg.conf file --- if it's still existing ;-)

Ah, for jockyburns: one thing I had learned is that having /home (and /usr/local if you like to install things outside the distro) as a separate partition is worthwhile, makes the pain of a reinstall go mostly away.

---

### Post by mörgæs on 2011-11-16
Sorry, changed again.

---

