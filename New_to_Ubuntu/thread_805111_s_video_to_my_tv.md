---
title: "s video to my tv"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by chee on 2008-05-23
so my laptop sits close enough to my tv that i would like to be able to link them with my s-video output so i can watch clips and motorcycle races that i download without having to burn them.  i used to do it when i was running windows all the time but i was wondering if i can do this in linux.  i have a dell inspiron 6400 and am running the newest version of ubuntu.  any suggestions or ideas are welcome

---

### Post by wootah on 2008-05-23
What type of video card do you have?

Post output of:
lspci | grep VGA
glxinfo
/etc/X11/xorg.conf

Thanks! :-D

---

### Post by davemolloy64 on 2008-05-23
I have an HP pavilion that the S-video works for. In my case, simply having it plugged in before booting works perfectly. Although, since upgrading to Hardy Heron, I've had some trouble with the "big desktop" mode.

In short, if you're asking if its possible, then yes. Plug it in and have a go. But it's not as fool-proof as in Windows, and might require some "tweaking". Also, if you haven't already got the cable, make sure you buy one that can carry colour: S-video to s-video rather than S-video to Scart, I think (but I'm no electrician).

---

### Post by chee on 2008-05-23
is this what you are looking for?

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)

if not i apologize ... and need more noob ready instuctions :)

---

### Post by davemolloy64 on 2008-05-23
He means to open a terminal (in the applications, accessories menu) and type:

1. lspci | grep VGA
and hit return: then post what you see.

2. glxinfo
and hit return: then post what you see.

3. Post the content of the text file located in your "filesystem" (under 'places' at the top of the screen, select 'computer' and you'll see the filesystem folder) in /etc/X11/xorg.conf

Newbie-friendly enough? :)

---

### Post by wootah on 2008-05-23
Ack I apologize for not being clear chee :(

The output of those should help a lot. So you have an Intel based graphics card. Have you tried just plugging in your laptop to your TV with the s-video cable? If it doesn't come up right away, keep it plugged in and go to System | Preferences | Screen and Graphics. I believe in there you should be able to set everything up.

Let us know what happens :)

---

### Post by NT4usB on 2008-05-23
just for fun, lets simplify even further.
You can copy and paste in a terminal... helps prevent typing errors and finger fatigue.
The commands are slightly different than global copy/paste. Instead of Ctrl+c or Ctrl+v, to copy and paste in a terminal the commands are Ctrl+Shift+c and Cntrl+Shift+v (Hold down Ctrl _and_ Shift and type c to copy or v to paste.)

For xorg.conf, type in a terminal:```
cat /etc/X11/xorg.conf
``` and that will print the contents of xorg.conf to the terminal. From there you can copy and paste to your post.

(May no longer apply) When I set up MythTV output to TV (an older CRT) I had to rtfm and find the TVStandard format it supported. In this case, HD480i:```
Section "Screen"
    Identifier     "Screen[0]"
    Device         "Device[0]"
    Monitor        "Monitor[0]"
    DefaultDepth    24
    Option         "TVStandard" "HD480i"
    Option         "ConnectedMonitor" "TV[0]"
    SubSection     "Display"
        Depth       24
        Modes      "1024x768"
    EndSubSection
EndSection
```
This information had to be added to xorg.conf to make it work.
Without it, the entire picture had a blue tint.

---

### Post by chee on 2008-05-23
no apologies are needed i assure you all.  it has been a while since i have done anything in a terminal and even so the things i knew how to do were minimal.  the weird thing is i have no screen and graphics option in my preferences.  not sure if it might be labelled something else 

oh and when i typed glxinfo there was a lot that came up so i can post it but im not sure if it is worth it.

---

### Post by wootah on 2008-05-23
Hmm.. I'm not are my desktop machine right now so I can't quite give you the exact name of the option.

Let's try this: in the terminal type:
```
gksudo displayconfig-gtk &
```
You will have to type in your password for this. This should hopefully bring up the menu I was referring to. Play with that and see what happens :)

---

### Post by NT4usB on 2008-05-23
> **chee said:**
> ...oh and when i typed glxinfo there was a lot that came up so i can post it but im not sure if it is worth it.

Sometimes with very long files, the output scrolls off the terminal. You miss the first part.
you can dump the output to a textfile and read or copy from there:```
glxinfo >~/glxoutput
```will create a textfile *glxoutput* in your home folder with all the output from the command.
Be sure to use the 'Code' format when posting long files... (the # icon above.)

---

### Post by davemolloy64 on 2008-05-23
Screens and graphics is usually under "system" at the top of the screen, then "admnistration" (not "preferences").

---

### Post by wootah on 2008-05-23
> **davemolloy64 said:**
> Screens and graphics is usually under "system" at the top of the screen, then "admnistration" (not "preferences").

Whoops, my bad :)

---

### Post by chee on 2008-05-23
alright so i think i found what i need but i am still not sure what to do. oh and there still isn't a screen and graphics option so i used gksudo displayconfig-gtk & which worked fine.  so under screen i have screen 1 and 2 obviously and screen 2 doesn't seem to be set up.  not sure what to do in there really or if i am in the right spot.

---

### Post by davemolloy64 on 2008-05-23
From there, you should be able to change the options to enable Screen 2 as a second screen: either to mirror (copy) screen one, or to extend it (so you can drag windows between screens) to the left, right, etc.

You might have to log out and back in (or otherwise restart the x server) to see the effects. Hope it's not more complicated than that.

---

### Post by chee on 2008-05-25
alright so i think i could figure out how to put another monitor on using those options but to my tv is a different story since i will be using the s-video  and not the monitor port.  it gives me monitor options but i don't know if this is what i need. has anyone else done this.  does it matter that it is an older tube style tv and not an LCD.

---

### Post by wootah on 2008-05-26
> **chee said:**
> alright so i think i could figure out how to put another monitor on using those options but to my tv is a different story since i will be using the s-video  and not the monitor port.  it gives me monitor options but i don't know if this is what i need. has anyone else done this.  does it matter that it is an older tube style tv and not an LCD.

Sorry for the delay chee. Yes it is possible to hook up to a tube style tv--that is exactly what I have for watching movies. I have an ATI card and it comes with a configuration utility.

I found an article that will help you out though: [http://blog.dotkam.com/2007/05/18/dual-monitor-on-ubuntu-704-feisty-fawn-nc2400-with-intel-945gm/]("http://blog.dotkam.com/2007/05/18/dual-monitor-on-ubuntu-704-feisty-fawn-nc2400-with-intel-945gm/")

Try that out and let us know!

Good luck!

---

### Post by chee on 2008-05-26
i guess the reason i thought it wouldn't be a big deal is because when i was using windows i just had to configure a clone through my display settings.  the link that was mentioned (and i do appreciate that by the way :)  ) seems more specific to a monitor.  the guy sets his resolution and the size and all the specifics whereas i don't know what i would use for that based on my 32" toshiba.  plus i don't really understand a lot of what he was doing there so i couldn't really get if he was using the s-video port or not.  like i said i am kinda lost and really do appreciate any help.  plus i hate windows :)

---

### Post by wootah on 2008-05-26
As far as I know, using either a s-video out or another monitor out makes no difference. In my situation, I am using s-video out. The only difference was I had to force the resolution to be 640x480 (standard tv size).

After reading more carefully through that howto, it does seem not that straight forward. Unfortunately, dual-head setups have always been somewhat of a pain to setup. Even I prefer the way Windows does it. Linux and X are slowly getting there however.

May I suggest checking out this thread as well: [http://ubuntuforums.org/showthread.php?t=221174]("http://ubuntuforums.org/showthread.php?t=221174"). It will be a bit of reading, but that should cover everything you need.

Let us know if that helps!

---

### Post by chee on 2008-05-26
if somebody could have a look and tell me how this looks before i try it as i kinda messed it up the first time and i almost couldn't get back into ubuntu. almost had to use my windows partition :(  

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"0 Configured Video Device"
         Screen          0
        Option "DDCMode" "True"
        Option "MonitorLayout" "LVDS"
EndSection

Section "Device"
	Identifier	"1 Configured Video Device"
         Screen          1 
        Option "DDCMode" "True"
        Option "MonitorLayout" "CRT"
EndSection

Section "Monitor"
	Identifier	"0 Configured Monitor"
EndSection

Section "Monitor"
	Identifier	"1 Configured Monitor"
EndSection

Section "Screen"
	Identifier	"0 Default Screen"
	Monitor		"0 Configured Monitor"
	Device		"0 Configured Video Device"
EndSection

Section "Screen"
	Identifier	"1 Default Screen"
	Monitor		"1 Configured Monitor"
	Device		"1 Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen	     0  "0 Default Screen"
	Screen       1  "1 Default Screen" RightOf "0 Default Screen"
        InputDevice	"Synaptics Touchpad"
        Option "Xinerama" "true"
EndSection

---

### Post by NT4usB on 2008-05-26
Looks like you're running 8.04. xorg is truly wacky on Hardy. I just did an install of 8.04 and fought the video, trying to get it to work.
Finally trashed that Windows-like generic *Configured Monitor* crap and entered in all the configurations manually.
I don't have a clue how to make a xorg work using the generic settings.
If you want to configure manually, probably make it work.
Here's what I used to run a 15" LCD and a CRT TV on 7.10.
_It will not work for you as it is_
but you can use the format and input your driver, refresh, resolutions, and of course, change Component to SVIDEO and whatever TVStandard your TV supports.
The "files" and "Module" "InputDevice" section will probably be completely different.
Before you start, back up your original and learn to work from a terminal so when you break it you can copy it back using the command line..
Last resort:```
sudo dpkg-reconfigure -phigh xserver-xorg
```will get your video back.


```

Section	"ServerLayout"
    Identifier     "Simple Layout"
    Screen      0  "Screen[0]" 0 0
    Screen      1  "Screen[1]" RightOf "Screen[0]"
    InputDevice    "Generic Keyboard" "CoreKeyboard"
    InputDevice    "Configured Mouse" "CorePointer"
EndSection

Section "Files"
	# path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc104"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "Buttons"               "8"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "false"
        Option          "ButtonMapping"         "1 6 3 2 4 5"
        Option          "Resolution"            "100"
EndSection

Section "Monitor"
 #LCD
    Identifier     "Monitor[0]"
    HorizSync       30.0 - 62.0
    VertRefresh     50.0 - 75.0
    Option         "DPMS"
EndSection

Section "Monitor"
 #TV
    Identifier     "Monitor[1]"
    HorizSync       30.0 - 50.0
    VertRefresh     60.0 - 60.0
EndSection

Section "Device"
    Identifier     "Device[0]"
    Driver         "nvidia"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
     Identifier     "Device[1]"
    Driver         "nvidia"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Screen[0]"
    Device         "Device[0]"
    Monitor        "Monitor[0]"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen[1]"
    Device         "Device[1]"
    Monitor        "Monitor[1]"
    DefaultDepth    24
    Option         "TVOutFormat" "Component" #or SVIDEO Composite etc
    Option         "TVStandard" "HD480i" # "NTSC"
    Option         "ConnectedMonitor" "Monitor[1]"
    SubSection     "Display"
        Depth       24
        Modes      "1024x768_60" "720x576_60" "720x480_60" "640x480_60" "480x320_60"
    EndSubSection
EndSection
```

---

### Post by wootah on 2008-05-27
chee I would suggest that you find out all the settings for your monitor (eg: supported resolution, colour depth, refresh rates). It is pretty close though. I'm not exactly sure if it would work right away, but it is close :)

---

