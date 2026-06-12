---
title: "CCSM not doing anything. 11.10"
date: 2011-10-20
forum: New to Ubuntu
---

### Post by corl45 on 2011-10-20
Hi, I used to use Ubuntu pretty often on one of my older computers (I ran 9.04 I believe), and got into it quite a bit, though I was and still am a beginner. I messed around with CCSM to get the rotation cube a everything, and though it was cool. But I fell out of Ubunut for a while, then recently I got a new Netbook, that came with Windows 7 starter and I didn't want to buy a new OS for it, so I just wiped it and installed Ubtuntu 11.10. I got used to the Unity interface, and finally decided to mess around with a few Compiz settings. I downloaded CCSM, and found that when I changed ANYTHING, nothing happened. I messed around with wobbly windows and tried changing some shortcut keys on various things, but nothing worked. I tried to set the Unity bar to auto hide, instead of doge windows, because I want it always hidden, but it still hasn't done anything.

Here is a screeny of my system info attached, and while in system info, if I click on "Graphics", under experience it says "standard". Though I'm not sure if that has to do with anything.


Is there something simple I'm missing, or is there a problem?

Thanks,
Corl45

---

### Post by d4m1r on 2011-10-20
It not doing anything is the least of your worries...for most users, it breaks something.

It is not officially support for 11.10 yet AFAIK (wasn't really on 11.04) either so I would just wait as I am sure an update is coming based on its popularity...

---

### Post by PaulInBHC on 2011-10-20
The Unity plugin box is not checked in CCSM by default. Login and select  unity 2d. Open CCSM and check the Unity plugin box. Log out and back in  with Unity selected.

---

### Post by grahammechanical on 2011-10-21
At least your System Info says Ubuntu 11.10. Mine says Ubuntu 11.04.

When I first installed 11.10 alpha, System Info said Gnome 3 with a big image of the Gnome footprint. Then an update changed it to Ubuntu but 11.04 instead of 11.10.

Also every time I tried to change a setting using Compiz Config Settings Manager, it crashed. The settings got changed but the settings manager crashed.

That does not happen now and I have since found that I can use CCSM to set wobbly windows and it works correctly. In 11.104 it would remove the top panel. So there have been improvements over the last six months.

Did you install 11.10 before the release date? Try removing/uninstalling CCSM and then installing it again. Some times a change in settings will take effect immediately and sometimes a particular change will take effect after a reboot.

Regards.

P.S. My graphics is called standard in System Info as well. It is one of those things that will improve over time. If you had stayed with Ubuntu from 9.04 until 10.10 you would have noticed changes but in many ways the desktop would have looked the same.

There have been massive changes to what lies underneath the desktop between 11.04 and 11.10. This is why there is still a need to get little bits of it working as they should. This is what we get when there is a 6 months release schedule.

---

### Post by philinux on 2011-10-21
The reason is that you are running unity 2d. Have a look in additional drivers. You may not have installed your graphics driver. If this option is not available then you will not be able to run unity 3d.

See here for a discussion in the testing forum.

 [http://ubuntuforums.org/showthread.php?t=1864143](http://ubuntuforums.org/showthread.php?t=1864143)

---

### Post by User Abuser on 2011-10-21
It's not because of Unity Fallback. CCSM edits the settings of Compiz and Gnome-shell uses Mutter. Prolly one reason it doesn't work

---

### Post by jrbales on 2011-10-24
> **PaulInBHC said:**
> The Unity plugin box is not checked in CCSM by default. Login and select unity 2d. Open CCSM and check the Unity plugin box. Log out and back in with Unity selected.
 
Man, I wish I'd found your post sooner! It would have saved me at least two reinstallations. I found that whenever I opened CCSM in unity, everything crashes. I can use Ctrl+Alt+F1 to open a terminal and reboot the system. When I went back in using Ubuntu 2D and into CCSM, I found that the Unity Plug-in had been disabled. Once I checked it and resolved three conflicts, Unity came back after restarting the system. 
 
This was the third installation where the simple act of going into CCSM (no changes made) crashed Unity. This is a major bug!  Thanks for the info, you saved me!

---

