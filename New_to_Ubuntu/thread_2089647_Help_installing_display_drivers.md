---
title: "Help installing display drivers"
date: 2012-11-29
forum: New to Ubuntu
---

### Post by Trevellyan on 2012-11-29
Ok so I've got a fresh install of the latest Ubuntu on my pc, but it's detecting the wrong monitor, I've got it hooked up to a 46" sony tv with an hdmi cable hooked up to the A75-UD4H motherboard and it's detecting a 72" sony tv.  The display works but it cuts off a bunch of the screen, I can just see the edge of the icons at the left side of the screen and I can't full screen any window because I'll lose the window conrols.

Anyways I'm trying to install the drivers for the AMD APU A8 3850 and here's what I get, I unpacked the .run file and  after clicking it the menu pops up, I select "install driver 9.002 on X.Org 6.9 or later 64-bit", then it says it had error, check the log file, which displays this:

Supported adapter detected.
Check if system has the tools required for installation.
fglrx installation requires that the system have kernel headers.  /lib/modules/3.5.0-18-generic/build/include/linux/version.h cannot be found on this system.
One or more tools required for installation cannot be found on the system. Install the required tools before installing the fglrx driver.
Optionally, run the installer with --force option to install without the tools.
Forcing install will disable AMD hardware acceleration and may make your system unstable. Not recommended.

What tools? How do I know what's missing, there's not a lot to go off here, please any help would be appreciated!

---

### Post by audiomick on 2012-11-29
Had you already tried the additional drivers facility?

On 12.10, I believe it is in the menu system settings> software. Failing that, you might be able to search for it in the search box in the dash. I can't check; this machine is still on 10.04.

You need to have a functioning internet connection for that facility to work. What it should do is go off and find the appropriate driver for your video card and install it for you.

---

### Post by Trevellyan on 2012-11-29
I tried the "Additional Drivers" option in software sources, it lists my APU Graphics card I believe: 

Advanced Micro Devices[AMD] nee ATI:BeaverCreek [Radeon 6550HD]
This device is using the recommended driver
o Using X.Org X Server - AMD/ATI display driver wrapper from xserver-xorg-video-ati(open source, tested)
o Using Video driver for the AMD graphics accelerators from fglrx(proprietary)
o Using Video driver for the AMD graphics accelerators from fglrx-updates(proprietary)

The first item is selected, should I try one of the other driver sets, if that is what they are? I'm trying the second set right now, just clicked "Apply Changes", but it's taking a while. 

Will report back with results.

---

### Post by sandyd on 2012-11-29
> **Trevellyan said:**
> I tried the "Additional Drivers" option in software sources, it lists my APU Graphics card I believe: 

Advanced Micro Devices[AMD] nee ATI:BeaverCreek [Radeon 6550HD]
This device is using the recommended driver
o Using X.Org X Server - AMD/ATI display driver wrapper from xserver-xorg-video-ati(open source, tested)
o Using Video driver for the AMD graphics accelerators from fglrx(proprietary)
o Using Video driver for the AMD graphics accelerators from fglrx-updates(proprietary)

The first item is selected, should I try one of the other driver sets, if that is what they are? I'm trying the second set right now, just clicked "Apply Changes", but it's taking a while. 

Will report back with results.
use the second one - the fglrx-updates can sometimes be problamatic.

---

### Post by Trevellyan on 2012-11-30
Thanks for clarifying sandyd, so I set up those drivers, reset, and now the screen is letterboxed,like there's a 2 inch black bar from the edge of my TV screen except now I've lost the left bar completely, weirder the mouse is locked to the screen so its like the left bar isn't even there,all I can see is desktop.

I can right click 'change desktop background' to get to the settings, but it still says I'm using a 72 inch TV, at least now ehn I go to system -> details -> graphics it actually registers something:

Driver: VESA:SUMO
Experience: Standard

No idea where to go from here

---

### Post by sandyd on 2012-11-30
> **Trevellyan said:**
> Thanks for clarifying sandyd, so I set up those drivers, reset, and now the screen is letterboxed,like there's a 2 inch black bar from the edge of my TV screen except now I've lost the left bar completely, weirder the mouse is locked to the screen so its like the left bar isn't even there,all I can see is desktop.

I can right click 'change desktop background' to get to the settings, but it still says I'm using a 72 inch TV, at least now ehn I go to system -> details -> graphics it actually registers something:

Driver: VESA:SUMO
Experience: Standard

No idea where to go from here
sounds like the resolution is incorrect and/or you need to adjust your overscan settings.

Does Alt+F2 bring up anything?

If so, type in 
```

gksu amdcccle
```

---

### Post by Trevellyan on 2012-11-30
Ok so Alt-F2 didn't work, but Ctrl-Alt-T brought up a terminal, and I tried the snippet you gave me, and it brought up the catalyst control center.  From there I found a dropdown arrow by a monitor-like image(this is by memory now, I tried a few things while I was at home at lunch, I'm back at work) and it said something about multiple displays, I changed it to single display, and that brought up the correct resolution in the resolution box below. I applied the changes then tried a reset. Nothing had changed.

I went back to the Additional drivers screen, went back to the first option, reset, got the sliver of the left bar back and got rid of the black border, but when I used that command for the Catalyst Control Center  in the terminal it didn't work. I ran out of time by then and had to get back to work.

I'll keep testing when I get home, see if I can find the right combination of options.

---

