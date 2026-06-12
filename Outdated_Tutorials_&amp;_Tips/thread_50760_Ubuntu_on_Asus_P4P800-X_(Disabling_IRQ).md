---
title: "Ubuntu on Asus P4P800-X (Disabling IRQ)"
date: 2005-07-21
forum: Outdated Tutorials &amp; Tips
---

### Post by scorpio2002 on 2005-07-21
Hi there! 
I'd like to share my experience with the community. If you own an Asus P4P800-X motherboard you could have some problems while installing linux, like getting a loop message "Disabling IRQ" and not being able to complete the installation.

If that's the case, the only thing you can do to get it to work is installing a BIOS update available on the asus web-site.

If that shouldn't work, you can try giving some parametres to the kernel:

linux noirqdebug
linux irqfixup = 0
linux noprobe

If you're really unlucky and you can't get Ubuntu to install yet, try going into the BIOS setup and turn off the OS PandP.

Hope this helps :-)
Bye,
Donato

---

