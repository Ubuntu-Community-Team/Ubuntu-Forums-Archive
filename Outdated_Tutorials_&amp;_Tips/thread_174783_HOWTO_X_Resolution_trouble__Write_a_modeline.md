---
title: "HOWTO: X Resolution trouble?  Write a modeline"
date: 2006-05-12
forum: Outdated Tutorials &amp; Tips
---

### Post by mattlach on 2006-05-12
Having trouble getting X to display at the resolution and refresh rate you like?

As much as I hate to rely on windows here's what I usually do when all else fails.

**WARNING:**
Double check your entries from this HOWTO.  Some older CRTs without protection circuitry can be damaged if you write the wrong modeline.  I am not responsible if you kill or damage your monitor.

Also, make sure you are familliar with editing config files from the console, cause the slightest typo in the above will likely make X refuse to start.



Anyway moving right along, windows is better at detecting screen modes than X.

Boot the computer in windows.

Install a screen management package like [Power Strip](http://www.entechtaiwan.com/util/ps.shtm).

Switch to the mode you want to use and go to the detail screen, screenshot it, and print it or transfer it somewhere you can look at it while you edit your xorg.conf  (/etc/X11/xorg.conf)

Mine looked like this:
[img]https://home.comcast.net/~mkarlsson/ubuntuforums/timings.jpg[/img]

Now we write a modeline.

```
Modeline "1920x1200@60" 153.562 1920 1968 2000 2080 1200 1203 1209 1235 +hsync -vsync
```

The first set of quotes is the name of the modeline.  You can call it whatever you want.  I used something descriptive for mine.

The first number (153.562 for me) is the dot clock of the mode.  Get this from the top left side of the powerstrip details screen.

The second number (1920 for me) is the number of horizontal active pixels from the screenshot.  The second number is the number of horizontal pixels plus the front porch.  The third number = active pixels + front porch + sync width.  Fourth number = active pixels + front porch + sync width + back porch (or the same as the total field)

Now the fifth number is the number of vertical active pixels.  Add the vertical numbers up the same way as the horizontal numbers.

The last two depend on whether the screen is synced horizontally or vertically.   This can be seen on which + or - button is checked on the left side of the screen shot.


Now this mode line goes in your xorg.conf in thre monitor section.  It will look sortof like the below:

```
Section "Monitor"
        Identifier      "Dell1920x1200"
        Option          "DPMS"
        HorizSync       30-81
        VertRefresh     56-76
        Modeline        "1920x1200@60" 153.562 1920 1968 2000 2080 1200 1203 1209 1235 +hsync -vsync
```

The HorizSync and VertRefresh are properties of your monitor as well.  These can usually be found in your manual, but I would just use the same as what xorg detected for you unless the mode you are trying to set is outside those numbers (see screenshot again) cause if it is X will give you a big fat error message.

Now you have to add the mode you defined to the list of modes used by your monitor in the Screen section.  See below:

```
Section "Screen"
        Identifier      "Dell1920x1200"
        Device          "NVIDIA Corporation NV40 [GeForce 6800 GT]"
        Monitor         "Generic Monitor"
        DefaultDepth    24

        Subsection "Display"
                Depth           8
                Modes           "1920x1200@60" "1600x1200" "1280x1024" "1280x960" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1920x1200@60" "1600x1200" "1280x1024" "1280x960" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1920x1200@60" "1600x1200" "1024x768" "800x600" "640x480"
                ViewPort        0 0
        EndSubSection
EndSection
```

If your drivers are ok, this should work.  Restart X and try it.

---

