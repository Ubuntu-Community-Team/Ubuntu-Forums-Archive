---
title: "Flickery screen savers?!"
date: 2008-06-18
forum: New to Ubuntu
---

### Post by Roger-Roger on 2008-06-18
Hi,

My Ubuntu screensavers are all flickery.

For example, the "Plasma" screen saver has 4-5 indistinct, but noticeable "lines" (regions?) across the screen that you can see as it's repainting.  Plasma is probably the worst.  "Lattice" shows only one such flicker line.  if you don't understand what I mean by "flicker" it like when you see a video screen recorded with a video camera, you can see the two refresh rates (screen and camera) get out of synch.  Maybe it's a type of interference pattern?

I'm using a Nvidia video card:
[INDENT]nVidia Corporation Geforce 9600 GT 512mb (rev a1)[/INDENT]

With the nvidia (beta) proprietry driver at 1920x1200, compiz turned up to 11.

I have "Sync to VBlank" and "Allow Flipping" checked in the Nvidia control panel.  I really did expect this to fix it, but it didn't change it at all.

In this office environment, all operating systems are judged on the strength of their screen-savers!  But some of the ubuntu ones look great, but their animation is all flickery.  Can I force the screen saver to only paint the screen during the vertical retrace?  :confused:

thanks
R-R

---

### Post by sdennie on 2008-06-18
Setting vsync in nvidia-settings probably makes the problem worse.  I would disable that and then:

```

sudo apt-get install compizconfig-settings-manager

```

Then go to System->Preferences->Advanced Desktop Effects.  Go to General Options then Display Settings.  Uncheck, "Detect Refresh Rate", manually set the slider to the refresh rate of your monitor (if it's an LCD, it's probably 60) and check sync to vblank.

If that doesn't work then go to the "General" tab of that same area and uncheck, "Unredirected Fullscreen Windows".

If none of that works, reboot and see if it does.  Once you set any options in nvidia-settings and properly loaded them, all bets are off until you reboot.

---

