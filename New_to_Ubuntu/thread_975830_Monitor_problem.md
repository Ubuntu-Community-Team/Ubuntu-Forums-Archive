---
title: "Monitor problem"
date: 2008-11-08
forum: New to Ubuntu
---

### Post by davidtrickett on 2008-11-08
My monitor recently expired, and I bought a new one - Samsung 943N.

The old one worked fine when I started using Ubuntu - all resolutions in place etc. However the new one is not so co-operative. Maximum resolution was 640x480. After some mucking around with xorg.conf on the next reboot Ubuntu didn't like it & gave me a monitor configuration screen, but this decided that my monitor was "plug & play" and the 943N was not listed.

I accepted what it wanted me to do, and resolution is now up to 800x600 - better but still well short of the 1280x1024 I should be getting.

Can someone help please?

Thank you.

---

### Post by alienexplorers on 2008-11-08
Set up your monitor section of your xorg.conf with the following data:
> Synchronization
Horizontal      30 ~ 81 kHz
Vertical        56 ~ 75 Hz


Your xorg.conf monitor section should then look like:
```
Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Samsung"
    ModelName      "Samsung 943N"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
    ModeLine       "1280x1024_60.00" 108.9 1280 1360 1496 1712 1024 1025 1028 1060 -hsync +vsync
    Option         "DPMS"
EndSection
```

---

### Post by davidtrickett on 2008-11-09
Many thanks for your help - but unfortunately it doesn't seem to have got me anywhere - max. resolution is still firmly stuck at 800x600.

I see that there is another section in xorg.conf as follows:

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	Defaultdepth	24
	Sub Section "Display"
		Depth	24
		Modes		"640x480@60" "800x600@60" "1280x1024@60"
	EndSubSection
EndSection

The 800x600 & 1280x1024 modes I added myself - it was after this that I did get 800x600.

Should I be amending this section?

---

### Post by dabl on 2008-11-09
Just a hunch -- change that Defaultdepth 24 to Defaultdepth 16, restart X, and let's see if it makes a difference.  You can always change it back if it doesn't help.  :)

---

### Post by Kellemora on 2008-11-09
Hi DT

Have you installed the Screens&Graphics module?

It often works to solve screen resolution problems!

Here is a copy that includes how to do that about midway through the article.

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

---

