---
title: "HOW TO: Enable Intellimouse Support in Nautilus and Firefox"
date: 2007-03-19
forum: Outdated Tutorials &amp; Tips
---

### Post by CocoAUS on 2007-03-19
From [Ubuntu How-To (thad hopkins)]("http://othello.alma.edu/~07tmhopk/ubuntuhowto.html#intellimouse"):

[COLOR="Red"]Note:[/COLOR] This works for a Microsoft IntelliMouse Explorer 3.0A mouse, and may or may not work for other similar 7-button mice. I don't really know how this works; it's the result of hours of mucking around with stuff. As always, backup your files before editing.

The following will configure the IntelliMouse to work with Gnome, Nautilus, Firefox, Epiphany, etc, with full support for the back and forward side buttons and scrolling with the wheel.

Install **imwheel**
```
sudo aptitude install imwheel
```

Edit xorg.conf:
```
sudo gedit /etc/X11/xorg.conf
```
Replace the mouse section with the following:
```
Section "InputDevice"
    Identifier "Configured Mouse"
    Driver "mouse"
    Option "CorePointer"
    Option "Device" "/dev/input/mice"
    Option "Protocol" "ExplorerPS/2"
    Option "Buttons" "7"
    Option "ButtonMapping" "1 2 3 6 7"
    Option "Emulate3Buttons" "false"
EndSection
```

Create .imwheelrc:
```
sudo gedit .imwheelrc
```
Paste in the following:
```
".*"
None, Up, Alt_L|Left
None, Down, Alt_L|Right

"(null)"
None, Up, Alt_L|Left
None, Down, Alt_L|Right
```

Make imwheel start with X by editing the startup file:
```
sudo gedit /etc/X11/imwheel/startup.conf
```
Find this line and change the 0 to a 1:
```
IMWHEEL_START=0
```

Add one final file"
```
sudo gedit /etc/X11/Xsession.d/63xmodmap
```
Paste in this code:
```
killall imwheel
xmodmap -e "pointer = 1 2 3 4 5 6 7"
BINARY=$(which imwheel)
$BINARY -k -p -b "6 7"
```

Make the file executable by all:
```
sudo chmod 777 /etc/X11/Xsession.d/63xmodmap
```

Restart X (CTRL + ALT + BACKSPACE), and you're done!

---

### Post by Crushyerbones on 2007-03-21
Quick note: If doing this on Feisty, don't accidentally let ubuntu "reformat" xorg.conf automatically. Mine did and it took me a while to figure out what was wrong.

---

### Post by tblehr on 2007-04-03
Thank you, this worked perfect for my Razor Copperhead mouse as well!

---

### Post by sloggerkhan on 2007-04-16
might have to check this out later. I have a copperhead as well, never configured it for the side buttons on linux.

---

### Post by Oby on 2007-04-19
This actually works :-) Thank you!

---

### Post by sethd32 on 2007-06-20
worked perfectly on feisty 7.04 and an IntelliMouse Explorere 2.0!

Thx

---

### Post by C_B-A on 2007-07-22
Also worked for me!
With Intellimouse Explorer 2.0A USB.
Thanks for the howto :)

---

### Post by lefthand on 2007-07-31
Make sure that .imwheelrc is created in you home folder. My terminal was in a different folder so it was created elsewhere. The back button won't work in nautilus otherwise

---

### Post by Kreat on 2007-08-28
This worked perfectly!  This was the first tutorial to tell you exactly what to do for all the steps.  Thanks I appreciate it!

---

### Post by Crashmaxx on 2007-08-29
Good to see this still works. I was using another method for a while but it only worked with firefox. Great to have nautilus work again.

But I can't believe there is still no good auto-detect and gui for this. Does the bullet-proof-x and gui-xorg-config in Gusty have mouse buttons?

---

### Post by tomski on 2007-09-27
I am so glad that this works :)

the way thing are going i can see me wiping my winxp partition this side of xmas!!
lets hope Gutsy is so much of a big improvment that small hacks like this will not be needed but then again i do like the the way you have to hunt around to get things working and you learn something along the way too unlike windows dumbness!!

---

### Post by Jayhak on 2007-09-29
I have IntelliMouse explorer 4.0 and I got the tilt wheel and scroll wheel to work, but the thumb (back/forward) buttons won't work :/
Ubuntu 7.04 doesn't even recognize those side buttons anymore.
I changed it to 9-button with tilts, but it uses 4 5 as tilt and 6 7 as scroll, so the tilt takes the place of side buttons which won't work then...

---

### Post by Dropknee on 2007-09-30
I'm looking for this for a very long time.... man you make my night, at last have this bottom working in Ubuntu, I hate clicking the back and forward icons in Firefox, this bottoms make my surf a breeze once again :)

---

### Post by jdogzilla on 2007-10-11
One more satisfied user on Ubuntu 7.04 with MS Intellimouse ... thanx!!!

---

### Post by ozp on 2007-10-12
I am typing with a gutsy and my mouse is like before: CRAP

so Gutsy is no good with 5 bottom mouses 

Does this fix works for gutsy too?

---

### Post by Sunflower1970 on 2007-10-12
> **ozp said:**
> I am typing with a gutsy and my mouse is like before: CRAP

so Gutsy is no good with 5 bottom mouses 

Does this fix works for gutsy too?

It seems to work with Gutsy. I bit the bullet and installed Gutsy on one side of the old PII I had. Fresh install and I used this hack to get my MS Wireless Intellimouse to use all 5 buttons again.

---

### Post by Hasen_A on 2007-10-14
Hello guys,

I am having trouble activating my back and forward buttons in nautilus. The setup works for firefox but not for Nautilus :(. I have an iWith Intellimouse Explorer 2.0A USB mouse as well, but am running my system on a laptop where i disabled the touchpad. Does that change anything?

---

### Post by IronSheick67 on 2007-10-15
Great Stuff!!!

This is the first tutorial that has actually worked for me!!!  I love the IntelliMouse and the side button functionality is an absolute must.
Thank you

---

### Post by loman18 on 2007-10-30
Thanks. It worked for me too, on Gutsy Gibbon

---

### Post by Sunflower1970 on 2007-10-30
> **Hasen_A said:**
> Hello guys,

I am having trouble activating my back and forward buttons in nautilus. The setup works for firefox but not for Nautilus :(. I have an iWith Intellimouse Explorer 2.0A USB mouse as well, but am running my system on a laptop where i disabled the touchpad. Does that change anything?

It won't work for Nautilus, unfortunately. Just your browsers. I just use Alt+ <-- to go back in Nautilus

There *is* a way to do it. I know there is because when I was new to Ubuntu using Edgy I somehow got it to work, but I don't know what I did because I was trying so many different commands etc and didn't really know what each one did. But a combination of them worked and I was able to use it in Nautilus...

---

### Post by Hasen_A on 2007-10-31
> **Sunflower1970 said:**
> It won't work for Nautilus, unfortunately. Just your browsers. I just use Alt+ <-- to go back in Nautilus

There *is* a way to do it. I know there is because when I was new to Ubuntu using Edgy I somehow got it to work, but I don't know what I did because I was trying so many different commands etc and didn't really know what each one did. But a combination of them worked and I was able to use it in Nautilus...

Same here for me, that's why asked in the forum :D. Please tell me how, if you figure it out again.

---

### Post by kelbizzle on 2007-11-29
I have 7.10 I just changed this and firefox works with buttons 6 7 
Section "InputDevice"
   Identifier     "Configured Mouse"
   Driver         "mouse"
   Option         "CorePointer"
   Option         "Device" "/dev/input/mice" 
   Option         "Protocol" "ExplorerPS/2"
   Option         "ZAxisMapping" "4 5"
   Option         "Emulate3Buttons" "true"
   Option         "Buttons" "7" 
   Option         "ButtonMapping" "1 2 3 6 7"

---

### Post by Hasen_A on 2007-11-30
> **kelbizzle said:**
> I have 7.10 I just changed this and firefox works with buttons 6 7 
Section "InputDevice"
   Identifier     "Configured Mouse"
   Driver         "mouse"
   Option         "CorePointer"
   Option         "Device" "/dev/input/mice" 
   Option         "Protocol" "ExplorerPS/2"
   Option         "ZAxisMapping" "4 5"
   Option         "Emulate3Buttons" "true"
   Option         "Buttons" "7" 
   Option         "ButtonMapping" "1 2 3 6 7"
That just do it for me when I want to use the back- and forward buttons in nautilus. I am using a notebook and neither my mouse buttons nor the touchpad does the trick. Here's my xorg.conf section
```
Section "InputDevice"
	Identifier	"External Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ExplorerPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Buttons"		"7"
	Option		"Emulate3Buttons"	"false"
	Option		"ButtonMapping"		"1 2 3 6 7"
	Option 		"Resolution"		"100"
EndSection

```

---

### Post by pannerrammer on 2007-12-08
I must be getting old. Works for my Intellimouse Explorer USB/PS2 (original version, no number!) and Gutsy. Thanks.

Any idea how to reassign the buttons? I want to click the right button once and get a double-click, and the left thumb button once to get a right click.

---

### Post by lord_loafer on 2007-12-08
Thank you so much!! I have only been using Ubuntu for a couple of weeks, and love it, but this post alone made me want to register for the forum!

Thanks again...

An EX Windows user...

:guitar:

---

### Post by Crashmaxx on 2007-12-09
> **pannerrammer said:**
> I must be getting old. Works for my Intellimouse Explorer USB/PS2 (original version, no number!) and Gutsy. Thanks.

Any idea how to reassign the buttons? I want to click the right button once and get a double-click, and the left thumb button once to get a right click.

Go to this step:
```

sudo gedit .imwheelrc

```
And change it to this:
```

".*"
Output Repetitions 2, Up, Button1
None, Down, Button3

"(null)"
Output Repetitions 2, Up, Button1
None, Down, Button3

```
If the buttons are backwards, switch the Up and Down parts. See:
```

man imwheel

```
for more details, or if it doesn't work as expected.

---

### Post by pannerrammer on 2007-12-12
In thread 870, **falconed** posted a method of getting all the Intellimouse to work properly **without** installing imwheel. It worked on falconed's MS Wireless Laser Mouse 6000, and worked for my Intellimouse Explorer (on Gutsy AMD64). I've repeated it below:

In /etc/X11/xorg.conf:  
```
Section "InputDevice"
         Identifier      "Configured Mouse"
         Driver          "mouse"
         Option          "CorePointer"
         Option          "Device"                "/dev/input/mice"
         Option          "Protocol"              "ExplorerPS/2"
 EndSection

```                                 In /etc/X11/Xsession.d/63modmap
 ```
xmodmap -e "pointer = 1 2 3 4 5 8 9 6 7"
``` Restart X and that's it!

---

### Post by GackY2K on 2007-12-17
I've tried everything under this thread to try and get my MS Wireless Intellimouse Explorer 2.0 to function and have Forward/Back enabled in Firefox.  The mouse works, but not the navigation (side buttons).


I saw one thread elsewhere that recommended using:
```
cat /proc/bus/input/devices

```

To accurately see how my mouse is detected.  Here is what that reports:

```
I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/class/input/input0
U: Uniq=
H: Handlers=mouse0 event0 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0003 Vendor=045e Product=008c Version=0111
N: Name="Microsoft Microsoft Wireless Optical Mouse&#65533; 1.0A"
P: Phys=usb-0000:00:0b.0-1/input0
S: Sysfs=/class/input/input4
U: Uniq=
H: Handlers=mouse1 event1 
B: EV=7
B: KEY=1f0000 0 0 0 0 0 0 0 0
B: REL=1c3

I: Bus=0003 Vendor=045e Product=00dd Version=0111
N: Name="Microsoft Comfort Curve Keyboard 2000"
P: Phys=usb-0000:00:0b.0-4/input0
S: Sysfs=/class/input/input5
U: Uniq=
H: Handlers=kbd event2 
B: EV=120003
B: KEY=10000 7 ff800000 7ff febeffdf f3cfffff ffffffff fffffffe
B: LED=107

I: Bus=0003 Vendor=045e Product=00dd Version=0111
N: Name="Microsoft Comfort Curve Keyboard 2000"
P: Phys=usb-0000:00:0b.0-4/input1
S: Sysfs=/class/input/input6
U: Uniq=
H: Handlers=kbd event3 
B: EV=10000f
B: KEY=7fff 2c3027 bf004440 0 0 1 10f80 8837c407 ffe77bfa d9715fff febeffdf ffefffff ffffffff fffffffe
B: REL=40
B: ABS=1 0

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/class/input/input7
U: Uniq=
H: Handlers=kbd event4 
B: EV=40001
B: SND=6

I: Bus=0019 Vendor=0000 Product=0002 Version=0000
N: Name="Power Button (FF)"
P: Phys=button_power/button/input0
S: Sysfs=/class/input/input8
U: Uniq=
H: Handlers=kbd event5 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button (CM)"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/class/input/input9
U: Uniq=
H: Handlers=kbd event6 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0006 Vendor=001f Product=001f Version=0000
N: Name="Mouseemu virtual keyboard"
P: Phys=
S: Sysfs=/class/input/input10
U: Uniq=
H: Handlers=kbd event7 
B: EV=100003
B: KEY=1ffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff

I: Bus=0006 Vendor=001f Product=001e Version=0000
N: Name="Mouseemu virtual mouse"
P: Phys=
S: Sysfs=/class/input/input11
U: Uniq=
H: Handlers=mouse2 event8 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=103

```

I've edite my xconf SOOOoooo many times, trying using everything I can think of to get it to work (all 5 buttons) but to no avail.  Here is my current xorg.conf

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Wed Nov 14 17:10:54 PST 2007

# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Microsoft Microsoft Wireless Optical Mouse&#65533; 1.0A"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "glx"
    Load           "v4l"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier 	"Microsoft Microsoft Wireless Optical Mouse&#65533; 1.0A"
	Driver 		"mouse"
	Option 		"CorePointer"
	Option 		"Device" 	"/dev/input/mice"
	Option 		"Protocol" 	"ExplorerPS/2"
	Option 		"ZAxisMapping" 	"4 5"
	Option		"Emulate3Buttons" 	"true"
	Option 		"Buttons" 	"7"
	Option 		"ButtonMapping" "1 2 3 6 7"
EndSection

Section "Monitor"
    Identifier     "Failsafe Monitor"
    VendorName     "Plug 'n' Play"
    ModelName      "Plug 'n' Play"
    Gamma           1
    ModeLine       "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
    ModeLine       "640x480@72" 31.5 640 664 704 832 480 489 491 520 -hsync -vsync
    ModeLine       "640x480@75" 31.5 640 656 720 840 480 481 484 500 -hsync -vsync
    ModeLine       "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
    ModeLine       "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
    ModeLine       "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
    ModeLine       "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
    ModeLine       "832x624@75" 57.3 832 864 928 1152 624 625 628 667 -hsync -vsync
    ModeLine       "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
    ModeLine       "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -hsync -vsync
    ModeLine       "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
    ModeLine       "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
    ModeLine       "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
    ModeLine       "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
    ModeLine       "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
    ModeLine       "1280x960@75" 129.9 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
    ModeLine       "1400x1050@60" 122.6 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
    ModeLine       "1400x1050@75" 155.8 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync
    ModeLine       "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
    ModeLine       "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
    ModeLine       "1792x1344@60" 204.8 1792 1920 2120 2448 1344 1345 1348 1394 -hsync +vsync
EndSection

Section "Device"
    Identifier     "Failsafe Device"
    Driver         "nvidia"
    BoardName      "vesa"
    Screen          0
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Failsafe Device"
    Monitor        "Failsafe Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Virtual     1792 1344
        Depth       24
        Modes      "1280x1024@60" "800x600@72" "800x600@75" "800x600@56" "800x600@60" "640x480@75" "832x624@75" "640x480@72" "1024x768@75" "640x480@60" "1024x768@70" "1024x768@60" "1152x864@75" "1280x1024@75" "1280x960@60" "1280x1024@60" "1280x960@75" "1400x1050@60" "1400x1050@75" "1600x1200@65" "1600x1200@60" "1792x1344@60"
    EndSubSection
EndSection

```

If anyone has ANY suggestions or spots my problem...plz let me know.   For what it's worth...I had a logitech MX 1000 wireless laser mouse and could never get the side buttons or middle button to work in it either.   /sigh

TX!

---

### Post by cadlewv on 2007-12-18
Not working for me.  I am using an Intellimouse Explorer 7-button mouse and it won't work with Gutsy 7.10.  In fact, I can't see my desktop now.  It keeps giving me an error about Nautilus not being able to start.

---

### Post by elmaska on 2007-12-19
> **kelbizzle said:**
> I have 7.10 I just changed this and firefox works with buttons 6 7 
Section "InputDevice"
   Identifier     "Configured Mouse"
   Driver         "mouse"
   Option         "CorePointer"
   Option         "Device" "/dev/input/mice" 
   Option         "Protocol" "ExplorerPS/2"
   Option         "ZAxisMapping" "4 5"
   Option         "Emulate3Buttons" "true"
   Option         "Buttons" "7" 
   Option         "ButtonMapping" "1 2 3 6 7"

Worked great with my MS Wireless Intellimouse Explorer on Gibbon too!. I permitted myself to change "Emulate3Buttons" to "false" and tje change didn't affect negativly

---

### Post by pannerrammer on 2007-12-19
CrashMaxx suggested I look at ```
man imwheel
```I did. I'm back now! 

If I got it right, imwheel clicks are numbered according to function - 8 & 9 are the thumb buttons (and 6 & 7 are the left/right scroll wheel, even if you don't have them). Most of the stuff here seems to attempt to number the thumb buttons to 6 7, and then remap everything else to match.  I've done a similar thing, but using 8 9. 

Also, restarting X doesn't seem to be always enough, as sometimes things worked differently after a reboot (ie. make your changes then reboot, don't just restart X). 

This is what I've ended up with:

**/etc/X11/xorg.conf**
```
Section "InputDevice" 
     Identifier    "Configured Mouse"  
     Driver        "mouse" 
     Option        "CorePointer" 
     Option        "Device"    "/dev/input/mice" 
     Option        "Protocol"    "ExplorerPS/2" 
     Option        "Buttons"    "7" 
     Option        "ButtonMapping"    "1 2 3 8 9"  
     Option        "Emulate3Buttons"    "false" 
 EndSection  
 
```Notice the **8 9** not **6 7**. I didn't need the line about 4 5 for the zAxis.

[B]/etc/X11/imwheel/startup.conf

[/B]  Enable the wheel by changing the 0 to 1

 ```
IMWHEEL_START=1
```The final line in this file is commented out. I tried enabling it but made no difference (I think it's supposed to do what the last line in the 63xmodmap file does, but not sure).

** /etc/X11/Xsession.d/63xmodmap**
 
```
killall imwheel  
 xmodmap -e "pointer = 1 2 3 4 5 8 9"  
 BINARY=$(which imwheel)  
 $BINARY -k -p -b "8 9" 
 
```Again **8 9** not **6 7**. I'm unsure what the $BINARY command does, but the -k and -b parameters exist as imwheel parameters so I guess it's more or less what the last line of the startup.conf file does.

Finally, my .imwheelrc contains

```
 ".*"
None, Up, Alt_L|Left
None, Down, Alt_L|Right

"(null)"
None, Up, Alt_L|Left
None, Down, Alt_L|Right
```None means the mouse action happens without Shift or Alt or Ctrl held down.
Up and Down are imwheel references to the thumb buttons.
Alt_L is the left Alt key.
Left and Right are the keyboard arrows.


Good luck!

---

### Post by Nion on 2007-12-20
After trying this guide and a few others with no luck, i read the imwheel manual and found a simpler and (imo) more proper solution.

**1. Install imwheel:**

```
sudo aptitude install imwheel
```

**2. Edit imwheels startup.conf**

```
sudo nano /etc/X11/imwheel/startup.conf
```

Change the lines in here to the following (make sure that the second one is uncommented).

```
IMWHEEL_START=1
```

```
IMWHEEL_PARAMS='-b "0 0 8 9"'
```

In case you have a two axis scroll wheel (like my Intellimouse explorer 3.0) then the second line should read:

```
IMWHEEL_PARAMS='-b "0 0 0 0 8 9"'
```

**3. Create a config file in your home directory**

```
nano ~/.imwheelrc
```

and paste the following:

```
".*"
None, Thumb1, Alt_L|Left
None, Thumb2, Alt_L|Right

"(null)"
None, Thumb1, Alt_L|Left
None, Thumb2, Alt_L|Right
```

**And now you're done!** 

You dont need to white a script and remap buttons, or even edit xorg.conf. 

Hopefully this could be helpful for someone. :)

---

### Post by pannerrammer on 2007-12-21
Nion, your settings didn't work for me. Seems likely different versions of this pesky mouse operate in different ways! Perhaps we need to build a list of working configs for the various versions of the mouse?

I'm running Gutsy 64, I've got an original (late 2002) Intellimouse Explorer USB (with PS2 adapter) and my instructions worked for me (doh!)

---

### Post by Nion on 2007-12-21
> **pannerrammer said:**
> Nion, your settings didn't work for me. Seems likely different versions of this pesky mouse operate in different ways! Perhaps we need to build a list of working configs for the various versions of the mouse?

I'm running Gutsy 64, I've got an original (late 2002) Intellimouse Explorer USB (with PS2 adapter) and my instructions worked for me (doh!)

From what ive read around the net there are many different solutions to this problem, and it works differently for almost everyone. The difficult thing is that there appears to be no way to tell why there is a difference. Maybe we could make a list of mouse models, but i doubt we can make a complete list since there are many different models.

---

### Post by remu on 2007-12-28
WOW!!
It works!!
Thank you so much, I have tried so many things, and this works, I am amazed! Again, thanks alot!

EDIT: I'm using a Logitech MX518

---

### Post by jgrover on 2007-12-29
Thanks for this write up! Worked perfectly!:guitar:


 I only have one question though... why did you have us create .imwheelrc ?

Jason

---

### Post by Smittysmit on 2007-12-30
I just tried the instructions at the start of this thread and now my other buttons work in Firefox with my Kensington 'Expert Mouse (trackball)".  VERY COOL.

Next question is can I configure the button in the scroll wheel to lock so I just roll the ball up & down to scroll up & down a web page?  Typically in windows, I just 'left click' to unlock this feature.

---

### Post by krimzonstarr on 2008-02-12
Just switched over from XP to Gutsy 2 days ago, and your info helped me a great deal. Thank you

---

### Post by ilovenicotine on 2008-03-20
> **Smittysmit said:**
> 
Next question is can I configure the button in the scroll wheel to lock so I just roll the ball up & down to scroll up & down a web page?  Typically in windows, I just 'left click' to unlock this feature.


Type: about:config in the address bar in Firefox.
in the Filter box type autoscroll
you're looking for general.autoScroll
when you've found it right-click and hit toggle so that it's now "true"
middle click on any regular web page and you're auto scrolling!

---

### Post by misterhead on 2008-03-24
worked like a champ. Intellimouse Explorer 3.0 on a docked Dell D810.

Thnx!

---

### Post by daninkorea_ on 2008-04-10
> **CocoAUS said:**
> From [Ubuntu How-To (thad hopkins)]("http://othello.alma.edu/~07tmhopk/ubuntuhowto.html#intellimouse"):

[COLOR="Red"]Note:[/COLOR] This works for a Microsoft IntelliMouse Explorer 3.0A mouse....


Dude, awesome! Thanks for posting this, I logged on as a new forum user just to say thanks. My mouse is finally kicking *** again :guitar:

---

### Post by sporkinum on 2008-04-13
Thanks.. the original steps workd for me. Gutsy Kubuntu, Intellimouse Explorer 3.0A.

---

### Post by evencoil on 2008-05-23
I tried pannerrammer's technique (post #31) both with buttons 6 7 and 8 9.

Before I had no thumb button action at all. Now, with either 6 7 or 8 9, the left thumb button does nothing and the right thumb button scrolls the current window down slightly (like what would happen if I rolled my scroller one click). All other buttons (left/right, scroller up/down, and center click on scroller) are working fine. This seems promising...anyone have any ideas how I can get the left one to work and the right one to go forward?

Oh, this is a USB IntelliMouse on Hardy.

---

### Post by pannerrammer on 2008-05-24
> **evencoil said:**
> I tried pannerrammer's technique (post #31) both with buttons 6 7 and 8 9.

Before I had no thumb button action at all. Now, with either 6 7 or 8 9, the left thumb button does nothing and the right thumb button scrolls the current window down slightly (like what would happen if I rolled my scroller one click). All other buttons (left/right, scroller up/down, and center click on scroller) are working fine. This seems promising...anyone have any ideas how I can get the left one to work and the right one to go forward?

Oh, this is a USB IntelliMouse on Hardy.

Hi evencoil. 

Hardy seems to have broken the techniques described in this thread! 

I've created a new HowTo [http://ubuntuforums.org/showthread.php?p=4917621](http://ubuntuforums.org/showthread.php?p=4917621) which I think might help you. 

Let me know how you get on.

---

### Post by evencoil on 2008-05-24
> **pannerrammer said:**
> Hi evencoil. 

Hardy seems to have broken the techniques described in this thread! 

I've created a new HowTo [http://ubuntuforums.org/showthread.php?p=4917621](http://ubuntuforums.org/showthread.php?p=4917621) which I think might help you. 

Let me know how you get on.

Thanks! Following the directions of that post solved the problem seamlessly.

---

### Post by evencoil on 2008-05-25
a tidbit you might find interesting...

Originally I had installed Ubuntu->Kubuntu->Xubuntu, and the thumb buttons didn't work until I followed your fix. I just did a clean install of Xubuntu and now the thumb buttons work perfectly right out of the box. Curious, eh?

---

### Post by pannerrammer on 2008-05-25
> **evencoil said:**
> a tidbit you might find interesting...

Originally I had installed Ubuntu->Kubuntu->Xubuntu, and the thumb buttons didn't work until I followed your fix. I just did a clean install of Xubuntu and now the thumb buttons work perfectly right out of the box. Curious, eh?

Is this true for Nautilus as well as Firefox?

---

### Post by evencoil on 2008-05-25
Ahh, yep..worked only for firefox.

---

### Post by mcweck on 2009-04-01
This is/was a great manual and always helped me to get my mouse working. But since i installed Ubuntu 8.10 it does not work for my Razer Copperhead anymore, at least it fails in my fav game Enemy Territory.
here is my xorg.conf: [http://pastebin.com/f72bc34e8](http://pastebin.com/f72bc34e8)
I would be very happy if someone can help me.

---

### Post by mcweck on 2009-04-03
Got it working now. Added to the bottom of the xorg.conf this

> Section "ServerFlags"
   Option      "AutoAddDevices" "false"
EndSection

As my keyboard lost the german layout after that i added this:
> Section "InputDevice"
    Identifier     "Keyboard0"
    Driver         "kbd"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "de"
    Option         "XkbVariant" "nodeadkeys"
EndSection

Anyone know how to configure the mouse with the new xserver without disabling the AutoAddDevices?

---

### Post by ksample on 2009-11-24
> **Nion said:**
> After trying this guide and a few others with no luck, i read the imwheel manual and found a simpler and (imo) more proper solution.


Awesome.  I tried Nion's solution on Linux Mint 7 "Gloria" with a Logitech MediaPlay mouse and forward/back buttons work great in both Firefox and Nautilus.  Thanks!

ks

---

### Post by keypox on 2010-05-24
> **Nion said:**
> After trying this guide and a few others with no luck, i read the imwheel manual and found a simpler and (imo) more proper solution.

**1. Install imwheel:**

```
sudo aptitude install imwheel
```

**2. Edit imwheels startup.conf**

```
sudo nano /etc/X11/imwheel/startup.conf
```

Change the lines in here to the following (make sure that the second one is uncommented).

```
IMWHEEL_START=1
```

```
IMWHEEL_PARAMS='-b "0 0 8 9"'
```

In case you have a two axis scroll wheel (like my Intellimouse explorer 3.0) then the second line should read:

```
IMWHEEL_PARAMS='-b "0 0 0 0 8 9"'
```

**3. Create a config file in your home directory**

```
nano ~/.imwheelrc
```

and paste the following:

```
".*"
None, Thumb1, Alt_L|Left
None, Thumb2, Alt_L|Right

"(null)"
None, Thumb1, Alt_L|Left
None, Thumb2, Alt_L|Right
```

**And now you're done!** 

You dont need to white a script and remap buttons, or even edit xorg.conf. 

Hopefully this could be helpful for someone. :)

perfect thanks :)

---

### Post by HKJGN on 2010-08-13
this just broke my xorg.conf file, says cannot parse configuration file :|

---

