---
title: "Conquered Network Issues, now the dreaded 800 x 600 Resolution"
date: 2008-09-23
forum: New to Ubuntu
---

### Post by FFken on 2008-09-23
Alright, I've searched high and low and I'm coming up with nothing. I somehow manged to figure out how to connect to the network via my wired connection (many thanks to the wealth of info here), but it took me 4 days to find the info and I'd like to solve my next issue quicker.

Right now my screen resolution is set to 800 x 600, in fact the screens and graphics only shows 800 x 600 and a another res (600 x 400, or something along those lines)...

I've been looking around and I can provide you with this info:

I have a Dell Inspiron 4000 (a laptop I found and decided to tinker with), I have a  Pentium III processor, with a  ATI Technologies Inc Rage Mobility M3 AGP 2x (rev 02) graphic card... (found by "lspci" in terminal)

I have tried using the command ```
gedit /etc/X11/xorg.conf
```

And here is what I get:

```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
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
	InputDevice	"Synaptics Touchpad"
EndSection
```

I must be missing something, but I honestly don't want to edit this and screw things up not knowing what I'm doing...

I'd like to be able to use this laptop at a higher res, it would make life so much easier.

I appreciate the help.

---

### Post by neill on 2008-09-23
backup xorg.conf

run sudo dpkg-reconfigure xserver-xorg and pick an appropriate set of resolution options (be conservative !!)

---

### Post by Kellemora on 2008-09-23
Hi FFK

Here are two articles I put together as a Noob that seems to help a lot of folks resolve the resolution problem.  Then, if you end up with a HUGE screen on boot up I'll include the article for that too.  Hope it helps in your case!

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
9/10/08 – rev 9/15/08



Huge Log-in Screen?  Easy fix!
Ubuntu 8.04 Hardy Heron

From a Noob for fellow Noobs!

Preliminary Note:
FWIW:  I did NOT have any luck using StartUpManager from Synaptic.  Editing /etc/usplash.conf xres and yres was unnecessary as they were already correct.  Neither dpkg-reconfigure -phigh xserver-xorg nor update-initramfs -u worked either to correct the HUGE Log-in screen problem.

This is from a total Noob, but took much research to find out exactly, what changed where, to figure it out.  It's also fairly long because it is geared toward big dummies like myself, hi hi.....

A Simple Test:
If you return your monitor to the original default settings, you should find that your log-in screen once again works right.  This was the CLUE to finding out which file controlled the log-in screen for me!

How to change screen resolution (not using Properties) is in another document titled “Screen Resolution Problems?  Easy fix!”  This too might cause log-in screen obesity!

Being a Noob, there may be an easier faster way to do this, but this is what consistently works for me.

The following changes are made using the “ROOT TERMINAL”.

The Terminal in Applications/Accessories does not work for me.  No Permission when you go to save!
If you do not have the Root Terminal under Applications/System Tools, then RIGHT CLICK on Applications, select Edit Menus (by left click) and a Main Menu will appear shortly.  In Main Menu (under Menus) select System Tools and the screen (titled Items) to your right will change.  Place a check mark in the box to the left of Root Terminal and select CLOSE.  The Root Terminal will now appear as a selection when  you select Applications/System Tools.

NOW, Select the Root Terminal.  Before the Root Terminal Opens you will have to Log-in as Administrator.  This is your NORMAL log-in!  Why it doesn't ask for Root Log-in I have no idea.
Even though it shows you are IN Root, you will notice that you are still in your /home/name/ directory.  If you try to open the required file from here, you will get a blank screen so DON'T save it, Close without Saving.

At the prompt type  cd ..  this will take you back to your /home directory.
Type  cd ..  again and you will be in the ROOT Directory and can perform the following command.

Note that the X is a capital letter, all others are lower case!  It's X Eleven not XII.

gksu gedit /etc/X11/xorg.conf  This will open your xorg.conf file for editing.

SAFETY OPTION:  Right Click on File, select SAVE AS (left click).  Add  .old  behind the filename xorg.conf so it reads xorg.conf.old, then Right Click on SAVE.  You will now be VIEWING the saved file so select Right Click on the OPEN Icon and select xorg.conf to reopen the working file for changes.  You can always revert back to the original file by saving it as xorg.conf without the word .old behind it.  End of Safety Option.

Scroll down (near the bottom) and you will find a line titled Section “Screen”, tabbed in twice you will find a line that reads Virtual followed by two sets of digits.  You should recognize these digits as being common screen resolutions.
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
9/10/08 – rev 9/15/08

---

### Post by FFken on 2008-09-23
> **neill said:**
> backup xorg.conf

run sudo dpkg-reconfigure xserver-xorg and pick an appropriate set of resolution options (be conservative !!)

I appreciate your very fast input...

> **Kellemora said:**
> Hi FFK

TTUL
Gary/aka Kellemora
9/10/08 &#8211; rev 9/15/08

Gary, many many thanks! I feel dumb that that was too easy!!

Thanks guys! I'm up and running well!

---

