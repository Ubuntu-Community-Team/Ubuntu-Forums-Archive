---
title: "nVidia driver installed correctly, but I cannot get correct resolution (8.10)"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by akiratheoni on 2008-10-31
I have an nVidia Geforce 9500 GT with Ubuntu 8.10.

The nVidia driver was able to install correctly but I did some screwing around and ended up installing the driver from the website ([http://www.nvidia.com](http://www.nvidia.com)), which got rid of the nVidia configuration GUI from System -> Administration... not sure how to add it back.

I can enable Compiz and get the wobbly windows but my resolution is stuck at 1024x768 rather than 1680x1050. Any idea how to get it to 1680x1050? Thanks.

---

### Post by eternalnewbee on 2008-10-31
You could try in: Main Menu> System > Preferences > Screen Resolution.
Hope this helps.
_____________________________
Ubuntu Release 8.10 (intrepid)
Kernel Linux 2.6.7-7
GNOME 2.24.1
AMD Athlon(tm) XP 899.219 MHz 256 KB
GeForce 7300 GT

---

### Post by starcannon on 2008-10-31
Then nvidia.com driver puts the gui in Applications>System Tools.
If you want the changes to be permanent, then:

Alt-F2
gksu nvidia-settings

Make your adjustments and choose the "Save to X configuration file"

If all else fails you can use a modeline generator like this one:
[http://xtiming.sourceforge.net/cgi-bin/xtiming.pl](http://xtiming.sourceforge.net/cgi-bin/xtiming.pl)

And manually add the mode to the xorg.conf

GL and have fun.

---

### Post by akiratheoni on 2008-10-31
> **eternalnewbee said:**
> You could try in: Main Menu> System > Preferences > Screen Resolution.
Hope this helps.


Already did that, it didn't work. 1680x1050 didn't show up at all at some points and when 1680x1050 showed up, the monitor wasn't set at that resolution.

> **starcannon said:**
> Then nvidia.com driver puts the gui in Applications>System Tools.
If you want the changes to be permanent, then:

Alt-F2
gksu nvidia-settings

Make your adjustments and choose the "Save to X configuration file"

If all else fails you can use a modeline generator like this one:
[http://xtiming.sourceforge.net/cgi-bin/xtiming.pl](http://xtiming.sourceforge.net/cgi-bin/xtiming.pl)

And manually add the mode to the xorg.conf

GL and have fun.

I added the modeline to my /etc/X11/xorg.conf then it gave me an error (I probably did it wrong). Then I removed it, ran the sudo nvidia-xconfig and now I get an "Out of Range" error for my monitor, so now I'm on Vista right now.

Help... I'm getting so frustrated about this, Hardy played so nicely with my nvidia card, but Intrepid isn't... I've ALWAYS had screen resolution problems with EVERY Ubuntu release and now it's starting to bug me. Hardy and Gutsy took five seconds to fix, though (that might've been because I was using an integrated card then, before I got my nVidia Geforce 9500 GT). I heard though that the new Xorg had issues with ATI and nVidia but that was during the Intrepid release candidate; I installed the RC originally but since then I've updated to the final version.

---

### Post by starcannon on 2008-10-31
Please post your currently broken xorg.conf along with the modeline you created using the generator, and I'll help you put it together correctly (this assumes the generator spat out the correct modeline, the one I linked has never let me down yet).

I'll keep checking back kon this thread.

GL and keep smiling, half the point is having fun, I forget what the other half is, so I don't worry about it.

---

### Post by akiratheoni on 2008-10-31
Ok my xorg.conf is attached. I had to rename it to xorg.conf.txt to let me upload it though. I can't copy and paste it because I'm in Vista right now because I don't have a GUI in Ubuntu. I had to copy my xorg.conf onto an external hard drive. When I opened up the xorg.conf with Notepad, it screwed up the formatting. Hopefully it won't be screwed up for you.

Thanks.

If I were to install a clean Hardy over Intrepid, then get my resolution problem solved, then upgrade to Intrepid, do you think it would fix the problem? Or would the newer Xorg conflict with it and stop working?

Here is the modeline:

```
Modeline "1680x1050@0" 0.00 1680 1712 1712 1744 1050 1076 1076 1103
```

---

### Post by lH)4~mK0e on 2008-10-31
Usually the nvidia-settings command will make a backup of your previous xorg.conf file (xorg.conf.backup or something similar).  If you are comfortable with the terminal (use Ctrl + Alt + F1) you can:

```

sudo cp /etc/X11/<insert xorg.conf.backup here> /etc/X11/xorg.conf

```

This will revert back to your previous settings.  Then when you restart (Ctrl + Alt + Del is easiest) you should be back into X under 1024x768.

When you make it back to your desktop do the **sudo nvidia-settings** from the terminal application and when you are configuring your resolution and refresh rate, manually enter your refresh rate and resolution.  This will force the xorg.conf to use the resolution and refresh rate you specified.  If you don't have any immediate desire to use dual monitors, or your card does not support it you can:

```

sudo gedit /etc/X11/xorg.conf

```

and look for the entry for Section "Screen"

Add the option:

```

Option   "DynamicTwinView" "0"

```

and that should allow you to accurately specify the resolution and refresh rate through the normal Ubuntu application (System --> Preferences --> Screen Resolution).

---

### Post by akiratheoni on 2008-10-31
Okay thanks I was able to get my GUI back.

I did what you said and the nVidia settings and the Screens & Resolutions option SAYS it's 1680x1050. It "sort of" is at 1680x1050. It's as though the 1680x1050 was too big for the desktop and I'm zoomed in like really far and I have to navigate the desktop by moving my cursor around the edges. I'm not sure if that makes any sense.

Also if it matters, if I hit the OSD button on my monitor, it will show me the options and also tell me the resolution of the screen; in this case, it says it's 1024x768. So I have both a 1024x768 and a 1680x1050 desktop at the same time. I think it might be only DISPLAYING 1024x768. To access the rest of the desktop, I have to move my cursor around the edges of the desktop and the screen moves along.

I guess it's important to note as well that this is as far as I got before I posted for help here. Thanks though, I was able to recover my GUI -- I was about to tear my hair out if I didn't get it working. I'll be off to bed soon so I won't respond for awhile because I'll be out all day tomorrow.

---

### Post by starcannon on 2008-10-31
Okay using the Modeline you posted here is your xorg.conf; however, if you have problems with this, you may want to do the modeline generator again, this time setting refresh rate to 60, you left it at 0. You should be able to see from this post where to put it and which subsection to alter as well.
```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder63)  Wed Oct  1 15:09:35 PDT 2008


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       30.0 - 110.0
    VertRefresh     50.0 - 150.0
    Option         "DPMS"
    Modeline "1680x1050@0" 0.00 1680 1712 1712 1744 1050 1076 1076 1103
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1680x1050@0"
        Virtual    1680 1050
    EndSubSection
EndSection
 
```
GL and have fun.

---

### Post by lH)4~mK0e on 2008-10-31
Under Section "Screen"

Change:

Virtual    1680 1050

To:

#Virtual    1680 1050

and Ctrl + Alt + Backspace

Please Note:  Consult your monitor's documentation to be sure that your monitor is capable of this resolution before attempting to perform this fix.  Serious consequences could result from not verifying that your monitor can handle this.  I would also try the suggestion in the previous post beforehand and maybe change the 0 directly in the xorg.conf file to 60 just to verify that you can view it properly before adjusting the refresh rate manually in the nvidia-settings program.

---

### Post by wonderbriefs on 2008-10-31
I'm having the same problem, but none of this helps.

I have an nVidia 8600 graphics card and use an Akai HDTV with native resolution of 1366x768 at 60 Hz. Windows Vista works just fine in 1366x768. When I used to use 7.04 after a lot of tweaking I eventually got Ubuntu working in 1360x768; close enough. But 8.10 won't give me a higher res than 1024x768.

I installed the nVidia driver just fine. All the advanced desktop effects work just fine. 

I ALT-F2 then gsku nvidia-settings, then select 1360x768 from the drop-down box and hit apply.

My HDTV stays in 1024x768 while the desktop then stretches off screen. 

I then edit my xorg.conf with sudo nano /etc/X11/xorg.conf and find that there is no "Virtual" setting under "Screen" and adding one makes no difference.

Adding a modeline usually kills X.

HELP!

---

### Post by wonderbriefs on 2008-10-31
UPDATE:

This was really bizarre. My problem was solved, but seemingly out of nowhere. Here's what I did.

I rebooted my system, and when it loaded, it was back in it's regular stretched-out 1024x768 resolution.

Alt-F2 -> gksudo nvidia-settings -> 1360x768 refresh 60 hz -> Save to X

I now once again had a desktop size of 1360x768, while the monitor was still only displaying 1024x768

Then just for kicks I decided to look at X. sudo nano /etc/X11/xorg.conf

Didn't see anything out of the ordinary. Not even any modelines. In fact, it was about as bare as I've ever seen an X config.
> Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        DefaultDepth    24
        EndSection

Section "Module"
        Load    "glx"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver  "nvidia"
        Option  "NoLogo"        "True"
EndSection


Then I decided to look at my nvidia settings again. Alt-F2 -> gksu nvidia-settings -> resoultion 1360x768 
BUT HERE'S THE KICKER: I now had two refresh rates to choose from. "60 hz (1)" and "60 hz (2)"
So I select "60 hz (2)" and hit apply.

Suddenly, my TV snaps into 1280x720. This isn't the 1366x768 O needed, but it will do.
This solution was far from elegant. Anyone else have a similar experience?

---

### Post by akiratheoni on 2008-11-01
> **starcannon said:**
> Okay using the Modeline you posted here is your xorg.conf; however, if you have problems with this, you may want to do the modeline generator again, this time setting refresh rate to 60, you left it at 0. You should be able to see from this post where to put it and which subsection to alter as well.
```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder63)  Wed Oct  1 15:09:35 PDT 2008


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       30.0 - 110.0
    VertRefresh     50.0 - 150.0
    Option         "DPMS"
    Modeline "1680x1050@0" 0.00 1680 1712 1712 1744 1050 1076 1076 1103
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1680x1050@0"
        Virtual    1680 1050
    EndSubSection
EndSection
 
```
GL and have fun.

I added that and changed the refresh rate to 60, but I still got an 'out of range' error. I'm pretty sure my monitor can handle it because I'm currently running Vista at 1680x1050 and I've run previous versions of Ubuntu at 1680x1050. Thanks for the help. Maybe I'll re-install Ubuntu 8.10 sometime and start completely over... maybe that'll do something.

---

### Post by akiratheoni on 2008-11-01
Weirdest freaking thing happened. Well, two. 1.) Ubuntuforums.org no longer shows images. Whatever.

2.) This:
[http://upload.zantherus.com/files/8zh2yd1m7l6hu6h1qmwh.png](http://upload.zantherus.com/files/8zh2yd1m7l6hu6h1qmwh.png)

For the record, I downloaded the final 8.10 and burned it and installed it over my 8.10 RC (which was updated to the final version, so it really shouldn't have mattered). Same issues as before, except now this is happening. I changed the screen resolution under the nVidia X Server Settings, then I changed the screen resolution under System -> Preferences -> Screen Resolution and now it's like that. If I change the screen resolution under the nVidia X Server Settings, then the problem in the screenshot I posted goes away. 

I REALLY want to fix this problem. Every resolution freaking works except the one that I really, really need. I'm starting to hate Ubuntu for the very first time, I thought if Hardy could easily adjust to my new graphics card, Intrepid should. I don't like using old versions so I might install Hardy, then fix everything there, then upgrade to Intrepid and hope it stays. 

Ug. Help, please.

---

### Post by akiratheoni on 2008-11-02
Bump, I'm using Vista right now and I really miss scrolling down in an unfocused window :( help! Lol.

---

### Post by jengo on 2008-11-03
im having a very similar problem with a different video card. I cant seem to be able to force my monitor into a higher refresh rate. i got the whole resolution problem worked out though. 

if you are trying to fix your resolution go look to this thread it is at the end:
[http://ubuntuforums.org/showthread.php?t=966763](http://ubuntuforums.org/showthread.php?t=966763)

but the last thing i havent fixed is this refresh rate. Any help would be appreciated, and ive tried the mode line generator but that didnt even do anything. If anyone knows how i should edit my xorg.conf file to get my resolution up it would greatly be appreciated.

---

### Post by akiratheoni on 2008-11-03
> **jengo said:**
> im having a very similar problem with a different video card. I cant seem to be able to force my monitor into a higher refresh rate. i got the whole resolution problem worked out though. 

if you are trying to fix your resolution go look to this thread it is at the end:
[http://ubuntuforums.org/showthread.php?t=966763](http://ubuntuforums.org/showthread.php?t=966763)

but the last thing i havent fixed is this refresh rate. Any help would be appreciated, and ive tried the mode line generator but that didnt even do anything. If anyone knows how i should edit my xorg.conf file to get my resolution up it would greatly be appreciated.

Thanks, that actually fixed my problem in Hardy. I think I'll back up my xorg.conf and upgrade to Intrepid and see if that fixes anything later today. Thanks again!

---

### Post by akiratheoni on 2008-11-04
I installed Hardy, fixed the resolution, then upgraded to Intrepid. Broke it. Same problem.

I think it's the nvidia-xconfig. It gives me headaches since whatever resolutions are listed in the program, those are the only resolutions I can get. If I set the panning differently, then the desktop stretches beyond the scope of the monitor.

How can I change the nvidia-xconfig to allow me to choose the resolution I want? If I run nvidia-xconfig on the command line, it sets me at an 'out of range' error on my monitor.

---

### Post by anomalous_underdog on 2008-11-22
Try using nvidia-settings instead of nvidia-xconfig. nvidia-settings is a GUI frontend that can let you preview your chosen resolutions without restarting X (its kinda like the nvidia control panel in windows).

Also, to fix your monitor resolution, try using this:
[http://xtiming.sourceforge.net/](http://xtiming.sourceforge.net/)

It will compute for you an appropriate Modeline that you can insert in your xorg.conf that could set your monitor to the desired resolution.

you'll need to know for sure what your monitor's technical specs are though

---

