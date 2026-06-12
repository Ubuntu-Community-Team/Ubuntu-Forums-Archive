---
title: "intel 915GM drivers"
date: 2008-09-10
forum: New to Ubuntu
---

### Post by guesswho on 2008-09-10
hi all. i've just installed ubuntu on my laptop which has an intel 915GM graphics card....
in searching around i noticed that people have been having a lot of trouble getting it to work with ubuntu...wondering if someone can help me out.

i have the drivers installed (boxes are green when i open synaptic package manager and search for i915).
however, system -> administration -> hardware drivers says no propietary drivers are in use...which means my comp is not using the drivers.

compiz and other things are running very choppily...i would greatly appreciate any help. thanks.

---

### Post by Titan8990 on 2008-09-10
Intel doesn't make proprietary Linux drivers for their integrated chipsets.

I would consider Compiz out of the question.

---

### Post by Tom--d on 2008-09-10
> **Titan8990 said:**
> Intel doesn't make proprietary Linux drivers for their integrated chipsets.

I would consider Compiz out of the question.

What?!

Intel make OPEN SOURCE drivers for Linux with 3D support. I have the 965 chip set using the i915 driver. Works Perfectly with Compiz and 3D games!

This means your graphics card will work out of the box!

---

### Post by guesswho on 2008-09-10
my card isn't working out of the box though...that's the prob...the drivers installed automatically, but the system isn't using those drivers...it's still using like the basic ones or whatever

---

### Post by SunnyRabbiera on 2008-09-10
Strange, my intel card is the same as yours and works perfectly.
what version of ubuntu are you using and what are your full computer specs?

---

### Post by Crafty Kisses on 2008-09-10
I'd like to see the results of this command:
```
glxinfo
```

---

### Post by SunnyRabbiera on 2008-09-10
It might even be a monitor issue, I know I had to tweak my monitor settings once to get my system to work properly under gutsy...
But that was gusty, didnt have that issue under hardy.

---

