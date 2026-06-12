---
title: "Video hookup to Projecter Doesn't Work - Looks almost like Dual Screen"
date: 2013-05-13
forum: New to Ubuntu
---

### Post by GregA on 2013-05-13
Hi, 

On Saturday, I installed Kubuntu 13.4 on an HP Laptop (tx1210us).  Laptop specs include nvidia GeForce 6150 , 2gb ddr2 ram.   We wanted to show our club completed install, and while the laptop display looked fine, the wall-screen showing the projector image looked like the lappie was thinking the hookup was a dual monitor.   As a result, I couldn't display the actual screen I was seeing on the laptop, or any of the panel at bottom, etc.  If you saw the mouse pointer on the screen, it disappeared from the laptop screen.

I did install the video drivers (304.88 for NV Control v1.28), using the ubuntu drivers search/install process (jockey-qt).   The driver shows active but not running.  Also, I don't see any options in the NVIDIA control program that looks like a way to control dual screens or overhead projectors.   We were hooked up using standard media port (not hdmi).

Any tips to handle this - at the next monthly meeting, I'd like to demonsrate the install to our comp. club.

Thanks.

---

### Post by SeijiSensei on 2013-05-14
Did you set the laptop's screen resolution to something the projector can support?  A lot of projectors don't go beyond 800x600 or 1024x768.

---

### Post by GregA on 2013-05-14
I don't have the exact resolution handy, but the laptop has the standard 1280 x 800 WXGA display.   The projector is a pretty good Epson model, and seems to support 1280 x 800 on my Acer Timeline running Kubuntu Precise, and other hardware running Win 7 etc.  I think it has something to do with the nVidia drivers,  but haven't figured it out yet.  What I need to zero in on (I believe) is the process to select single display output versus twin display output.

---

### Post by SeijiSensei on 2013-05-15
What do you mean by "the driver shows active but not running?"  If you run "lsmod | grep -i nvidia" in a terminal, does it show that the NVIDIA kernel module is loaded?  Can you run the NVIDIA control panel application?

Did you install the driver from the Additional Drivers application?  (I think that is equivalent to running jockey.)

I have a ASUS 1201n with an NVIDIA card that I connected to a projector, and it "just worked."  The display appeared on both the screen and the projector.

---

### Post by GregA on 2013-05-15
OK, here's more info.
>   The "Additional Drivers Window" displays the following when the nvidia 304 update is selected (clicked on):  "This driver is activated but not currently in use"
>   lsmod | grep -i nvidia shows "nvidia          10287292  33"
>   The driver was installed via the "Additional Drivers" application
>   Yes, I can start and run the Nvidia Control Panel aka Nvidia X Server Setting application.  The driver version is 304.88, the display is set to 1280 x 800 for a single flat panel display (DFP-0), the Screens setting shows "1"

I wonder if the overhead functionality wasn't working because I was still in the process of installing the drivers - maybe they hadn't fully downloaded and installed.   Next month, we'll have another chance to do the hook up and see if working.   On my personal laptops, I have Intel graphics and they just work perfectly with the projector display device.

If as expected, we retest next month, I'll update this thread.   Thanks much for the tips.

Greg

---

