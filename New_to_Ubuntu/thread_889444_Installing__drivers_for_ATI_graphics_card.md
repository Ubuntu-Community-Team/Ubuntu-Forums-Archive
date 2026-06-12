---
title: "Installing  drivers for ATI graphics card"
date: 2008-08-14
forum: New to Ubuntu
---

### Post by loseby on 2008-08-14
Have just reinstalled Ubuntu from scratch with my new ATI 4870 Graphics card. Previously couldnt get any better then 800x600 when I upgraded the graphics card so did the complete reinstall. Now have not added anything except the updates that Ubuntu wanted. Now I want to get my graphics running at 1920x1200 with all the 3d effects etc. Now what is the best method to install the latest drivers for this card ?  Eventually I want to try playing games using Wine but you must walk before you run so its hep required in getting my graphics card operating fully.

---

### Post by zipperback on 2008-08-14
You should be able to activate the ATI driver with:

System -> Administration -> Hardware Drivers

Enable the "ATI Accelerated graphics driver" and it should install it for you.

I have an ATI Radeon 1100 and that's how I activated mine.

- zipperback
:popcorn:

---

### Post by zipperback on 2008-08-14
Something else you might want to consider is using Envy.

It's something I didn't know about when I initially did the install on my system.

You can install it from the repositories.

You can get more information from this page.
[http://albertomilone.com/envyngfaq.html]("http://albertomilone.com/envyngfaq.html")

That is the homepage of the developer of the application.

- zipperback
:popcorn:

---

### Post by loseby on 2008-08-14
Looks like they havent a driver for the 4870 yet and envy doesnt reqonise the grahics card

---

### Post by neoplasme on 2008-08-16
I tried installing the ATI driver with envy but when I restarted my computer everything froze and the the screen was black. Same thing with Hardware Drivers
  What do you think is the problem?

by the way I have an ATI 1300

---

### Post by th3t1nm4n on 2008-08-23
*bump*
I have this same video card, the 4870 and want to know how to get it fully working in Ubuntu since it's not recognized in the restricted drivers utility (it's pci-id is too new I think)
I tried manually installing both the fglrx drivers and the new open source ati drivers and both times it didn't work, it just went into low-graphics mode at boot.

I tried the latest Intrepid, but it gets red lines after boot so that didn't work.
Any ideas other than waiting until October for Intrepid to have a final release?

---

### Post by loseby on 2008-08-25
the card has been out for a while and with the new x2 version been released on the 12th of August to the Geneal Public this again shows up the gulf between Windows and Linux when it comes to drivers .

---

### Post by th3t1nm4n on 2008-08-26
I just tried the 8.8 drivers, still no luck. Mesa runs and it runs in "low graphics mode" even though xorg.conf has the fglrx driver in it.

---

### Post by mzentz on 2008-08-26
I have an ATI Radeon 9200/9250 card, have installed the drivers from ATI and installed Envy.  I think the biggest problem might be my xorg.conf file (partially shown below).  Can anyone tell me why I don't have any "Device" detail?  I've run "sudo dpkg-reconfigure xserver-xorg" several times and don't even get to a video settings part.  It's all about configuring the keyboard.




xorg.conf
----------------------------------------------------------
Section "Device"
        Identifier      "Configured Video Device"
        Option          "UseFBDev"              "true"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
EndSection

---

