---
title: "[SOLVED] Screen Width Problem"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by anachronon on 2008-05-29
Hey everyone,

This is more of a hardware question.  I just got the proper display driver installed in Ubuntu Studio 8.04, and I now have the display resolution that I need.  However, the image is not filling the screen on the monitor, as it should.  I suspect the reason for this is that the monitor wants a refresh rate of 60Hz, while the video card can only supply that resolution at 57Hz.

So, here's my question.  Is there a way to overclock the video card, to get an output frequency up to 60Hz?  If so, can I overclock just the video card, or would I need to overclock the entire system?  I would only need a boost of 5%.  Would this even work?

I should also ask if anyone knows a different/better way to deal with this problem.  Other than the refresh frequency, I can find no other reason why my image is not filling the screen.  There is no malfunction with the monitor itself.

---

### Post by Thelasko on 2008-05-29
There are separate horizontal and vertical refresh frequencies.  You don't have to "overclock" anything because it's not a hardware issue.  It's a problem with your video driver.  What kind of video card do you have?

---

### Post by anachronon on 2008-05-29
> **Thelasko said:**
> There are separate horizontal and vertical refresh frequencies.  You don't have to "overclock" anything because it's not a hardware issue.  It's a problem with your video driver.  What kind of video card do you have?
It's an nVidia GeForce 5200.  I am using a Linux driver that I downloaded directly from nVidia.  "dispalyconfig" says that the card is sending out the signal at 57Hz, but the monitor's on-screen display says that it is working at 60Hz.

The monitor is actually a 15" flat-panel TV, that can also function as a computer monitor.  That may be why the refresh is stuck at 60Hz.  I was thinking that the different rates could be my problem because the horizontal width control is labeled "clock".

Oh yes, before I forget to mention this again, I have adjusted the horizontal width of the monitor out as far as it will go.  That was the first thing that I tried.

---

### Post by unutbu on 2008-05-29
I have never tried this myself, but I believe this may help: edit your xorg.conf to include a "DisplaySize" line. For example:

```
Section "Monitor"
    Identifier  "My Monitor"
    HorizSync   31.5 - 48.5
    VertRefresh 50-70
    **DisplaySize 355 237**
EndSection
```

The numbers following DisplaySize are the horizontal and vertical size of your monitor in millimeters.

You can find out what your current DPI is by running
```

xdpyinfo | grep -B1 dot
```

I'm getting my info from Appendix E of /usr/share/doc/nvidia-glx-new/README.txt.gz (An unusually information-packed README!). You should have this file too if you use the nvidia-glx-new package.

---

### Post by Thelasko on 2008-05-30
[Here is an old guide.]("http://ubuntuforums.org/showthread.php?t=98456")  Unfortunately the developers redesigned the xorg configuration utility for Hardy Heron.  The new utility is supposed to be easier to use, but I haven't tried it yet.

---

### Post by Thelasko on 2008-05-30
apparently the new configuration tool is "[gnome-display-properties]("http://ubuntuforums.org/showthread.php?p=4590782")".

---

### Post by Thelasko on 2008-05-30
I don't know why they disabled the old tool but here's a[ petition to bring it back.]("http://brainstorm.ubuntu.com/idea/7655/")

---

### Post by anachronon on 2008-05-31
OK, I've read several different versions on how to do this, each from a different xorg.conf.  So, to help answer questions, here is a copy of the relevant section from my current xorg.conf (my comments follow the quote):

> Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1280x1024"
	Horizsync	31.5-64.0
	Vertrefresh	56.0 - 65.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
	Gamma	1.0
EndSection

Section "Monitor"
	Identifier	"monitor1"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
	Gamma	1.0
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"nvidia"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Screen	0
EndSection

Section "Device"
	Identifier	"device1"
	Boardname	"nvidia"
	Busid		"PCI:1:0:0"
	Driver		"nvidia"
	Screen	1
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1280	1024
		Modes		"1280x960@60"	"1280x1024@60"	"1024x768@60"	"800x600@60"	"800x600@56"	"640x480@60"
	EndSubSection
EndSection

Section "Screen"
	# 
	Identifier	"screen1"
	Device		"device1"
	Monitor		"monitor1"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Modes		"640x480@60"
	EndSubSection
EndSection

Note that, though I am using a 1280x800 monitor at 1280x800 resolution.  That resolution is not mentioned anywhere in this xorg.cong file!  I know that I need to add it in a number of places, but I wanted to get any comments or warnings first.  Yes, I have already saved a copy of this as "xorg.conf.backup".

Please note eespecially the first section of the xorg file, the one where the lines begin with "modeline".  If I add a line with "1280x800@60", what numbers do I add after?  Also would "hsync" and "vsync" be "+" or "-"?  Also, where it says: 'Modelname  LCD Panel 1280x1024"',  do I need to change it to 'Modelname "LCD Panel 1280x800"'?

Anything else that I need to add or remove?

Finally, all of this would have to be handled manually, as displayconfig-gtk can't seem to get it right.  I can select a 1280x800 monitor, but for some reason, that monitor selection won't give me that resolution as an option.

---

### Post by unutbu on 2008-05-31
Please post your "ServerLayout" section.
You have posted 2 Devices, 2 Monitors, 2 Screen. You only need one for a working xorg.conf. The ServerLayout will tell us which stanzas you are actually using.

Are you trying to change your resolution to 1280x800? Last time you posted, it sounded like you had the resolution you wanted.

[URL="http://en.wikipedia.org/wiki/XFree86_Modeline"]
Modelines are deprecated[/URL]. The nvidia X driver can retrieve the valid frequency ranges from a modern monitor's [EDID]("http://en.wikipedia.org/wiki/Extended_display_identification_data"). A flat panel LCD should be able to communicate its natural resolution and that should be what the nvidia X driver would choose by default. Therefore, I would comment out all the modelines and edit the Screen section to include Modes "nvidia-auto-select":

```
Section "Screen"
    Identifier "screen1"
    Device "device1"
    Monitor "monitor1"
    Defaultdepth 24
    SubSection "Display"
        Depth 24
        Modes "nvidia-auto-select"
    EndSubSection
EndSection
```

---

### Post by Cappy on 2008-05-31
Your monitor is already working at 60Hz. The Display Configuration doesn't show the correct frequency when you use the nvidia driver.

nvidia-settings or the LCD display will show the ACTUAL frequency being used.

I also ran into this bug this week.

---

### Post by anachronon on 2008-06-01
> **Cappy said:**
> Your monitor is already working at 60Hz. The Display Configuration doesn't show the correct frequency when you use the nvidia driver.

nvidia-settings or the LCD display will show the ACTUAL frequency being used.

I also ran into this bug this week.
Thanks.  I guess that answers that question.  Now, if I could just find why the image won't fill my screen, even with the width adjused all the way out.

---

### Post by Cappy on 2008-06-01
All you should need to do for that is run
```
gksudo nvidia-settings
```
and pick out the 1280x800 resolution and then click "Save to X" (something like that).

Then you can press Alt+Control+Backspace and it will restart X. If everything went will you will be using the correct resolution.

---

### Post by philinux on 2008-06-01
When I had this I fixed it by simply pressing the AUTO reset button on the monitor. Worth a press.

---

### Post by anachronon on 2008-06-01
> **unutbu said:**
> Please post your "ServerLayout" section.
You have posted 2 Devices, 2 Monitors, 2 Screen. You only need one for a working xorg.conf. The ServerLayout will tell us which stanzas you are actually using.

Are you trying to change your resolution to 1280x800? Last time you posted, it sounded like you had the resolution you wanted.

[URL="http://en.wikipedia.org/wiki/XFree86_Modeline"]
Modelines are deprecated[/URL]. The nvidia X driver can retrieve the valid frequency ranges from a modern monitor's [EDID]("http://en.wikipedia.org/wiki/Extended_display_identification_data"). A flat panel LCD should be able to communicate its natural resolution and that should be what the nvidia X driver would choose by default. Therefore, I would comment out all the modelines and edit the Screen section to include Modes "nvidia-auto-select":

```
Section "Screen"
    Identifier "screen1"
    Device "device1"
    Monitor "monitor1"
    Defaultdepth 24
    SubSection "Display"
        Depth 24
        Modes "nvidia-auto-select"
    EndSubSection
EndSection
```
Here is the code from "Server Layout":

> Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"	"CoreKeyboard"
	Inputdevice	"Configured Mouse"
EndSection

Should I still change the "modes", as you suggested?  Should I also remove the line "Virtual  1280 1024", or should I change it of 1280 800, to match my monitor?

Yes, I do have it displaying at 1280x800 resoultion.  However, the image is distorted and not filling the screen, even though the width control is adjusted all the way out.  From what folks have been saying, it is a software issue, and not a hardware issue.

---

### Post by anachronon on 2008-06-01
> **philinux said:**
> When I had this I fixed it by simply pressing the AUTO reset button on the monitor. Worth a press.
Already tried that.  On this monitor, it is call "Auto Adjust".  Works well centering the image, but the width is all wrong (way too small).

P.S.  By the way, anyone know how I can mark a quote from xorg or any other file as "code", rather than just a quote?

---

### Post by anachronon on 2008-06-01
Thanks.  That got "displayconfig" straightened out.  But, I still have the width problem.  Also, displayconfig now says that it is running at 50HZ, while the monitor is still claiming 60Hz.  "xrandr -q" is also claiming 50Hz.

I don't know if this make a difference, but "xrandr -q" is also showing the display as "0mm x 0mm".  Does that make a difference, or has that parameter been outmoded?

---

### Post by unutbu on 2008-06-01
To mark text as code, highlight the text and then press the # button above the text field. 
If you don't see the button, click on "User CP">Edit Options go down to Miscellaneous options and select Standard Editor. 

You say you have a LCD TV/computer monitor. That means its pixel width is fixed. That means that 1280 pixels have a fixed width. There is no way to expand the image unless you increase the resolution.

I could be wrong about this, and would be very grateful if other forum readers would correct me if I'm wrong.

I have no idea how to fix the waviness. I thought that didn't happen on LCD displays...

---

### Post by anachronon on 2008-06-01
> **unutbu said:**
> To mark text as code, highlight the text and then press the # button above the text field. 
If you don't see the button, click on "User CP">Edit Options go down to Miscellaneous options and select Standard Editor. 

You say you have a LCD TV/computer monitor. That means its pixel width is fixed. That means that 1280 pixels have a fixed width. There is no way to expand the image unless you increase the resolution.

I could be wrong about this, and would be very grateful if other forum readers would correct me if I'm wrong.

I have no idea how to fix the waviness. I thought that didn't happen on LCD displays...
Actually, I don't have wavy lines.  Instead, some vertical lines are fuzzy, while others are sharp.  Can be hard on the eyes.  This is likely caused by some lines being out of phase and straddling pixels, because the width of the image is not in sync with the resolution of the monitor.

On the code tag question, I am using the editor in "standard mode".  Do I need to switch to "enhanced mode", to use the code tag?

---

### Post by philinux on 2008-06-01
The code tag is the .................................# above when your replying.

---

### Post by anachronon on 2008-06-01
> **philinux said:**
> The code tag is the .................................# above when your replying.
Don't have one of those.

---

### Post by philinux on 2008-06-01
As shown

---

### Post by unutbu on 2008-06-01
anachronon, please post 

```
xvidtune -show
grep pixel /var/log/Xorg.0.log

```
From the output of xvidtune we can compute the refresh rate and horizontal sync rate at which your video card is driving the monitor. The grep command will tell us the maximum pixel clock that the monitor can achieve. If the max pixel clock is great enough, and if your video card can support it, you may be able to run at a higher resolution than 1280x800.

I have read that all LCDs operate at 60 Hz refresh rate, but I am not entirely positive that this is true. Let's test if this is the case for you.

---

### Post by anachronon on 2008-06-01
> **philinux said:**
> As shown
Unfortunately, I don't have most of those controls.  I was going to post a screen shot, but for some reason, I have no way to upload it.

---

### Post by anachronon on 2008-06-01
> **unutbu said:**
> anachronon, please post 

```
xvidtune -show
grep pixel /var/log/Xorg.0.log

```
From the output of xvidtune we can compute the refresh rate and horizontal sync rate at which your video card is driving the monitor. The grep command will tell us the maximum pixel clock that the monitor can achieve. If the max pixel clock is great enough, and if your video card can support it, you may be able to run at a higher resolution than 1280x800.

I have read that all LCDs operate at 60 Hz refresh rate, but I am not entirely positive that this is true. Let's test if this is the case for you.
Here is the output of "xvidtune -show"

> "1280x800"     83.46   1280 1344 1480 1680    800  801  804  828 +hsync +vsync


According to these numbers, its running at a 60Hz refresh rate.

And, here is the output of "grep pixel /var/log/Xorg.0.log":

> (--) NVIDIA(0): CRT-0: 350.0 MHz maximum pixel clock

Is it a problem if the monitoer is labeled "CRT-0", when it is actually an LCD?  Or, is it just a name?

---

### Post by iaculallad on 2008-06-01
What about doing this:

Backup your current xorg.conf file then copy and paste the following sections (Monitor and Scree) to your config file, replacing the original sections from the file (I edited the config file your posted before).

```
Section "Monitor"
	Identifier "Configured Monitor"
	Vendorname "Generic LCD Display"
	Modelname "LCD Panel 1280x1024"
	HorizSync 30-110
	VertRefresh 50-160
EndSection

Section "Screen"
Identifier "Default Screen"
Device "Configured Video Device"
Monitor "Configured Monitor"
DefaultDepth 24
	SubSection "Display"
		Depth 24
		Modes "1280x1024"
	EndSubSection
EndSection
```

---

### Post by unutbu on 2008-06-01
According to [http://www.nvidia.com/page/pg_20040109440047.html](http://www.nvidia.com/page/pg_20040109440047.html), the GeForce FX-5200 (Ultra and GPU) can display resolutions up to 2048×1536 @ 85Hz. Is yours an Ultra or GPU?

Do you have any specs on your monitor? What is the maximum resolution it can display?

If you find that the monitor can display a resolution higher than 1280x800, then you may want to try the instructions [http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973) to see if you can take advantage of your extra horizontal space.

---

### Post by anachronon on 2008-06-02
> **unutbu said:**
> According to [http://www.nvidia.com/page/pg_20040109440047.html](http://www.nvidia.com/page/pg_20040109440047.html), the GeForce FX-5200 (Ultra and GPU) can display resolutions up to 2048×1536 @ 85Hz. Is yours an Ultra or GPU?

Do you have any specs on your monitor? What is the maximum resolution it can display?

If you find that the monitor can display a resolution higher than 1280x800, then you may want to try the instructions [http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973) to see if you can take advantage of your extra horizontal space.
The video card I'm using is a GPU.  According to the manufacturer, the monitor is rated at 1200x800.  Though the card can create higher recolutions, and the monitor can even display a few, the sharpest image should be at 1280x800.

I just seem to have some sort of timing problem, which isn't allowing the 1280 pixels of the image to spread out across all 1280 pixels of the screen.  As a result, the pixels drift in and out of phase as the image is scanned horizontally, creating numerous vertical lines of fuzziness.  If I knew how to post an image to this forum, I photograph a test pattern, to show what I mean.

---

### Post by anachronon on 2008-06-02
> **iaculallad said:**
> What about doing this:

Backup your current xorg.conf file then copy and paste the following sections (Monitor and Scree) to your config file, replacing the original sections from the file (I edited the config file your posted before).

```
Section "Monitor"
	Identifier "Configured Monitor"
	Vendorname "Generic LCD Display"
	Modelname "LCD Panel 1280x1024"
	HorizSync 30-110
	VertRefresh 50-160
EndSection

Section "Screen"
Identifier "Default Screen"
Device "Configured Video Device"
Monitor "Configured Monitor"
DefaultDepth 24
	SubSection "Display"
		Depth 24
		Modes "1280x1024"
	EndSubSection
EndSection
```
OK, I was studying the changes, and I understand which lines I need to change.  Before I do though, I just have a couple questions.  First, I am trying to get my monitor to work properly at 1280x800.  I selected 1280x1024 as a monitor choice because that was the only one to give me the 1280x800 option.

Also, I ran "gksudo nvidia-settings, and that utility added this section to my xorg.conf file:

```
Section "Screen"

# Removed Option "metamodes" "1280x800_60 +0+0; 1024x768@60 +0+0; 800x600@60 +0+0; 800x600@56 +0+0; 640x480@60 +0+0"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "1280x800 +0+0"
EndSection

```

Does this make a difference?

P.S.  Typing my reply, in plain text mode, I tried substituting the command "CODE" where ever it said "QUOTE".  Hopefully, that will give the result I want.

---

### Post by anachronon on 2008-06-08
> **iaculallad said:**
> What about doing this:

Backup your current xorg.conf file then copy and paste the following sections (Monitor and Scree) to your config file, replacing the original sections from the file (I edited the config file your posted before).

```
Section "Monitor"
	Identifier "Configured Monitor"
	Vendorname "Generic LCD Display"
	Modelname "LCD Panel 1280x1024"
	HorizSync 30-110
	VertRefresh 50-160
EndSection

Section "Screen"
Identifier "Default Screen"
Device "Configured Video Device"
Monitor "Configured Monitor"
DefaultDepth 24
	SubSection "Display"
		Depth 24
		Modes "1280x1024"
	EndSubSection
EndSection
```
Well, I tried making these changes to my xorg.cong file.  But, after doing so, X would not load.  So, I simply copied the backup file back to xorg.  Of course, that means that I still have the width problem at 1280x800.

I suspect that the reason it didn't work was because the "nvidia-settings" utility made some changes.  Here is the new xorg.conf file that utility created, the one I am currently using:

```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Generic Keyboard" "CoreKeyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Module"
    Load           "glx"
    Load           "v4l"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
    VendorName     "Generic LCD Display"
    ModelName      "LCD Panel 1280x1024"
    HorizSync       31.5 - 64.0
    VertRefresh     56.0 - 65.0
    Gamma           1
    ModeLine       "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
    ModeLine       "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
    ModeLine       "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
    ModeLine       "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
    ModeLine       "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
    ModeLine       "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
EndSection

Section "Monitor"
    Identifier     "monitor1"
    VendorName     "Plug 'n' Play"
    ModelName      "Plug 'n' Play"
    Gamma           1
    ModeLine       "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-0"
    HorizSync       31.5 - 64.0
    VertRefresh     56.0 - 65.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    BoardName      "nvidia"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "device1"
    Driver         "nvidia"
    BoardName      "nvidia"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce FX 5200"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Virtual     1280 1024
        Depth       24
        Modes      "1280x960@60" "1280x1024@60" "1024x768@60" "800x600@60" "800x600@56" "640x480@60"
    EndSubSection
EndSection

Section "Screen"

	# 
    Identifier     "screen1"
    Device         "device1"
    Monitor        "monitor1"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "640x480@60"
    EndSubSection
EndSection

Section "Screen"

# Removed Option "metamodes" "1280x800_60 +0+0; 1024x768@60 +0+0; 800x600@60 +0+0; 800x600@56 +0+0; 640x480@60 +0+0"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "1280x800 +0+0"
EndSection

```

Note that the normal resolution of this monitor is 1280x800, despite what has been entered into the xorg.conf file.  At this point, I really don't know what to do, as this width problem can't be good for the monitor.

---

### Post by unutbu on 2008-06-08
Before we proceed any farther, please tell us the model and maker of your TV/monitor.

Do you have a Windows machine that you can hook up to the TV/monitor? Are you able to achieve the width that you want? If so, what is the resolution under Windows?

---

### Post by mgmiller on 2008-06-08
Here is the new gui as supplied for hardy:


1) Right click Applications and select "Edit Menus"
2) Scroll to and select, by left clicking, the "Other" location on the left side.
3) On the right side put a check mark in the box next to "Screens and Graphics", then click "Close".
4) Go to Applications > Other > Screens and Graphics
5) On the screen tab, click the drop down next to model.
6) If you can find your model, great, if not, select generic LCD (assuming it's an LCD)
If it is a wide screen monitor, don't forget to check the wide screen box.
7) Now you can find & select your resolution and refresh rate from the list on the right side. Click OK.
8 ) Go to the Graphics Card tab.
9) Click on Driver and select what you need.
10) Click the test button to make sure all is ok.
11) Click ok and you're done.

Pay special attention to #6 above about checking the wide screen monitor check box.  This will set the timings for you for a wide screen monitor at 1280 x 800.

---

### Post by anachronon on 2008-06-08
> **unutbu said:**
> Before we proceed any farther, please tell us the model and maker of your TV/monitor.

Do you have a Windows machine that you can hook up to the TV/monitor? Are you able to achieve the width that you want? If so, what is the resolution under Windows?
The monitor is a Polaroid TLA-01511c.  I don't know if that will help much, as the chassis was likely made by a different manufacturer, like Sharp or Samsung.  Haven't been able to cross reference it.

The only Windows machine I might be able to use is a Dell laptop.  Coincidentally, it also uses 1280x800.  Not sure how to hook it up though, as it is only an occasional loaner.

---

### Post by unutbu on 2008-06-08
Googling "Polaroid TLA-01511c" produced
[http://salestores.com/polaro15.html](http://salestores.com/polaro15.html), which claims the monitor is capable of 1440x900. Perhaps you should try that?

---

### Post by mgmiller on 2008-06-08
Hardy is moving away from using xorg.conf for many settings, although it can still be used to override (sometimes).  

Please refer to my post #31 above and give it a try.

---

### Post by anachronon on 2008-06-09
> **unutbu said:**
> Googling "Polaroid TLA-01511c" produced
[http://salestores.com/polaro15.html](http://salestores.com/polaro15.html), which claims the monitor is capable of 1440x900. Perhaps you should try that?
That makes sense.  In fact, that makes a whole lot more sense than the "1280x800" quoted in the owner's manual that I downloaded from Polaroid.  It makes sense because the monitor switches to 720x400 whenever in pure text mode (terminal/root).  I saw that, and I wondered if I should really be trying 1440 width.  But, I guess that I was just too hung up on the "1280" quoted in the manual.  Perhaps, sometimes, reading the instructions is NOT the best way to go.  Thanks for finding that; I never would have thought.

Anyway, as soon as I get a chance, I'll give 1440x900 a shot, see if it is supported, what bugs I might have, etc.  I think I'll start with the method described in post #31 (above), and if that doesn't work, I'll use the other tricks I've picked up from this thread.  One way or the other, I'll let everyone know what happened.

---

### Post by anachronon on 2008-06-09
> **mgmiller said:**
> Here is the new gui as supplied for hardy:


1) Right click Applications and select "Edit Menus"
2) Scroll to and select, by left clicking, the "Other" location on the left side.
3) On the right side put a check mark in the box next to "Screens and Graphics", then click "Close".
4) Go to Applications > Other > Screens and Graphics
5) On the screen tab, click the drop down next to model.
6) If you can find your model, great, if not, select generic LCD (assuming it's an LCD)
If it is a wide screen monitor, don't forget to check the wide screen box.
7) Now you can find & select your resolution and refresh rate from the list on the right side. Click OK.
8 ) Go to the Graphics Card tab.
9) Click on Driver and select what you need.
10) Click the test button to make sure all is ok.
11) Click ok and you're done.

Pay special attention to #6 above about checking the wide screen monitor check box.  This will set the timings for you for a wide screen monitor at 1280 x 800.
I tried this.  But unfortunately, there are no options under "other" (step 4) that I can check.  That was a far as I got.

---

### Post by anachronon on 2008-06-09
> **unutbu said:**
> Googling "Polaroid TLA-01511c" produced
[http://salestores.com/polaro15.html](http://salestores.com/polaro15.html), which claims the monitor is capable of 1440x900. Perhaps you should try that?
Well, it seems that I don't have support for 1440x900.  I can select that size of LCD monitor in "gksudo displayconfig-gtk".  But, again, I cannot select that resolutuon.  I have tried both the options in "dispalyconfig" and "xrandr".  I also played with other resolutions, but none listed 1440x900 as an option.

Don't know if it is a Linux driver problem, or if my card does not support that resolution.  If it is the card, I don't know what I'm going to do.

As I started to say earlier, 1440x900 makes a lot of sense, as the monitor switches into 720x400 when booting (text only), and that image DOES fill the screen.  Seems that the native resolution (width) may truly be 1440.

---

### Post by unutbu on 2008-06-09
```

cd /etc/X11
sudo mv xorg.conf xorg.conf.20080609
gksudo gedit xorg.conf

```

A blank text editing window will appear. Paste this into it:

```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Screen0" 0 0
    InputDevice    "Generic Keyboard" "CoreKeyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Module"
    Load           "glx"
    Load           "v4l"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce FX 5200"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-0"
    HorizSync       31.5 - 64.0
    VertRefresh     56.0 - 65.0
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection "Display"
    	 Depth 24
	 Modes "1440x900"
    EndSubSection
EndSection

```
Save and exit.
Log out. Press Ctrl-Alt-Backspace to restart the X server. If it doesn't work, post /var/log/Xorg.0.log.

---

### Post by mgmiller on 2008-06-09
> I tried this. But unfortunately, there are no options under "other" (step 4) that I can check. That was a far as I got.

If you successfully did steps 1 through 3, then "Screens and Graphics" should appear in "Other".  If you did not do steps 1,2 & 3, then step 4 will not work.

You may need to log off and back on to make it appear in your menus.

The "Screens and Graphics" GUI is a new feature that was added for Hardy, but was not made visible in the menus by default.  If you are running Hardy Heron, then you should have this.  It makes setting up your monitor very easy.

You can also run it from terminal:
```
gksu displayconfig-gtk
```

---

### Post by anachronon on 2008-06-10
I tried pasting the above code (post #38) into xorg.conf, but unfortunately, all I got was a blue screen saying that it was "not supported".

Now, to add to my frustration, for some reason, the forum quick-reply won't let me post the output of in /var/log/Xorg.0.log.  It claims that I am trying to include 25 images in my reply, when there is nothing but plain text.

---

### Post by unutbu on 2008-06-10
```
cp /var/log/Xorg.0.log .
bzip2 Xorg.0.log
```

Then try to attach ~/Xorg.0.log.bz2.

---

### Post by mgmiller on 2008-06-10
> It claims that I am trying to include 25 images in my reply, when there is nothing but plain text.

If you click the "Preview Post" button before trying to post, you will see the problem.  Many of the strings of text correspond to "smileys" and each is counted as an image.


Have you tried entering the command I posted in my last entry in a terminal to run the screens and graphics GUI?

---

### Post by anachronon on 2008-06-10
> **mgmiller said:**
> If you click the "Preview Post" button before trying to post, you will see the problem.  Many of the strings of text correspond to "smileys" and each is counted as an image.


Have you tried entering the command I posted in my last entry in a terminal to run the screens and graphics GUI?
I don't get it.  For some reason, I don't have a "Preview Post" button anymore!  I used to, but, for some reason, it and a lot of other controls are gone.  I checked my settings, and I'm still on "standard".  It won't even let me post a screen shot, so that everyone else can see.  This is true of both Firefox on the Linux machine that I am trying to get going, and the Windoze laptop.

AAAAAARRRRRGH!!!

---

### Post by mgmiller on 2008-06-10
> I don't get it. For some reason, I don't have a "Preview Post" button anymore! 

This happens if you try to go back and edit an existing post of yours.  You would need to click the "go advanced" button to get all the choices back.

On a fresh post though, all the choices should be there.

---

### Post by anachronon on 2008-06-11
Thanks for the "Go Advanced" tip.  That fixed a number of infuriating problems.  Anyway, here is the output from /var/log/Xorg.0.log, when I tried the new xorg from post from "unutbu" (I disabled the smilies so that it would post):

> This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at [http://bugs.freedesktop.org/](http://bugs.freedesktop.org/).
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See [http://wiki.x.org/wiki/GitPage](http://wiki.x.org/wiki/GitPage) for git access instructions.

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9)
Current Operating System: Linux the-beast 2.6.24-18-rt #1 SMP PREEMPT RT Wed May 28 23:38:58 UTC 2008 i686
Build Date: 15 April 2008  05:26:17PM
 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Jun 10 14:38:49 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Videocard0"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81dc500
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 2.0
	X.Org XInput driver : 2.0
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Video Driver, version 2.0
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1039,0655 card 1043,80aa rev 50 class 06,00,00 hdr 80
(II) PCI: 00:01:0: chip 1039,0003 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:02:0: chip 1039,0964 card 0000,0000 rev 36 class 06,01,00 hdr 80
(II) PCI: 00:02:5: chip 1039,5513 card 1043,810e rev 01 class 01,01,80 hdr 00
(II) PCI: 00:02:7: chip 1039,7012 card 1043,810d rev a0 class 04,01,00 hdr 00
(II) PCI: 00:03:0: chip 1039,7001 card 1043,810e rev 0f class 0c,03,10 hdr 80
(II) PCI: 00:03:1: chip 1039,7001 card 1043,810e rev 0f class 0c,03,10 hdr 00
(II) PCI: 00:03:2: chip 1039,7001 card 1043,810e rev 0f class 0c,03,10 hdr 00
(II) PCI: 00:03:3: chip 1039,7002 card 1043,810e rev 00 class 0c,03,20 hdr 00
(II) PCI: 00:04:0: chip 1039,0900 card 1043,80a7 rev 91 class 02,00,00 hdr 00
(II) PCI: 00:05:0: chip 1039,0180 card 1043,810e rev 01 class 01,04,85 hdr 00
(II) PCI: 01:00:0: chip 10de,0322 card 1458,3419 rev a1 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfca00000 - 0xfeafffff (0x2100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xe7f00000 - 0xf7efffff (0x10000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:2:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) nVidia Corporation NV34 [GeForce FX 5200] rev 161, Mem @ 0xfd000000/24, 0xe8000000/27, BIOS @ 0xfeae0000/17
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xf8000000 from 0xfbffffff to 0xf7ffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xfebfb000 - 0xfebfbfff (0x1000) MX[B]
	[1] -1	0	0xfebff000 - 0xfebfffff (0x1000) MX[B]
	[2] -1	0	0xfebfe000 - 0xfebfefff (0x1000) MX[B]
	[3] -1	0	0xfebfd000 - 0xfebfdfff (0x1000) MX[B]
	[4] -1	0	0xfebfc000 - 0xfebfcfff (0x1000) MX[B]
	[5] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[6] -1	0	0xfeae0000 - 0xfeafffff (0x20000) MX[B](B)
	[7] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[8] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[9] -1	0	0x0000ef90 - 0x0000ef9f (0x10) IX[B]
	[10] -1	0	0x0000efe0 - 0x0000efe3 (0x4) IX[B]
	[11] -1	0	0x0000efa8 - 0x0000efaf (0x8) IX[B]
	[12] -1	0	0x0000efe4 - 0x0000efe7 (0x4) IX[B]
	[13] -1	0	0x0000eff0 - 0x0000eff7 (0x8) IX[B]
	[14] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[15] -1	0	0x0000ec00 - 0x0000ec7f (0x80) IX[B]
	[16] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[17] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[19] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfebfb000 - 0xfebfbfff (0x1000) MX[B]
	[1] -1	0	0xfebff000 - 0xfebfffff (0x1000) MX[B]
	[2] -1	0	0xfebfe000 - 0xfebfefff (0x1000) MX[B]
	[3] -1	0	0xfebfd000 - 0xfebfdfff (0x1000) MX[B]
	[4] -1	0	0xfebfc000 - 0xfebfcfff (0x1000) MX[B]
	[5] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[6] -1	0	0xfeae0000 - 0xfeafffff (0x20000) MX[B](B)
	[7] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[8] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[9] -1	0	0x0000ef90 - 0x0000ef9f (0x10) IX[B]
	[10] -1	0	0x0000efe0 - 0x0000efe3 (0x4) IX[B]
	[11] -1	0	0x0000efa8 - 0x0000efaf (0x8) IX[B]
	[12] -1	0	0x0000efe4 - 0x0000efe7 (0x4) IX[B]
	[13] -1	0	0x0000eff0 - 0x0000eff7 (0x8) IX[B]
	[14] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[15] -1	0	0x0000ec00 - 0x0000ec7f (0x80) IX[B]
	[16] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[17] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[19] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[20] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfebfb000 - 0xfebfbfff (0x1000) MX[B]
	[5] -1	0	0xfebff000 - 0xfebfffff (0x1000) MX[B]
	[6] -1	0	0xfebfe000 - 0xfebfefff (0x1000) MX[B]
	[7] -1	0	0xfebfd000 - 0xfebfdfff (0x1000) MX[B]
	[8] -1	0	0xfebfc000 - 0xfebfcfff (0x1000) MX[B]
	[9] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[10] -1	0	0xfeae0000 - 0xfeafffff (0x20000) MX[B](B)
	[11] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[12] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000ef90 - 0x0000ef9f (0x10) IX[B]
	[16] -1	0	0x0000efe0 - 0x0000efe3 (0x4) IX[B]
	[17] -1	0	0x0000efa8 - 0x0000efaf (0x8) IX[B]
	[18] -1	0	0x0000efe4 - 0x0000efe7 (0x4) IX[B]
	[19] -1	0	0x0000eff0 - 0x0000eff7 (0x8) IX[B]
	[20] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[21] -1	0	0x0000ec00 - 0x0000ec7f (0x80) IX[B]
	[22] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[23] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
(II) "extmod" will be loaded by default.
(II) "dbe" will be loaded by default.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "freetype" will be loaded by default.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
(II) NVIDIA GLX Module  169.12  Thu Feb 14 18:45:56 PST 2008
(II) Loading extension GLX
(II) LoadModule: "v4l"
(II) Loading /usr/lib/xorg/modules/drivers//v4l_drv.so
(II) Module v4l: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 0.1.1
	ABI class: X.Org Video Driver, version 2.0
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.4.0.90, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.4.0, module version = 1.2.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 2.0
(II) v4l driver for Video4Linux
(II) NVIDIA dlloader X Driver  169.12  Thu Feb 14 17:55:38 PST 2008
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Assigning device section with no busID to primary device
(--) Chipset NVIDIA GPU found
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
	compiled for 1.4.0.90, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfebfb000 - 0xfebfbfff (0x1000) MX[B]
	[5] -1	0	0xfebff000 - 0xfebfffff (0x1000) MX[B]
	[6] -1	0	0xfebfe000 - 0xfebfefff (0x1000) MX[B]
	[7] -1	0	0xfebfd000 - 0xfebfdfff (0x1000) MX[B]
	[8] -1	0	0xfebfc000 - 0xfebfcfff (0x1000) MX[B]
	[9] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[10] -1	0	0xfeae0000 - 0xfeafffff (0x20000) MX[B](B)
	[11] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[12] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[13] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[14] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[15] -1	0	0x0000ef90 - 0x0000ef9f (0x10) IX[B]
	[16] -1	0	0x0000efe0 - 0x0000efe3 (0x4) IX[B]
	[17] -1	0	0x0000efa8 - 0x0000efaf (0x8) IX[B]
	[18] -1	0	0x0000efe4 - 0x0000efe7 (0x4) IX[B]
	[19] -1	0	0x0000eff0 - 0x0000eff7 (0x8) IX[B]
	[20] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[21] -1	0	0x0000ec00 - 0x0000ec7f (0x80) IX[B]
	[22] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[23] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfebfb000 - 0xfebfbfff (0x1000) MX[B]
	[5] -1	0	0xfebff000 - 0xfebfffff (0x1000) MX[B]
	[6] -1	0	0xfebfe000 - 0xfebfefff (0x1000) MX[B]
	[7] -1	0	0xfebfd000 - 0xfebfdfff (0x1000) MX[B]
	[8] -1	0	0xfebfc000 - 0xfebfcfff (0x1000) MX[B]
	[9] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[10] -1	0	0xfeae0000 - 0xfeafffff (0x20000) MX[B](B)
	[11] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[12] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[13] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[14] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[15] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000ef90 - 0x0000ef9f (0x10) IX[B]
	[19] -1	0	0x0000efe0 - 0x0000efe3 (0x4) IX[B]
	[20] -1	0	0x0000efa8 - 0x0000efaf (0x8) IX[B]
	[21] -1	0	0x0000efe4 - 0x0000efe7 (0x4) IX[B]
	[22] -1	0	0x0000eff0 - 0x0000eff7 (0x8) IX[B]
	[23] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[24] -1	0	0x0000ec00 - 0x0000ec7f (0x80) IX[B]
	[25] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[26] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[31] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[32] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
(II) NVIDIA(0): NVIDIA GPU GeForce FX 5200 (NV34) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 131072 kBytes
(--) NVIDIA(0): VideoBIOS: 04.34.20.87.00
(II) NVIDIA(0): Detected AGP rate: 8X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce FX 5200 at PCI:1:0:0:
(--) NVIDIA(0):     CRT-0
(--) NVIDIA(0): CRT-0: 350.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1440x900"
(II) NVIDIA(0): Virtual screen size determined to be 1440 x 900
(WW) NVIDIA(0): Unable to get display device CRT-0's EDID; cannot compute DPI
(WW) NVIDIA(0):     from CRT-0's EDID.
(==) NVIDIA(0): DPI set to (75, 75); computed from built-in default
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfebfb000 - 0xfebfbfff (0x1000) MX[B]
	[5] -1	0	0xfebff000 - 0xfebfffff (0x1000) MX[B]
	[6] -1	0	0xfebfe000 - 0xfebfefff (0x1000) MX[B]
	[7] -1	0	0xfebfd000 - 0xfebfdfff (0x1000) MX[B]
	[8] -1	0	0xfebfc000 - 0xfebfcfff (0x1000) MX[B]
	[9] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[10] -1	0	0xfeae0000 - 0xfeafffff (0x20000) MX[B](B)
	[11] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[12] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[13] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[14] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[15] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[16] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[17] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[18] -1	0	0x0000ef90 - 0x0000ef9f (0x10) IX[B]
	[19] -1	0	0x0000efe0 - 0x0000efe3 (0x4) IX[B]
	[20] -1	0	0x0000efa8 - 0x0000efaf (0x8) IX[B]
	[21] -1	0	0x0000efe4 - 0x0000efe7 (0x4) IX[B]
	[22] -1	0	0x0000eff0 - 0x0000eff7 (0x8) IX[B]
	[23] -1	0	0x0000e400 - 0x0000e4ff (0x100) IX[B]
	[24] -1	0	0x0000ec00 - 0x0000ec7f (0x80) IX[B]
	[25] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[26] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[31] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[32] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) NVIDIA(0): Initialized AGP GART.
(II) NVIDIA(0): Setting mode "1440x900"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(II) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(==) RandR enabled
(II) Setting vga for screen 0.
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) Initializing extension GLX
(**) Option "CoreKeyboard"
(**) Generic Keyboard: always reports core events
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(WW) Configured Mouse: No Device specified, looking for one...
(II) Configured Mouse: Setting Device option to "/dev/input/mice"
(--) Configured Mouse: Device: "/dev/input/mice"
(==) Configured Mouse: Protocol: "Auto"
(**) Configured Mouse: always reports core events
(**) Option "Device" "/dev/input/mice"
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(--) Configured Mouse: PnP-detected protocol: "ExplorerPS/2"
(II) Configured Mouse: ps2EnableDataReporting: succeeded

---

### Post by unutbu on 2008-06-11
I find it particulary interesting that Xorg.0.log shows no error message when it set the mode to 1440x900:

```
(II) NVIDIA(0): Setting mode "1440x900"
```

I am completely stumped as to why X would not leave an  error message in Xorg.0.log, and yet give you a blue screen and an "not supported" message when you log in.

How about try this: using the same xorg.conf (to set 1440x900 mode), restart X and try to log in. You'll get the blue screen and the "not supported" message.  Please copy it down so we can take a look at exactly what it says. Press 'Ok' if it gives you that option. Then I suppose you'll be tossed back to the gdm login screen. 

Now press Ctrl-Alt-F2 to get to a virtual terminal.
Log in, and type
```

cp ~/.xsession-errors ~/.xsession-errors-20080611
```

Then post the complete "not supported" error message, and the contents of .xsession-errors-20080611.

---

### Post by anachronon on 2008-06-11
> **unutbu said:**
> I find it particulary interesting that Xorg.0.log shows no error message when it set the mode to 1440x900:

```
(II) NVIDIA(0): Setting mode "1440x900"
```

I am completely stumped as to why X would not leave an  error message in Xorg.0.log, and yet give you a blue screen and an "not supported" message when you log in.

How about try this: using the same xorg.conf (to set 1440x900 mode), restart X and try to log in. You'll get the blue screen and the "not supported" message.  Please copy it down so we can take a look at exactly what it says. Press 'Ok' if it gives you that option. Then I suppose you'll be tossed back to the gdm login screen. 

Now press Ctrl-Alt-F2 to get to a virtual terminal.
Log in, and type
```

cp ~/.xsession-errors ~/.xsession-errors-20080611
```

Then post the complete "not supported" error message, and the contents of .xsession-errors-20080611.


Actually, there is no error message on the blue screen, other than the words, "Not Supported".  Even the monitor's menu had no clues.  I figured that it would at least show what resolution it was trying to display

Here is the output of the xsession-errors:

```
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
SESSION_MANAGER=local/the-beast:/tmp/.ICE-unix/5324
** Message: another SSH agent is running at: /tmp/ssh-KSVWGf5324/agent.5324
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
xrdb:  "*Label.background" on line 220 overrides entry on line 150
xrdb:  "*Text.background" on line 226 overrides entry on line 191
xrdb:  "*Label.foreground" on line 232 overrides entry on line 151
xrdb:  "*Text.foreground" on line 238 overrides entry on line 192
Window manager warning: Failed to read saved session file /home/dustin/.metacity/sessions/default0.ms: Failed to open file '/home/dustin/.metacity/sessions/default0.ms': No such file or directory
11
seahorse nautilus module initialized
Initializing nautilus-share extension
Initializing nautilus-image-converter extension

** (nautilus:5441): WARNING **: Unable to add monitor: Not supported
x-session-manager: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
gnome-settings-daemon: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
XIO:  fatal IO error 0 (Success) on X server ":0.0"

gnome-panel: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
      after 12 requests (12 known processed) with 0 events remaining.

Window manager warning: nautilus: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
Fatal IO error 11 (Resource temporarily unavailable) on display ':0.0'.
firefox: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
update-notifier: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
applet.py: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
gnome-screensaver: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
[1213228883,000,xklavier.c:xkl_engine_start_listen/] 	The backend does not require manual layout management - but it is provided by the application
```

There seem to be quite a few references to "Fatal IO error 11".  I also noticed that it could not find a file called "/.metacity/sessions/default0.ms".

Also, there is a possibility that my monitor can't support 1440x900.  That was obviously an upgrade added to this model in mid-production.  The question is whether mine was made before or after that upgrade.

Also, there may be a question as the whether the video card is addressing the ports in a way that the monitor can understand.  About 15 years back, I remember there being no standard for the resolutions higher than 640x480.  Each manufacturer seemed to have their own system, and finding the right set of commands was often by trial and error.

---

### Post by mgmiller on 2008-06-12
The "not supported" error messages are produced by the monitor, not the OS, hence there will not be an error log file produced.  As far as the OS is concerned, it is sending a valid signal to the monitor.  What the monitor is doing with that signal is another story. 

Try reducing your color depth and see what happens.  I had a monitor recently that does 1280x1024, but constantly told me out of range on startup till I changed my color depth to 8 bit for the vesa mode graphics driver used during boot.  startupmanager made it very easy to set that up.

---

### Post by jtrindle on 2008-06-12
According to other sites, this monitor is good for 1280x800, not the 1440x900 res mentioned above.

I suggest you drop back to 1280x800, and change the line

HorizSync       31.5 - 64.0

in your xorg.conf  to

HorizSync       31.5 - 80.0

and see what happens.

---

### Post by anachronon on 2008-06-12
> **jtrindle said:**
> According to other sites, this monitor is good for 1280x800, not the 1440x900 res mentioned above.

I suggest you drop back to 1280x800, and change the line

HorizSync       31.5 - 64.0

in your xorg.conf  to

HorizSync       31.5 - 80.0

and see what happens.
Went back to 1280x800, and made the change to HorizSync suggested.  No effect.

---

### Post by mgmiller on 2008-06-12
You can also try switching between 16 and 24 bit color depth for your desktop resolution.  When using the standard drivers  after logging on, this used to cause a lot of problems.  It was supposedly fixed about 1 1/2 years ago, but, it's easy to test.

---

### Post by anachronon on 2008-06-12
Y'know, the more I study this, the more I am convinced that it is a hardware problem, and not a software problem.  Upon closer inspection, ALL of the screen modes seem to have a width problem.  If I go to one of the more standard modes, like 640x480 or 1024x768, circles look like eggs standing on end.  At first, I thought that it was just an optical illusion, caused by all of the blank space on the sides.  But, the image really IS distorted in all modes.

Further, whenever I go into recovery mode, where I just have a terminal/text screen, it switches to 720x400, which DOES fill the screen.  But then, why that resolution, instead of 640x400 or 720x450, which would match the aspect ratio of the screen?  There's something funny going on here!  The width seems to be off by a factor of 640/720 (1280/1440) or 0.89.

However, I did not have this problem when I was first putting this machine together.  At that time, I was using a funky, old CRT.  It had a terrible picture, but the width and height were just fine.  The width problem didn't start until I switched to this Polaroid (Hemorrhoid) flat-panel.  If I was having this problem with an old CRT, I would know how to fix it.  But, I know nothing about the guts of these new LCD's.

---

### Post by anachronon on 2008-06-13
> **mgmiller said:**
> You can also try switching between 16 and 24 bit color depth for your desktop resolution.  When using the standard drivers  after logging on, this used to cause a lot of problems.  It was supposedly fixed about 1 1/2 years ago, but, it's easy to test.
Well, gave that a try.  No effect.  Width still too small.

Has anyone found a hardware problem, similar to the one I mentioned above?  If so, are there any fixes?

---

### Post by anachronon on 2008-06-16
Nobody has any more thoughts on this quandary?  Is there any way of knowing whether the problem is the monitor or the card?

---

### Post by mgmiller on 2008-06-17
> Nobody has any more thoughts on this quandary?  Is there any way of knowing whether the problem is the monitor or the card?

I did some googling on your monitor and graphics card and I suspect the problem is that your graphics card does not support 1440x900 which is the native resolution of your monitor.

I found this list of supported resolutions for your card on the last page of a pdf at this site:
[http://www.fujitsu-siemens.co.uk/rl/servicesupport/techsupport/boards/graphic/nVidia/geforcefx5/GeForce_FX_Series_enu.pdf](http://www.fujitsu-siemens.co.uk/rl/servicesupport/techsupport/boards/graphic/nVidia/geforcefx5/GeForce_FX_Series_enu.pdf)


                         
   Resolution
   640 x 480              
   800 x 600              
   1024 x 768             
   1152 x 864
   1280 x 768             
   1280 x 960             
   1280 x 1024            
   1600 x 1200            
   1920 x 1440             
   2048 x 1536

I had a similar problem a while back when I wanted to change from a 19" 1280x1024 monitor to a wide screen 1680 x 1050 22".  I was using an AGP nvidia geforce 6800, which did not do wide screen.  I had to get nvidia 7800 to run my monitor at it's native resolution.  

Since you are using a TV as a monitor, it may have some other controls that allows it to fill the screen from the signal it's getting.  On your remote, is there a button labelled "wide"?  If so, try toggling that.  There may also be something in the on screen setup that lets it stretch images.  

I realize these are not perfect solutions as it may result in a distorted picture, but short of getting a different video card that you know supports 1440 x 900, you may be stuck.  

Price out standard aspect ratio (non-widescreen) 17" and 19" monitors.  These use 1280 x 1024 and should work fine with your video card.  They are also fairly inexpensive these days.  They would make a nice upgrade to the 15" screen you are using now and the price difference between a new video card to keep the 15" screen versus  a 19" monitor using your existing video card will not be that huge.

---

### Post by anachronon on 2008-06-17
> **mgmiller said:**
> I did some googling on your monitor and graphics card and I suspect the problem is that your graphics card does not support 1440x900 which is the native resolution of your monitor.

I found this list of supported resolutions for your card on the last page of a pdf at this site:
[http://www.fujitsu-siemens.co.uk/rl/servicesupport/techsupport/boards/graphic/nVidia/geforcefx5/GeForce_FX_Series_enu.pdf](http://www.fujitsu-siemens.co.uk/rl/servicesupport/techsupport/boards/graphic/nVidia/geforcefx5/GeForce_FX_Series_enu.pdf)


                         
   Resolution
   640 x 480              
   800 x 600              
   1024 x 768             
   1152 x 864
   1280 x 768             
   1280 x 960             
   1280 x 1024            
   1600 x 1200            
   1920 x 1440             
   2048 x 1536

I had a similar problem a while back when I wanted to change from a 19" 1280x1024 monitor to a wide screen 1680 x 1050 22".  I was using an AGP nvidia geforce 6800, which did not do wide screen.  I had to get nvidia 7800 to run my monitor at it's native resolution.  

Since you are using a TV as a monitor, it may have some other controls that allows it to fill the screen from the signal it's getting.  On your remote, is there a button labelled "wide"?  If so, try toggling that.  There may also be something in the on screen setup that lets it stretch images.  

I realize these are not perfect solutions as it may result in a distorted picture, but short of getting a different video card that you know supports 1440 x 900, you may be stuck.  

Price out standard aspect ratio (non-widescreen) 17" and 19" monitors.  These use 1280 x 1024 and should work fine with your video card.  They are also fairly inexpensive these days.  They would make a nice upgrade to the 15" screen you are using now and the price difference between a new video card to keep the 15" screen versus  a 19" monitor using your existing video card will not be that huge.
Thanks for that.  One of the first things I tried was the "wide" button (it's labeled "Pic Size" on this remote).  It will stretch a standard aspect ratio image (like 1024x768) to fill the screen.  But unfortunately, the feature is disabled when the monitor/TV is receiving a wide-screen signal.

So, I guess the video card just can't handle a wide-screen monitor.  I wish that I could afford a more compatible monitor.  But unfortunately, I live on a very small, fixed income.  I could not afford a new monitor, no matter how "cheap" they might be.  Virtually this entire computer has been put together from parts salvaged from other machines.  As for the TV/monitor I am using, that was donated by a former in-law, when he saw the funky old CRT that I was going to try to use.  The monitor had just been gathering dust at his place.

So, I don't know.  Should I just tag this thread as "solved", and let it go.  Don't know what else to do.  I had been dreaming of doing graphics work on this computer.  But, this machine is pretty useless to me in its present state.

---

### Post by mgmiller on 2008-06-17
Just for giggles, lets try one last thing.

Run:
```
nvidia-settings
```Click "X Server Display Configuration" on the left side.

On the right side, click the "Resolution" drop down and see if 1440 x 900 is listed.  If it is, select it and then click the " Apply" button and if all is OK, click "Save to X Configuration File" button.

You can also experiment with the "Detect Display" button to see if it finds your display.

If it isn't, try clicking the "Advanced" button and in the "Panning" field, try entering 1440 x 900 and then click the "Save to X,etc." button as above.

Also, on the left side try clicking on the triangle to the left of "GPU 0" to open the list below it and then click on DFP-1 to get the settings for the monitor.  
On the right side there are some "Flat Panel Scaling" options that you can play with.

---

### Post by anachronon on 2008-06-18
> **mgmiller said:**
> Just for giggles, lets try one last thing.

Run:
```
nvidia-settings
```Click "X Server Display Configuration" on the left side.

On the right side, click the "Resolution" drop down and see if 1440 x 900 is listed.  If it is, select it and then click the " Apply" button and if all is OK, click "Save to X Configuration File" button.

You can also experiment with the "Detect Display" button to see if it finds your display.

If it isn't, try clicking the "Advanced" button and in the "Panning" field, try entering 1440 x 900 and then click the "Save to X,etc." button as above.

Also, on the left side try clicking on the triangle to the left of "GPU 0" to open the list below it and then click on DFP-1 to get the settings for the monitor.  
On the right side there are some "Flat Panel Scaling" options that you can play with.
Success?  I played with the settings that you mentioned, and the results were mixed.  I tried using the "Advanced->Panning" option to set my resolution to 1440x900, but it was not supported.

Under "GPU 0", there is no "DFP-1", only "Power Mizer" and "CRT-0".  CRT-0 did not have the adjustmensts that I needed.

However, I WAS successful with the "Resolution" drop-down menu.  When I tried 1280x768, I actually (finally) got a full screen!  Funny thing is, the monitor now claims that it is diplaying 1366x768.  What resolution I REALLY have is a good question.  This monitor/graphics card combination just can't seem to get it together.  "System->Preferences->Screen Resolution" still thinks I'm at 1280x768.  But, it seems to be working; the circles are round and the text is more readable.

Still, before I mark this as "solved", perhaps I should wait for others to chime in.  Does anyone see any potential problems here?  IMO, the image could be a little clearer (pixel phasing), but that may be because this is a TV being used as a monitor, and is subject to some compromise.  Any other thoughts?

---

### Post by mgmiller on 2008-06-18
> IMO, the image could be a little clearer (pixel phasing), but that may be because this is a TV being used as a monitor, and is subject to some compromise. Any other thoughts?Go to System > Preferences > Appearance and click on the "Fonts" tab.

Under the rendering area near the bottom, click on "Sub Pixel Smoothing (LCDs)".

That should sharpen things up a bit.

As far as potential problems, as long as the panel is displaying an image, it is not out of range for it and will not harm anything.  I think that if you are getting full screen with round circles, etc.  you should count your blessings and consider it "fixed".

I also had a video card once that had the system say 1280 x 768, but the display (also an LCD TV) thought it was getting 1366 x 768 and displayed full screen without any other issues.  I lived with it.

Hopefully, things will be sharp enough for you to now do the image editing you wanted to do.

---

### Post by anachronon on 2008-06-19
Well,thanks everyone for all of your help.  It looks like I can go ahead and mark this thread as solved.  Apparently, the answer to fixing the width problem is to set the resolution to "1280x768" (not 1280x800).  This seems to be a trend with these new, combo, flat-panel TV/monitors.  The "1366x768" reading on the monitor is just a fluke generated by the 16x9 aspect-ratio circuitry.

As for the image quality, it is obviously not all that a good LCD could produce.  It is a compromise caused by the monitor's duel function.  The suggestion above ("Sub Pixel Smoothing (LCDs)")did sharpen the text a little, but not all the way.  Still, it's better than the image produced by most old CRT's.  I suppose the only real problem might come when I try to sharpen photos.  But, hopefully, I can live with it until I find a real monitor.

Thanks all.

---

### Post by mgmiller on 2008-06-20
One last suggestion.  Some LCD TV's do fine using a regular VGA cable for the video, but some do much better if you use a DVI-d cable instead.  See if there is a DVI input on the back of the TV and if you have a DVI output on your video card.  

Unfortunately, this costs something to implement, unless you can borrow a cable from someone to try it with first.  

To make sure the video card is using the DVI port (assuming it has one) turn off the computer before swapping the cable and make sure the TV is turned on and the DVI input is selected before booting up.

I used this technique with a 30" Syntax/Olevia LCD-TV a friend of mine had and the difference was striking.

PS;

To officially thank someone in the forums, look in one of their helpful posts and click the gold star in the lower right corner.

---

### Post by anachronon on 2008-06-20
> **mgmiller said:**
> One last suggestion.  Some LCD TV's do fine using a regular VGA cable for the video, but some do much better if you use a DVI-d cable instead.  See if there is a DVI input on the back of the TV and if you have a DVI output on your video card.  

Unfortunately, this costs something to implement, unless you can borrow a cable from someone to try it with first.  

To make sure the video card is using the DVI port (assuming it has one) turn off the computer before swapping the cable and make sure the TV is turned on and the DVI input is selected before booting up.

I used this technique with a 30" Syntax/Olevia LCD-TV a friend of mine had and the difference was striking.

PS;

To officially thank someone in the forums, look in one of their helpful posts and click the gold star in the lower right corner.
Thanks.  This particular video card doesn't have a DVI output.  However, I did ask my brother-in-law about that.  He had been using this TV/monitor to play video games, and he claimed that the VGA port yielded much better results from a computer than the DVI port.

Yes, I found the little gold stars.  In fact, I sent you one yesterday.

---

