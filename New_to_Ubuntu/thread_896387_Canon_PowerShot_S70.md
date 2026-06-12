---
title: "Canon PowerShot S70"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by pjhartt on 2008-08-21
When I connect my Canon PowerShot S70 camera nothing happens. I even have to turn the camera on manually (this turns on automatically in Windows!) but still the computer does not see the camera.

I am using LinuxMint 5.0.

Regards
Peter

---

### Post by silkstone on 2008-08-21
I don't have a direct solution for you - many people find that their cameras are not recognised when connected directly to a Linux machine - but I can suggest a simple solution, which is to use a card reader.

Personally I find a card reader much simpler and quicker anyway - just remove the card from the camera and slot it into the reader. No cables, no drain on the camera battery, and the transfer speed is likely to be quicker too.

You can get a good card reader for less than £4 - the Hama 35-in-1 reader from Amazon works just fine, and also supports SDHC.

---

### Post by aloshbennett on 2008-08-21
Is there a setting on the camera to choose between PTP and Mass Storage mode?
Try selecting PTP if usb connectivity is set as Mass Storage Mode.

---

### Post by philinux on 2008-08-21
There is currently a confirmed bug.

[https://bugs.launchpad.net/ubuntu/+bug/242644](https://bugs.launchpad.net/ubuntu/+bug/242644)

You can however fire up Gthumb from the Graphics menu. This will import. But watch the time stamps of the files downloaded. This aspect might be fixed now. However I now use a card reader.

[edit] the timestamp issue has been resolved.

---

