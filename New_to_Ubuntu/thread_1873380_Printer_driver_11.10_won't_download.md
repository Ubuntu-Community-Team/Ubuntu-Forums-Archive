---
title: "Printer driver 11.10 won't download"
date: 2011-11-01
forum: New to Ubuntu
---

### Post by rimibchatterjee on 2011-11-01
I have an HP 1020 Laserjet printer. I managed to install it on Ubuntu 10.04 after a series of tweaks. This time on Ubuntu 11.10 the system detected it correctly and even attempted to do an auto download of the required driver. however it couldn't find the driver, and manual search of HPLIP confirmed that no drivers are tagged Ubuntu 11.10, the latest is 11.04. Is there anywhere else you can get the driver or do we have to wait for HP to come up with it.
Here's a screenshot of my XTERM window when the download fails. This happens every time I boot or attempt to use the printer.

EDIT: It's weirder than that. The printer shows up in the printer panel with a big green tick on it, and hp-setup -i worked in so far as it brought up the make and model of the printer, it then said (in red) you must be root to run this program and crashed. The comp knows my printer is there, attached to the usb port, but I just can't print. Not even a lousy test page.

---

### Post by rimibchatterjee on 2011-11-03
Furthermore,
As you will see from the screenshot, this app calls a resource at [http://www.openprinting.org/download/printerdriver/auxfiles/hp/plugins/hplip-3.11.7-plugin.run](http://www.openprinting.org/download/printerdriver/auxfiles/hp/plugins/hplip-3.11.7-plugin.run). However, if I navigate manually to this site it says it's down for maintenance. Any idea why?

---

### Post by cavh on 2011-11-03
I had similar openprinting.org connection problems. I think that site's down to the recent attack on the Linux Foundation, but don't quote me on that.

In my case I deleted the printer (a Canon, not that the make matters), and then found an appropriate PPD file on the Canon website. Then I installed the printer using CUPS directly, running it from [http://localhost:631]("http://localhost:631"). 

I can now print, but only in black and white (not colour), so I probably don't have the right PPD; but can't be bothered to change it. :o

---

### Post by wolfen69 on 2011-11-03
> **rimibchatterjee said:**
> I have an HP 1020 Laserjet printer. I managed to install it on Ubuntu 10.04 after a series of tweaks. This time on Ubuntu 11.10 the system detected it correctly and even attempted to do an auto download of the required driver. however it couldn't find the driver, and manual search of HPLIP confirmed that no drivers are tagged Ubuntu 11.10, the latest is 11.04. Is there anywhere else you can get the driver or do we have to wait for HP to come up with it.
Here's a screenshot of my XTERM window when the download fails. This happens every time I boot or attempt to use the printer.

EDIT: It's weirder than that. The printer shows up in the printer panel with a big green tick on it, and hp-setup -i worked in so far as it brought up the make and model of the printer, it then said (in red) you must be root to run this program and crashed. The comp knows my printer is there, attached to the usb port, but I just can't print. Not even a lousy test page.

You can't download the plugin because it downloads from openprinting.org, which is down at the moment.

---

### Post by mijdrawoh on 2011-11-03
See:[http://ubuntuforums.org/showthread.php?t=1849652](http://ubuntuforums.org/showthread.php?t=1849652)

---

### Post by rimibchatterjee on 2011-11-05
Thank you Wolfen69 and mjldrawoh. I figured it must be a server problem. Will see if I can fix it in the interim with a close as dammit PPD. Thanks for the heads up

---

