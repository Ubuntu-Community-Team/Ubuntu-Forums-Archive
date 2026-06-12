---
title: "[SOLVED] compiz alt+scroll transparency not working"
date: 2008-11-16
forum: New to Ubuntu
---

### Post by whitethorn on 2008-11-16
The title pretty much says it all.  I know compiz is working because I have the cube activated and it works fine.  For some reason since I've installed Ibex the alt + scroll no longer sets a window transparent. Is there a way to turn it on and off?  I looked through some of the compiz stuff but I wasn't able to find anything.

---

### Post by SamNSane on 2008-11-17
If you don't already have ccsm (compizconfig-settings-manager) installed, open Synaptic and search for it (using exactly the wording / lettering I used within the first set of parentheses). Install it.

They've change the default compiz settings for Intrepid so that this function isn't set up by default. The function names are a little different, too. I'm not in 8.10 right now, but what you're looking for is in the Compiz Config Settings Manager's "Accessibility" section.

---

### Post by whitethorn on 2008-11-17
I had a look through the accessibility section and I wasn't able to find it.  Darn

---

### Post by SamNSane on 2008-11-17
Trust me, it's there. I found it confusing, too. It's named (maybe) almost exactly the opposite of what you'd expect. Maybe "opacity" or something like that.

---

### Post by whitethorn on 2008-11-17
Wow you're right.  It's called Opacity, Brightness and Saturation I just had to activate it and it worked.  Thanx

---

### Post by SamNSane on 2008-11-17
Terrific.

It is weird that they call it that, isn't it? It's kinda bass-ackwards.

;)

Have a good one!

---

### Post by glavspirt on 2008-12-15
Hello! I can't enable this option :confused: 8.10

---

### Post by SamNSane on 2008-12-15
> **glavspirt said:**
> Hello! I can't enable this option :confused: 8.10

Can you tell us more about your system? What video subsystem and what video driver is it using? Can we assume that you're using ccsm (compizconfig-settings-manager)?

It might also be good to tell us whether or not this is a upgrade installation of the operating system. Some of those seem to run into the odd problem with desktop effects.

---

### Post by glavspirt on 2008-12-15
Thanks! But I've solved the problem already. There was not checked something like 'automatically sort the modules' in settings.

---

