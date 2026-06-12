---
title: "Linux misidentifies my graphics card + everything runs slowly"
date: 2015-08-12
forum: New to Ubuntu
---

### Post by asdfhello on 2015-08-12
I have a Radeon R9 390x but Ubuntu (And every other distro I've tried) identifies it as a 290.

Coming from Windows 7 and being on a gaming PC, I'm used to things running smoothly. My PC can max the settings on most games with good FPS. Yet simply browsing the web feels slow and unresponsive in linux. Opening a program takes several seconds. I think I've installed the proper drivers correctly, so I really can't figure out what the problem should be.

---

### Post by QIII on 2015-08-12
Hello!

Are you using the proprietary AMD driver or the default driver installed with Ubuntu?

That card is new enough that the open source developers may not have caught up to it.

---

### Post by QIII on 2015-08-12
I've had a chance to review the tech specs of the 390X, and it is essentially an overclocked 290X with double the memory and bumped memory speed running on PCIe 3.0.  So I wouldn't be terribly concerned by the "misidentification" at this point.  It's the same Hawaii GPU at heart with a massive bump in memory bandwidth.

I would be very surprized if the AMD proprietary driver does not work -- the one in the repo for your release or, if it is more recent, the one you can download from AMD.

Canonical and AMD have had a romance for a number of years now, and the fglrx driver in the Ubuntu repo is the most recent AMD driver available at release time.

---

### Post by asdfhello on 2015-08-13
This is the one, right?

[https://i.imgur.com/mMxMAMr.png](https://i.imgur.com/mMxMAMr.png)

I've tried installing, uninstalling it. There is literally no perceivable difference. Also, I can't seem to find the catalyst control center anywhere even though it should be installed(That's what marked box indicates, yes?).

EDIT: I found the control center, but there aren't really any settings that have an impact on performance.
2nd EDIT: The browser lag was fixed by... Switching to another one (Yes, I **am **embarassed to not have thought of this earlier -- I've been running firefox for years and years on windows with zero issues... But yeah...)...

Now, to prevent this pitiful thread from having been a total waste, I do have a legitimate question: How come there is no real difference between pre/post driver install? Does ubuntu come with temporary drivers or something? I'm used to booting an OS for the first time and being greeted by terrible resolution and pixels the size of houses.

---

### Post by QIII on 2015-08-13
There are plenty of settings in CCC that affect performance.

When you installed the driver, did you do

```
sudo amdconfig --adapter=all --initial 
```

before rebooting?

If we can get to where we think the driver is working properly, we can move on to adding some hardware acceleration as I have described in the driver link in my signature.

Yes, Ubuntu comes installed with the open source Radeon driver.  As I said, the open source developers may not have caught up to that card.  AMD works very hard with the dedicated open source developers, but these things take time.

If the proprietary driver for Linux does not work properly, that is on AMD, not Canonical.  OEMs write the proprietary drivers for their hardware, not Linux distributors.  That the Windows driver works is of no consequence here.  It works for Windows because AMD makes sure it does.  Windows is about 95% of the PC market.  Of course AMD expends a lot of resources on the Windows driver.

Microsoft doesn't do a thing to make Windows compatible with AMD cards.  AMD makes sure their drivers are compatible with Windows.  Neither Microsoft nor the Linux community can modify the closed-source AMD binaries.

In any case, I think this may be an issue with setup and may have little to do with the driver -- depending on your release of Ubuntu and what driver was available at the time of release.

---

### Post by buzzingrobot on 2015-08-13
As do almost all Linux distributions, Ubuntu defaults to the open source driver for the video card it detects. These offer fine 2D support. Some users find the 3D support adequate, some do not.

The machine needs to be rebooted to use a new video driver, if it has been installed correctly. The best way to install/uninstall is via Ubuntu's Additional Driver tool. Other approaches to uninstalling a video driver may be problematic due to the  complexity of the install and the need to "get it all" before trying another install.

Extreme video degradation can be due to failure to identify a card and falling back to a lowest common denominator failsafe video approach. Typically, also, resolution is far from optimal.

It's unlikely that this affected the browser. It would have looked below par, but the actual networking bits would be per usual.

---

