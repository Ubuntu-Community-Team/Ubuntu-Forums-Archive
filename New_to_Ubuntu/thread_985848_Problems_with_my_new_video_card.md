---
title: "Problems with my new video card"
date: 2008-11-18
forum: New to Ubuntu
---

### Post by h4ppydaze on 2008-11-18
I got my computer running fine with my integrated card with a bit of tinkering... disabling compiz. I installed nvidia x but it says "You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. " when I open nvidia X. I updated my xconfig to show Driver   "nvidia" and rebooted to change my peripheral settings in BIOS from integrated to PCI. Now things were going smoothly, with the signal going through my new card, but when Ubuntu is loading, it stops at about three bars and will not continue. I left it for an hour or so with no progress. Please help. I had to revert to the integrated card and my integrated card is boo boo. It won't even let me run compiz because of compatibility issues. I would really like to get this running. It doesn't boot in recovery mode either with the new card.

---

### Post by Elfy on 2008-11-18
Run recovery mode and when it gets to the menu use the xfix option then let it boot with that and shutdown. Install your new gpu and reboot - it will start with the basic driver.

Run hardware drivers to let it install the driver for your card when it prompts to restart and it will then use the nvidia driver.

---

### Post by h4ppydaze on 2008-11-18
thanks I will be trying this tonight.

---

