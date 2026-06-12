---
title: "Can't copy files to PSP"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by thomsany on 2008-05-30
Hey guys!!
Whenver I connect the PSP to my USB drive, Ubuntu detects the memory card. No problem there. However, everytime I want to copy a file to the memory sticks, Nautilus lets me copy it without a problem but everytime I disconnect it and reconnect it, the files are gone. Its like they are never copied to the device.
I tried to do a sudo nautilus to go in as root and do the copying but still nothing changes! I am running out of options here.. I want to copy some files and I want them to stay there.
Ubuntu detects the memory card without issues, but I can't really copy anything, not even in command line with cp and sudo.
Any suggestions is appreciated..
thanks much.
Regards,

Teo

---

### Post by anjilslaire on 2008-05-30
When finished copying, you need to Safely Remove (unmount) the PSP on th linux side, then close the usb connection on the PSP side. This will correctly write the data and sync everything.

I'm not sure how this is done in Gnome (I use KDE), but for my system (kubuntu hardy), I right-click the PSP drive and select Safely Remove. This is critical for the PSP for some reason, moreso than most usb drives (but a good habit to get into, regardless).

---

