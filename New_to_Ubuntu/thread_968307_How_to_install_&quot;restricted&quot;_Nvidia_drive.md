---
title: "How to install &quot;restricted&quot; Nvidia drivers for kubuntu 8.10"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by gregphil on 2008-11-02
I updated to kubuntu 8.10 and now I can't enable any of the 'advance' desktop display features.

I can't find the menu(s) to download or enable the 3rd party 'restricted' Nvidia drivers under kubuntu 8.10.

Can anyone help by suggesting (in detail) the procedure needed to get full video functionality with kubuntu 8.10?

BTW, same question for ubuntu 8.10

---

### Post by phidia on 2008-11-02
Does the card/driver show up from System > Admin > Hardware drivers?

If you can't enable the card from there open synaptic package manager from the same menu path and search for nvidia.

---

### Post by gregphil on 2008-11-02
That is the problem. ALL the 8.10 menus are totally different  (why ?????)

I did find (under Applications - System - Hardware Drivers) a menu that looks like it might be the right spot to "enable" a Nvidia driver, but it says there are "no proprietary drivers in use on this system".  The 3rd party Nvidia drivers were installed prior to the upgrade form 8.04.1 to 8.10

I can't find anything useful under the Adept installer, they REALLY screwed up the user interface to this tool.  It can't even show what is installed or waiting to update.  Using a separate way to get to Adept (applications - System - Package manager) shows a slightly different Adept screen.  It has buttons that I think are intended to allow filtering the packages available but I can't seem to get them to function.  If I type in "Nvida" in the search box I get lots of hits, but no hint on which one might work.  Most packages seem to claim they need a "special kernel" to be compiled and used.  What does this need to be so hard?  Under the previous version (8.04.1) I simply checked a box to enable the true Nvidia driver.

So, again. what are the exact recommended steps to use the true Nvidia driver?

Such as 
1. download driver from ???? by executing command ?????
2. place driver in special spot in kubuntu tree ?????
3. Invoke some special kubuntu menu (Hardware Drivers menu ?)
4. reboot?

---

### Post by wgrant on 2008-11-02
Ubuntu 8.10 uses a recent version of X.org. NVIDIA has so far failed to release versions of their legacy proprietary drivers that work with our new version of X.

If you have a fairly old NVIDIA card, that would be why. We can do nothing about it until NVIDIA fixes their drivers.

---

### Post by gregphil on 2008-11-02
I would have been nice if the release notes mentioned that Nvidia cards must run in brain dead mode for now (under 8.10)

Thanks for your reply, now I can stop looking for a solution to that problem.

---

### Post by Newtothegame on 2008-11-02
Hey gregphil, 

I like you had many issues with Ubuntu and my video drivers. However the menus on my two installs have never changed. I did notice that i could click on system on the top and it would launch random programs. This was due to screen resolution. You need to do a complete update in System>admin>update manager. The check what was mentioned above. 

If that doesnt work let me know. 

Also what driver are you attempting to instal. For me I had the best luck with 169 verson but since upgrading and playing around a bit 177 has been awesome. 

-Newtothegame

---

### Post by PatrynXX on 2008-11-13
I had just updated from 8.04 to 8.10 kubuntu and it was a visual change.  I had just about given up on 8.04 because of the Nvidia restricted drivers didn't quite work but when I upgraded to 8.10 beta, suddenly my res was way out and that rocked.  But today it installed the updates requiring a restart and now I'm back to square one.  What changed today or the past week so that I can't use restricted drivers anymore?  I assume I'm no longer in Beta.  Now I'm back to the 90 year old man zoomed pictures that are hard on my eyes.  Maybe I'll stay subscribed to this thread until someone reports Nvidia has a fix or if there's another way to trick it into setting my resolution back up to something other than 800x600.   :confused:

---

### Post by jimv on 2008-11-13
Envy has been released for 8.10, and that should get us up and running.

FIRST:

You need to install Envy.  Run this command:

```
sudo apt-get install envyng-qt
```

SECOND:

Run Envy to grab the latest drivers:

```
envyng -t
```

THIRD:

Press 1 to install the Nvidia drivers.  On the next screen, press the appropriate number for the driver you want to install...which will be the one marked with a + under the Recommended column.

FOURTH

Once the install is finished, it will ask you to reboot.  Reboot.

---

