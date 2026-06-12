---
title: "edit compiz settings"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by aBitLater on 2008-07-08
How do I edit compiz settings?  I get an intermittend flash on my screen (ubuntu 8.04 / nvidia non-free driver) when I run Vuze.  I'm thinking there is a related problem with a compiz setting, but can't find the "settings app" that I used in 7.10.

I used to have a gui for setting compiz.. something other than the system / preferences / appearance / visual effects settings.

---

### Post by nkri on 2008-07-08
> **aBitLater said:**
> I used to have a gui for setting compiz.. something other than the system / preferences / appearance / visual effects settings.

The GUI was probably Compiz Configuration Settings Manager:
```
sudo apt-get install compizconfig-settings-manager
```

Good luck!
-nkri

---

### Post by LowSky on 2008-07-08
What Happens when you turn off Compiz and use just Metacity?
Does the video still flicker?

Also in Synaptic there is an option for a Compiz fusion icon for the desktop. Very helpful for switching between Compiz and Metacity

---

### Post by aBitLater on 2008-07-08
> **LowSky said:**
> What Happens when you turn off Compiz and use just Metacity?
Does the video still flicker?

Also in Synaptic there is an option for a Compiz fusion icon for the desktop. Very helpful for switching between Compiz and Metacity

I'll look for the icon, but what is metacity?

---

### Post by sayakb on 2008-07-08
Metacity is a window manager that doesnot use a composite desktop like compiz and has very lite graphical effects that work on any onboard VGA as well. Goto System->Preferences->Screen Resolution and select a different Refresh Rate and see if the flickering stops.

---

### Post by LowSky on 2008-07-08
hope this helps

[http://en.wikipedia.org/wiki/Metacity](http://en.wikipedia.org/wiki/Metacity)

---

### Post by aBitLater on 2008-07-08
> **LinuxIsInnovation said:**
> Metacity is a window manager that doesnot use a composite desktop like compiz and has very lite graphical effects that work on any onboard VGA as well. Goto System->Preferences->Screen Resolution and select a different Refresh Rate and see if the flickering stops.


Refresh rate is at 50 Hz, and that is the only option.  The 'window' on the applet indicates an unknown monitor. I'm using a laptop - HP Pavilion dv8000

---

