---
title: "HOWTO: Screen Resolution in Hoary 5.04"
date: 2005-03-25
forum: Outdated Tutorials &amp; Tips
---

### Post by Cybermagellan on 2005-03-25
**DISCLAIMER:** I am not responsible if the steps you take cause your video card/monitor to become a projectile or otherwise increase the refresh rate to the point of cooking your popcorn that is sitting in a bag beside it.

Xorg  only see's that my monitor can handle 1024x768. Well I'm not blind and I'm 24 so I'm not losing my sight so what was the next logical step after not being able to install the Nvidia card I have. That's right deal with what I have onboard and make Hoary think my monitor can handle 1280x1024 (which it did in Windows but we wont go there).

Step:

1. In Hoary we use Xorg so lets get there. Open up to...  /etc/X11/

2. Open up xorg.conf in a text editor (gedit works PERFECT for this) however make sure you have write permissions so we can edit this file.

3. Scroll down to the bottom of the file. You should see some lines as:

```
SubSection "Display"
		Depth		1
		Modes	          "1024x768" "800x600" "640x480"
	EndSubSection
``` 

Now I know what everyone is thinking but I'll never use a color depth of 1. Well ladies and gents I didn't make the rules and this is a demo anywas but pay attention.

4. Notice a format here... Mode [resolution] [resolution] [resolution]? Right so when in Rome...do as the Romans. Add a resolution so it looks like this.

```
SubSection "Display"
		Depth		1
		Modes		**"1280x1024"** "1024x768" "800x600" "640x480"
	EndSubSection
``` 

5. Now repeat for all the Depths you have 1,4,8,15,16,24...whatever.

6. Save file, Reboot the computer. When it comes back up you should see your new lovely screen.

Like I said this worked for me. I also wrote the ACPI HOWTO in this forum. Notice how everything is my own experience. Bingo. Now go forth and be fruitful.

Shawn

---

### Post by ctrlz on 2005-03-25
Thanks for the great HOWTO, Shawn!

I just want to make a minor suggestion for Step 6. It is not necessary to reboot the computer. I would suggest editing Step 6 to say:

6. Save file, CTRL+ALT+F1, then: sudo /etc/init.d/gdm restart

You can take it, or leave it :) I just find it much easier to restart GDM instead of rebooting.

---

### Post by Cybermagellan on 2005-03-25
Yeah while it really isn't I find when I crash GDM (Ctrl+Alt+Backspace) or like you said restart it (Ctrl+Alt+F1) my monitor makes wierd noises. I already lost one monitor due  to refreshing blowing out the gun in it....I can't afford to do it again. But yes your right if you have like a plasma screen or a LCD monitor you can definatly restart X and it'll take effect.

Shawn

---

### Post by kezza on 2005-03-25
I looked into my xorg.conf and found only one resolution "1280X800" available for all resolution depths. Thing is, my display is running at 1024x760 only. Hoary's desktop resolution tool only makes the 1024 resolution available also !

Doing sudo dpkg-reconfigure xserver-xorg doesn't help either.

I have a widescreen laptop, and every other aspect of Ubuntu is absolutely fine - I'd just like to be able to use my full screen real estate. Any clues ?

---

### Post by Darrena on 2005-03-25
[QUOTE=kezza]I looked into my xorg.conf and found only one resolution "1280X800" available for all resolution depths. Thing is, my display is running at 1024x760 only. Hoary's desktop resolution tool only makes the 1024 resolution available also !

Doing sudo dpkg-reconfigure xserver-xorg doesn't help either.

I have a widescreen laptop, and every other aspect of Ubuntu is absolutely fine - I'd just like to be able to use my full screen real estate. Any clues ?[/QUOTE]

Kezza:

[http://www.celifornia.com/documents/dell700m.html#3._855resolution](http://www.celifornia.com/documents/dell700m.html#3._855resolution)

---

### Post by amerigo5 on 2005-03-25
I have a 15.4 widescreen Toshiba M35X and using the following on /etc/X11/xorg.conf worked for me:

Identifier "Generic Monitor"
HorizSync 30-107
VertRefresh 50-185
Option "DPMS"
Modeline "1280x800" 159.74 1280 1296 1552 1664 800 800 815 835
ModeLine "1680x1050" 214.51 1680 1800 1984 2288 1050 1051 1054 1103

Refer to the original post at
[http://www.ubuntuforums.org/showthr...ighlight=50-185](http://www.ubuntuforums.org/showthr...ighlight=50-185)

---

### Post by Rhodan on 2005-03-26
How do I go about changing the refresh rate as Ubuntu only lets me select 60hz ?

---

### Post by kb00heda on 2005-03-27
Rhodan,

You may have a look at a program called gtf (asked about it in another thread):

[http://www.ubuntuforums.org/showthread.php?t=21537](http://www.ubuntuforums.org/showthread.php?t=21537)

I was able to use it anyway (but my change was from 85 to 100 Hz -- it's almost hard to tell the difference); hopefully so will you. If you give it a try, please let me know the results!

/David

---

### Post by Paperweight on 2005-03-29
I don't have an xorg.conf in my /etc/X11 folder. It isn't hidden, either. I tried applying these changes to my XF86Config-4 file, which looks the same, but the new resolutions still won't show up in Screen Resolution.
Where can I get an xorg.conf file?

---

### Post by Leif on 2005-03-29
If you're using warty, you don't have an xorg.conf file, you need to use the xfree one instead. When you upgrade to hoary, you will have to switch to xorg - long story. If you believe the resolutions you've added should work at the given depth, try pressing ctrl alt + to cycle thru resolutions. If you hear a whining noise from your monitor, click it again quick until you hit a working resolution.

---

### Post by neshaug on 2005-03-31
How will the modeline be for a 12" laptop LCD with 1024x768?

---

### Post by arnoct on 2005-03-31
also, just FYI, if you're running an nvidia card and your monitor says it doesn't support a resolution, it won't let you change to it. In order to fix this problem, go into the "Device" section of your xorg.conf and add the following line:

```

Option "IgnoreEDID" "true"

```

**THIS IS NOT RECOMMENDED UNLESS YOU KNOW WHAT YOU'RE DOING.** You can severely damage your monitor if you set it to an unsupported resolution.

---

### Post by Ren on 2005-03-31
argh, Ive followed the guide on how to change resolution, but its still locked at 60hz
I use 1280x960 @72hz when Im using windows and would really love to use it on ubuntu

heres my xorg.conf

```

Section "Device"
	Identifier	"NVIDIA Corporation NV17 [GeForce4 MX 420]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
	Option "IgnoreEDID" "true"
EndSection

Section "Monitor"
	Identifier	"IBM E74"
	Option		"DPMS"
#	DisplaySize	270	203	# 1024x768 96dpi
	DisplaySize	338	254	# 1280x960 96dpi
#	DisplaySize	338	270	# 1280x1024 96dpi
#	DisplaySize	370	277	# 1400x1050 96dpi
#	DisplaySize	423	370	# 1600x1400 96dpi
	Modeline "1280x960_72.00"  124.54  1280 1368 1504 1728  960 961 964 1001  -HSync +Vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV17 [GeForce4 MX 420]"
	Monitor		"IBM E74"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1200x800" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1200x800" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1200x800" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1200x800" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1200x800" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1280x960" "1200x800" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by pannerrammer on 2005-04-04
Hi Ren. I've had low refresh rate problems too with a 19" iiyama Vision Master Pro 450. I've tried the various suggestions with little effect, so I got a bit bold:

My /etc/X11/xorg.config file contained the section

[INDENT]Section "Monitor"[INDENT]Identifier "Generic Monitor"
Option "DPMS"
HorizSync 28-64
VertRefresh 43-60
[/INDENT][/INDENT] 

I simply stuck a 1 in front of each of the 6's (ie 28-164 and 43-160), saved, rebooted and lo!, I get refresh rates options of 60, 75 and 85hz.

Hope this is of assistance.

---

### Post by shakin on 2005-04-04
[QUOTE=pannerrammer]
I simply stuck a 1 in front of each of the 6's (ie 28-164 and 43-160), saved, rebooted and lo!, I get refresh rates options of 60, 75 and 85hz.

Hope this is of assistance.[/QUOTE]

I don't know what you did, but the proper way to force a single refresh rate is below:


[INDENT]Section "Monitor"
[INDENT]Identifier "Generic Monitor"
Option "DPMS"
HorizSync 28-64
VertRefresh 85
[/INDENT][/INDENT] 

That would be fore 85hz. The VertRefresh number is all you care about. You can give it a range as well. Your default range maxed out at 60hz, which is why you couldn't go higher.

---

### Post by pannerrammer on 2005-04-05
Thanks for your comments, noted and appreciated. 

Setting the VertRefresh to 85 gives me _just_ the 85hz refresh rate... but none of the lower rates, which I assume I might require if I swap to another (possibly even older) monitor. Setting the VertRefresh to a range (50-85 seems about right) gives me the options of 60, 75 and 85hz

I've spent another happy hour fiddling to verify my settings and it appears that the HorizSync setting is indeed also of crucial relevance. See the table below:[INDENT][FONT=Fixedsys]
HorizSync . . . . VertRefresh . . . . max resolution
30-75 . . .  . . . . . . 50-85 . . .  . . . . . . .  1024x768@85hz (plus 75, 60hz)
30-90 . . .  . . . . . . 50-85 . . .  . . . . . . . 1024x768@75hz (plus 60hz)
30-100 . .  . . . . . . 50-85 . . .  . . . . . . . 1280x1024@85hz (plus 75, 60hz)[/FONT]
[/INDENT]

So, the settings below seem to work best for me
[INDENT]HorizSync 30-100
VertRefresh 50-85[/INDENT]

Thanks again.

---

### Post by shakin on 2005-04-07
[QUOTE=pannerrammer]I've spent another happy hour fiddling to verify my settings and it appears that the HorizSync setting is indeed also of crucial relevance.[/QUOTE]

I believe it is monitor-dependent. Eg, different monitors will run at a different HorizSync for each resolution/VertRefresh. This is not generally a problem you need to worry about since keeping the default should almost always work.

---

### Post by Riggs on 2005-04-07
[QUOTE=amerigo5]I have a 15.4 widescreen Toshiba M35X and using the following on /etc/X11/xorg.conf worked for me:

Identifier "Generic Monitor"
HorizSync 30-107
VertRefresh 50-185
Option "DPMS"
Modeline "1280x800" 159.74 1280 1296 1552 1664 800 800 815 835
ModeLine "1680x1050" 214.51 1680 1800 1984 2288 1050 1051 1054 1103

Refer to the original post at
[http://www.ubuntuforums.org/showthr...ighlight=50-185](http://www.ubuntuforums.org/showthr...ighlight=50-185)[/QUOTE]

I've got a Toshiba laptop as well, (P10-S429) and after installing Ubuntu, it defaulted to 1280x800 automatically, which was nice.  Fedora I had to do something similar to what you have above.

---

### Post by mappler on 2005-04-08
Thanks for the guide.

BTW: Will ANYONE ever actually fix this kludge?

Linux folks like to bash MS folks, but Windows seems to be able to change screen resolutions without resorting to obscure text file editing.

 -Matt

---

### Post by ichtys on 2005-04-11
I already had all the resolutions in xorg.conf, but wasn't able to choose anything higher than 800x600. After changing the defaultdepth from 24 to 16, it all worked   :-P 

[I]Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. 3D Rage IIC (AGP)"
	Monitor		"L1730B"
	DefaultDepth	16[/I]

My monitor is LCD and my graphic card is very old.

---

### Post by heimo on 2005-04-13
[B][SIZE=3]Howto solve some of the resolution problems

This HOWTO is [COLOR=Red]not maintained[/COLOR], the current one (for Breezy Badger) is at:
[URL="http://ubuntuforums.org/showthread.php?p=454217"][SIZE=2]http://ubuntuforums.org/showthread.php?p=454217
[/SIZE][/URL] [SIZE=1]
[SIZE=2]
Check[/SIZE][/SIZE][/SIZE][/B][SIZE=2] FixVideoResolutionHowto
[/SIZE][[SIZE=3][SIZE=2]https://wiki.ubuntu.com/FixVideoResolutionHowto[/SIZE][/SIZE]]("https://wiki.ubuntu.com/FixVideoResolutionHowto")
[https://wiki.ubuntu.com/DebuggingXAutoconfiguration]("https://wiki.ubuntu.com/DebuggingXAutoconfiguration")

**[SIZE=2]Integrated Intel graphics card?[/SIZE]**
[http://ubuntuforums.org/showthread.php?t=27029]("http://ubuntuforums.org/showthread.php?t=27029")
[http://ubuntuforums.org/showthread.php?t=24923]("http://ubuntuforums.org/showthread.php?t=24923")
[http://www.x.org/X11R6.8.2/doc/i810.html]("http://www.x.org/X11R6.8.2/doc/i810.html")

**[SIZE=2]Problems with login screen refresh rate?[/SIZE]**
 [http://ubuntuforums.org/showpost.php?p=253944&postcount=3]("http://ubuntuforums.org/showpost.php?p=253944&postcount=3")


[SIZE=2]**Backup your configuration file**[/SIZE]
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
``` [SIZE=2][B]
How to edit xorg.conf file[/B][/SIZE]
Run in terminal or console:
```
sudo nano /etc/X11/xorg.conf
``` online help in nano: ctrl+g (ctrl+x exits)

**[SIZE=2]How to edit or add HorizSync and VertRefresh lines[/SIZE]**
Find your monitors manual (manufacturers website and Google are useful). 
Look for hozizontal sync and vertical refresh rates, also if bandwidth or maximum dot clock / pixel clock is mentioned, write it down.

Edit xorg.conf and put correct values to your xconf.org's *Monitor section*. Something like this:
```
Section "Monitor"
    Identifier    "CM752ET"
    HorizSync     31-101
    VertRefresh    60-160
EndSection

``` Be sure that Identifier is same as the Monitor line in *Screen section*.


**[SIZE=3][SIZE=2]Adding custom modeline[/SIZE][/SIZE]**
Now, if you know what your monitor can do, for example 1024x768@75Hz (edit: choose decent resolution / refreshrate), you can open another terminal window (keep xorg.conf open in gedit) and enter:

```
 gtf horizontalresolution verticalresolution refreshrate
for example:
gtf 1024 768 75
``` Copy paste the output to your *Monitor section*.

```
 
  # 1024x768 @ 75.00 Hz (GTF) hsync: 60.15 kHz; pclk: 81.80 MHz
  Modeline "1024x768_75.00"  81.80  1024 1080 1192 1360  768 769 772 802  -HSync +Vsync

``` 
Watch that the hsync is in range with the HorizSync on the same section (in this example the range is 31-101 and this modelines hsync is 37.65, so we're safe). Also the VertRefresh and the refresh rate you selected (75Hz in this example) should match - in this example VertRefresh is 60-160 and modeline is 75Hz, so that's all good.

Now you can select the defaul resolution and colordepth by tweaking the *Screen section*. It should look something like this:

```
Section "Screen"
    Identifier    "Default Screen"
    Device        "NVIDIA Corporation NV34 [GeForce FX 5200]"
    Monitor        "CM752ET"
    DefaultDepth    16
    SubSection "Display":
        Depth        16
        Modes      "1280x1024" "1024x768"
    EndSubSection
EndSection

``` 
Monitor name here (CM752ET) matches the Identifier on your Monitor Section. Device line here matches the identifier on your Device section - you get the idea? :) It ties together some settings for your screen - the graphics card and your monitor. You may have more Subsections here, but only one is needed.

Change the DefaultDepth to what you would want it to be, 16 (65536 colors) or 24 (16M colors). Change the Modes line to match the resolutions you want to use - Depth must match DefaultDepth (here it's 16).

Save the config. If you're in X, hit CTRL+ALT+BACKSPACE to restart X (if you're running logon manager like xdm, kdm or gdm). Change between virtual consoles with CTRL + F1 F2 F3 and so on - your X should be on F7. 

Starting the X:
*startx* OR *sudo /etc/init.d/gdm start* (in KDE it's kdm)

If that doesn't work, try fixing the xorg.conf or get back to your original by copying the backup over your changed one with:
```
sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
``` 
When you're back in X, you can cycle through different modes by pressing CTRL+ALT++ (plus sign on numpad), or go to System->Preferences->Screen Resolution.

[B][SIZE=2]
[/SIZE]How to adjust position of your screen?
[/B][SIZE=2]open terminal[/SIZE](Applications->Accessories->Terminal), run xvidtune (type: "xvidtune"), adjust the screen and hit Show-button. You'll see a line with something like this on the terminal screen:
```
"1280x1024"   157.50   1280 1332 1492 1728   1024 1025 1028 1072 +hsync +vsync
``` 
Next you should:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo gedit /etc/X11/xorg.conf

``` In Monitor section, add the above line with a prefix "Modeline", like this:
```
Modeline "1280x1024"   157.50   1280 1332 1492 1728   1024 1025 1028 1072 +hsync +vsync
``` 
That should do it. There should be no need to restart X if you did make the change (hit Apply in xvidtune), but you should test that this new change works. Hit ctrl+alt+backspace to restart X. If it doesn't work, you can copy back the old configuration file using:
```
sudo /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
``` and restart X using:
```
sudo /etc/init.d/gdm start

``` 

[B][SIZE=2]Where is the log file?
[/SIZE][/B]/var/log/Xorg.0.log


[B][SIZE=2]How to reconfigure Xorg
[/SIZE][/B] You can do the whole X configuration process by entering:
sudo dpkg-reconfigure xserver-xorg



[B]Why must I set the correct screen resolution on every startup?
[/B][http://www.ubuntuforums.org/showpost.php?p=248755&postcount=5]("http://www.ubuntuforums.org/showpost.php?p=248755&postcount=5")

[B][SIZE=3][SIZE=2]How to ask help [/SIZE]
[/SIZE][/B]personally I prefer to help on these problems if the question is asked on correct forum on its own thread, it makes answering a lot easier (than trying to remember everyones nick, GPU, monitor and so on). It will also give more attention to your question as more people will read it.

 Helpful information you can add to your post when asking help on this subject[LIST]
[*]What are the symptoms[LIST]
[*]Do you get only low resolution
[*]Do you get only black or distorted screen?[/LIST] [/LIST][LIST]
[*]which monitor do you have?[LIST]
[*]make and model
[*]**link to specification sheet or user manual**, if possible[/LIST] 
[*]which graphics card do you have?[LIST]
[*]chipset, amount of memory[/LIST] 
[*]some parts of /etc/X11/xorg.conf -file[LIST]
[*]**Monitor-section**
[*]Device-section
[*]Beginning of Screen-section (~10 lines)[/LIST] 
[*]resolution you want to use
[*]**attached */var/log/Xorg.0.log*** (compressed preferred), ***NOT*** INLINE[/LIST]**[SIZE=3][SIZE=2]:!: [/SIZE][/SIZE]**[SIZE=2]**Things to try:**[/SIZE][LIST]
[*]if you're using kvm (keyboard/video/mouse-switch), try reconfiguring without
[*]vesa driver instead of your graphics card specific driver
[*]nv instead of nvidia
[*]16-bits colors instead of 24-colors[/LIST][LIST]
[*]adding HorizSync and VertRefresh line in Monitor section with correct values from monitors specification
[*]adding custom modeline for your monitor in Monitor section[LIST]
[*][online modeline generator]("http://xtiming.sourceforge.net/cgi-bin/xtiming.pl")
[*]using gtf
[*]gtf generator online: [http://www.sh.nu/nvidia/gtf.php]("http://www.sh.nu/nvidia/gtf.php")[/LIST] 
[*]reconfiguring Xorg[LIST]
[*]```
sudo dpkg-reconfigure xserver-xorg
```[/LIST] [/LIST]Thank you!

---

### Post by fede on 2005-04-16
Thanks everyone for the tips.

Still, I cannot get my video at the desired 1024x768, 100Hz refresh.  I've tried everything I've found here (and elsewhere in the forums), and it doesn't work. 
---
**EDIT:** *Fixing wrong hardware info... *
I'm running an ASUS A7V400-MX with  VIA KM400A chipset (+ VIA VT8235 CE). [Product Info HERE](http://www.asus.com/products.aspx?l1=3&l2=13&l3=63&model=228&modelmenu=1) 
**/EDIT**

**The same system does the desired 1024x768@100Hz under windows 2000.**
Some info on my system

sudo xresprobe via
id: S/M 750p
res: 1280x1024 1024x768 832x624 800x600 720x400 640x480
freq: 30-96 50-160
disptype: crt

So I've set this in the monitor section of /etc/X11/xorg.conf:
Section "Monitor"
	Identifier	"S/M 750p"
	Option		"DPMS"
	HorizSync      30-96
	VertRefresh   50-160
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video"
        Monitor         "S/M 750p"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
[... same for 4,15,16...]
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
EndSection

Then I added the modeline generated by GTF in the monitor section (right before EndSection)

  # 1024x768 @ 100.00 Hz (GTF) hsync: 81.40 kHz; pclk: 113.31 MHz
  Modeline "1024x768_100.00"  113.31  1024 1096 1208 1392  768 769 772 814  -HSync +Vsync

Restarted GNOME and it's still at 85Hz. I tried to force 100Hz by changing the previous modeline to

  Modeline "1024x768"  113.31  1024 1096 1208 1392  768 769 772 814  -HSync +Vsync

(so that, I suppose, "1024x768" in the "Screen" "Display" subsections would take the resolution from this gtf-generated modeline). 
The result was a blue error screen: **cannot start X**, bla bla. 

So I'm still working at 85Hz (after restoring my previous settings). 

Any help would be really appreciated. Thanks!

---

### Post by heimo on 2005-04-16
Put the first modeline back in and change* VertRefresh   50-160* to* VertRefresh 99-160* and try then.

---

### Post by fede on 2005-04-16
[QUOTE=heimo]Put the first modeline back in and change* VertRefresh   50-160* to* VertRefresh 99-160* and try then.[/QUOTE]
 Hello heimo,

Thanks for the reply. I've tried it and it doesn't work. The same error. In the log it says

(WW) VIA(0): Mode pool is empty
(EE) VIA(0): No valid modes found

after finding all modes either "(bad mode clock/interlace/doublescan)" or (vrefresh out of range)

Actually, after doing what you told me (modeline + vertrefresh 99-160), I've tried leaving only the VertRefresh line you suggested (commented out the modeline), and the same error pops up. If instead I leave the modeline and take away the vertrefresh lower limit, gnome starts in 832x624, the next resolution in the Displays section.

Anything else would be appreciated... thanks again!

---

### Post by heimo on 2005-04-16
Next thing I'd probably try is put back the:
```
 	HorizSync      30-96
	VertRefresh   50-160

``` 

and create bunch of modelines...
 ```

  # 1024x768 @ 100.00 Hz (GTF) hsync: 81.40 kHz; pclk: 113.31 MHz
  Modeline "1024x768_100.00"  113.31  1024 1096 1208 1392  768 769 772 814  -HSync +Vsync
  # 1024x768 @ 98.00 Hz (GTF) hsync: 79.67 kHz; pclk: 110.91 MHz
  Modeline "1024x768_98.00"  110.91  1024 1096 1208 1392  768 769 772 813  -HSync +Vsync
  # 1024x768 @ 95.00 Hz (GTF) hsync: 77.04 kHz; pclk: 107.25 MHz
  Modeline "1024x768_95.00"  107.25  1024 1096 1208 1392  768 769 772 811  -HSync +Vsync
  # 1024x768 @ 92.00 Hz (GTF) hsync: 74.52 kHz; pclk: 102.54 MHz
  Modeline "1024x768_92.00"  102.54  1024 1088 1200 1376  768 769 772 810  -HSync +Vsync
  # 1024x768 @ 90.00 Hz (GTF) hsync: 72.81 kHz; pclk: 100.19 MHz
  Modeline "1024x768_90.00"  100.19  1024 1088 1200 1376  768 769 772 809  -HSync +Vsync
  # 1024x768 @ 88.00 Hz (GTF) hsync: 71.10 kHz; pclk: 97.84 MHz
  Modeline "1024x768_88.00"  97.84  1024 1088 1200 1376  768 769 772 808  -HSync +Vsync
  # 1024x768 @ 86.00 Hz (GTF) hsync: 69.40 kHz; pclk: 95.50 MHz
  Modeline "1024x768_86.00"  95.50  1024 1088 1200 1376  768 769 772 807  -HSync +Vsync

``` 

Try to find where's the line - what works, what doesn't and fine tune afterwards.

---

### Post by maurom on 2005-04-16
Try setting

VertRefresh    100

so you leave no other choice to X than to set 100 Hz

---

### Post by fede on 2005-04-16
Thanks again heimo, but it still doesn't work. I've tried them all.

In fact, I've become suspicious of the lines generated by gtf: I' ve tried generating modelines for 1024x768@85 and 800x600@85 and X also found thouse modes unusable when the modelines where present. You see, there shouldn't be a problem with 1024x768@85, because it ran right out of the box (also 1280x1024@85), and when I remove (or comment out) all modelines it works fine, but it doesn't with the modelines present.

Same thing using the Modeline Generator at [http://xtiming.sourceforge.net/cgi-bin/xtiming.pl](http://xtiming.sourceforge.net/cgi-bin/xtiming.pl)

The firmest hypothesis I've found (must have tried over 50 xorg.conf combinations in the last hours) is that for some reason X does not "like" modelines, at least for my config...

Any ohter clues?

Regards,

Federico.

---

### Post by fede on 2005-04-16
Thanks for your reply maurom, but it still doesn't work. Same thing as when I tried heimo's suggestion: setting a higher lower limit for VertRefresh makes X cry that it can't find a valid video mode (with or without modelines defined)

---

### Post by heimo on 2005-04-16
I'm running out of ideas. Try switching to defaultdepth 16, use the actual sync/refresh rates of your monitor and post your /var/log/Xorg.0.log 

Hopefully you can find a way to fix it. Do you have any more spesific information / links to information about that motherboard and graphics chip on it? (I couldn't find it from Asus' site.)

EDIT: Are you sure you should be using via driver? Try *savage*.

---

### Post by m3jsh on 2005-04-17
I knew this would happen... I followed the OP's instruction for the xorg.conf file but my laptops monitor cannot go above 1024x768 and now the X server wont start up correctly, how can I remedy this?

---

### Post by heimo on 2005-04-17
Go to rescue mode / console, login. edit xorg.conf. If don't know what to fix, you can reconfigure (dpkg-reconfigure). One thing that has saved me in that kind of situation is to connect it to external monitor and fix the settings.

---

### Post by m3jsh on 2005-04-18
Great, thanks.

---

### Post by fede on 2005-04-19
Thanks again, heimo,

>  Do you have any more spesific information / links to information about that motherboard and graphics chip on it? (I couldn't find it from Asus' site.)
Reading this I realize that I posted inaccurate info on my motherboard (thought I rememebered... I apologize for this dumb error - I edited my previous post). It's actually an ASUS A7V400-MX ([Info Here](http://www.asus.com/products.aspx?l1=3&l2=13&l3=63&model=228&modelmenu=1)) with a VIA  KM400A chipset.
> EDIT: Are you sure you should be using via driver? Try *savage*.
I tried it also, but it doesn't work. Now that I verified the chipset info, I'm pretty sure the correct driver is via, since the driver's [project page](http://unichrome.sourceforge.net) specifically says that my chipset is supported.

My [Xorg.0.log is here](cablemodem.fibertel.com.ar/fstafforini/Xorg.0.log), I'm using [this xorg.conf](cablemodem.fibertel.com.ar/fstafforini/xorg.conf)

Apparently DRI and DRM do not work. Can this have anything to do with my refresh rate limitations? I've seen that other people have been able to compile the open source via driver into their system with DRI support. 

Related threads in Ubuntu Forums:
[Unichrome support in Ubuntu](http://www.ubuntuforums.org/showthread.php?t=23038&highlight=unichrome)
[Xorg   "via" driver broken](http://www.ubuntuforums.org/showthread.php?t=24503&highlight=unichrome)
[Need "via" kernel module for Epia CLE266](URL=http://www.ubuntuforums.org/showthread.php?t=24680&highlight=unichrome) 

I'm not sure this might be it, though: I'm a newbie. It appears that for some reason the via driver is not fully working in Hoary. I read that the unichrome driver (which is an open source project for the via driver) would be included in kernel 2.6.11, so I also tried installing that kernel with no luck with respect to these error messages regarding DRI and DRM. 

Do you think DRI and DRM have anything to do with my refresh limitation?

Thanks. Regards,

fede.

---

### Post by heimo on 2005-04-19
To my eye it looks like it doesn't recognize your manufacturer/chipset combination.

Log:
```
(--) PCI:*(1:0:0) unknown vendor (0x1106) unknown chipset (0x7205) rev 1, Mem @ 0xe4000000/26, 0xe8000000/24

``` 

However looks like Unichrome projects driver would recognize your GPU (at least the latest one, I don't know about kernel):
[http://cvs.sourceforge.net/viewcvs.py/unichrome/xfree86/via_id.c?rev=1.16](http://cvs.sourceforge.net/viewcvs.py/unichrome/xfree86/via_id.c?rev=1.16)

You can try uncommenting the module dri in xorg.conf, but I doubt it'll make any difference.

Have you tried generic drivers, like vesa or vga? No problems with those?

(Wow, I got a headache of thinking about this. ](*,))

---

### Post by fishbone on 2005-04-22
I have a Dell Optiplex GX260 with an integrated Intel card & Dell 1501 15" LCD display but xorg only displays in VGA mode - Hoary picked it up & uses the i830 driver.  

I tried changing the display resolution to only allow 1024 x 768 @ 60Hz - preferred setup for this LCD screen & also tried variations of colour depth - all to no avail.

Has anyone tried setting up Ubuntu on a similar Dell ? - my thinking is it's due to the crap Intel integrated card (not being a big fan of integrated motherboard anything personally =; )

Cheers....

---

### Post by Consumer on 2005-04-25
I've had the problem with being stuck in 640x480 but altering the xorg.conf file hasn't made any difference for me, and I still have no other options in gnome other than 640x480 :( any ideas ?

---

### Post by nobodysbusiness on 2005-04-27
My desktop resolution also gets stuck in 640x480 mode whenever I shut my computer off and then turn it back on. After I turn it on, I restart (without shutting it completely off), and it goes back to normal. I was rechecking this thread hoping that someone might have the solution to this problem. It's tolerable, but still annoying. My rez is 1280x1024 at 60 Hz.

---

### Post by izzydahedgehog on 2005-04-27
[QUOTE=Consumer]I've had the problem with being stuck in 640x480 but altering the xorg.conf file hasn't made any difference for me, and I still have no other options in gnome other than 640x480 :( any ideas ?[/QUOTE]

Same problem.

I have an nVidia GeForce 5200 card and a Sony Multiscan E210 monitor, if that helps at all.

---

### Post by DeMachina on 2005-04-28
I was stuck in 1024x768 and  change made to xorg.conf didn't do anything. I just found out why. If you followed the nVidia driver install in the wiki, it ask you to do "sudo nvidia-glx-config enable". Undo that ("sudo nvidia-glx-config disable") and the change to xorg.conf will be recognized.

Hope this helps a few of you.

---

### Post by bikeboy on 2005-04-28
I tried dpkg-reconfigure several times with different options and it didn't fix my prob of being stuck in 640x480. However I eventually got it to work and now I'm wondering what would be the best way of letting other users of my computer or similar (toshiba 2510cds laptop) know how I fixed it. For me it was specifying the horiz and vert sync rate range in dpkg. The auto detected ones just stopped it working right.

Thanks

---

### Post by heimo on 2005-04-28
Hi!
 
Lots of people having these problems. I updated my original post on this same thread. [Here.]("http://www.ubuntuforums.org/showpost.php?p=129379&postcount=21")
 
I'd like to politely ask people with these problems to start a new thread (unless you already have), with as much information of the problem as possible. Do not send it under Tips&Tricks. Good forum is probably Hoary/Installation help:
[http://www.ubuntuforums.org/forumdisplay.php?f=56]("http://www.ubuntuforums.org/forumdisplay.php?f=56")
 
This will make it a lot easier to answer and help you, because keeping track of who's who is quite a challenge if you have four different discussions going on in one thread. I'm sure you understand.
 
If you already have posted your question and it has not been answered, you can probably edit your message on this thread to include link to that other thread. Me and many others will have better chance to help. Your message will also probably be seen by more people than now posting on this long old thread.
 
Thank you very much for understanding. :)
 
 
EDIT: Of course this reflects just what I think and I'm not (and do not wish to be) MOD.

---

### Post by izzydahedgehog on 2005-04-28
Whoever ends up starting a new thread, could they post a link to it here?  You know, for continuity.

BTW, I switched to the "vesa" driver and it works fine, although the refresh rate is not a little sketchy.

---

### Post by andlinux21 on 2005-05-25
[FONT=Comic Sans MS]Thanks guys for all the howto info i got my display changed on my Micron Transport XKe and it looks great[/FONT]

---

### Post by vincent_stehle on 2006-04-28
Hi,

I just wanted to let you guys know that I managed to have 1680x1050 with VIA CLE266.

The modeline I use is:

[INDENT][FONT="Courier New"]Modeline "custom" 122.00 1680 1684 1700 1803 1050 1052 1064 1082 +hsync +vsync[/FONT][/INDENT]

You can find all the details here: [http://vincent.stehle.free.fr/cle266/](http://vincent.stehle.free.fr/cle266/)

Cheers,

--
Vincent Stehlé

---

### Post by voneicken on 2006-07-02
I also have a VIA mini ITX board with a CLE266 and have been trying to get 1680x1050. The modeline posted by vincent stehle didn't work for me. But I finally figured out the following one:

Modeline "1680x1050" 148.5 1680 1784 1960 2240 1050 1053 1059 1089

This is for a Dell 2007WFP display which provides the following info:

(II) VIA(0): Supported additional Video Mode:
(II) VIA(0): clock: 146.2 MHz   Image Size:  434 x 270 mm
(II) VIA(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
(II) VIA(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
Note that I use a pixel clock of 148.5Mhz, which is the highest value under 150Mhz that is listed in via_mode.h of the driver.
Good luck!

---

### Post by vincent_stehle on 2007-03-04
> **voneicken said:**
> The modeline posted by vincent stehle didn't work for me. But I finally figured out the following one:

Modeline "1680x1050" 148.5 1680 1784 1960 2240 1050 1053 1059 1089

This is for a Dell 2007WFP display[..]

Hi voneicken,

Your modeline saved my life months after. I now have a Belinea 22W hooked to my via, and my original modeline does not work for that screen any more.

...but yours does!

So, thanks.

---

### Post by Jonathan Métillon on 2007-03-27
Thanks Voneicken for the modeline. It makes my 2007FPW works on my  Via/S3G UniChrome!

---

### Post by Zubbus on 2009-03-25
Greetings, my predicament may well belong to a whole other category, but it did pop up while I was following the instructions to change modify my xorg.conf

Quite simply, I got told:

Could not save the file /etc/X11/xorg.conf.
You do not have the necessary permissions to save the file.

Now. It definitely is my computer and I installed Ubuntu here and no one else even uses it. So I guess I should be able do this. But how?

Thanks for help.

---

### Post by sleepyjon on 2009-03-25
> **Zubbus said:**
> Greetings, my predicament may well belong to a whole other category, but it did pop up while I was following the instructions to change modify my xorg.conf

Quite simply, I got told:

Could not save the file /etc/X11/xorg.conf.
You do not have the necessary permissions to save the file.

Now. It definitely is my computer and I installed Ubuntu here and no one else even uses it. So I guess I should be able do this. But how?

Thanks for help.

Unless you're running 5.04, you probably don't might want to look at another guide...

Anyway, you don't have permission to save because you're not editing /etc/X11/xorg.conf as root.

Use sudo gedit /etc/X11/xorg.conf

---

### Post by IamAcoconut on 2009-03-31
I had this issue with an old Toshiba laptop, solved by just copying xorg.conf from MEPIS live, which seems to handle every display correctly.

---

### Post by get2shashank on 2009-04-16
hung up ubuntu:is that a graphics problem ?
I installed ubuntu 7.10 on my machine. It installed all the way fine. When i was prompted to reboot the system (after removing the disc from the system) i did so which booted the new install.

I then type in my username and password and then it is. It accepts my details [i.e. no incorrect username/password message] and then it just sits there on the light orange blank screen. It proceeds to nowhere even after waiting for long periods of time [neither can i see the hard drive read LED on. the system seems to be doing no working on my login attempt]. I just cannot login to my GUI desktop [although i can login at the terminals==>Ctrl+Alt+F2 to F6].

What do i do.I think it is due to some graphics issue.
**One thing...I have a higher screen resolution at the login screen than what i set at the ubuntu desktop during live disk session.
**Also the screen refresh frequency seems to be lower than 85Hz which is recommended for my CRT monitor.
**the recommended primary mode for my CRT monitor is 1024x768 (85Hz). This is what i set during the live disk session before initiating the install. i should get that thereafter, but i dont.
**When i booted from the CD for the first time, then before the GUI of ubuntu took up the screen, i was prompted with messgaes like...
load boot time graphics [y/n] and a few more like this. [i answered with Y everytime]
My buddy tells me these things are not experienced in his machine. So is some thing wrong here.

I have an integrated graphics on my motherboard. Its Intel 845GL (64 MB).

---

