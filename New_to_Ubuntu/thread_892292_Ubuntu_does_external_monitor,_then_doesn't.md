---
title: "Ubuntu does external monitor, then doesn't"
date: 2008-08-17
forum: New to Ubuntu
---

### Post by pteri498 on 2008-08-17
I'm trying to boot the live cd for 8.04 (Hardy). I have a laptop with an ATI Radeon IGP 345M chip in it. I also have a 19-inch external monitor that I'd like to use with my laptop.

When I boot the Hardy Live CD up, everything shows up well on my external monitor, however when Gnome starts up, it quits using the external monitor.

Basically, it works at first and then quits.

Any idea why this might be happening?

---

### Post by jualin on 2008-08-17
External monitor is not configured by default in Ubuntu you might need to install propietary video card drivers for this.

---

### Post by jualin on 2008-08-17
Try using Envy to automatically install the drivers for you. Just install the package Envy-ng using Synaptic Package Manager and then open Envy-ng located under System tools and follow the instructions.

---

### Post by jualin on 2008-08-17
If Envy fails to install the driver then try following the instructions on [this thread]("http://ubuntuforums.org/showthread.php?t=579596&page=5"). Hope this helps!

---

### Post by pteri498 on 2008-08-17
Envy uses the wrong drivers, and the display is wrong (doesn't fill the screen), however both screens work (go figure, only when the drivers are broken).

None of the xorg configurations on that post seem to do it, but it makes me think that I should be adding a monitor to my xorg.conf, but I'm not sure how to do it correctly...

---

### Post by overdrank on 2008-08-17
> **pteri498 said:**
> Envy uses the wrong drivers, and the display is wrong (doesn't fill the screen), however both screens work (go figure, only when the drivers are broken).

None of the xorg configurations on that post seem to do it, but it makes me think that I should be adding a monitor to my xorg.conf, but I'm not sure how to do it correctly...

Hi and if you have installed Ubuntu then you can try and use the command using the alt, F2 keys and enter ```
gksu displayconfig-gtk
``` to detect and setup up the external monitor. Please correct me if I am wrong but that is the model ati 7000 series graphics?

---

### Post by pteri498 on 2008-08-17
> **overdrank said:**
> Please correct me if I am wrong but that is the model ati 7000 series graphics?

I think this is not a 7000 series... In all the studying for this driver I've done, I've really had no reason to believe that it is. Nothing tells me that.

Following [this guy's experiences]("http://kagashe.blogspot.com/2008/07/my-struggle-with-ubuntu-hardy-heron.html") I decided to download the updated video drivers for Debian Sid (Unstable), and *that* managed to take care of my external monitor.

However, the screen is leaking off to the right side a bit, which is not critical but annoying.
During my brief play with openSUSE, I noticed that it had a very nice utility that allowed me to push my screen in exactly as much as I needed it do.

Is there a screen cropping-type utility like that out there for Ubuntu?

---

