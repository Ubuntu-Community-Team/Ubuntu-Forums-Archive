---
title: "Can not enable broadcom wireless on dell"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by dvdivx on 2008-04-29
Dell Vostro 1500 with B43 broadcom wireless on 32 bit 8.04. Driver is installed from DVD, it correctly identifies the card if I run the hardware wizard (which just crashes after I close it). The In use has a green check mark by it but if I check enable it prompts for a reboot. No matter how many times I reboot it remains unchecked. The Nvidia card did except the enabled check and appears to be working.

---

### Post by lwvmobile on 2008-04-29
Might I suggest using ndiswrapper, most people including myself, have much better results than with b43-fwcutter utility.

However, this method isn't without bugs in Hardy. Here is a guide if you would like to explore this avenue.

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff")

If this does or could work for you, you may have to add b43 to the /etc/modprobe.d/blacklist file and add

modprobe -r ssb
modprobe -r ndiswrapper
modprobe ndiswrapper

to the /etc/rc.local file

Good luck, you'll need it with a broadcom wireless card.

---

### Post by dvdivx on 2008-04-29
Is there a different offline installer I can download for it or is it all just through the terminal?

---

