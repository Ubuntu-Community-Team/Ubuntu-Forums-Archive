---
title: "Multiple Montors - Intel 900 - Extend Desktop"
date: 2008-07-30
forum: New to Ubuntu
---

### Post by JoneYee on 2008-07-30
Ok, this is my last hurdle for my primary workstation setup.

I am running on a HP 1331se Laptop with an Intel 900 Integrated Graphic Controller.

I am trying to determine how to extend the desktop (working space) across the two monitors.  

I have read the information contain here: [http://sernaonubuntu.wikidot.com/multiple-monitors](http://sernaonubuntu.wikidot.com/multiple-monitors)
and have been unsuccessful, for one major reason.  When I look at my xorg.conf where you would expect to see devices listed as such:

```
Section "Device"
    Identifier    "NAME YOU'RE GIVING THE CARD"
    Driver        "DRIVER"
    BusID        "BUS LOCATION"
    Option        "OPTION" "OPTION VALUE"
    Screen        NUMBER OF THE MONITOR, STARTING AT 0
EndSection

```

I only see:
```
Section "Device"
Identifier "Configured Video Device"
EndSection
```

This is a laptop, trying to use the laptop monitor as the primary display and a 19 inch Westinghouse LCD as the extended display.  

Ubuntu 8.04 is recognizing the other monitor and I am able to mirror output to it natively in System-> Screen Resolution.


I know this is not the easiest of things to do in Linux, or in Ubuntu, but any help, direction, references or insight would be appreciated.

Also, I am not in front of this machine at the moment (at work) so any additional requests for terminal command results will be delayed by about 3 hours.

---

### Post by JoneYee on 2008-07-31
**waves his arms feverishly**

unanswered thread =P

just a bump... any takers?  I didn't figure anyone would be eager on this one.

---

### Post by overdrank on 2008-07-31
HI and I have a laptop with the intel graphics and have tried setting up the extended desktop but with not much luck. You may try and use 
```
gksu displayconfig-gtk
``` and see if the monitor is detected. I am off the next two day and I will take a look some more.

---

### Post by JoneYee on 2008-07-31
> **overdrank said:**
> HI and I have a laptop with the intel graphics and have tried setting up the extended desktop but with not much luck. You may try and use 
```
gksu displayconfig-gtk
``` and see if the monitor is detected. I am off the next two day and I will take a look some more.

The monitor is detected, I can mirror desktop to it.  

output of gksu displayconfig-gtk:  detected there as well.

---

### Post by skajoeska on 2008-08-20
bump

----------------
Now playing: [The Sex Pistols - Pretty Vacant (Album Version)](http://www.foxytunes.com/artist/the+sex+pistols/track/pretty+vacant+(album+version))
via [FoxyTunes](http://www.foxytunes.com/signatunes/)

---

### Post by freezman on 2008-10-10
Hi folks,

I'm a newbie to Linux also, it means spending evenings on googling for so simple stuff as force Ubuntu to work on two monitors.

This one worked for me on Ubuntu Hardy Heron 8.04 on laptop HP NC 4400 with connected DELL LCD. NC 4400 has Mobile Intel 945GM Express Chipset with screen resolution 1024x768.

Screen resolutions:
Laptop screen: 1024x768
DELL LCD: 1440x900

All the stuff can be configured simply in 3 steps:
[LIST=1]
[*]modify the xorg.conf
[*]reload the X
[*]run xrandr
[/LIST]

**1. modify the xorg.conf**.
*!!!do not forget to make a backup file!!!*
[LIST]
[*]run Aplications - Accessories - Terminal
[*]type: sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
[/LIST]
in the case you need to revert to the original file simply overwrite the xorg.conf by copying the backup file back
[LIST]
[*]type: sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
[/LIST]


Configuration of xorg.conf:

Original lines


```

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

```

changed to

```
Section "Monitor"
	Identifier	"Laptop LCD"
EndSection

Section "Monitor"
	Identifier	"DELL LCD"
	Option		"RightOf"	"Laptop LCD"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"DELL LCD"
	Device		"Configured Video Device"
	DefaultDepth    24
	SubSection      "Display"
		Depth   24
		Virtual 2464 900
        EndSubSection

EndSection

```

the value 2464 in the line *Virtual 2464 900* is sum of horizontal values 1024 and 1440 of my two monitors and the vertical I left the higher 900.


**2. reload X**

I reload the X by pressing <Ctrl<Alt><BkSpc>. Have to logon again.


**3. xrandr command**
[LIST]
[*]run Apllications - Accessories - Terminal
[*]type: xrandr
[/LIST]

```
laptop:~$ xrandr
Screen 0: minimum 320 x 200, current 2464 x 900, maximum 2464 x 900
VGA connected 1440x900+0+0 (normal left inverted right x axis y axis) 408mm x 255mm
   1440x900       59.9*+   75.0     59.9  
   1152x864       75.0     74.8  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     66.7     60.0  
   720x400        70.1  
LVDS connected 1024x768+0+0 (normal left inverted right x axis y axis) 246mm x 184mm
   1024x768       60.0*+
   800x600        60.3  
   640x480        59.9  
TMDS-1 disconnected (normal left inverted right x axis y axis)
TV disconnected (normal left inverted right x axis y axis)

```

[LIST]
[*]type: xrandr --output VGA --left-of LVDS
[/LIST]

this made the LCD running on the left side and laptop screen on the right side. 
To check it
[LIST]
[*]type: xrandr
[/LIST]
```
laptop:~$ xrandr
Screen 0: minimum 320 x 200, current 2464 x 900, maximum 2464 x 900
VGA connected 1440x900+0+0 (normal left inverted right x axis y axis) 408mm x 255mm
   1440x900       59.9*+   75.0     59.9  
   1152x864       75.0     74.8  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     66.7     60.0  
   720x400        70.1  
LVDS connected 1024x768+1440+0 (normal left inverted right x axis y axis) 246mm x 184mm
   1024x768       60.0*+
   800x600        60.3  
   640x480        59.9  
TMDS-1 disconnected (normal left inverted right x axis y axis)
TV disconnected (normal left inverted right x axis y axis)

```


huh, I've got it :-)

Now the only issue is every time after I login, I have to execute the xrandr command to get the desired setting. :-(

I'm sure there are some methods how to make force the configuration happens automatically, thanks a lot to let me know if you find some way.

I found a nice article for Randr - 
[http://www.thinkwiki.org/wiki/Xorg_RandR_1.2]("http://www.thinkwiki.org/wiki/Xorg_RandR_1.2")
the section *Now automate it on login* can answer my question, but not at 2am morning :-), if you will find the article worthy give a shout.

Additional reading for the Linux Intel Graphics [http://www.intellinuxgraphics.org/documentation.html]("http://www.intellinuxgraphics.org/documentation.html")

Regards, 
MiMr

---

