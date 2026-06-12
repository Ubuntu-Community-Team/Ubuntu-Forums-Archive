---
title: "google earth - unsupported graphics card"
date: 2014-05-14
forum: New to Ubuntu
---

### Post by debroos on 2014-05-14
I have installed Google Earth on a pc which displayed fine with XP.  When I try to run it on Ubuntu I get the message "Unsupported Graphics Card.  Your graphics card does not meet the minimum spec required to run Google Earth,which is a 3D accelerated card with shader support.   It is strongly recommended that you try running Google Earth on a different machine or in a different rendering mode or upgrade to a newer graphics card.  You may continue,but the application is unlikely to work."  Needless to say it doesn't work, but I can't see that the graphics card is at fault, given that it works fine on XP.  Any help would be very much appreciated.  Much as I like Ubuntu this may well be the last straw before its demise.

---

### Post by HiImTye on 2014-05-14
the second answer [here](http://askubuntu.com/questions/47506/how-do-i-install-extra-drivers)
Google is amazing

---

### Post by debroos on 2014-05-14
Thanks for that Hilm.  I've already followed the additional drivers route and it comes up with "No proprietary drivers are in use on this system".  I notice that someone else put this same question/dilemma on another forum to no avail.

---

### Post by HiImTye on 2014-05-14
what video hardware do you have? if unsure```
lspci | grep -i vga
```

---

### Post by debroos on 2014-05-14
It's the following  - 00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)

---

### Post by monkeybrain20122 on 2014-05-14
Which Ubuntu are you on? You can try update your driver with [https://launchpad.net/~oibaf/+archive/graphics-drivers](https://launchpad.net/~oibaf/+archive/graphics-drivers) (Ubuntu 13.10/14.04) or [https://launchpad.net/~pali/+archive/graphics-drivers](https://launchpad.net/~pali/+archive/graphics-drivers) ( Ubuntu 12.04)

---

### Post by HiImTye on 2014-05-14
your graphics chipset hasn't had updated drivers from Intel for eons, so you should try using a Google Earth 6.x version and see if you have any better luck. how are you installing Google Earth?

---

### Post by debroos on 2014-05-15
Thanks for all the help.  I've not had chance to follow any of the latest through, nor will I until after the weekend, but my hopes are raised

---

### Post by debroos on 2014-05-19
Thanks for the info.  I update the PPA and did an apt-get update.  I uninstalled Google Earth, I could only find the one previous version of the software, but it would only download a bin file for some unknown reason, which I was unable to open.  I've reinstalled v7.1 but the the same message comes up.  I've installed it per the instructions from here [https://help.ubuntu.com/community/GoogleEarth](https://help.ubuntu.com/community/GoogleEarth) - followed them to the letter. I have to yield.

---

### Post by debroos on 2014-05-19
Further to the above I uninstalled compiz in case that was affecting the display.  I don't know if the current situation is caused by that, or by drivers from the launchpad archive.  Whatever the cause, I'm now only able to run Ubuntu in recovery mode.  'Regular' mode just shows a blank screen without any icons - the same on all the accounts. Should I do a complete reinstall ...?

---

### Post by monkeybrain20122 on 2014-05-19
You can remove the ppa with ppa-purge from recovery mode.
If you have not installed it already
```
sudo apt-get install ppa-purge
```
then
```
sudo ppa-purge ppa:oibaf/graphics-drivers
```

So that part is reversible.

As for compiz, what is your desktop evironment originally? If it is unity then of course you have a problem as it is a compiz plugin, if you remove compiz then you can't boot into the desktop. You can reinstall compiz in the recovery mode. If that is the case reinstall compiz first and don't bother with the driver yet. If you can boot back into the desktop then you can keep the ppa.

Now if you could run compiz I am not sure why you had a problem running google earth.

---

### Post by debroos on 2014-05-19
The saga continues.  I've got my GUI back with ..install Ubuntu desktop, but still no joy with Google Earth

---

### Post by monkeybrain20122 on 2014-05-19
So are you using the oibaf driver or not?

---

