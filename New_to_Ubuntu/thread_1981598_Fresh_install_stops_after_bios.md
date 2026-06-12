---
title: "Fresh install stops after bios"
date: 2012-05-17
forum: New to Ubuntu
---

### Post by Kaero on 2012-05-17
I decided to take my old Dell Inspiron 1521 and install the latest version of Ubuntu on it via a USB stick. It boots fine off the usb stick but when I remove that and just power on the laptop, I get the bios screen and then a black screen with a flashing white underscore and it stays like that. Also when using it via the USB stick the wifi doesn't work, it doesn't seem to detect the wifi card. I'd love to get this up and running.

---

### Post by wilee-nilee on 2012-05-17
Take a look at this to get in with nomodeset if this gets you in then run the command to identify the card as well and post it.

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

For the card.

```
[FONT=Verdana, sans-serif][SIZE=1]lspci | grep -i wireless[/SIZE][/FONT]  
```If you see nothing try this one as well.

```
[FONT=Verdana, sans-serif][SIZE=1]lspci | grep Broadcom[/SIZE][/FONT]
```So if you can  use a ethernet cord to get updated and upgraded the graphic problem may get fixed, check the app additional drivers for any drivers.

You can also run this command to identify the graphic card if needed.
```
 [FONT=Verdana, sans-serif][SIZE=1]lspci | grep VGA[/SIZE][/FONT]
```

---

### Post by Kaero on 2012-05-17
Thanks, I couldn't get into the grub menu at all so I ended up just reinstalling Ubuntu and enabling the nomodeset thing before the installation and everything worked out fine after that, wireless drivers are proprietary I guess so it's downloading and installing those now. Didn't have an ethernet cable plugged in the first time I installed it and I guess that caused some problems.

---

### Post by wilee-nilee on 2012-05-17
> **Kaero said:**
> Thanks, I couldn't get into the grub menu at all so I ended up just reinstalling Ubuntu and enabling the nomodeset thing before the installation and everything worked out fine after that, wireless drivers are proprietary I guess so it's downloading and installing those now. Didn't have an ethernet cable plugged in the first time I installed it and I guess that caused some problems.

Cool, enjoy.

---

