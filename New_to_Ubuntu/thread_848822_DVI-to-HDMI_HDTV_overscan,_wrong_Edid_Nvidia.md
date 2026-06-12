---
title: "DVI-to-HDMI HDTV overscan, wrong Edid Nvidia"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by ZabiGG on 2008-07-03
Hi :)

I wasn't sure where this should be posted, so I figured this was the best place to get the most replies.

After experiencing loads of problems with an ATI 2600HD Pro, I bought an Nvidia 8800 GT which solved all those problems, but created two new ones:

overscan (I'd say at least 5% all around, cause I can only see 2-3 pixels of the bottom or top of the panels, and the side edges are missing).

From hours of research here and on the Web, I understand it's caused by bad EDID detection, which is confirmed by the fact that the ATI card detected many different resolutions and refresh rates that the Nvidia fails to detect, and did not overscan. The HDTV is connected on main dvi to HDMI. System is 64-bit AMD.

Results from the /var/log/Xorg.0.log files from both cards are attached.

The NVidia now only gives me these modes:

   1920x1080      50.0*    51.0  
   1440x480       52.0  
   1280x720       53.0     54.0  
   800x600        55.0  
   720x480        56.0     57.0  
   640x480        58.0     59.0  
   400x300        60.0  
   320x240        61.0

Which actually don't compute with the ATI ones at all (1920x1080@30 instead of 50 for instance).

When I set all EDID checks to false, the NVidia card still resets to 1920x1080 even when I enter a list of correct and complete modelines (using the gtf method described [here]("http://wiki.debian.org/XStrikeForce/HowToRandR12")) in Xorg, and the log states that those modes are invalid.

I understand that it might be possible to correct the overscan and lacking resolutions problem -- which is an issue since I work at least 10 hours a day with this screen and NEED the marvelous 1680x1050@60 resolution I used to get with the ATI since 1920x1080 is just too small for my older thirtysomething eyes.

Is there a user-friendly way to create a custom edid.bin file from the hex ATI values listed in my old Xorg.0.log file?

I know there are fixes for this in Vista and XP, but I couldn't find anything I could understand for linux. The few pages I found were hex talk for hex knowledgeable people, which I am absolutely not... yet ;)

Thanks!

Z.

---

### Post by ZabiGG on 2008-07-05
After an endless series of tests with custom modelines and trying to disable edid detection, I came to the conclusion that the Nvidia driver is just plainly THICK. From the var/log/Xorg.0.log files, it became obvious that it simply won't budge from its internal edid settings, period.

I managed to open the edid file to find the hex was exactly the same as with the ATI, just not interpreted the same way by the card driver. I'm sure there is a way to change those values, by I couldn't find information on which sets of hex data apply to which aspects of the display.

Of course, since the card is an 8800, there is no overscan setting in the Nvidia control panel.

So I'll have to live with either the tiny or huge resolutions (there's no middle ground) and overscan.

A workaround while I wait for Nvidia to solve this issue (and I'm clearly not the only one with this problem, from the number of unsolved queries all over the Web)) would be to find a panel that includes a system tray (or taskbar, if you will) that can be sized and moved anywhere else than on the edges of the display), since only 3 pixels of the gnome panel are currently visible due to the overscanning.

Pointers, anyone?

Z.

---

### Post by ZabiGG on 2008-07-06
Well, 

I've at least found a workaround to offset the gnome panel and make it visible notwithstanding the overscan. 

[B]Changing offset values in gconf-editor

[/B]- ALT-F2 to open a command line, enter gconf-editor
- In the editor: Apps > Panel > Top levels > top_panel_screen_0 (if hdtv is main, 1 if secondary)
- In the window on the right, 
     set x to 50 (or whichever value compensates for the overscan)
     set y to 50 (or whichever value compensates for the overscan)

x and y are the absolute position axes of the display.

You may also choose to centre the panel horizontally or vertically, but this is a matter of taste.

Make sure the panel is not set to "expand" in the panel properties, or you will lose the right-hand edge to overscanning.

It's a good idea to choose "Show hide buttons" (arrows) in the panel properties to be able to make the panel disappear if it gets in the way.

If you use compiz, it is also possible to create window rules to define how your windows should maximize and offset accordingly. There is a guide [here.]("http://http://wiki.compiz-fusion.org/WindowMatching") There is a forum thread [here]("http://forum.compiz-fusion.org/showthread.php?t=1768") also.

Hope this help anyone.

Z.

---

### Post by Zimmer on 2008-08-31
[http://ubuntuforums.org/showthread.php?t=884211](http://ubuntuforums.org/showthread.php?t=884211)
This may help,
 I just wish I could find something similar to solve my monitor issues with an ATI Radeon 9600 and Acer AL1511. Can get right resolutions with a custom xorg.conf providing I use a VGA extension lead that prevents the EDID info being read!! 
If I plug the monitor directly into the card socket incorrect EDID data is produced and I am in low res hell!

---

