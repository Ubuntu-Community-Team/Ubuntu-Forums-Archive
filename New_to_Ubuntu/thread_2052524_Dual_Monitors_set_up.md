---
title: "Dual Monitors set up"
date: 2012-09-03
forum: New to Ubuntu
---

### Post by cthatch on 2012-09-03
Hello,

I currently run an acer 23inch and a asus 23 inch monitors (both with the same resolution). I run a GTX 580 graphics card. When I go into the display settings it says I'm using a laptop(I'm not sure if that's the problem). Anyways how do I set up dual monitor support in Ubuntu 12.04. Also when I boot into Ubuntu the screen is shifted to the left a centimeter or so on a single monitor.

Any advice is greatly appreciated!! thanks!

---

### Post by cortman on 2012-09-03
> **cthatch said:**
> Hello,

I currently run an acer 23inch and a asus 23 inch monitors (both with the same resolution). I run a GTX 580 graphics card. When I go into the display settings it says I'm using a laptop(I'm not sure if that's the problem). Anyways how do I set up dual monitor support in Ubuntu 12.04. Also when I boot into Ubuntu the screen is shifted to the left a centimeter or so on a single monitor.

Any advice is greatly appreciated!! thanks!

You can go to System Settings > Display and adjust them there.
Or you can do it from the command line with xrandr.
This assumes your graphics card is set up correctly...

---

### Post by Bartender on 2012-09-03
Have you used the "Hardware Drivers" utility to download/install the nVidia drivers?

Once that's done, hit the Alt+F2 keys and type in:

```
gksudo nvidia-settings
```

The nVidia utility should come up.

I attached a screenie of what mine looks like.  The second tab down is the one you want, "X Server Display Configuration".  Both of your monitors (hopefully) will be detected.  

Let's see here - check to make sure you have the correct monitor chosen as "primary display for the X screen."  If everything seems OK, click on "Save to X Configuration File".  Even if you get some goofy error message, such as Default Display needs driver, go ahead and save the X configuration and close out of the nVidia utility.

In [this thread]("http://ubuntuforums.org/showthread.php?t=1967803&page=2"), I posted (#20) complaining about some problems I was having with 12.04 and dual displays.  I edited my post to include some of the fixes I came across when I did some research after posting.  Rather than doing research before posting, which is generally the better thing to do ;)

So the first step (to me anyway) is to use the nVidia utility to get xconfig set up.  

Then go back to Ubuntu to turn off sticky edges if your mouse hangs up between screens (as described in my post; just google 'ubuntu 12.04 mouse magnet') 

Use the Ubuntu Display utility to set up launcher on just one monitor if that's how you want it.

If you drag a window over to the secondary display and maximize it, does the window jump back to the main display?  As mentioned in post #20, you can install Compiz Configuration Settings, then go into it and turn on Wobbly Windows which disables Snapping Windows.  I imagine you could just turn off Snapping Windows without turning on Wobbly Windows.

There may be other fixes to that last annoyance, but using Compiz was easy and quick.

I also got the "Laptop" identification.  I don't know if there's a fix for that.  But it seems to me that the "Laptop" thingie is an annoyance, not a deal-breaker.

---

