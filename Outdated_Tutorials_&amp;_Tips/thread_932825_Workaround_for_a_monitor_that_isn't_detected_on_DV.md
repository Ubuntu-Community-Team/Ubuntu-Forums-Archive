---
title: "Workaround for a monitor that isn't detected on DVI"
date: 2008-09-28
forum: Outdated Tutorials &amp; Tips
---

### Post by overridex on 2008-09-28
[SIZE="4"]Introduction[/SIZE]

Ok.  First off this is not necessarily Ubuntu-specific, however Ubuntu is what I'm running and this particular workaround deals with specifically Linux, although it could be adapted to work on other OS's.

I also don't know if anyone will actually read and use this, but if you do please reply!  I'd be interested to know if anyone else runs into a similar situation.  I'm putting this out there because I was unable to find any solution anywhere else, aside from replacing the monitor.

[SIZE="4"]Back story and the Problem[/SIZE]

I've had a Viewsonic VX2025w for a few years now, using DVI, and have had no problems with it.  I wanted to get a second and setup Twinview, so I purchased a second of the same model refurbished.

The problem is, when I received it, it works fine on D-Sub, but when connected via DVI the monitor never comes out of standby.  I tried different cables, ports, etc. to no avail.  Some searches found that this has happened to others, especially with this monitor:

[http://www.munky.net/hardware/viewsonic-dvi/](http://www.munky.net/hardware/viewsonic-dvi/)
[http://www.tomshardware.com/forum/185719-33-6600-viewsonic-vx2025wm-monitor](http://www.tomshardware.com/forum/185719-33-6600-viewsonic-vx2025wm-monitor)

After trying all the steps and the DVI recover program listed in those pages, I still had no DVI signal.  Others that had this issue seem to have had to replace the monitor, it was pretty frustrating.

[SIZE="4"]The Solution[/SIZE]

The reason the monitor is not detected has something to do with the EDID as mentioned in the other posts, mine doesn't appear to send it at all when connected via DVI.  But, with some Nvidia options in xorg.conf and my good monitor, I was able to workaround it:


**1. Download the EDID from the good monitor:**

```
sudo apt-get install nvidia-settings
```

Once you've installed nvidia-settings, run it, click on your good display under your GPU, then click Acquire EDID and save it to a file.

**2. Edit /etc/X11/xorg.conf**

Add the following options to your xorg.conf file, assuming EDID file you saved is located at /etc/X11/edid-dvi.bin:

```
Option         "ConnectedMonitor" "DFP-0, DFP-1"
Option         "CustomEDID" "DFP-1:/etc/X11/edid-dvi.bin"
```

In my case, my "Screen" section of xorg.conf looks like this:

```
Section "Screen"
 
Identifier     "Screen0"
Device         "Videocard0"
Monitor        "Monitor0"
DefaultDepth    24
Option         "ConnectedMonitor" "DFP-0, DFP-1"
Option         "TwinView" "1"
Option         "TwinViewXineramaInfoOrder" "DFP-0"
Option         "CustomEDID" "DFP-1:/etc/X11/edid-dvi.bin"
Option         "metamodes" "DFP-0: nvidia-auto-select +0+0, DFP-1: nvidia-auto-select +1680+0"
EndSection

```

**3. Restart X**

```
sudo /etc/init.d/gdm restart
```

[SIZE="4"]Conclusion[/SIZE]

While this is a pretty specific situation, hopefully if anyone else runs into the same problem they find this and don't have to spend frustrating hours getting nowhere like I did.

I'm attaching my EDID bin file in case you have the same monitor and don't have a good one to download it from.  Obviously, don't use this EDID if you don't have this same model monitor.

---

### Post by Karpah on 2008-10-29
(sorry to bump a rather old thread but...)

Ah! This post is exactly what I've been looking for! Not quite the info itself, but the EDID attached at the bottom!

I'm using a ViewSonic VX2235w, and while it isn't exactly the same model as yours, Xorg is quite happy to use the same EDID and provide me with all the missing resolutions. Finally, a proper resolution on my 22", I was having a hell of a time getting past 1024x768 >_<

---

