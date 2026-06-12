---
title: "Nvidia 8400GS PCI-E"
date: 2013-11-04
forum: New to Ubuntu
---

### Post by wolfen10862 on 2013-11-04
I have had this distro for 3 days now, and I LOVE IT, Windows Vista totally crashed on me and I couldn't re install it from the cd or anything to svae my life, so far with Ubuntu 13.10 I can print, scan, do cd's and dvd/s but I do have one problem.
I have a Nvidia 8400GS PCIE video card and i don't know how to install drivers for it or even where to get them.
I can open a terminal, but that's as far as my current level of knowledge goes.
if it comes up with password: I am totally lost right there.
Please somebody help me install this video card, its the last thing I need to do to make this operateing system better than anything else on the planet

---

### Post by TheFu on 2013-11-04
1st, Ubuntu and Linux is not like Windows.  The most current, proprietary driver often is NOT what you want. It breaks things.  Staying with the drivers provided with the distribution is a best practice, especially for someone extremely new to Linux.

Also, downloading drivers directly from the vendor is seldom a good idea, unless you are comfortable in the shell.  You will probably figure it out, assuming everything goes perfectly, but ... if something goes wrong, some shell-fu will be needed.

There is some good news.  [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia) explains how to install nVidia drivers.

In my hope to teach you to fish, not just hand you a fish to eat today, I used google with search of **ubuntu nvidia driver** to find that link.  Knowing the right question to ask is critical.  The help.ubuntu.com website has many pre-built instructions.

---

### Post by wolfen10862 on 2013-11-04
Thank you very much. 
as for teaching me how to fish, please teach me instead of handing me a fish :) I'm 50 years old and I am under the asumtion that he who dies with the most knowledge wins, and I have plenty of room left in my brain to learn :)

Oh btw the link you gave me just got bookmarked

---

### Post by philinux on 2013-11-04
> **wolfen10862 said:**
> I have had this distro for 3 days now, and I LOVE IT, Windows Vista totally crashed on me and I couldn't re install it from the cd or anything to svae my life, so far with Ubuntu 13.10 I can print, scan, do cd's and dvd/s but I do have one problem.
I have a Nvidia 8400GS PCIE video card and i don't know how to install drivers for it or even where to get them.
I can open a terminal, but that's as far as my current level of knowledge goes.
if it comes up with password: I am totally lost right there.
Please somebody help me install this video card, its the last thing I need to do to make this operateing system better than anything else on the planet

If you are running version 13.10 then click the gear top right on the desktop and choose system settings. From there click on Software and Updates. Then click the additional drivers tab. Choose the recommended one.
It will ask for a password. That's the same as your login password. A reboot is needed to activate the new driver.

---

### Post by mastablasta on 2013-11-04
under item 2: [http://www.omgubuntu.co.uk/2013/04/10-things-to-do-after-installing-ubuntu-13-04](http://www.omgubuntu.co.uk/2013/04/10-things-to-do-after-installing-ubuntu-13-04)

> Just open the *Software Sources *app via the Dash (or through *System Settings*) and click the *&#8216;Additional Drivers*&#8216; tab to see what&#8217;s available for your device.

---

### Post by philinux on 2013-11-04
> **wolfen10862 said:**
> Thank you very much. 
as for teaching me how to fish, please teach me instead of handing me a fish :) I'm 50 years old and I am under the asumtion that he who dies with the most knowledge wins, and I have plenty of room left in my brain to learn :)

Oh btw the link you gave me just got bookmarked

as with all things, things change and that link has out of date info in relation to the latest ubuntu versions.

I've also edited the title of the thread to make it more meaningful.

---

### Post by wolfen10862 on 2013-11-04
LOL, I did 9 of those things so far, all that's left is to spread the word.

---

### Post by grahammechanical on 2013-11-04
When you installed Ubuntu did you tick the box labelled Install Third Party Software? If you did that then Ubuntu installed the most applicable proprietary video driver for you. In your case that would have been a Nvidia driver. If we do not tick that box we get the Open Source video driver installed. It is called Nouveau. I find it suitable. The very latest proprietary video driver may have some benefit for the very latest video cards. That is not the 8400GS, is it? I used to have one. I now have a GT 220 and I am using Nouveau with it.

---

### Post by wolfen10862 on 2013-11-04
Yes I did click the third party software box. I also clicked updates too. It may very well be the fame in trying to play. The fame us called World of Tanks, and its for windows, andvsinxe everything else seems to work. I'm going to try a different game and see what happens.  I might very well have everything right because the minuter IS plugged into the video card with a HDMI cable.

---

