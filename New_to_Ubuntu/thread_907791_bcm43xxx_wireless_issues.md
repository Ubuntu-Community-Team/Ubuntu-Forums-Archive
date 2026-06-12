---
title: "bcm43xxx wireless issues"
date: 2008-09-01
forum: New to Ubuntu
---

### Post by PatrickMoore on 2008-09-01
anyone know how to get broadcom wireless cards to work i have an hp pavillion dv6109 laptop with bcm94311mcg wlan mini pci (rev 01)

---

### Post by anewguy on 2008-09-01
Do you have, or are you able to download, any Windows XP drivers for it?

---

### Post by PatrickMoore on 2008-09-01
> **anewguy said:**
> Do you have, or are you able to download, any Windows XP drivers for it?

i couldnt find them

---

### Post by drs305 on 2008-09-01
Here is a link that will start to explain things and then take you where you need to go. I have a broadcom 4311 and it works fine although it took a bit to set it up. The author of the referenced thread says 5 minutes...

[http://ubuntuforums.org/showthread.php?t=475963]("http://ubuntuforums.org/showthread.php?t=475963")

---

### Post by ctswhole on 2008-09-01
This sounds very similar to the Broadcom wireless I had in a Compaq laptop I had (Compaq f500).  I followed the guide from here:

[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper)]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper)")

After doing this, my wireless worked perfectly!

---

### Post by anewguy on 2008-09-01
Another thread regarding the 94311 specifically:

May 13th, 2008, 02:24 PM 
This [http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/](http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/) posted by mmichalik and adding this:  echo -e '\n#hardy ssb bug-fix\nrmmod b43\nrmmod b44\nrmmod ssb\nrmmod ndiswrapper\nmodprobe ndiswrapper\nmodprobe ssb\nmodprobe b44' | sudo tee -a /etc/init.d/rc.local  worked perfectly for me. I'm on a HP dv2410us with the bcm94311, and this guide is what it took. I restarted before reading that last bit of code and nothing worked, but when I added that and then restarted, perfect. Wireless works just fine now. 


July 20th, 2008, 08:47 AM 
The links to the driver downloads are at [http://invaleed.wordpress.com/2007/1...ci-ubuntu-710/](http://invaleed.wordpress.com/2007/1...ci-ubuntu-710/)

---

### Post by PatrickMoore on 2008-09-01
> **drs305 said:**
> Here is a link that will start to explain things and then take you where you need to go. I have a broadcom 4311 and it works fine although it took a bit to set it up. The author of the referenced thread says 5 minutes...

[http://ubuntuforums.org/showthread.php?t=475963]("http://ubuntuforums.org/showthread.php?t=475963")

i have no internet connection to that laptop. im using my girlfriends to talk here

---

### Post by anewguy on 2008-09-01
Can you hard wire to the router?

---

### Post by PatrickMoore on 2008-09-01
no we run only on wireless. the modem we have does not recognize my computer. i had it working on ubuntu 8.04 when i had that running. would i be able to follow the same process? i used a live cd to install builessentials

---

### Post by ctswhole on 2008-09-01
> **PatrickMoore said:**
> i have no internet connection to that laptop. im using my girlfriends to talk here

One option you could try is to follow anewguy's link that he provided to get the drivers for you wireless card and save it to a disc or thumb drive.  Transfer this to your laptop and install ndisgtk from Synaptic (it's included on the CD).  You could then install the driver from the ndiswrapper GUI (**System --> Administration --> Windows Wireless Drivers**

---

### Post by Slug71 on 2008-09-01
Have you tried to see if you have a restricted driver in Admin-Hardware Drivers? When i was using Hardy i had to enable the wl restricted driver to get my wireless going. I too have Broadcom

---

### Post by anewguy on 2008-09-02
Try this:

modprobe b43

Then see if your wireless is there.

---

