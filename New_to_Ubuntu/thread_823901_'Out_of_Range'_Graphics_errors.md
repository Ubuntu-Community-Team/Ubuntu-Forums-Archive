---
title: "'Out of Range' Graphics errors"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by Throbkin on 2008-06-09
Im an extreme NooB with a first post, so please treat me like an idiot when responding. :) 

I keep getting a blank screen with the monitor error of 'Out of Range' on certain games. It was happening consistently with Wine applications until I configured a wider virtual desktop. Now those games run but their idea of 'Full-screen' is the same small screen on a blue background. Then I got the same error with an X11 program - XGalaga. I don't know how to set the X Windows graphics settings and suspect this may be a more global problem. 

I'm running an Nvidia GeoForce Fx 5950 and when I clean installed 8.04 it grabbed what I assumed to be the correct updated drivers for 3D from Nvidia. I have not checked their website to confirm, mainly 'cause I wouldn't know how to install them. Screen resolution is set to 1280X1024 with refresh rate of 50. All other graphics are working fine, including Flash, 3D effects, etc...

Is this just a Wine/X11 problem? Is there a way to configure my graphics to handle when a program wants to switch the resolution? Also is there a hot-key for closing a program that is unresponsive or which can't be seen? Xgalaga responded to Alt-Q, is that universal? 

Sorry, that was four questions, any answers to any would be most appreciated. 

Thanks in advance

---

### Post by mike555 on 2008-06-09
I also get errors like that with some games (not in wine) I'm wondering if it's display color bit , but I don't know how to change it or check it , nvidia 5200 card.

---

### Post by Throbkin on 2008-06-09
With the thought that what does not work is equally as useful as what does, here is what I have learned in the past few hours:

I downloaded the updated drivers from Nvidia only to find that they must be installed with X11 off. I used /etc/init.d/gdm stop to cancel X then Alt-Shift-F1 (or was it F2?) to call up a logon, logged on and navigated to the downloaded directory and ran the program as Nvidia had directed. 

I got a very strange error about my Libc header files not being up to date. A quick forum check gave me a solution that involved updating my Lib6 and Lib7 files (somehow).

So far so good. 

Redid the gdm stop trick and ran through all of Nvidia's hoops. Installed nicely after asking about a bunch of things I did not understand. Nvidia said everything updated just fine. 

Then Gnome would not restart. 

On reboot I just got the terminal. It said gdm was running fine but I could not switch over to the GUI to save my life. Multiple reboots, some swearing, and a fresh partitioning and re-installation and I'm back at square one. A wiser and ever so slightly older man. 

I'm going to look into backing up my personal data and trying this thing again. Good news is Ubuntu re-installs in like 45 min. tops. 

Sigh.

---

### Post by heatpumpcontrol on 2008-06-09
> **Throbkin said:**
> 
On reboot I just got the terminal. It said gdm was running fine but I could not switch over to the GUI to save my life. Multiple reboots, some swearing, and a fresh partitioning and re-installation and I'm back at square one. A wiser and ever so slightly older man. 

I'm going to look into backing up my personal data and trying this thing again. Good news is Ubuntu re-installs in like 45 min. tops. 

Sigh.

What you might want to do is use [this gentleman's page]("http://www.albertomilone.com/nvidia_scripts1.html") to download the program that will install the proper nvidia drivers for you.

Once done say yes to update your xorg.conf file and reboot.

Now, for your original issues, try  your personal app without activating the advanced desktop effects. Right click on the desktop->change desktop background->visual effects.

Ensure that you are using the nvidia drivers System->Administration->Restricted Drivers-> select enabled.. reboot.

In wine try different settings within the wine config file. Applications->wine->configure wine and under Applications, try setting the Windows Version Windows 2000 or XP.

Miguel

---

### Post by cariboo on 2008-06-09
If you are using a crt type monitor you may not have the horizontal and vertical frequencies set just right.

Jim

---

### Post by Unix_Slayer on 2008-06-09
You might want to check out this thread. ===>[http://ubuntuforums.org/showthread.php?t=819043]("http://ubuntuforums.org/showthread.php?t=819043")

---

### Post by Throbkin on 2008-06-10
Miguel,

Envy installed and updated the Nvidia drivers, killed the Adv. Desktop effects, enabled the restricted 3d drivers. 

And...same thing. Xgalaga crashes the screen as does the 'Fullscreen' option of the windows game. I tried killing a bunch of the visual effects in Pref-Adv Desktop effects settings. Even fully stripped down, same problem. 

Diddling with Wine's emulation also had no effect; I tried Vista all the way down to Windows 2000. I also tried disabling Wine's window management. Nothing, same problem. Like before I can emulate a desktop environment that floats the game in a larger field but it still won't expand. 

I downloaded the manual for my monitor (an LCD btw, Jim, thanks anyway) and the only problem I can see is that the refresh rates are way off. Manual says no lower than 75 Hz, system-monitor resolution settings says I'm at 50 Hz, the monitor menu itself says I'm at 59.9 Hz. I can't imagine that this is a refresh problem, but what do I know? 

I appreciate your help btw, Miguel...any other suggestions?

---

