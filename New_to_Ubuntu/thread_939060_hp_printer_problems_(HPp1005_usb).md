---
title: "hp printer problems (HPp1005 usb)"
date: 2008-10-05
forum: New to Ubuntu
---

### Post by zadstyx on 2008-10-05
it looks like it works but fails to print anything. When i plugged it in it was recognized and set as ready to print. the print jobs (looking at the logs) show successful, but nothing prints. 

even the print icon shows up and indicates the job as processing, then it goes away and nothing prints... 

I've tried reinstall, updated and installed HPLIP toolbox, same effect there, all action nothing prints.  

printing url : hp:/usb/HP_LaserJet_P1005?serial=BB03AXA

read a few other posts, but it appears everything is right except nothing prints.

---

### Post by eternalnewbee on 2008-10-07
If you are still using windows, try and see if the printer Does work. If so then you might need to update your drivers. If not then you should have your printer checked.
That's all I can think of...
Good luck

---

### Post by neilengineer on 2008-10-07
My answer seems to be stupid, but anyway:

You'd better check your printer first.
1. Are you sure there is any ink/paper in the printer?
2. Try another USB port on PC? Maybe?

If printer is fine.
1. Try another OS(if you have) on the same PC.
2. Try another PC.

---

### Post by PierreDeKat on 2008-10-07
According to [HLIP's documentation]("http://hplipopensource.com/hplip-web/supported_devices/laserjet.html"), your printer should be supported by version 2.8.2 and upward. Except that a *"downloadable driver plug-in is required for printing support."* 

So you're probably going to have to research that a little more. Perhaps snooping HP's website would yield a Linux driver. Or you might try [asking the HPLIP support folks]("http://hplipopensource.com/hplip-web/support.html").

---

### Post by jimmy the saint on 2008-10-07
Are you sure you are selecting the right printer when you go to print?  Ubuntu comes with "print to PDF" printer that may be selected by default.  
Just a thought

Good Luck!

---

### Post by PierreDeKat on 2008-10-07
Oh, wait a minute, [here's a little more]("http://hplipopensource.com/hplip-web/models/laserjet/hp_laserjet_p1005.html") about the driver installation for HPLIP.

---

### Post by rlogan on 2008-10-07
From my experience HP printers normally work 1st up when they are connected, I know I didn't do anything special when I installed out HP for the first time, was all very easy.

Someone suggested the PDF printer bit that gets a couple of the people that use my home network. Also check out the HP printer info in one of the links previous to mine.

Cheers

---

