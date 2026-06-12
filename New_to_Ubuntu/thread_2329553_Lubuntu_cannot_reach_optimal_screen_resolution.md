---
title: "Lubuntu cannot reach optimal screen resolution?"
date: 2016-07-03
forum: New to Ubuntu
---

### Post by timesandwich on 2016-07-03
I recently came across an orphaned Samsung NC10 and started working on it (1.6Ghz Atom with 2GB RAM and a 60GB SSD).  The display is (allegedly) a 1024x600 LCD with a 60 hertz refresh rate.  It's driven by an Intel 945 Express.  I installed Windows 10 and it runs at the appropriate resolution, and all the hardware reports in correctly against the manufacturer's spec above.


I then installed Lubuntu (so good) but cannot get it to display at the 1024x600 correct resolution.  It looks pretty derpy on a wide-format screen.


I've tried using xrandr to add the correct resolution as a mode, as in [this thread]("http://askubuntu.com/questions/189246/how-set-my-monitor-resolution"), but I got several unexpected gamma errors (although it sounds like they're [not a problem]("http://askubuntu.com/questions/441040/failed-to-get-size-of-gamma-for-output-default-when-trying-to-add-new-screen-res")?) and the computer doesn't do anything:


    ```
alex@dongle:~$ cvt 1024 600 60
    # 1024x600 59.85 Hz (CVT) hsync: 37.35 kHz; pclk: 49.00 MHz
    Modeline "1024x600_60.00"   49.00  1024 1072 1168 1312  600 603 613 624 -hsync +vsync
    alex@dongle:~$ xrandr --newmode "1024x600_60.00"   49.00  1024 1072 1168 1312  600 603 613 624 -hsync +vsync
    xrandr: Failed to get size of gamma for output default
    alex@dongle:~$ xrandr --verbose
    xrandr: Failed to get size of gamma for output default
    Screen 0: minimum 800 x 600, current 800 x 600, maximum 800 x 600
    default connected 800x600+0+0 (0x26f) normal (normal) 0mm x 0mm
        Identifier: 0x26e
        Timestamp:  18212
        Subpixel:   unknown
        Clones:    
        CRTC:       0
        CRTCs:      0
        Transform:  1.000000 0.000000 0.000000
                    0.000000 1.000000 0.000000
                    0.000000 0.000000 1.000000
                   filter: 
      800x600 (0x26f) 36.000MHz *current
            h: width   800 start    0 end    0 total  800 skew    0 clock  45.00KHz
            v: height  600 start    0 end    0 total  600           clock  75.00Hz
      1024x600_60.00 (0x289) 49.000MHz -HSync +VSync
            h: width  1024 start 1072 end 1168 total 1312 skew    0 clock  37.35KHz
            v: height  600 start  603 end  613 total  624           clock  59.85Hz
    alex@dongle:~$ xrandr --addmode default "1024x600_60.00"
    xrandr: Failed to get size of gamma for output default
    alex@dongle:~$ xrandr --output default --mode "1024x600_60.00"
    xrandr: Failed to get size of gamma for output default
    xrandr: screen cannot be larger than 800x600 (desired size 1024x600)

```

Interestingly, if I go to Display Settings I can see the new mode, but selecting and applying it doesn't do anything.


Earlier I noticed that the screen has a min, current, and max of 800x600.  So I lifted the [xorg.conf file for the NC10 from here]("https://help.ubuntu.com/community/NC10") and then followed [this process]("https://wiki.archlinux.org/index.php/xrandr#Resolution_lower_than_expected") in order to add a virtual screen at 1024x600 @ 60hz to increase it, but when I reboot the machine it goes to a black screen (Ctrl+Alt+F1 console is available to revert).  Here's what that looked like:


```
    Section "Screen"
        ...
        SubSection "Display"
                Virtual 1024 600
        EndSubSection
    EndSection

```

I'm pretty well at my wit's end.  Any other ideas on how to get this laptop to detect the true screen resolution?

---

### Post by sudodus on 2016-07-03
Welcome to the Ubuntu Forums :-)

Have you tried to install this program package with drivers for Intel?

[code]sudo apt-get install xserver-xorg-video-intel[/url]

It helps with some Intel graphics chips (after reboot).

---

