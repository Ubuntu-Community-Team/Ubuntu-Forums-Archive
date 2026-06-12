---
title: "Google earth on ubuntu?"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by bob16 on 2008-06-26
when i was using gusty, i installed google earth using automatix
now, i dont think theres automatix on hardy

is there any other way to install google earth?
i tried the one from the site and i also downloaded it from synaptics buy couldnt find it

---

### Post by whitethorn on 2008-06-26
A quick google search and 

1)    [http://ubuntuforums.org/showthread.php?t=744783](http://ubuntuforums.org/showthread.php?t=744783)

2)    [http://ubuntuforums.org/showthread.php?t=779664](http://ubuntuforums.org/showthread.php?t=779664)

---

### Post by jrusso2 on 2008-06-26
I believe its in the mediabuntu repository if you add that you can install it with apt or synaptic.

Also, you can always download it from Google and install it.

---

### Post by drs305 on 2008-06-26
This was a post from today:
[http://ubuntuforums.org/showthread.php?t=841352#2]("http://ubuntuforums.org/showthread.php?t=841352#2")

Added: this link provides instructions to install from synaptic after repositories are enabled. The way to add the repositories to sources.list changed recently. These are the correct procedures.

---

### Post by ajmorris on 2008-06-26
you could go here:
[http://earth.google.com/download-earth.html](http://earth.google.com/download-earth.html)

and install it manually
But also, the mediubuntu repositories have it in them, just add this to /etc/apt/sources.list for the mediubuntu hardy repos:

deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) hardy free non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) hardy free non-free

AJ

---

