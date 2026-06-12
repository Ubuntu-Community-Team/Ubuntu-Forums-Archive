---
title: "New Install Issues"
date: 2012-06-20
forum: New to Ubuntu
---

### Post by mcarbaja on 2012-06-20
I just installed latest version of ubuntu on my windows 7 and after a successful install I rebooted and have had a black screen for 15 minutes! I can see pop up window when I play with the keyboard I've even logged in but I don't have a task bar. Any help?

---

### Post by Kakers on 2012-06-20
Hello mcarbaja,

To help others wishing to provide assistance could you give a little more information? Such as is this the Wubi installer? If not where was it installed an how?

---

### Post by mcarbaja on 2012-06-20
> **Kakers said:**
> Hello mcarbaja,

To help others wishing to provide assistance could you give a little more information? Such as is this the Wubi installer? If not where was it installed an how?
Sure first off it's an E-Machines ET-1831. I went into the ubuntu website,downloaded the 32 bit version, since it was an ISO image file I burned it to a DVD when it was finished I rebooted hit F12, went into the boot menu and selected DVD drive it rebooted fine,went through all of the installation then it said it needed to reboot but when it came back on it remained black (screen) till now.

---

### Post by Kakers on 2012-06-21
Do you have 2 hard drives or different partitions? If you have two hard drives with Windows on one and Linux on the other, It might be the grub (boot loader) has been installed on the other hard drive, you could try going into your bios (setup) and changing the boot order for the hard drives.

---

