---
title: "Visual Effects Problem"
date: 2008-06-29
forum: New to Ubuntu
---

### Post by Johnathannn on 2008-06-29
Whenever I go to my Appearance Preferences, and click on Visual Effects, I change it from None to Normal, but it doesn't work and it gives me an error message that says "Desktop Effects Could Not Be Enabled"... Anyway to fix this?

---

### Post by Matthewslf on 2008-06-29
Make sure you have a glx package installed (search in synaptic for glx). I cannot tell you which one to use since I don't know what your graphics card is.

---

### Post by RomeReactor on 2008-06-29
Hi. If you have an ATI or nVidia card, go to 'System->Administration->Hardware Drivers' and enable your card's driver there.

---

### Post by Rocket2DMn on 2008-06-30
In terminal, run
```
lspci | grep VGA
```
If you are using an ATI card older than the Radeon 9500, you need to follow this thread: [http://ubuntuforums.org/showthread.php?t=764633](http://ubuntuforums.org/showthread.php?t=764633)

Otherwise, see here: [http://ubuntuforums.org/showthread.php?t=799070](http://ubuntuforums.org/showthread.php?t=799070)

---

### Post by Johnathannn on 2008-07-03
Hey, sorry for the late reply... Typed that in the terminal, and got this...

01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter

---

### Post by ledzeppelin on 2008-07-03
it would be smarter to install compiz fuzion because that way, you can customize which effects you want, and which button installs them, not just have every effect and not knowing how to use them.

---

### Post by RomeReactor on 2008-07-03
It's very unlikely that card will be able to run Compiz. See this [semi-related thread]("http://ubuntuforums.org/showthread.php?t=835617") for more.

---

### Post by Rocket2DMn on 2008-07-03
Agreed, your card does not support Compiz Fusion.  Sorry, buddy.

---

