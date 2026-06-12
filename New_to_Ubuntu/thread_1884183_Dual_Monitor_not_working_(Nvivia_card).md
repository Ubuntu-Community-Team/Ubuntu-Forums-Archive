---
title: "Dual Monitor not working (Nvivia card)"
date: 2011-11-20
forum: New to Ubuntu
---

### Post by juliandracos on 2011-11-20
I have read through these forums and searched online and I have not found a solution.

It should be noted that if I run Ubuntu 11.10 64 bit from the disk both monitors work, but now that it is installed, only one monitor works.  Fixing it creates more problems.  Problems so bad that with my tiny bit of linux knowledge renders me incapable of fixing forcing me to reinstall.  

Problem 1:  Only one monitor working/connected

Attempt Solution 1:  Install and use Gnome.  Nothing changed

Attempt Solution 2:  Install new Nvidia drivers.  Result:  only one monitor displays and everything is frozen except for the mouse.  No programs work.  I can do crtl-alt-f1 to get to the terminal.

Attempt Solution 3:  Changed nvidia settings by tying gksu nvidia-settings.  Result is that I could get both monitors detected.  I set the second monitor to be the extension of the desktop.  Rebooted and this leads to:

Problem 2.  Second monitor is all white.  Mouse can go to the second monitor, but it cannot be used.

Attempt solution 1:  Chang nvidia settings again.  This time I clicked for xcinema.  I then restarted.  This led to:

Problem 3:  Both monitors now display on reboot.  I have the background on both monitors.  The menu bar is displayed on the main monitor.  However the system is now no responsive.  I click and nothing happens.  crtl-alt-f1 pulls up a terminal.  I try to login, but it now says the password is incorrect.  It is possible that on reinstalling I put in the wrong password, but I doubt it.  


So what I am looking for is two things.

First, when attempting to get the second monitor to work and things go bad, how can I get things back to where they were so I do not have to reinstall?

Second, Provided I have the answer to #1.  What other solutions to you propose to get both monitors workings?  

Thanks for your time

---

### Post by juliandracos on 2011-11-21
Sorry for the bumbpage.  Just want to give this one more try before I give up on Ubuntu.

---

### Post by MrLeek on 2011-11-21
I was experimenting with this the other day. It seems to work ok for me - I loaded up the "Nvidia X Server Settings" (search the dash for Nvidia). I had to help things along a little by enabling the second screen

I've also read that "Twin view" is better overall - it caused me less trouble to set up to be honest.

The biggest problem I had was that software that wanted a full screen (like a game in Steam) couldn't really understand what screen to use so it all went wrong. Since the 2nd screen I was using might be having issues showing green (it's a 5 yr old screen so might be about to die) I've not really gone that much further.

Sorry - not a lot of help (I'm sure a clever person will be along soon!). But I didn't really have to do that much to get an image to appear on the 2nd screen. As long as the Nvidia drivers are installed it shouldn't be that hard - maybe I got lucky? 

Oh - final thought. The "displays" option was really unhelpful - even when I had 2 screens working the Ubuntu diplay setting manager was only able to see the original screen. It still doesn't know what the monitor make/model is - which the Nvidia settings thing does.  

Apologies if none of that helps - you're not alone with the battle to learn this OS :)

---

### Post by juliandracos on 2011-11-22
The solution I found was to switch to a different linux based OS.  From my experience, both Mint and Zorin OS work.  This leads me to the assumption that part of the problem is with Unity.  All three use Ubuntu as the base, but Ubuntu uses Unity and the others do not.  It seems that the problem I had was with breaking the GUI in Ubuntu.  I tried using Gnome and Unity 2D and it still didn't work so I am not sure if Unity was the cause of the problem.

Additionally, part of the problem seems to be the inability to write when saving the configuration when you run the nvidia-settings.  There were less problems with the other OS than with Ubuntu.  

For anyone that will search these forums for the same problem, this is what I have found out.  Twinview has less problems than xinerama.  Avoid checking that is possible (I had to click it for Ubuntu to get the screen to display, but not in the other OS).  Second, if you go to save something and it says that what you are trying to save is too long and wants to truncate things because not truncating it will cause problems - *don't believe it!*  By writing the entire files everything worked great (at least with other linux OS.)

It seems weird that Ubuntu based OS do not have this problem while Ubuntu does.  It is also shocking that given numerous complaints about this with Ubuntu that Ubuntu has not resolved the problem or at least has some official post on how to fix the problem.  I hope this post will help the developers fix this problem or at the very least help those searching these forums who have the same problem.

---

