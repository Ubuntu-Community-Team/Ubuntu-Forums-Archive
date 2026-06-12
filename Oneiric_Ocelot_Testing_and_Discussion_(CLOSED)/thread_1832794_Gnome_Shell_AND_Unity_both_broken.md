---
title: "Gnome Shell AND Unity both broken"
date: 2011-08-25
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by sgage on 2011-08-25
After updates yesterday, both my Gnome Shell and Unity are broken, and in a similar fashion:

All I get for either one is the desktop, no top panel or launcher. Right-clicking on the desktop does, however, bring up the context menu, so I suppose nautilus is running.

Unity 2D is working fine (that's what I'm using). Any idea how to fix this?

---

### Post by Harry33 on 2011-08-25
> **sgage said:**
> After updates yesterday, both my Gnome Shell and Unity are broken, and in a similar fashion:

All I get for either one is the desktop, no top panel or launcher. Right-clicking on the desktop does, however, bring up the context menu, so I suppose nautilus is running.

Unity 2D is working fine (that's what I'm using). Any idea how to fix this?

So you did update clutter and mutter from Oneiric repos?
My 64-bit and 32-bit gnome-shell setups are running fine (without any additional PPAs).
Also the one with Ricotz Staging PPA works very well ATM.

---

### Post by sgage on 2011-08-25
> **Harry33 said:**
> So you did update clutter and mutter from Oneiric repos?
My 64-bit and 32-bit gnome-shell setups are running fine (without any additional PPAs).
Also the one with Ricotz Staging PPA works very well ATM.

Yes, completely updated. I tried staging as well - the exact same problem. It may just be time for...

...a fresh install!  :KS

---

### Post by rbrick49 on 2011-08-25
mine are working fine again after I nuked fglrx. sgage I had a few updates today all is ok by the way i have gone back to i386 system to see what happens

---

### Post by Syirrus on 2011-08-25
I have an Nvidia setup (boo hiss) and I was able to install 285.03 BETA drivers (up from the latest stable) and my Unity 3d is back.

Syirrus

---

### Post by sgage on 2011-08-25
> **Syirrus said:**
> I have an Nvidia setup (boo hiss) and I was able to install 285.03 BETA drivers (up from the latest stable) and my Unity 3d is back.

Syirrus

I have nvidia, too. How do I install the beta drivers?

---

### Post by Quackers on 2011-08-25
I have Nvidia too and have not had any problems updating recently. I also notice that the need to purge nvidia-current then re-install it when a new kernel arrives is gone now.

---

### Post by Peter09 on 2011-08-25
After recent upgrade I too have the same problem. (Intel)

---

### Post by budluva04 on 2011-08-25
I explained this in another post...

open a new tab, browse to /usr/bin and open up gnome-terminal....launch ccsm...and load the unity plugin by clicking the checkbox...

then in that terminal sudo killall nautilus and bam, your cookin' with emerald...

---

### Post by Peter09 on 2011-08-25
Thanks - that worked

---

### Post by Harry33 on 2011-08-25
> **sgage said:**
> I have nvidia, too. How do I install the beta drivers?

You can go and get the beta drivers from xorg-edgers.
Simple installation with dpkg works.

---

### Post by sgage on 2011-08-25
> **budluva04 said:**
> I explained this in another post...

open a new tab, browse to /usr/bin and open up gnome-terminal....launch ccsm...and load the unity plugin by clicking the checkbox...

then in that terminal sudo killall nautilus and bam, your cookin' with emerald...

Didn't work here. Sudo killall nautilus, and bam, nothing at all.

---

### Post by TakisX on 2011-08-26
How you open terminal if the launcher is not there ?

---

### Post by budluva04 on 2011-08-26
when you first login, you need to open a new tab with the nautilus window that already exists, navigate to /usr/bin and open gnome-terminal....then run ccsm and load the unity plugin THEN sudo killall nautilus

---

### Post by keithy on 2011-08-27
Great,

Thank you. Thats fixed unity.

Gnome3 is still broken. How do I fix that???

---

### Post by sgage on 2011-08-27
> **keithy said:**
> Great,

Thank you. Thats fixed unity.

Gnome3 is still broken. How do I fix that???

Yes, how do we fix that - mine is still broken too.

---

### Post by walt.smith1960 on 2011-08-27
My Gnome 3 shell and classic have continued to work.  I had no Unity 2D or Unity 3D.  Went to Synaptic and checked unity and unity 2D & installed.  Both seem to be working now.  This is on a fresh install 64 bit.

---

### Post by keithy on 2011-08-29
Anybody?

I want my gnome3 back and its still broken :(

---

### Post by sgage on 2011-08-29
> **keithy said:**
> Anybody?

I want my gnome3 back and its still broken :(

OK, I'm back after 24+ hours without power (thanks Irene!)

I have finally figured out the cause of my breakage, and after all this fuss, it's a bit embarrassing. I hope it solves your issue as well, keithy.

Turns out that there was some theme breakage somewhere along the line. After totally reinstalling, GS was working fine. I did the same theme tweakage I'd done before, and the exact same failure mode presented itself. Changed the theme back (in Unity), and GS came up fine. I haven't done the experimentation yet to figure out whether it's Adwaita or Metabox or whatall. I set everything to Radiance, and it's working fine (though I hate orange!) I will try tweaking, but at least I know how to get 'er going again.

---

### Post by keithy on 2011-08-30
Hi,

Glad you survived the 'storm'

gnome tweak tool had disappeared from my 11.10.

reinstalling it brought gnome back to life

cheers

---

