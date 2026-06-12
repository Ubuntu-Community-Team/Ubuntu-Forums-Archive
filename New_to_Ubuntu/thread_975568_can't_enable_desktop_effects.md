---
title: "can't enable desktop effects"
date: 2008-11-08
forum: New to Ubuntu
---

### Post by cartisdm on 2008-11-08
I used to use Compiz effects before back when I ran Gutsy so I decided I'd go back to them again (now I'm using Hardy).  I can't seem to get the desktop effects to work though.

I ran:
```
$ sudo apt-get install compizconfig-settings-manager
```

and everything looked like it install but when I try to enable them in the Appearance tab I get the following error (see screenshot)

---

### Post by phidia on 2008-11-08
In the System > Admin > Hardware drivers menu item is your video card enabled?

---

### Post by alienexplorers on 2008-11-08
I have the same problem as you.  If I find an answer I will pass it on.

---

### Post by hictio on 2008-11-08
> **phidia said:**
> In the System > Admin > Hardware drivers menu item is your video card enabled?

++
On my Intrepid install, once the NVIDIA drivers were enabled, donwloaded and installed, everything went golden with the Desktop Effects.
cartisdm, what is that theme you are running? Care to post a link to it?
TIA.

---

### Post by cartisdm on 2008-11-08
Enabling my video card did the trick, strange that I didn't have it enabled already.  I do so many re-installs that I must have forgotten to do it.

hictio, I tried finding the link to where I downloaded my theme but I couldn't find it.  I used [http://www.gnome-look.org/](http://www.gnome-look.org/) though so search around and you'll probably find it

---

### Post by B34ST1Y on 2008-11-08
please make sure to mark this thread as [RESOLVED]

---

### Post by hictio on 2008-11-08
> **cartisdm said:**
> Enabling my video card did the trick, strange that I didn't have it enabled already.  I do so many re-installs that I must have forgotten to do it.


What I find strange, is that you were able to install Compiz Manager, without having the Desktop Effects enabled, at lest, to the medium level.

> **cartisdm said:**
> 
hictio, I tried finding the link to where I downloaded my theme but I couldn't find it.  I used [http://www.gnome-look.org/](http://www.gnome-look.org/) though so search around and you'll probably find it

Can you at least post the name of it? :p ;) :D

---

### Post by alienexplorers on 2008-11-08
Use hardware driver to unload your drivers.  Reboot.  Use hardware driver to reload your driver.  Reboot.  Try to enable desktop effects.  If it fails once then try again.  It took me two times to get mine working.

---

