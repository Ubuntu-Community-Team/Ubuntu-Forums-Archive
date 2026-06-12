---
title: "Max display brightness"
date: 2008-10-06
forum: New to Ubuntu
---

### Post by dontocsata on 2008-10-06
I have my power management set up so that on AC power, the screen does not dim, but on Battery, it does.

However, it only dims by about a 1/3 of the bar (when switching from AC to battery).  I would like to it be on full brightness when on AC, and minimum brightness on battery.

Additionally, if I manually lower the brightness, it seems to jump up to about 2/3 every so often.

Any ideas?

Plus if anyone has any power saving tips, I'm trying to maximize the battery life any way I can.

---

### Post by niteshifter on 2008-10-06
Hi,

Does your power management look like the attached screen caps? If so, welcome to the power management confusion club - and keep reading. If not, the below will be of no help.

The sliders for display brightness control are different:
AC Power: the slider sets how bright you wish the display to be.
Batt Power: the slider sets how much you *wish to dim* the display. 

If you want display brightness lower on battery move the slider more to the right.

> Additionally, if I manually lower the brightness, it seems to jump up to about 2/3 every so often.

Yep, thats the way it works, although not necessarily 2/3. It goes to where it's set to go depending upon which power source is in use.

---

### Post by dontocsata on 2008-10-06
Thank you for the quick reply.  My power management window does NOT look like that though.

Does this mean my Ubuntu is outdated? Or GNOME is?  On the Battery tab it simply reads: "Dim display brightness" with a checkbox.  I have it checked.  See attached.

---

### Post by niteshifter on 2008-10-06
Hi,

The screen caps I posted are from Ubuntu 7.10, GNOME 2.20.1

To find out what version of Ubuntu you have open a terminal and type:
```
lsb_release -d
```

To find out what version of GNOME on the menu bar at the top click System, then click About GNOME.

I think - and I might very well be wrong - the one you posted is from Ubuntu 6.10 (don't recall the GNOME version). But use the comamnds above to be sure.

---

### Post by dontocsata on 2008-10-06
Distributor ID:	Ubuntu
Description:	Ubuntu 8.04.1
Release:	8.04
Codename:	hardy

GNOME: 2.22.3
Distributor: Ubuntu
Build Date: 7/09/2008

My GNOME isn't the newest version (I believe the newest is 2.24); the version I have currently installed is that one included with 8.04 distro of Ubuntu.  I don't think there's a Ubuntu specific version of GNOME 2.4 yet...

I used Synaptic to reinstall gnome-power-manager.  No change though.

---

### Post by niteshifter on 2008-10-06
Hi,

A newer version that what I use so my help isn't going to be much, hopefully an 8.04 user will jump in here ...

What I do know: More-or-less there are two methods of power management for laptops with the GNOME desktop - laptop_mode (archaic) and GNOME's Power Manager app.

Most likely GNOME's Power Manager is in effect. You can check / control it via the Configuration Editor (gconf-editor). Invoke the editor (it may be in Applications / System Tools, or by typing:
```
gconf-editor
```
in a terminal. Under apps look for gnome-power-manager. Under that is the "backlight" category which may be useful for you.

---

### Post by dontocsata on 2008-10-06
Well, although I can't use the nice pretty GUI to do it, using gconf-editor, worked perfectly.  Thank you.

For others who read this:

Open terminal
Run:
```
gconf-editor
```
Go to: apps=>gnome-power-manager=>backlight
Edit "brightness_battery" to set the Brightness while on battery (1=lowest, 100=max)

---

