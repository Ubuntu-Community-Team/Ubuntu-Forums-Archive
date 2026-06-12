---
title: "About to install Lubuntu"
date: 2019-05-05
forum: New to Ubuntu
---

### Post by Cognition on 2019-05-05
Hi, I'm about to install Kubuntu on my HP Stream 14-cb1xx. It has an Intel Celeron N4000 (CPU @ 1.10 GHz) and the wireless is handled by a Realtek RTL8822BE. From what I seen, this guy ([https://ubuntuforums.org/showthread.php?t=2410264](https://ubuntuforums.org/showthread.php?t=2410264)) got help getting his wireless set up with his HP Stream. He got the same deb files that apparently I will need. I've gone ahead and gotten those, and plan to transfer them from my Galaxy J7. Is there anything I should be aware of before I go ahead with the install?

---

### Post by SeijiSensei on 2019-05-05
I'd first try using System Settings > Driver Manager to see if the system can determine the driver(s) you need.  Connect the computer with an Ethernet cable to your router so the system can look online for the drivers.  It's always better to do things within the Ubuntu system first, and only resort to third-party files when Ubuntu fails to find what you need.

You can use the "Try Kubuntu" option when you boot the installation image and see if Driver Manager finds the files.

---

### Post by Cognition on 2019-05-05
I'll be using UNetbootin unfortunately...

Edit: I meant Lubuntu, not Kubuntu. [CENTER][COLOR=#000000]#-o[/COLOR][/CENTER]

---

### Post by mastablasta on 2019-05-08
> **Cognition said:**
> I've gone ahead and gotten those, and plan to transfer them from my Galaxy J7. Is there anything I should be aware of before I go ahead with the install?

Galaxy J7 might not be recognised by the OS. i have J6 and have it locked. i can't get to it's files even if i unlock it. so check first if you can actually access the file on mobile phone in a live session. or use SD card to do the transfer.

---

### Post by oldrocker99 on 2019-05-09
> **Cognition said:**
> I'll be using UNetbootin unfortunately...

Etcher is a big improvement over unetbootin. Here's how to install on various distros:

[https://www.fossmint.com/etcher-usb-sd-card-bootable-image-creator-for-linux/](https://www.fossmint.com/etcher-usb-sd-card-bootable-image-creator-for-linux/)

Debian/Ubuntu is the first. Copy and paste each line in a terminal, and it'll be installed.

---

### Post by Rubi1200 on 2019-05-09
Another option to consider (from a Windows install) is Rufus:
[https://rufus.ie/](https://rufus.ie/)

---

