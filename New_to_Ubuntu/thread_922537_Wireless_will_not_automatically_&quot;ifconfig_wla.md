---
title: "Wireless will not automatically &quot;ifconfig wlan0 up&quot;"
date: 2008-09-17
forum: New to Ubuntu
---

### Post by jbrown96 on 2008-09-17
I typically use the hardware switch to turn off wireless on my laptop to save battery. I recently switched back to KDE3 on Kubuntu 8.04.1. For some reason, when I turn the switch back on the wireless does not activate. I have to use ```
sudo ifconfig wlan0 up
``` to activate the interface. Everything is fine from there. Is there a config file that I can edit to automatically have the interface come up?

Thanks

---

### Post by zerhacke on 2008-09-17
There's a network manager for KDE that functions similiarly to Gnome's network manager.  It should be in your taskbar.

---

### Post by jbrown96 on 2008-09-17
Right. I am using KNetworkManager, but it still will not bring the interface up. If I click on it, it will only show a grayed out section for wired devices (since nothing in plugged in), but there isn't even a section for wireless. As soon as I run ```
sudo ifconfig wlan0 up
``` a section appears that says there are no networks available, but then populates the list in about 15 seconds (after it has scanned). 
Is KNetworkManager supposed to be bringing the interface up? If so, how would I force it to? There wasn't any settings like that in the GUI config.

---

