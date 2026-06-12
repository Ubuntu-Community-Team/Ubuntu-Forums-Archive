---
title: "Randomly going to lock/user change screen...."
date: 2014-07-14
forum: New to Ubuntu
---

### Post by badtlc on 2014-07-14
at some point within the last 2 weeks, my lubuntu 14.04 install has started going to the lock screen asking for a password.  I had it set to boot directly to the desktop and still do.  I'm not sure why it is doing this.

It seems to do it when the monitor goes off due to a timeout.

I have noticed that after a reboot, if i go to power settings it says XFCE power manager isn't running and asks if I want to enable this.  it didn't have that problem before either.

Anyone know how to get rid of this annoying behavior?

---

### Post by gilligan216 on 2014-07-14
in Ubuntu 14.04  goto system settings, brightness and lock. uncheck the box with the caption "require my password when waking from suspend.

---

### Post by bapoumba on 2014-07-15
Just to make sure, are you talking about login in your user account after booting up or going back to your session after inactivity ?

For the later, please try 
Prefs > Light Locker Settings > Auto Lock the Session set to never.
You'll probably need to log out and log back in to take effect.

---

### Post by linux_dream on 2014-07-15
> **bapoumba said:**
> Just to make sure, are you talking about login in your user account after booting up or going back to your session after inactivity ?  For the later, please try  Prefs > Light Locker Settings > Auto Lock the Session set to never. You'll probably need to log out and log back in to take effect.  I do not think this is enough to fix it. At least this doesn't fix the problem in my computer. Here are 2 threads about the same problem, and they are not solved:  1)[http://ubuntuforums.org/showthread.php?t=2233575](http://ubuntuforums.org/showthread.php?t=2233575) 2)[http://ubuntuforums.org/showthread.php?t=2233295](http://ubuntuforums.org/showthread.php?t=2233295)

---

### Post by uRock on 2014-07-15
> **linux_dream said:**
> I do not think this is enough to fix it. At least this doesn't fix the problem in my computer. Here are 2 threads about the same problem, and they are not solved:  1)[http://ubuntuforums.org/showthread.php?t=2233575](http://ubuntuforums.org/showthread.php?t=2233575) 2)[http://ubuntuforums.org/showthread.php?t=2233295](http://ubuntuforums.org/showthread.php?t=2233295)

Have you filed or found a bug report on this issue? If it is indeed a new setting via updates, then it needs to be fixed.

---

### Post by linux_dream on 2014-07-15
> **uRock said:**
> Have you filed or found a bug report on this issue? If it is indeed a new setting via updates, then it needs to be fixed.  No I have not, because I am not sure what program is faulty exactly. I've been reading [https://wiki.ubuntu.com/Lubuntu/ReportingBugs](https://wiki.ubuntu.com/Lubuntu/ReportingBugs) and I wouldn't know how to report that bug in an effective manner.  As a sidenote, I tried to follow the answer given at [http://askubuntu.com/questions/130808/stop-xscreensaver-from-locking-screen-once-screensaver-starts](http://askubuntu.com/questions/130808/stop-xscreensaver-from-locking-screen-once-screensaver-starts) (removing xscreensaver) but this didn't work either as in my system xscreensaver was not installed by default nor did I install it despite that "locate xscreensaver" would return several files in my computer.

---

### Post by badtlc on 2014-07-18
Yeah, i have the same problems as the other threads.  It doesn't ask for my PW on reboot, only after waking.  Disabling light locker didn't fix it.

---

