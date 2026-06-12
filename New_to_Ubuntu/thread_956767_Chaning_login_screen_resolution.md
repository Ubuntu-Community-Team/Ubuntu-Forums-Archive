---
title: "Chaning login screen resolution"
date: 2008-10-23
forum: New to Ubuntu
---

### Post by fredscripts on 2008-10-23
Hi!

I've found this thread:

[http://ubuntuforums.org/showthread.php?t=151192](http://ubuntuforums.org/showthread.php?t=151192)


Which explains the way to set the login screen resolution. But my xorg.conf file looks like this:

```
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"es"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection
```

Can't really find that Display subsection, don't wanna try anything dangerous creating the subsection myself, so anyone could post the correct xorg.conf file contents to get my login screen resolution to 1280x960 ?

Thanks so much!

---

### Post by fredscripts on 2008-10-23
bump...should I try to add that subsection?

---

### Post by fredscripts on 2008-10-23
:( ... xorg configuration it's a classical issue, I'm sure anyone can help me with this simple task :(


Is there any way to change the login screen resolution without editing config files?

---

### Post by Kellemora on 2008-10-23
Hi Fred

If you are looking for a way to set screen resolutions not using Terminal, perhaps this might help.

TTUL
Gary

Screen Resolution Problems?  Easy fix!
Ubuntu 8.04 Hardy Heron

From a Noob for fellow Noobs!

Preliminary Note:
This document is to address Changing Screen Resolution using Preferences causes Screen to Roll horizontally, vertically or just mess up royally.  Also, only 640 x 480 resolution available in Preferences.  This fix may or may not allow you to select other available resolutions from the Preferences Option without changing MODE lines in /etc/X11/xorg.conf which I am not addressing here.
If this fix causes log-in screen obesity (HUGE SCREEN), see my other post titled Huge Log-in Screen?  Easy fix!  Which addresses that problem separately and easily.

To get started we need the Tool called Screens and Graphics.
If it is not available under Applications/Other, then RIGHT CLICK on Applications, select Edit Menu (left click) and wait for the Main Menu screen to open.  From the Main Menu, left column (Menus) select 'Other' and a new list of text will appear in the right screen (items).  Place a check mark in the box to the left of Screens and Graphics, this will automatically select 'Other' if it was NOT in your drop down list under Applications.  Close this window.
You will have to REBOOT for the change to take affect.

Once you're up and running again, left click on Applications/Other/Screens and Graphics.
A log-in screen will appear, type your Normal log-in password.  Why it don't ask for Root I don't know.

In the Screens and Graphics Preferences window select Graphics Card first just to check to make sure your correct graphics card is displayed.  Normally these entries are correct, but check them anyhow!

OK, now select the Screen Tab and get things set up to run properly.

Click on the little Monitor icon to the right of Model:  It may currently say Plug n Play.  A new (Choose Screen) window opens, from the Left window, select the Manufacturer of your Monitor.  The screen on the right will change to the models that manufacturer makes.  Scroll through the list to find your Monitors model name and number and/or identification.
If you have an .inf driver for your particular monitor and it is not listed, select add and follow the directions there.  I've not found a monitor not already in the listing yet.  Then I never have many new things either, that might not be listed long before I get it, hi hi.........  IF a Test button comes up, just IGNORE IT, because your screen will mess up royally.  After selecting your monitor, select OK!  This will bring you back to the Screen and Graphics Preferences screen.
Here you will select the desired resolution you would like your DESKTOP to run in.  The proper bandwidth should self-select, but check to make sure it's right for your monitor.  A wrong setting could damage your monitor!
Select OK and it will change and ask you if you want to Keep this setting.  If all looks OK, select YES.
This change, and all the default parameters for your selected monitor WILL be written to the /etc/X11/xorg.conf file.  Also, the Screens and Graphics window may show UNKNOWN for your monitor.  The result of this Unknown Monitor or sometimes even if the Monitor is KNOWN and displays correctly the resultant change to the xorg.conf file, may cause your log-in screen to become OBESE (HUGE) and you might not be able to see your log-in boxes.

But don't worry, you KNOW they are there! 
Just type in your log-in name, hit enter and type your password, hit enter and wait for the log-in to complete.  Your xwindow (Gnome or others) should be at the desired resolution now.

IF you did have the HUGE log-in problem, see my post on Huge Log-in Screen?  Easy fix!

The above was tested on the following machines with complete success:
HP Pavilion 753n, 2.53GHz Intel P4, 512mb, Intel 82845G/GL video, Samsung SyncMaster 955df.
e-machines T4165, 1.6GHz Intel P4, 256mb, AGP 3D video, AOC monitor.
Compaq 5420, 1.47GHz Athlon XP1700, Savage 4 AGP video, Samsung SyncMaster 3Ne.


TTUL
Gary/aka Kellemora
9/10/08 &#8211; rev 9/15/08

---

### Post by fredscripts on 2008-10-23
thanks for answering!


But my problem is just in the login screen. On the desktop I have the good resolution 1280x960, but in login screnn I have another one which I'd like to change.

---

### Post by pastalavista on 2008-10-23
Check usplash.conf 
```
sudo gedit /etc/usplash.conf
```
make sure the screen resolution matches your monitor's. if you need to change it, save the changes in gedit and then run
```
 sudo update-initramfs
```

---

### Post by Kellemora on 2008-10-23
Hi Fred

I wrote this for those with the HUGE Log-in screen problem, but you can set the log-in screen to any resolution you want to using it.
However, it does use the root terminal, but my instructions are so clear, you can't possibly mess up.  (Disclaimer:  The term "you can't possibly mess up" is not warrantied in any way, Bill Gates might try to hold me to it!).

Huge Log-in Screen?  Easy fix!
Ubuntu 8.04 Hardy Heron

From a Noob for fellow Noobs!

Preliminary Note:
FWIW:  I did NOT have any luck using StartUpManager from Synaptic.  Editing /etc/usplash.conf xres and yres was unnecessary as they were already correct.  Neither dpkg-reconfigure -phigh xserver-xorg nor update-initramfs -u worked either to correct the HUGE Log-in screen problem.

This is from a total Noob, but took much research to find out exactly, what changed where, to figure it out.  It's also fairly long because it is geared toward big dummies like myself, hi hi.....

A Simple Test:
If you return your monitor to the original default settings, you should find that your log-in screen once again works right.  This was the CLUE to finding out which file controlled the log-in screen for me!

How to change screen resolution (not using Properties) is in another document titled &#8220;Screen Resolution Problems?  Easy fix!&#8221;  This too might cause log-in screen obesity!

Being a Noob, there may be an easier faster way to do this, but this is what consistently works for me.

The following changes are made using the &#8220;ROOT TERMINAL&#8221;.

The Terminal in Applications/Accessories does not work for me.  No Permission when you go to save!
If you do not have the Root Terminal under Applications/System Tools, then RIGHT CLICK on Applications, select Edit Menus (by left click) and a Main Menu will appear shortly.  In Main Menu (under Menus) select System Tools and the screen (titled Items) to your right will change.  Place a check mark in the box to the left of Root Terminal and select CLOSE.  The Root Terminal will now appear as a selection when  you select Applications/System Tools.

NOW, Select the Root Terminal.  Before the Root Terminal Opens you will have to Log-in as Administrator.  This is your NORMAL log-in!  Why it doesn't ask for Root Log-in I have no idea.
Even though it shows you are IN Root, you will notice that you are still in your /home/name/ directory.  If you try to open the required file from here, you will get a blank screen so DON'T save it, Close without Saving.

At the prompt type  cd ..  this will take you back to your /home directory.
Type  cd ..  again and you will be in the ROOT Directory and can perform the following command.

Note that the X is a capital letter, all others are lower case!  It's X Eleven not XII.

gksu gedit /etc/X11/xorg.conf  This will open your xorg.conf file for editing.

SAFETY OPTION:  Right Click on File, select SAVE AS (left click).  Add  .old  behind the filename xorg.conf so it reads xorg.conf.old, then Right Click on SAVE.  You will now be VIEWING the saved file so select Right Click on the OPEN Icon and select xorg.conf to reopen the working file for changes.  You can always revert back to the original file by saving it as xorg.conf without the word .old behind it.  End of Safety Option.

Scroll down (near the bottom) and you will find a line titled Section &#8220;Screen&#8221;, tabbed in twice you will find a line that reads Virtual followed by two sets of digits.  You should recognize these digits as being common screen resolutions.
Be very careful here!  It's better to be safe than sorry.
You may notice a High screen resolution listed here, one your monitor cannot recognize, like 1792 1344 (which defaults to 640 480), or it may be very low, like 640 480 already.  My desired screen resolution for the log-in screen is 1024 768 so those are the numbers I chose to replace the numbers.

DO NOT delete the existing numbers yet.  They appear to me to be in placeholders is why!

For safety reasons.  Place your cursor after the first digit of the first existing number and if different from the first number already listed, type the new single digit then move left one space and delete the first number, then move back right and enter your remaining numbers, then delete the old numbers from behind it.  If you are going from 1792 down to 1024, just place your cursor between the 1 and 7 and type 024 then delete the 792 ONLY.  I still use this method if I'm going from 640 up to 1024, placing the cursor between the 6 and 4 as my starting point, typing the whole number 1024.
OK, move to the second number, it may be 1344 and you want 768.  Use the same method here too!  Place your cursor between 1 and 3, type 768, delete the 344, move left and delete the leading 1.

This may be an unnecessary overkill way of doing it.  But why take chances when we're only Noob's?

Go to the top of the Screen and Select SAVE, then wait for a bit to make sure it saved before exiting the gedit program.

This has worked on all Ubuntu 8.04 Hardy Heron machines I have tried it on in my testing!

FWIW:  I did NOT have any luck using StartUpManager from Synaptic.  Editing /etc/usplash.conf xres and yres was unnecessary as they were already correct.  Neither dpkg-reconfigure -phigh xserver-xorg nor update-initramfs -u worked either to correct the HUGE Log-in screen problem.

The above was tested on the following machines with complete success:
HP Pavilion 753n, 2.53GHz Intel P4, 512mb, Intel 82845G/GL video card.
e-machines T4165, 1.6GHz Intel P4, 256mb, AGP 3D video card.
Compaq 5420, 1.47GHz Athlon XP1700, Savage 4 AGP video card.
e-machine T6524, 2.30GHz Athlon 64-3500+, ATP Radion Express 300 video card.

TTUL
Gary/aka Kellemora
9/10/08 &#8211; rev 9/15/08

---

### Post by AGSzabo on 2008-10-24
my usplash.conf reads "1280 x 800" but the boot image is still distorted..? running update-initramfs did not help: it requests parameters!

---

### Post by fredscripts on 2008-10-24
that uplash stuff didn't work for me.

Anyone could post the xorg.conf I should use to get login screen resolution 1280x960 having my current xorg.conf as:

```
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"es"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection
```

Please, I'm sure changing a resolution shouldn't be that difficult...

---

### Post by fredscripts on 2008-10-25
bump...:(

---

### Post by grainbarcelona on 2008-10-25
Perhaps you could try something much more simple.
- Install 'Start up manager' with 'Add/Remove programs'
- Run it (it'll be in  System > Administration.
- Change the display resolution (under 'boot options')

... and see whether that does the trick

---

### Post by fredscripts on 2008-10-25
Thanks for answering! but that software changes the boot screen resolution , not the login screen :(

---

### Post by Kellemora on 2008-10-25
Hi Fred

Refer back to my post #7, that's how you change the Log-in Screen Resolution!

TTUL
Gary

---

### Post by unutbu on 2008-10-25
This describes the same solution as Kellemora's, just stated differently:
[https://help.ubuntu.com/community/FixVideoResolutionHowto#GDM%20uses%20a%20different%20Resolution%20than%20my%20Desktop](https://help.ubuntu.com/community/FixVideoResolutionHowto#GDM%20uses%20a%20different%20Resolution%20than%20my%20Desktop)

Change
```

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```

to 
```

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
        DefaultDepth    24
        SubSection     "Display"
            Depth       24
            Modes      "1280x960"
	    Virtual    1280 960
        EndSubSection
EndSection
```
Change the Modes and Virtual lines to the resolution that is correct for you. You may also have to change DefaultDepth to 16 if your graphics card/monitor can not handle 24 bits (of color) per pixel.

---

### Post by fredscripts on 2008-10-25
Thanks for answering.


Kellemora, I've read your post but I don't have any Virtual section on my xorg.conf (I've posted it in the fist page).


unutbu,that was what I was looking for, the section to change in xorg.conf. I've done what you have told me:

```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"es"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
        DefaultDepth    24
        SubSection     "Display"
            Depth       24
            Modes      "1280x960"
	    Virtual    "1280x960"
        EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection
```

But neither with DefaultDepth and Depth set as 24 nor 16 works after restarting the system. It appears the Ubuntu warning that Low-quality will be used and the system boots in really low quality both login screen and desktop (which of course is not what I'm looking for (1280x960)).

Any other ideas? It's extrange there's no System->Login Screen->Login Screen Resolution , maybe will be in 8.10 :)

---

### Post by starcannon on 2008-10-25
On the rare occasion that I run into this sort of problem I use the modeline generator from here:
[http://xtiming.sourceforge.net/cgi-bin/xtiming.pl](http://xtiming.sourceforge.net/cgi-bin/xtiming.pl)

Then I add the modeline to my xorg.conf AFTER backing up xorg.conf, indeed lets do that now.
```
cp /etc/X11/xorg.conf ~/xorg.conf_BACKUP
```Okay that will make a copy of your xorg.conf in your /home/username folder, now lets tweak the original knowing that we can always roll it back to defualt. DO NOT copy paste from my xorg.conf, this one is tuned for an nfren 1500MA monitor on an nvidia 6600gt, your monitor and graphics card are likely different, only use my xorg.conf as a map on where to put the new modelines and subsections, etc...
```

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Thu Feb 14 18:20:37 PST 2008

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
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
    Modeline "1024x768@60" 64.56 1024 1056 1296 1328 768 783 791 807
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
        Modes       "1024x768@60"
    Virtual       1024 768
    EndSubSection
EndSection

```Yours may look a bit different, but you can add and remove from yours in the same way I did mine. Use mine as a guide to formatting and where to add the lines, do not copy paste from mine, as my monitor and graphics card may be very different from yours. 

GL let us know how it turns out.

---

### Post by fredscripts on 2008-10-25
Thanks for answering starcannon, but I don't think I'll be able to realize how to configure xorg.conf based on your xorg.conf. My graphics card is a Geforce MX/MX 400. It's extrange that having Desktop resolution 1280x960 on the Desktop, when I've configured xorg.conf as unutbu told me, the low-quality Ubuntu appeared after restarting. (btw it's not the first time I'm having problems with xorg.conf so I'm used to backup it before editing :))

So if anyone have another idea of how to change login screen resolution...

---

### Post by unutbu on 2008-10-25
I just realized there was a syntax error in my previous post. Perhaps try the "Virtual" line again, 
using the correct syntax:
```

	    Virtual    1280 960
```

rather than
```

	    Virtual    "1280x960"
```

(I also edited my previous post).

---

### Post by fredscripts on 2008-10-25
Yes unutbu!!! now it worked!!!!

Thanks you all very much for your help!!!!:)

---

