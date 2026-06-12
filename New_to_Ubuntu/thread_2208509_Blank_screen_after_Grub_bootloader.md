---
title: "Blank screen after Grub bootloader"
date: 2014-02-28
forum: New to Ubuntu
---

### Post by shadowofsolidus on 2014-02-28
Hi, guys. I just installed Ubuntu on a new hard drive and not the one that has Windows 7 on it. Anyways I installed it and got the cool Grub bootloader and chose Ubuntu to load for the first time. It went smooth until i installed video card drivers which required me to restart. After the reboot, and choosing Ubuntu to load from the Grub boot menu, the screen is just blank. Help please :(

---

### Post by mörgæs on 2014-03-01
Please finish your first thread by stating what you did and marking the thread 'solved'.

After that: Which screen card and which drivers?

---

### Post by grahammechanical on 2014-03-01
At the Grub boot menu we can chose Recovery Mode. How we get to recovery mode will depend upon what version of Ubuntu we are using. You see Ubuntu 12.04 is different in this respect from Ubuntu 13.10.

But at the Recovery menu we can select Resume and that will load or try to load to a desktop without using the proprietary video driver. Then when we get to the desktop we can use Additional Drivers to experiment with video drivers. We should get an offer of about 5 drivers including Nouveau, the open source video driver.

Regards.

---

### Post by mörgæs on 2014-03-01
Nouveau is a driver for Nvidia. If the card is AMD / Intel / something else this driver does not come into play.

---

### Post by rjt69 on 2014-03-01
Do you get a text based login screen if you press *<CTRL>+<ALT>+F1*  or *<CTRL>+<ALT>+F2*?

If so, login, tail out /var/log/syslog and see if there is a /home/username/.x* file(s)?

---

