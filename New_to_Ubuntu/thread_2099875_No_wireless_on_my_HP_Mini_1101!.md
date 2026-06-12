---
title: "No wireless on my HP Mini 1101!"
date: 2012-12-30
forum: New to Ubuntu
---

### Post by Sabre88 on 2012-12-30
Hi guys. I'v always been interested in Linux so I decided to go with Ubuntu. However after I installed it as the sole operating system on my HP Mini 1101 netbook I've been unable to connect to my wifi, I'm unable to see any networks. I've been looking at the settings and I haven't seen any options concerning connecting to a wireless network. Please help, I'm a total newbie to Linux and I don't want to go back to windows because of this. Someone please help me, I will greatly appreciate it. Thank you in advance.

---

### Post by squakie on 2012-12-30
Hold down the ctrl and alt keys and press F1 to get to a terminal.  Please type lspci and press enter.  Look for the network adapters, copy those lines and post them back here.  We need this to know the chipset your wireless is using so we can find out how to get the driver for you.

---

### Post by iMac71 on 2012-12-30
did you have selected the "third party software" option during installation? If not, you could have missed the necessary driver.

---

### Post by Sabre88 on 2013-01-01
@ squakie;
Network Controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (REV 01)

@ iMac71, yes I did choose the "third party software" option during installation.

thanks guys, awaiting your response!

---

### Post by JustinR on 2013-01-01
Hi,

installing the broadcom-sta driver should do the trick.

---

### Post by iMac71 on 2013-01-01
your network controller is supported (see hare: [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43) ); if you can temporarily use an internet wired connection, you can type in a terminal window:```
sudo apt-get install firmware-b43-installer
```

---

### Post by davidtrounce on 2013-01-01
I had success here: [http://ubuntuforums.org/showthread.php?t=2098998&page=2](http://ubuntuforums.org/showthread.php?t=2098998&page=2) getting my wireless working on a Toshiba NB305.

---

