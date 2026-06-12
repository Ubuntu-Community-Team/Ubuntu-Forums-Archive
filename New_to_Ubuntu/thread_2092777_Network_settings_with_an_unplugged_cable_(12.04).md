---
title: "Network settings with an unplugged cable (12.04)"
date: 2012-12-08
forum: New to Ubuntu
---

### Post by johnny bee on 2012-12-08
Hi all, I use Ubuntu on Live CD and I've noticed that I cannot configure the network settings when the cable is unplugged on 12.04. That was not the case on 10.x, I don't recall 11.x. With 10.04 for example, I could see the network settings, switch from dhcp to manual and so on, without the need to plug in the ethernet cable. This seems not possible on 12.04. Network window says 'Cable unplugged' and the Options button is grayed out. Can't I see or configure network settings without a cable plugged in to the newtork socket? Thanks

---

### Post by Bucky Ball on 2012-12-08
Wouldn't the settings be lost on the next reboot anyhow as you are running 'Try Ubuntu' from a CD??? Where would the settings be stored, exactly? A LiveCD is locked and no more data can be added (so installing drivers, etc, would be impossible).

---

### Post by johnny bee on 2012-12-08
Bucky Ball, thanks for the reply. The settings wouldn't be stored anywhere, and they would be lost indeed at the next reboot. I'm fine with that, thanks. All I wanted to know was if something has changed regarding network configuration policy from one version to another, or was it my fault not being able to open the network setings window.

---

### Post by johnny bee on 2012-12-14
First and the final bump. Regardless of if that makes sense or not, or where would I store the settings, or why should I need such a thing, on Ubuntu version 12.04:

Can I see and configure the network settings without conencting it to a network?

Thanks

---

### Post by GordThompson on 2012-12-14
> **Bucky Ball said:**
> Wouldn't the settings be lost on the next reboot anyhow as you are running 'Try Ubuntu' from a CD??? Where would the settings be stored, exactly? A LiveCD is locked and no more data can be added (so installing drivers, etc, would be impossible).
Well, I don't know... a Live CD wouldn't be very useful if you couldn't do *some* configuration so the system would actually work while you're testing it. For example, if I boot my Dell Inspiron 1720 from my bootable USB copy of 12.04 then I have to open "Additional Drivers" and activate the Broadcom wireless adapter driver so I can connect to the Internet. That makes some changes to the configuration, but they are only in effect for that session (i.e., they are not persistent).

---

### Post by GordThompson on 2012-12-14
> **johnny bee said:**
> First and the final bump. Regardless of if that makes sense or not, or where would I store the settings, or why should I need such a thing, on Ubuntu version 12.04:

Can I see and configure the network settings without conencting it to a network?

Thanks
It seems to depend on the path you take. I'm running from a bootable USB of 12.04, and if I choose

System Settings > Network > Wired

then the status says "Cable unplugged" and the "Options..." button is disabled. 

However, if I click the network icon on the right side of the desktop status bar and choose "Edit Connections..." then I *can* edit the settings of "Wired connection 1" even though it is not active.

---

### Post by johnny bee on 2012-12-14
Thanks a lot GordThompson. I tried the first path first, and trying to open the network settings from the icon wouldn't cross my mind at all once the first path didn't work. I'm marking this solved.

---

### Post by GordThompson on 2012-12-14
> **johnny bee said:**
> Thanks a lot GordThompson. I tried the first path first, and trying to open the network settings from the icon wouldn't cross my mind at all once the first path didn't work. I'm marking this solved.
Good to hear! Thanks for the update.

---

