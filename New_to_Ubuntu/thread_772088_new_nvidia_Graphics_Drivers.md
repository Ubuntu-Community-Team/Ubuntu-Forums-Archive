---
title: "new? nvidia Graphics Drivers"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by monofoso on 2008-04-28
Hello I have recently installed Ubuntu 8.04 (x64 if it matters) and am looking for drivers for a Geforce 9800GTX. 
Google seems to only give cryptic responses and I'm new to a lot of Linux stuff so the instructions or downloads that I used did not work (most likely through fault of my own). so I have started with a clean slate(new install). If anyone could help me with this is would be incredibly appreciated.[-o<

---

### Post by DezSP on 2008-04-28
System -> Administration -> Software sources

Tick "restricted" if it isn't already selected

System -> Administration -> Restricted Drivers Manager

Tick the nVidia drivers, they should be in the list there. You might need to run
```
sudo apt-get update
```
from the terminal first. Once that's done, hit Ctrl+Alt+Backspace and it'll reset X to use the new drivers. Have fun.

---

### Post by Tatty on 2008-04-28
Go to System->Administration->Hardware Drivers.  It should offer you some drivers in there.

---

### Post by kpkeerthi on 2008-04-28
You would need driver version [173.08]("http://www.nvidia.com/object/linux_display_ia32_173.08.html").  Follow [this]("https://help.ubuntu.com/community/NvidiaManual") instruction to install it manually.

---

### Post by alienexplorers on 2008-04-28
You could use Envy to load the new drivers.  Envy is availible in the repositories.

---

### Post by monofoso on 2008-04-28
first of all thank you all for helping 

> **DezSP said:**
> System -> Administration -> Software sources

Tick "restricted" if it isn't already selected

System -> Administration -> Restricted Drivers Manager

Tick the nVidia drivers, they should be in the list there. You might need to run
```
sudo apt-get update
```
from the terminal first. Once that's done, hit Ctrl+Alt+Backspace and it'll reset X to use the new drivers. Have fun.

The drivers weere not in the list so i ran sudo apt-get update and reset x, an nvidia logo popped up (most likely prom a previous failed attempt) however the drivers still do not appear in the list :S



> **kpkeerthi said:**
> You would need driver version [173.08]("http://www.nvidia.com/object/linux_display_ia32_173.08.html").  Follow [this]("https://help.ubuntu.com/community/NvidiaManual") instruction to install it manually.

Is this the reason the other attempt failed? And would envy do the same thing?

I will try following that and envy for now, thank you for all of your help.

EDIT: @kpkeerthi am i right in installing the 173.08 drivers labeled x64
[here]("http://www.nvidia.com/object/linux_display_amd64_173.08.html") instead of the ones linked to?

---

### Post by takuhii on 2008-04-28
Envy is the best solution to this, especially if you are a newbie. I use Envy, my linux skills are very limited, I have also found Envy to be the only useful tool when it comes to pre-configuring X server, everytime I have attempted a manual configuration, or used something that claims to be the ultimate NVIDIA configuration tool, it has screwed my X server over and left me re-using old xorg config files...

---

### Post by monofoso on 2008-04-28
in this tutorial im following i was told to remove conflicting software which includes nvidia-glx-new however whenenver i try to remove it with synaptic it throws an error:

An error occured

The following details are provided:

then

E: nvidia-glx-new: subprocess post-removal script returned error exit status 2

the other window shows this:
[IMG]http://img296.imageshack.us/img296/2055/screenshotchangesapplieur9.png[/IMG]

do i have to manually remove it, CAN i manually remove it am i doing somthing wrong again.. any help would be appreciated.

---

### Post by milia on 2008-04-28
> **alienexplorers said:**
> You could use Envy to load the new
 drivers.  Envy is availible in the repositories.

Envy won't install the latest beta drivers.

Using envyng-gtk (sudo apt-get install envyng-gtk) I managed to get
installed the 169.12 drivers. No later version is possible to install
it that way atm.

*Beta drivers:*

[http://www.nvidia.com/object/linux_display_ia32_173.08.html](http://www.nvidia.com/object/linux_display_ia32_173.08.html)

Latest *stable version* can be installed with envy, even if I don't really
trust scripts(sorry Alberto, don't take it personally i'm a bit a control freak).

Manually:

[http://www.nvidia.com/object/linux_display_ia32_169.12.html](http://www.nvidia.com/object/linux_display_ia32_169.12.html)

---

### Post by shayan_mihiran on 2008-04-28
If you want to install Nvidia drivers in Ubuntu Feisty and above versions is very easy to install.Ubuntu doesn’t include Nvidia drivers in a default installation for a number of reasons.

First you need to make sure you have nvidia disply card go to System—> Administration— > Restricted Drivers Manager

Now you should see similar to the following screen here you need to Check the box to enable the drivers

Enable Nvidia drivers popup here you need to select Enable Driver

Downloading the nvidia drivers in progress

Installing the software in progress

Nvidia Drivers installation completed.Now you need to reboot your machine to start using your nvidia drivers.

[http://www.ubuntugeek.com/how-to-install-nvidia-drivers-in-ubuntu-feisty-or-later-versions.html:lolflag:](http://www.ubuntugeek.com/how-to-install-nvidia-drivers-in-ubuntu-feisty-or-later-versions.html:lolflag:)

---

### Post by monofoso on 2008-04-30
Thanks you for all your help in the end i just used the nvidia installer with the x64 drivers. Thanks for pointing me in the right direction!
SOLVED!:grin:

---

### Post by milia on 2008-04-30
> **monofoso said:**
> Thanks you for all your help in the end i just used the nvidia installer with the x64 drivers. Thanks for pointing me in the right direction!
**[COLOR="#ff0000"]SOLVED[/COLOR]**!:grin:

Would you mind writing **[COLOR="Red"]it[/COLOR]** at the title of the thread ? :)

---

