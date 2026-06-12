---
title: "Upon logging in, monitor turns off"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by Sydius on 2008-06-10
I can get to the login screen where I type in my name/pass, and then an orange blank screen for a few moments, then it just kinda' turns off (sometimes with an out of range error) and goes back to the login screen.

I checked the xorg.conf, and everything is set to default, I've tried the reconfigure tip, but it just asks me about keyboard options and nothing about the monitor.

The monitor is an LCD with a native resolution of 1680x1050.

New install of 8.04 (never been able to log in).

---

### Post by cocopuffz on 2008-06-10
have you tried "gksudo displayconfig-gtk" then selecting your monitor from the list.. or go auto detect it. I've found that since  upgrading to hardy, this actually adds the right modes to your xorg.conf file. 

good luck

---

### Post by Sydius on 2008-06-10
I was able to fix it by logging into the Gnome failsafe and setting the resolution there (it was, oddly, already set to the correct resolution, but I went ahead and clicked "apply" anyway).  Now, I can log in normally, however I still get an annoying "out of range" message before the login prompt appears.  It goes away on its own, though, after a moment or two.

---

### Post by mgmiller on 2008-06-10
> however I still get an annoying "out of range" message before the login prompt appears. It goes away on its own, though, after a moment or two.

This is probably caused by sending too high a bit rate (color depth) while using the vesa driver.  The vesa driver is used until the login screen is displayed, at which point your regular driver is used.

```
sudo apt-get install startupmanager
```

Look in System > Administration > Startup Manager

In the middle of the "Boot Options" tab is a section called "Display"  set the 2 drop downs to the right of that to 640x480 and 8 bits.

Click close and let it finish its updating configuration thingy.

You will probably need to reboot (not just log off and on) to see the changes.

---

