---
title: "Stopping Suspend and login"
date: 2014-07-14
forum: New to Ubuntu
---

### Post by ray9 on 2014-07-14
How can I stop the computer from suspending?  Or just making it so I don't have to log in after being idle for some time.  I searched this and found references to system>preferences>screensaver but I can't find system preferences, much less screensaver.   Ubuntu 14.04 LTS.

Thanks

---

### Post by coffeecat on 2014-07-14
> **ray9 said:**
>  I searched this and found references to system>preferences>screensaver but I can't find system preferences, much less screensaver.



That's because you found an ancient howto telling you how to do this in the old gnome 2 desktop, which Ubuntu hasn't used since 10.10.

Assuming you are using Ubuntu 14.04 with the Unity desktop, click on the cogwheel icon top-right -> System Settings -> Power.

If you are not using Ubuntu 14.04, tell us which version of Ubuntu, which flavour and which desktop you are using. These forums are for support of Kubuntu, Xubuntu, Lubuntu, Edubuntu, Mythbuntu and Ubuntu Studio as well, so unless you say what you are using, it is difficult for people to help.

---

### Post by ray9 on 2014-07-14
Thanks.  I'm using 14.04 LTS.  I have the power setting at "never" and  "don't suspend".  It does it anyway.

---

### Post by coffeecat on 2014-07-14
Ah. Re-reading your first post, I think you must be referring to the lockscreen, not to a suspend. System Settings -> Brightness & Lock. Increase the time or set it to never for blanking the screen. And set lock to off if you don't want the screen to autolock and have to put in your password to unlock it.

**Edit**: I have my lock set to off, but I can lock the screen at will if I wish to with ctrl-alt-L.

---

### Post by ray9 on 2014-07-14
Thanks again.  I set as you recommended.  I also downloaded and installed "xscreensaver" as I didn't seem to have any screensavers on board.  I ran it through the terminal by entering "xscreensaver" and it opened and ran but now I don't know how to turn it off to set it or access in progress.

---

### Post by ajgreeny on 2014-07-14
You need to add xscreensaver to your startup applications, (not certain how to do that in unity), but the command needed to run it in the background is **xscreensaver -no-splash** then you can set it up to start and run as you want.

I can't remember if unity has gnome-screensaver installed by default but if it does you will need to make sure that is not running as well or there may be conflicts between the two.

EDIT:
It looks as if xscreensaver -nosplash is also a command that works, though some report that the extra - after "no" is needed.  Try both if one doesn't work for you.

---

### Post by buzzingrobot on 2014-07-14
Use "Startup Applications" to add , ummm, startup applications.

---

### Post by ray9 on 2014-07-15
Thank you for the help.

---

