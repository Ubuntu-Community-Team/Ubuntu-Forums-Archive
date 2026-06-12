---
title: "Intrepid+Screensaver+Freeze: temporary solution"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by bikrus on 2008-11-28
Hi guys!

I had a problem with gnome freeze. Scenarious:

1. Lock screen -> Screensaver works about 1 minute -> Screen backlight fade -> if I want to unlock screen in about 30 seconds or later system "freezed".

2. Gnome login screen (at system startup or after leave session) -> wait some time (haven't noted how much) -> system "freezed".

"Freezed" - display blank, sometimes with backligth, sometimes w/o, sometimes even with mouse pointer. Could be ssh remotely. Xorg about 100% CPU. Xorg couldn't be killed.

I have tried few solutions.

SOLUTION 1.
Replace gnome-screensaver with xscreensaver; replace gdm with xdm.
The problems with freeze has disappeared.

But because of "poor" view and functionality of replacements (x___) I decided to found the reason of problem with gnome tools.

SOLUTION 2.
(in my case I have reinstalled gnome-screensaver and gdm)
Main Menu -> System -> Preferences -> Screensaver
Power Management -> On AC Power -> Display: Put display to sleep -> Never (very right slider position)
Close Power Management Dialog
Close Screensaver Preferences
Alt+F2 (or other way to run console command) -> run gconf-editor
/apps/gnome-power-manager/timeout/sleep_display_ac <- check this value to be 0 (zero), if not set it to 0.
Close gconf-editor
Lockscreen, wait desired time (backlight will not fade), try to restore session.

Second solution works for me. At least 10 minutes of locked session and then restore session. Haven't tried it with login screen yet.

Maybe it will help someone else. Maybe these solutions are present in the net already, but spending few days of googling haven't found them. Maybe I haven't tested them good enough and they will not work as desired. But as temporary solution for me they are good.

Linux 2.6.27-10-generic #1 SMP Fri Nov 21 12:00:22 UTC 2008 i686 GNU/Linux
Samsung R65 (laptop)
nVidia Corporation G72M [GeForce Go 7400] (rev a1)
Gnome 2.24.1 build date 10/24/2008
Ubuntu 8.10 - the Intrepid Ibex

Sorry for my poor English. Good luck.

---

### Post by eternalnewbee on 2008-11-28
Hi there.
You might want to check whether your graphic card is installed properly.
To do that, go to: **Main Menu > System > Administration > Hardware Drivers**.

---

### Post by bikrus on 2008-11-28
Thanks for reply.

As far as I understand, my graphics card installed properly with NVidia driver (177). I have compiz-fusion and GL screensavers works nicely.

---

### Post by eternalnewbee on 2008-11-28
What happens when you press **ALT-F2**, and enter ```
compiz --replace
```?

---

### Post by bikrus on 2008-11-28
> **eternalnewbee said:**
> What happens when you press **ALT-F2**, and enter ```
compiz --replace
```?

When I did this everything disappeared from desktop, then in moment everything went back.

Is this related somehow to screensaver-freeze problem?

---

### Post by eternalnewbee on 2008-11-28
> When I did this everything disappeared from desktop, then in moment everything went back.

Is this related somehow to screensaver-freeze problem?
Nope. This is "normal behaviour" when switching **Window Decorators**.

---

