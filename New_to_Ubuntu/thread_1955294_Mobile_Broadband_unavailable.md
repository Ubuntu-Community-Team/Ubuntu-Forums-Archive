---
title: "Mobile Broadband unavailable"
date: 2012-04-09
forum: New to Ubuntu
---

### Post by Roger49 on 2012-04-09
Hi,
Over Easter, I've been looking at DE's that are available for use when I have to retire my 10.04 installation.
I have a dvd for 11.10, and installed it onto a new partition of a usb disk I use for testing.

The instructions with the dvd recommended that I connect to the internet before installing.
I was unable to do so.

When installed, occasionally the OS will try to connect on start-up, and then fail. Often it will not attempt to do anything to connect.

The old "right-click to enable mobile broadband" I am familiar with from 10.04 and 10.10 is no longer there.

The "3" dongle I use is no longer on the list of installed devices.

I have set up the broadband account.

I have reset the modem by unplugging it and plugging it back in again.

Does anybody have any suggestions?

It was a bit of a problem when I was testing 10.10 on the usb hard disk, but I was able to connect eventually.

Is it a problem caused by the "bottleneck" of a usb connection, or is there something I'm missing? (It wouldn't be the first time)

Regards,
Roger.

---

### Post by Linux_junkie on 2012-04-09
Unfortunately you cannot use a mobile broadband "dongle" to connect to the Internet when you install Ubuntu/Kubuntu/Xubuntu/Lubuntu from a live CD.

I use a T-mobile "dongle" and whenever I install any of the Canonical supported distros I have to install from the liveCD first then set up mobile broadband using Network Manager then download all extra packages at that stage.

Hope this helps.

---

### Post by Jose Catre-Vandis on 2012-04-09
I had a similar problem when trying to use my Android phone as a network access point. Had to upgrade the kernel to 3.1, so might this also work in your case?

---

### Post by Roger49 on 2012-04-12
Hi,
Fixed it.
I checked that the machine had detected the dongle with "lsusb", and it had.
If you right-click on the background, and choose "Applications", "System", "Users and Groups".
Click on "Advanced Settings", and enter your password.
Under the "User Privileges" tab is a list of tick-boxes. Printing and Modem use had not been ticked.
Click on the boxes you might need, save and close.
I now have Internet access.
I thought I would post it here for other users who are scratching their heads.
Regards,
Roger

---

