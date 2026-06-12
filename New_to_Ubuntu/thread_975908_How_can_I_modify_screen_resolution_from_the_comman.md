---
title: "How can I modify screen resolution from the command line?"
date: 2008-11-08
forum: New to Ubuntu
---

### Post by scudworths23 on 2008-11-08
I accidentally set my resolution too high and now I can't see the desktop!

I've tried running failsafe mode, editing xorg.conf, and this command:

*sudo dpkg-reconfigure -phigh xserver-xorg*

but nothing has worked.  Help please?

---

### Post by taurus on 2008-11-08
Maybe

```
sudo xfix
```

---

### Post by scudworths23 on 2008-11-08
command not found

---

### Post by Kellemora on 2008-11-08
Hi Scud

Can you see the top of your screen to get to the Applications pull down?

If so, maybe this will work for you!

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

---

### Post by mapes12 on 2008-11-09
If you can access your desktop allbeit in a strange screen res this fix may help: [http://ubuntuforums.org/showpost.php?p=6086662&postcount=8](http://ubuntuforums.org/showpost.php?p=6086662&postcount=8)

It worked for me.

---

### Post by meastwood on 2008-11-09
For permanent - overrides xorg.conf
~$echo "/usr/bin/xrandr -s <resolution>" > ~/.xprofile

eg:
~$echo "/usr/bin/xrandr -s 1024x768" > ~/.xprofile

For session only:
From desktop -> open a terminal
$xrandr            (to list supported and current resolution(s))
$xrandr -s <resolution>   (to set resolution)

To scale fonts to new resolution:
Measure dimensions of physical screen e.g. 17" ~ 13.3" x 10.75"
Desired resolution set to             e.g. 1280x1024
Horizontal resolution =               1280 / 13.3 = 96.2 dpi
Vertical resolution   =               1024 / 10.75 = 95.3 dpi

Close enough to 96 dpi
System -> Preferences -> Screen Resolution (Font Rendering Details dialog) top left hand corner, Resolution: 96 dots per inch

---

### Post by scudworths23 on 2008-11-09
> **Kellemora said:**
> Hi Scud

Can you see the top of your screen to get to the Applications pull down?



Thank you kellemora but if I could see the screen then I wouldn't be having this problem because I could just go to the display settings and change the resolution back.

---

### Post by scudworths23 on 2008-11-09
> **meastwood said:**
> For permanent - overrides xorg.conf
~$echo "/usr/bin/xrandr -s <resolution>" > ~/.xprofile

eg:
~$echo "/usr/bin/xrandr -s 1024x768" > ~/.xprofile

For session only:
From desktop -> open a terminal
$xrandr            (to list supported and current resolution(s))
$xrandr -s <resolution>   (to set resolution)

To scale fonts to new resolution:
Measure dimensions of physical screen e.g. 17" ~ 13.3" x 10.75"
Desired resolution set to             e.g. 1280x1024
Horizontal resolution =               1280 / 13.3 = 96.2 dpi
Vertical resolution   =               1024 / 10.75 = 95.3 dpi

Close enough to 96 dpi
System -> Preferences -> Screen Resolution (Font Rendering Details dialog) top left hand corner, Resolution: 96 dots per inch

I tried the permanent override unsuccessfully.

```

echo "usr/bin/xrandr -s 1024x768" > ~/.xprofile

```

is that right?  The second solution worked when I started from the terminal but how can I open the terminal from the desktop and then return to the desktop after I'm finished?

---

### Post by scudworths23 on 2008-11-09
Thank you, I've solved it.

---

### Post by Kellemora on 2008-11-09
Hi Scud

Most will say this don't work, BUT I have 8 computers here and have had to do it on 4 of them after I messed the resolution up royally.

If I keep hitting Ctrl-Alt-Backspace, which kills and restarts X, it is MY OPINION ONLY that this causes a rollback to 800x600 eventually (within 3 to 5 tries).......

It's got me out of a lot of jambs, because I'm always moving monitors around here.  hi hi.......

One other trick is to drop in a LIVE CD and reboot from it, then you can get to your config files to fix them.

TTUL
Gary

PS - Since you managed to get this fixed, it's a good idea to mark this thread SOLVED.  That's done using Thread Tools (in Red) at the top of the forum!

---

