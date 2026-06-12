---
title: "Chrome and Chromium not working"
date: 2018-09-10
forum: New to Ubuntu
---

### Post by mark194 on 2018-09-10
After starting my system today, neither Chrome nor Chromium work, both just give me a black window.  Firefox works fine. I tried updating, upgrading and rebooting but same result.  Completely clueless what do to.  Chrome worked fine until today.

---

### Post by &amp;KyT$0P# on 2018-09-10
Try running Chromium from Terminal with [FONT=Courier New]--disable-gpu[/FONT] switch -
```
chromium-browser --disable-gpu
```
Does it work?

---

### Post by mark194 on 2018-09-11
Yes, that works, but only when run from Terminal with the code you provided.  If I click on the icon I get the same black window.  Why is this?

---

### Post by ajgreeny on 2018-09-11
Go to the settings for chromium (and I assume chrome but have never used it), scroll to the bottom Advanced, and in System near the bottom turn off "Use hardware acceleration when available"

The browsers should now start fine and without the black window.

What graphics do you use and which driver?

---

### Post by mark194 on 2018-09-11
It's a GeForce 7300LE.  Driver says 'nouveau' which doesn't sound like a driver version to me.  Is this the problem?

Turning off the hardward acceleration worked.  Not sure where the problem arose b/c it worked fine for 2-3 wks then just stopped working without warning.

---

### Post by ajgreeny on 2018-09-11
Go to Additional Drivers and see if there's an nvidia driver available for that card. 
Install the recommended one if there is one, and then try chromium with hardware acceleration enabled again; that may be the reason for the problem.

---

### Post by mark194 on 2018-09-11
It shows 2 drivers available, one from NVIDIA and the nouveau driver which is says is from Xorg.X server.  The nouveau is highlighted. When I try to change to the NVIDIA legacy driver and click Apply Changes, it reverts back to highlighting the nouveau driver.  Restarting confirms that the change of driver wasn't made and Chrome won't work with hardware acceleration enabled. 

Am I doing something wrong to change the driver or is something preventing me from changing it?

---

### Post by ajgreeny on 2018-09-12
I don't think you're doing anything wrong; there is possibly no nvidia driver available for your card, but I have never had an nvidia card so I am no expert in this.

Wait to see if anyone knows better, but if not you will have to continue with the nouveau driver for now, and keep hardware acceleration disabled.

---

### Post by gcurtsinger on 2018-09-13
Have you tried uninstalling Chrome. then use Firefox to go to the Chrome website and download Chrome for Linux.

---

