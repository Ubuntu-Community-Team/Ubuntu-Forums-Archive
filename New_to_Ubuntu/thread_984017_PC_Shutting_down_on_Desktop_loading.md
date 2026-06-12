---
title: "PC Shutting down on Desktop loading"
date: 2008-11-16
forum: New to Ubuntu
---

### Post by stuart264 on 2008-11-16
Ok, something has gone seriously wrong with my ubuntu install.

I had just finished setting up my ide drives with LVM and I was in the process of copying the files back across the network when the graphics card crashed, on reboot the pc refused to even power on until I pulled out the ATI-9550 graphics card and went back to the onboard viachrome graphics driver but when I reboot I can get into recovery mode fine but when I try to start normally when the desktop starts to load the pc powers straight off.

So far I have uninstalled BOINC, clamav, compiz to see if thats causing the power off problem but with no success.

Any suggestions cos I am really desperate to get my Linux box back up and running even if I have to do a complete re-install

Stuart.

---

### Post by Peter09 on 2008-11-16
In recovery mode what happens if you type ```
startx
``` at the command prompt

---

### Post by stuart264 on 2008-11-17
Absolutely nothing, but i managed to track down the fault, I had added 3 spare IDE drives that i had salvaged and wanted to use with LVM to add some additional storage and they were pulling too many amps across the power supply and it was shutting down, once I pulled them the system started behaving now all I have to do today is put the ATI graphics card back in and test if thats toasted or not and order up a 500gb SATA drive to add more storage for multimedia on my machine, I suppose it serves me right for trying the cheap option but when you have spare drives around the house and a 500gb drive is about £45 and your broke you try the cheap option first.

---

