---
title: "Want to install Beryl...how?"
date: 2008-06-19
forum: New to Ubuntu
---

### Post by Sam324 on 2008-06-19
Hi.  I want to install Beryl on my new 8.04 installation.  The first step, according to [http://web.archive.org/web/20070717175102/wiki.beryl-project.org/wiki/Support_for_nVidia_cards](http://web.archive.org/web/20070717175102/wiki.beryl-project.org/wiki/Support_for_nVidia_cards) is to uninstall the old drivers.  I couldn't find
[LIST]
[*]nvidia-glx
[*]nvidia-settings
[/LIST]
in the package manager, but I successfully uninstalled nvidia-kernel-common.  It didn't seem to change anything.  I still have graphics.  Anyway, I see that upon installation my Ubuntu seems to include Compiz-Fusion.  Would it be better to install that instead?  I guess what I really want is to update my NVidia drivers.  When I tried installing them, it said I had an X Server running.  What's an X Server?:oops:  How do I install the driver(s) and then Beryl/Compiz Fusion?

---

### Post by ad_267 on 2008-06-19
Woah bad idea. Don't know exactly what that package does but I recommend reinstalling it. That sounds like a pretty old tutorial, Beryl isn't around any more. It's been merged with compiz to make compiz-fusion.

Read this: [http://ubuntuforums.org/showthread.php?t=809695](http://ubuntuforums.org/showthread.php?t=809695)

To install the drivers go to System - Administration - Hardware Drivers and tick next to the Nvidia drivers.

---

### Post by Xerp on 2008-06-19
Any reason you want to use such old stuff? You're right - 8.04 comes with Compiz-fusion built-in, you simply enable it :)

Here is an old link for 7.10:

[http://www.thelinuxnewbie.com/2007/10/21/running-desktop-visual-effects-on-gutsy-gibbon-ubuntu-710/](http://www.thelinuxnewbie.com/2007/10/21/running-desktop-visual-effects-on-gutsy-gibbon-ubuntu-710/)

You don't need the setting manager in 8.04 either :)

Installing Nvidia drivers is also simple - in fact, you should have been prompted to do so when you booted into Ubuntu for the first time. If not, go to the System > Administration menu, click on Hardware Drivers, and then enable the NVIDIA accelerated graphics driver checkbox in the Device Driver tree.

I've also found Envy to be useful - you can install it straight from Synaptic.

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by netztier on 2008-06-19
> **Sam324 said:**
> Hi.  I want to install Beryl on my new 8.04 installation.

Make sure your installation has the restricted driver for your graphics card installed and that it's active. See **System** -> **Administration** -> **Hardware Drivers**.

If you're after the desktop effects, just navigate to **System** -> **Preferences** -> **Appearance** and on the tab "Visual Effects", select the option you like. No need for separately installing Beryl or compiling things.

regards

Marc

---

### Post by Sam324 on 2008-06-19
Well, since I uninstalled the Nvidia driver I see nothing in Restricted Drivers.  There's no graphics change, though.  And it won't let me use levels two and three of Desktop Effects.

---

### Post by shifty_powers on 2008-06-19
try using envy

```
sudo apt-get install envyng-gtk
```

then go applications>system tools>envyng

---

### Post by ad_267 on 2008-06-19
First try reinstalling nvidia-kernel-common and installing the drivers the normal way. You can use "sudo apt-get install nvidia-kernel-common" or do it through synaptic.

---

### Post by steveneddy on 2008-06-19
> 
**[COLOR="Blue"]Want to install Beryl...how?[/COLOR]**


**Want to install Beryl...[COLOR="Red"]why[/COLOR]?**

Compiz-Fusion is better. Way better!

Trust me, I was around when Beryl was here, and I used it, and CF is better, and it is default installed in 8.04 already.

---

### Post by Sam324 on 2008-06-20
TY!  I updated the Nvidia drivers and Extra effects are working perfectly!  Is this how I enable Compiz Fusion?
Is it enabled by System->Prefs->Appearance->Visual Effects->Extra?
It doesn't seem the same as the fiery, jewely Beryl I watched on YouTube.  Plus, how do I get the minimization "stretch" effect and the 3D desktop cube?

---

### Post by Tom--d on 2008-06-20
> **Sam324 said:**
> TY!  I updated the Nvidia drivers and Extra effects are working perfectly!  Is this how I enable Compiz Fusion?
Is it enabled by System->Prefs->Appearance->Visual Effects->Extra?
It doesn't seem the same as the fiery, jewely Beryl I watched on YouTube.  Plus, how do I get the minimization "stretch" effect and the 3D desktop cube?

Install ccsm

```
sudo apt-get install compizconfig-settings-manager
```

then go to System > Pref > Advanced desktop effects thingy.

---

### Post by Sam324 on 2008-06-20
OK, I have everything but the minimize "stretch" effect and the fire effect when a window is closed.  How do I get these?  I tried enabling "Minimize effect" and "Paint fire on the screen" but to no avail.  What I want (the fire) is like in this video:  [http://youtube.com/watch?v=G3p8IBNNd88](http://youtube.com/watch?v=G3p8IBNNd88)

---

### Post by bubba_169 on 2008-06-20
In 'Advanced desktop effects settings' enable the 'animations' plugin. In this if you click the 'close animation' tab, you will see a list showing what effects are applied for what type of windows. In the appropriate one (type=normal), double click the entry, and choose 'burn' in the close effect list that pops up.

The minimize squash you talk about sounds to me like the effect named 'magic lamp'

---

### Post by Sam324 on 2008-06-20
Thanks!  I'm now happily using CF. :)

---

