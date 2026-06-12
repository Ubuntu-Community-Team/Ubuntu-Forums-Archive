---
title: "Locks Up"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by weaver4 on 2008-05-04
My Hardy Ubuntu locks-up when I am not using it.  When I am using the computer it is flawless, but if I walk away from the computer for 2-10 hours and press the spacebar about 1-out-of-10 times it will not respond.  I have the power management set up so that it does not go to sleep and I have the screen go blank after 6 minutes.

If I look at the logs I can see that the computer ran for several hours before it locked up, but there is no other indication of what was wrong.

When the computer locks up it disapears from the network, so it is not just the fact that the screen does not return.

Any ideas on what I should be looking for?

---

### Post by weaver4 on 2008-05-04
Bounce

---

### Post by weaver4 on 2008-05-07
Bounce

---

### Post by Delever on 2008-05-07
First, latest updates. Are they installed?

---

### Post by Poliwop on 2008-05-07
I upgraded to 8.04 last night and immediately began having the same problem.  I don't know how to look at logs or what to look for, but my laptop won't return from the blank screen (in my case, after I close the lid).  Latest updates are installed.

---

### Post by weaver4 on 2008-05-12
Sorry it took so long to get back with you.  I wanted to try a fresh install to see if anything changed.  It did not I still have the failure.  

I am a desktop unit not a laptop and I never let the unit go into standby so it is not a recover from standby problem.

But, the motherboard I am using is a mini-itx with both and interface for a LCD screen and a standard VGA.  I wanted to disable the LCD driver and test it again, but I can not figure out how to do that.

Any suggestions?

---

### Post by weaver4 on 2008-05-12
And yes, I do have the latest updates.

---

### Post by Kapitän Rotbart on 2008-05-12
My old laptop locked up upon a blank screen in Feisty and I believe in Gutsy as well (I haven't tried it since on that computer). This has never been an issue on my new laptop (which has other issues with Ubuntu, however suspend and hibernate work perfectly). Do you need to save power? If you're going to leave your computer for quite a while and you're not in the process of downloading/saving/etc. anything that would take a long time, consider suspending or hibernating your computer (assuming your computer supports suspend/hibernate), otherwise you can always shut it down.

If power saving isn't an issue, you can easily deactivate the blank screen by going to *System>Preferences>Power Management* and under the "AC Power" and "On Battery" tabs, set the action for when the laptop lid is closed to "Do Nothing" and your screen will not go blank.

Also, are you using a screensaver? If so, is it the Ubuntu screensaver or the compiz screensaver? If either screensaver results in a lock up, best deactive the screensaver :-P

---

### Post by weaver4 on 2008-05-13
Since my unit is not a laptop and is not going into standby or hibernate I think that the above problem is not related to my problem that started this thread.  

Please start another thread for your laptop problem.

---

