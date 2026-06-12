---
title: "Screen resolution issue"
date: 2012-11-18
forum: New to Ubuntu
---

### Post by JezzaV on 2012-11-18
Hi

Sony KDL37-W5500
Nec PC connected via VGA cable

I've a PC connected to my TV, install ubuntu no problems, after install all I get is the mouse cursor.  It seems to be missing any icons / menu bars, must be due to the screen resolution.  I have looked at the TV settings and can shift horizontally and vertically but still  cannot get anywhere useful to change resolution.

Any idea what next to try ?

Thanks

---

### Post by twipley on 2012-11-18
I would try changing resolution from the PC instead than from the TV. (Settings -> Displays)

Also, if you had a HDMI-output video card, that would be better than VGA. HDMI is digital, plus it supports higher resolution, which would display text better on TV, among others.

Good luck. ;)

---

### Post by JezzaV on 2012-11-19
Thanks for the reply

I would try that but can't get to display > settings as have nothing on the screen other than a mouse cursor.  If I do Ctrl Alt Del the logout dialog pops up so I know it can display things.  Also noticed after messing around at the login screen which does display some some items top right, if i try and create a remote login account a tiny Mozilla Firefox window opens up top left !  Strange issue but does seem resolution issue or similar.  I'll take a look and see if any shortcut keys may help to get into display > settings

---

### Post by LuisGMarine on 2012-11-19
Did you recently update the kernel and or video drivers?

---

### Post by JezzaV on 2012-11-20
Hi,

Its a fresh install and although I have done a apt-get update and upgrade its still the same, if I load off the DVD it also only gives me the mouse cursor, it's got a nvidia card in it so could it be the drivers ?  If so how can I remove and install later drivers

Thanks for any help

---

### Post by cwsnyder on 2012-11-20
On your Ubuntu installation disk, can you get a Live session? (That means to try Ubuntu without installation?)

If you can run the Live session, what resolution is reported for your display? (or open a terminal by Ctl-Alt-F2 and type **xrandr** on a line by itself to get a report on the resolutions that Ubuntu thinks it will support.)

---

### Post by LuisGMarine on 2012-11-20
Try this out ...
[http://ubuntuforums.org/showthread.php?t=2083636]("http://ubuntuforums.org/showthread.php?t=2083636")

I had a similar problem and running the commands here fixed it.  The commands are exactly what you need to pretty much re-install the nvidia drivers, and fix some issue with the linux-headers-generic package.

---

### Post by JezzaV on 2012-11-20
Hi

Cwsnyder, it's the same booting off disk, only mouse cursor, xrandr shows 1024x768

Luis, thanks for the commands, they worked sort of, all ran, rebooted, still no menu or icons but its now using a 4:3 ration and I can right click to change background and get into settings, display shows driver: VESA NV17 () board and experience is standard

Getting closer hopefully, any next suggestions ?

Thanks so far

---

### Post by cwsnyder on 2012-11-20
It is sounding more and more that the settings on the computer should be okay, but the settings on the television display are not set correctly.

Have you tried changing your screen format button and position controls to see if you can get a better display?

---

### Post by JezzaV on 2012-11-21
Hi

I got a bit further, I noticed a post about logging in and selecting a different theme using the cog next to the username, tried this and the top menu came up, I also found some commands to strip off the nvidia drivers and reinstall xorg, this then displayed the menu at a high res although still not quite right, I suspect the card is not supported with the latest nvidia driver so I will try and find a matching driver.  I did also move picture about like you mentioned.

Thanks for the help

---

### Post by LuisGMarine on 2012-11-21
> **JezzaV said:**
> Hi

I got a bit further, I noticed a post about logging in and selecting a different theme using the cog next to the username, tried this and the top menu came up, I also found some commands to strip off the nvidia drivers and reinstall xorg, this then displayed the menu at a high res although still not quite right, I suspect the card is not supported with the latest nvidia driver so I will try and find a matching driver.  I did also move picture about like you mentioned.

Thanks for the help

If it's a question about drivers try using the "nvidia-current", I hear that it is much more stable, thus it has more testing, than the "nvidia-current-updates" driver.

---

