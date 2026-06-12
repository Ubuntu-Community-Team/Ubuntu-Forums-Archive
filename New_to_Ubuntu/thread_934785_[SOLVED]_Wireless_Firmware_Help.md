---
title: "[SOLVED] Wireless Firmware Help"
date: 2008-09-30
forum: New to Ubuntu
---

### Post by Sparty26 on 2008-09-30
Hey, I need help once again, but please keep in mind I am completely new to Kubuntu and Linux, so forgive me, but this is probably a stupid question. I need to install the proper Firmware on my computer so that I can use my wireless. I was directed to this [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware]("website"). The problem I am having is that I don't understand the instructions? I downloaded and extracted the b43-fwcutter tarball (at least I think I did it successfully), but I don't understand what the instructions mean by "build it?" I don't know if I am supposed to run the code they give me in the terminal or if I am supposed to do something different? I know this is probably stupid, but any help is greatly appreciated, and clearing this up for me now will deffinantly help me in the future. Once again, I appologize for being so dumb.

-Adam

---

### Post by adult swim on 2008-10-01
if you can connect to the internet now with an ethernet connection, try going to a terminal and running ```
sudo apt-get install b43-fwcutter
```

---

### Post by lisati on 2008-10-01
The website [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware) says for ubuntu you need to run the following command to install it:
```
sudo /usr/share/b43-fwcutter/install_bcm43xx_firmware.sh
```

---

