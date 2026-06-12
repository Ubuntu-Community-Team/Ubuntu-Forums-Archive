---
title: "My Desktop hangs !!"
date: 2012-08-02
forum: New to Ubuntu
---

### Post by Muaaz17 on 2012-08-02
> [B]I have installed this AMD ATI Graphic drivers for my laptop hp pavillion g6 ... Everything is working fine, but after short duration let just say 30mins, my desktop icon hangs & i'm sure it's beacause of THis Graphic Software ....  I have unistalled this software & then reinstalled it too, but the problem never went. :(

Can you help me with this :?:[/B]

---

### Post by 2F4U on 2012-08-02
Does that mean you removed the ATI driver but the problem did not go away? How can you say that the problems are due to the graphics driver? Maybe some other programs are running in the background.
You should start by looking into the system log if there are any problems reported. Is there a pattern behind, e.g. always happens if particular applications are running?

---

### Post by Gone fishing on 2012-08-02
Log File viewer, would be a good starting place. You wll be able to check all logs and find what crashing.

---

### Post by Muaaz17 on 2012-08-02
when i unistalled AMD ATI Catalyst driver ... everything was working fine, but then i have to install it again so that i can switch to other graphic when my charger is not connected !! then the problem appears again :/

How to check the log files ???

---

### Post by Muaaz17 on 2012-08-02
> **2F4U said:**
> Does that mean you removed the ATI driver but the problem did not go away? How can you say that the problems are due to the graphics driver? Maybe some other programs are running in the background.
You should start by looking into the system log if there are any problems reported. Is there a pattern behind, e.g. always happens if particular applications are running?

when i unistalled AMD ATI Catalyst driver ... everything was working fine, but then i have to install it again so that i can switch to other graphic when my charger is not connected !! then the problem appears again :/

How to check the log files ???

---

### Post by dodo3773 on 2012-08-02
Have you tried this?:

[http://virtual-drive.in/2012/05/20/ubuntu-12-04-text-boot/](http://virtual-drive.in/2012/05/20/ubuntu-12-04-text-boot/)

---

### Post by Muaaz17 on 2012-08-02
> **dodo3773 said:**
> Have you tried this?:

[http://virtual-drive.in/2012/05/20/ubuntu-12-04-text-boot/](http://virtual-drive.in/2012/05/20/ubuntu-12-04-text-boot/)

idk anything about this text boot ... what does it do actually ??

---

### Post by dodo3773 on 2012-08-02
> **Muaaz17 said:**
> idk anything about this text boot ... what does it do actually ??

It will boot your machine in text boot. Pretty self explanatory. Instead of a graphical image you will see text while your os is booting up. If the hangup is a graphical one then maybe not booting directly into a graphical splash screen will help or at least you can read to see what's happening / why it's hanging up.

---

### Post by Rallg on 2012-08-02
If boot shows only text, it usually means that there is something wrong with your graphics driver. There is no possibility of providing a complete GUI without a graphics driver. However, you may be able to boot to "fail-safe" mode, which uses a generic back-up driver. If success, your screen will look wrong, but it will be GUI.

Try this: Boot to recovery mode. Enable networking. Networking may fail if you are using Wi-Fi and are not already connected. If that happens, try this: Use another operating system (Windows, Ubuntu Live CD) to log into the Wi-Fi. Then, reboot and quickly log in to Ubuntu. In many cases, the Wi-Fi provider will rememer that your computer is logged in, even if you change operating system.

In recovery mode (plain text), enter:

sudo apt-get update && sudo-apt-get upgrade

then provide your password. Allow the system to make changes.

To get out of the text mode,

sudo shutdown -r now

will reboot your system.

If that did not help, then in recovery mode you can use apt-get to install missing software, if you know the package name. If you only know some of the package name, then use * as wild card. Thus

sudo apt-get install nvidia*

will install any package beginning with nvidia.

---

