---
title: "Dual Displays won't install properly"
date: 2012-06-11
forum: New to Ubuntu
---

### Post by cncorbust on 2012-06-11
[IMG]http://ubuntuforums.org/images/rebrand/statusicon/user_offline.gif[/IMG] I am running Ubunto 12.04 in demo mode from a CD. I have dual displays on an Intel dual core 2.4GHz cpu, 4 Gbs memory.
The demo boots in and finds the two displays and correctly names them .
The "Displays setup screen" initially shows the two displays as "Mirrored". Unlocking the mirror then shows the two displays but the one physically on the left is shown as being on the right. Moving the representation for the display that is physically on the left to the left of its mate should correct the problem and allow for sliding the cursor from full left on the left display to full right on the right hand display. Doing so and selecting the "apply" button results in one or both displays going black and the system locks up. The only recovery that I have found that works is a general reset and reboot, not very useful. The action is inconsistent and has occasionally worked correctly but mostly all I get is a lockup. I can change the display parameters and select the "apply button" OK no lockup but as soon as I move either representation of the monitors and select "Apply" the lock up occurs.

---

### Post by cncorbust on 2012-06-11
Oops!

---

### Post by TheGuyWithTheFace on 2012-06-11
I had a similar problem, you may find this useful:

[http://blog.shevin.info/2012/05/how-to-fix-dual-monitor-freeze-in.html](http://blog.shevin.info/2012/05/how-to-fix-dual-monitor-freeze-in.html)

This may require you to have it installed, though, since if you're running from a live cd your changes will get reset when you turn your computer off.

---

### Post by cncorbust on 2012-06-11
This is embarassing, I am very new to Linux. I don't even know how to download to desktop and use your suggested steps to replace the part of the screen software that is acting up! Any help or even a pointing finger as to where I could find how to do the processes would be appreciated.

---

### Post by TheGuyWithTheFace on 2012-06-11
Sure! To move the files to your desktop, open your files, click on the downloads bookmark, and drag those files to your desktop. to run the "processes", press ctrl+alt+T and copy those commands. After restarting the computer, I'm pretty sure you can delete the files from your desktop.

---

### Post by Ubun2to on 2012-06-11
It's probably a driver issue. It took me awhile to get my dual display layout working. I can't part with my second monitor-I love the experience, and it's especially great for schoolwork (research paper on one monitor, webpage with information on the other).
What graphics card do you have? If you are not sure, type the following command in terminal (press CTRL + ALT + T if you are unsure how to get there):
```
lspci -v | less
```
You might have to scroll down awhile, but there should be something that says "VGA compatible controller: graphics card name here," unless you have a DVI-D or HDMI monitor, in which case I have no idea what to look for (DVI-D has a bunch of boxes and HDMI looks similar to USB ports if that helps you determine what you are using-VGA ports have holes and usually allow you to screw something in, unless you are using a laptop).
I have an AMD ATI Radeon HD 5450 (ATI is a subsidiary of AMD, if you're confused about that). Search for the card that you have-chances are, it requires proprietary drivers (since currently, all the companies out there can't seem to agree on anything, like the US government).
I hope this helps.

---

