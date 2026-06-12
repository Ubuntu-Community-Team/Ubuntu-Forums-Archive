---
title: "Sorry UBUNTU but it's back to XP for me..."
date: 2008-05-26
forum: New to Ubuntu
---

### Post by Foghornleghorn on 2008-05-26
I've been trying for the past three days to Boot Ubuntu with my  PNY Geforce 6200 (PCI 256 mb graphic card).Having read through lots of pages from these threads, nothing seems to work. Funny thing is if i revert back to my onboard Graphics then UBUNTU is happy to play ball. The new Graphics card is recognized by XP without any problems so i know that the card isn't at fault.
I really liked UBUNTU but until some GURU or more knowledgeable PERSON can help me out,then reluctantly i have to revert back to XP. 
I'm still a newbie when it comes to UBUNTU so any useful suggestions please bear this in mind.
Thanks in Advance.
regards,
Foghornleghorn.

---

### Post by dRock1286 on 2008-05-26
Have you tried searching for the Nvidia drivers for linux?  If so, have you tried the beta version?

---

### Post by Joeb454 on 2008-05-26
Did you try to install the Nvidia Drivers? Usually Ubuntu will find them and list them in System > Administration > Hardware Drivers :)

---

### Post by PmDematagoda on 2008-05-26
The 6200 is very Ubuntu-friendly, in fact I use it myself. What problems do you have with the card?

---

### Post by Foghornleghorn on 2008-05-26
Thanks All for taking timeout to try and assist.

After disabling the Onboard Graphics and Booting into UBUNTU with the Geforce, it goes to the logon screen the stroll bar appears for a few seconds then nothing else happens.

---

### Post by Nepherte on 2008-05-26
You'll have to specify/describe your problem with more details. Do you get to the login screen or does it seem to 'try starting the login screen in a loop' resulting in safe screen mode?

---

### Post by Foghornleghorn on 2008-05-26
Sorry forgot to add that having Ubuntu loaded using Onboard Graphics,i enabled the Nvidia drivers and then rebooted with the PCI card installed. Still unable to load UBUNTU.

---

### Post by Foghornleghorn on 2008-05-26
I'm currently posting using XP, will logoff and try rebooting UBUNTU again. Will post what happens in the next few minutes.
Thanks again.

---

### Post by Foghornleghorn on 2008-05-26
Just attempted to Boot into UBUNTU...

The first screen that appears gives me the option to press ESC to enter menu.
The Ubuntu Screen appears and the Orange bar strolls across successfully first time.
Second Orange bar stops, and another 2 Orange bars appears on screen...1 on left and 1 on far right of screen.
Nothing else happens after, so i manually shut the system off and reboot in xp.
Hope the above makes sense,but i'm posting what i see.
regards,
Foghornleghorn.

---

### Post by bravo331 on 2008-05-26
I know this is a stupid question and I only ask because I have done this myself. Do you have your monitor's cable plugged into the correct port on the GeForce video card, or is it still plugged into the motherboard onboard VGA port? The Ge Force has a VGA and a DVI port, correct? So you should have 3 different ports in total, 2 on your card and one for the on board graphics? I don't see anywhere in your posts any reference to unpluggng your monitor from onboard and plugging it into GeForce and back again when rebooting, is all!

---

### Post by Joeb454 on 2008-05-26
> **bravo331 said:**
> I know this is a stupid question and I only ask because I have done this myself. Do you have your monitor's cable plugged into the correct port on the GeForce video card, or is it still plugged into the motherboard onboard VGA port? The Ge Force has a VGA and a DVI port, correct? So you should have 3 different ports in total, 2 on your card and one for the on board graphics? I don't see anywhere in your posts any reference to unpluggng your monitor from onboard and plugging it into GeForce and back again when rebooting, is all!

Actually that's not stupid at all, I've done that a few times :oops:

---

### Post by bwhite82 on 2008-05-26
I can get you into an Ubuntu desktop at least, if you follow the exact steps that follow:

1) At the grub boot screen, press down and select the 'Recovery Mode' option (second option down)

2) When you get to the command prompt type:

> sudo nano /etc/X11/xorg.conf

3) Scroll down (arrow keys) until you see:

> Section "Device"

Underneath, that you will see:

> Driver  "nvidia" (OR something else in between the quotes)

4) Change the word in between the quotes to:
> 
Driver    "vesa"

5) Hit CTRL+X, then press 'Y', to save and exit the file.

6) Type in:

> startx

7) Enable the nvidia driver in 'Hardware Drivers' in the menu, if, failing that, read the wiki on how to get video working for your card.

8 ) Please stop threatening to return to XP, because, in all honesty, no one cares. We are all volunteers here.

If you have further questions, please post them.

-Cheers

---

### Post by PmDematagoda on 2008-05-26
Also, try booting Ubuntu in Recovery Mode and if the loading stops, post the error message you get.

---

### Post by Foghornleghorn on 2008-05-26
Originally Posted by bravo331  
I know this is a stupid question and I only ask because I have done this myself. Do you have your monitor's cable plugged into the correct port on the GeForce video card, or is it still plugged into the motherboard onboard VGA port? The Ge Force has a VGA and a DVI port, correct? So you should have 3 different ports in total, 2 on your card and one for the on board graphics? I don't see anywhere in your posts any reference to unpluggng your monitor from onboard and plugging it into GeForce and back again when rebooting, is all!

Yes i'm using the correct port for the PCI card...I'm Dual Booting with XP, so i diable the Onboard graphics via BIOS and then select PCI as my preference swapping the leads around.
I'm going to Boot into UBUNTU with the Onboard Graphics and try installing Envy maybe this may solve the problem. Fingers crossed.

---

