---
title: "wifi speed"
date: 2011-12-20
forum: New to Ubuntu
---

### Post by ub9876 on 2011-12-20
does this really do anything????



Is your WiFi connection working slow after doing an upgrade to Ubuntu 11.10 Oneiric Ocelot? This may be caused by your Atheros modules. In this tip we will show you a solution that may help you restore the default speed of your WiFi connection. This solution is also workable for LinuxMint11.

Getting Started

Open the terminal and run this sequence of commands:

sudo -s
gksu gedit /etc/modprobe.d/ath9k.conf

And at the end of the file, insert this line:

options ath9k nohwcrypt=1





does my Toshiba laptop most likely have atheros stuff??

---

### Post by pastalavista on 2011-12-20
> **ub9876 said:**
> does this really do anything????



Is your WiFi connection working slow after doing an upgrade to Ubuntu 11.10 Oneiric Ocelot? This may be caused by your Atheros modules. In this tip we will show you a solution that may help you restore the default speed of your WiFi connection. This solution is also workable for LinuxMint11.

Getting Started

Open the terminal and run this sequence of commands:

sudo -s
gksu gedit /etc/modprobe.d/ath9k.conf

And at the end of the file, insert this line:

options ath9k nohwcrypt=1





does my Toshiba laptop most likely have atheros stuff??

To find out run ```
sudo lshw -c network
``` and replace 'ath9k' in the fix code with whatever your wireless driver module is.

---

