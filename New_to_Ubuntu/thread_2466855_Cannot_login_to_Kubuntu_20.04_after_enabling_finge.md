---
title: "Cannot login to Kubuntu 20.04 after enabling fingerprint reader on thinkpad"
date: 2021-09-08
forum: New to Ubuntu
---

### Post by CAX on 2021-09-08
I install fingerprint reader with following commands:

sudo apt install -y fprintd libpam-fprintd
sudo pam-auth-update

then enrolled right index finger

Not when coming to the login screen I only have the option to type my password. If I do, nothing happens it seems like it is going to login (login screen disappear) but it just "freezes" (not sure what happens, just unresponsive). to swipe the index finger in that circumstance does not change anything. 

If I give no password, it freezes temporarily but then return to the login screen again (which never happens when you type correct password).

I can definitely live without fingerprint reader as long as I can get into my computer. 

Not sure where to start.  

Thinkpad T14 dualboot with windows 10 if that matters.

EDIT: just booted into recovery mode, ran the second command again and disabled the finger print login, rebooted and that solved the problem.

Now just figure out how to uninstall printd libpam-fprintd

---

### Post by monkeybrain20122 on 2021-09-08
Maybe you scratched your finger. But then I never like the idea of biometric based 'security'.

---

### Post by waffleusrex on 2021-10-17
I had  the same issue. After some digging, I found the answer here: [https://www.kubuntuforums.net/forum/currently-supported-releases/kubuntu-20-04-focal-fossa-lts/hardware-support/71109-fingerprint](https://www.kubuntuforums.net/forum/currently-supported-releases/kubuntu-20-04-focal-fossa-lts/hardware-support/71109-fingerprint)
You need to install and replace SDDM with Lightdm as the default desktop manager. The first time through, I had to change it from Plasma (Wayland) to Plasma (X11) as well and then reboot to get it working.

---

