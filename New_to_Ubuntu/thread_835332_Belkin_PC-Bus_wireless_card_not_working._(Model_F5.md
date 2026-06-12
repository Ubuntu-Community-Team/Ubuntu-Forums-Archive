---
title: "Belkin PC-Bus wireless card not working. (Model F5D6020)"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by neversmileatacrocodile on 2008-06-20
I am having some trouble getting my wifi card to work. I have a Thinkpad T23 laptop with two card ports. My ethernet card is detected and works fine, but the Belkin has errors.

I installed the ndiswrapper thingy, and I installed the 8180 realtek driver from the website, and terminal says it detects the driver and the device, but when I open the GUI wrapper it says my card is unmounted, even though I put it into the slot.

I don't know whats wrong. Is there something still I have to configure?

---

### Post by phidia on 2008-06-20
How did you load the driver and ndiswrapper? After you install ndiswrapper you need to sudo modprobe ndiswrapper. Perhaps you already did that though.
There is a wireless guide [here]("http://ubuntuforums.org/showthread.php?t=684495") for getting a connection through commandline and that can be helpful if network manager is causing problems. I think that guide is also good for troubleshooting connections.
Hope that helps.

---

### Post by neversmileatacrocodile on 2008-06-25
> **phidia said:**
> How did you load the driver and ndiswrapper? After you install ndiswrapper you need to sudo modprobe ndiswrapper. Perhaps you already did that though.
There is a wireless guide [here]("http://ubuntuforums.org/showthread.php?t=684495") for getting a connection through commandline and that can be helpful if network manager is causing problems. I think that guide is also good for troubleshooting connections.
Hope that helps.

I manually installed it, sudo apt-get install couldn't find the package. :( I've reinstalled Ubuntu anyways, can we try this from scratch step by step?

---

### Post by neversmileatacrocodile on 2008-06-27
respond, respond. :( why isn't anybody helping me?

---

