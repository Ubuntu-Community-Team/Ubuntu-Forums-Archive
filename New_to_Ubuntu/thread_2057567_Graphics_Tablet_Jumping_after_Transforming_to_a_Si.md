---
title: "Graphics Tablet Jumping after Transforming to a Single Monitor"
date: 2012-09-13
forum: New to Ubuntu
---

### Post by Defenistrat on 2012-09-13
Hi, I'm new here.

I have just installed Ubuntu 12.04 and I have a Mousepen 8x6 and dual monitors. By default the surface area of the graphics tablet is stretched across both monitors in such a way that when I move the pen across the tablet, it moves twice as fast in the horizontal direction as it does in the vertical direction.

I followed the instructions on the first post in [this thread]("http://ubuntuforums.org/showthread.php?t=1656089") to transform the the mapping to just my right monitor, using the following command:

```
xinput set-prop "Device name" --type=float "Coordinate Transformation Matrix" 0.5 0 0.5 0 1 0 0 0 1
```

Because my device is configured twice, as I will go into more detail below, I replaced "Device name" with the id of the graphics tablet.

However, after applying this transform, whenever I press the mouse pen on the tablet, it keeps jumping quickly to the right, at seemingly random lengths all the way to the edge of the monitor and back. But it only does this after I apply the transformation matrix.

[This thread]("https://help.ubuntu.com/community/TabletSetupWizardpen#Clicking_does_weird_things_or_the_cursor_jumps") says the problem is caused by the the graphics pad being configured twice. Sure enough, when I run xinput --list, the graphics pad is listed twice. 

```
&#8627; UC-LOGIC Tablet WP8060U                 	id=8	[slave  pointer  (2)]
&#8627; UC-LOGIC Tablet WP8060U                 	id=9	[slave  pointer  (2)]
```

The above post also says:

> This happens if you define both a specific section "InputDevice" in /etc/X11/xorg.conf and have an "InputClass" in /usr/share/X11/xorg.conf.d/70-wizardpen.conf.

Comment out either of them to solve the problem.

The strange thing is, at this point I had not configured the xorg.conf at all, and I don't have 70-wizardpen.conf in the specified directory. I have since configured xorg.conf, ran the transformation on both inputs, and I have tried updating the drivers gain using this ppa: ppa:doctormo/xorg-wizardpen, however I keep getting the same results. Not only that, but I don't seem to be getting the 70-wizardpen.conf file.

I'm pretty much a complete noob at all things Linux, and I'm going to guess I am missing something really obvious, or I've done something really stupid. Does anybody have any idea what might be wrong or know of any other resources I can use to try to solve this?

Thanks!

---

### Post by Favux on 2012-09-14
Hi Defenistrat,

Welcome to Ubuntu forums!


You're the second person to report a problem with the CTM and the evdev driver.  I seem to be seeing it too.  See [this thread]("http://forums.linuxmint.com/viewtopic.php?f=49&t=111890").  Does that seem to describe what you are seeing?

Maybe this "bug" is new?  With the Precise evdev?

That WizardPen wiki may be a little misleading.  If you look at the compatibility table on the DIGI*mend* site:  [http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_support_status](http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_support_status)  and then click on [UC-Logic Tablet WP8060U]("http://sourceforge.net/apps/mediawiki/digimend/index.php?title=UC-Logic_Tablet_WP8060U")  you see that your tablet can come with a mouse.  So there should be two entries in **xinput list**.  One for the tablet pen and the other for the tablet mouse.  It is just that the WizardPen driver never supported the mouse and so having a mouse available just confused it.  What Nick is doing on the DIGI*mend* site is fixing the tablet's usb descriptors in the usb HID part of the kernel.  In other works getting the kernel driver part of the tablet driver working correctly.  Then evdev, the X part of the tablet driver, should pick up the tablet automatically.  But the usb descriptor doesn't allow an easy wasy to say:
```
&#8627; UC-LOGIC Tablet WP8060U Pen                	id=8	[slave  pointer  (2)]
&#8627; UC-LOGIC Tablet WP8060U Mouse                	id=9	[slave  pointer  (2)]
```
Which is what is needed by some applications, not to mention clearing up everyone's confusion.  Still trying to figure out what to do for that.

---

### Post by Defenistrat on 2012-09-16
Hi Favux,

Thanks for the reply, you have cleared up a lot of questions for me.

Concerning the behavior of my cursor when using the bad, I would say mine is a little bit different. Where the poster explained that his "second cursor" moved in the opposite direction at a 45 degree angle, my cursor seems to jump around only when I press down on the pad with the pen, and only if I am not moving it. I've also noticed, after looking at it for some more time, that it doesn't look like it's being drawn randomly to the side, but rather looks like it very quickly moves to the point halfway between the right side of my right monitor and my current cursor location, then halfway from that point to the right, then half way from that point to the right, and all the way to the far right of the screen.

Also, I'm still not seeing the /usr/share/X11/xorg.conf.d/70-wizardpen.conf file. I'm guessing this could be part of the issue, but despite updating the drivers through the ppa, I am still not getting it. Has this file changed to something else, maybe?

---

### Post by Favux on 2012-09-18
Hi Defenistrat,

I don't think the PPA has a WizardPen for Precise.  It should be throwing up some sort of error message for you.  Anyway that is why you aren't seeing a 70-wizardpen.conf.  Neither it nor the WizardPen driver are being installed.

OK, I finally remembered some more about the dancing cursor bug with CTM on xf86-input-evdev.  In other words I already knew about it and spaced it.  Guess I had it mentally filed under Arch, oh well.  I explain it in more detail on this post:  [http://ubuntuforums.org/showpost.php?p=12245337&postcount=53](http://ubuntuforums.org/showpost.php?p=12245337&postcount=53)

---

