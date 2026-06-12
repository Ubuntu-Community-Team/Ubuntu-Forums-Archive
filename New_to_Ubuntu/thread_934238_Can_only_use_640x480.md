---
title: "Can only use 640x480"
date: 2008-09-30
forum: New to Ubuntu
---

### Post by Tony Williams on 2008-09-30
I'm using a nVidia 5200 PCI card.  Usually under Windows I can run my monitor at 1280x1024 @ 75Hz.  I am running Ubuntu 8.04 with it's Proprietary drivers. I can only select 640x480 or 320x240 @ 50/1Hz

I have attached my xorg.conf (.txt) file.

I'm sure it's an easy fix, I looked around the internet but couldn't find a fix that worked, bear in mind that I'm a bit of a n00b at this.

But thanks to any help.

---

### Post by abeisgreat on 2008-09-30
I had this same issue and if it is the same as my issue it is relatively easy to fix

1) Turn off the restricted drivers
2) go to the Application menu setup, make sure 'Other' is checked, and make sure 'Screen Setup' (Or something like that) is checked. 
3) Open the Screen setup thing in the Apps menu, you should be able to configure the settings to fit your moniter. then accept the changes and close the window. 
4) Turn on the restricted drivers
5) restart

That is very brief, but that is about the process you need to go through, I'm in class on a windows machine so I can't check what exactly those menu options are called. But as I recall it isn't to hard to tell when I mean. 

Hope this helps.

---

### Post by Tony Williams on 2008-09-30
Turned off the drivers, but I can't find the 'Application menu setup' you talked about ... I've got go myself so I'll look when I get back in about 5/6 hours.

Thanks.

---

### Post by aeiah on 2008-09-30
have you used the nvidia-settings control panel or just tried the gnome menu > preferances > resolution menu option? might be worth looking at the nvidia control panel (and installing it first if it isnt on your system). but try the other method first i guess :o

---

### Post by abeisgreat on 2008-09-30
> **Tony Williams said:**
> Turned off the drivers, but I can't find the 'Application menu setup' you talked about ... I've got go myself so I'll look when I get back in about 5/6 hours.

Thanks.

Try right clicking on the Applications menu and clicking edit menu, see if that helps.

---

### Post by SunnyRabbiera on 2008-09-30
its too bad the app you will need will be gone in ibex, guess everybody will be stuck at 640x480 unless they manually configure crap.

---

### Post by abeisgreat on 2008-09-30
> **SunnyRabbiera said:**
> its too bad the app you will need will be gone in ibex, guess everybody will be stuck at 640x480 unless they manually configure crap.

Seriously? thats just bull. Are they going to put in some alternative? Or maybe they could just combine it with the normal screen res app.

---

### Post by SunnyRabbiera on 2008-09-30
> **abeisgreat said:**
> Seriously? thats just bull. Are they going to put in some alternative? Or maybe they could just combine it with the normal screen res app.

well yes they have been merged, but the result is not that great.
On the live I am stuck at 800x600, it doesn't do a good job at all.
I know when Ibex comes out I will be directing people away from it.

---

### Post by Tony Williams on 2008-09-30
Right got it to run at 1280x1024 by doing what abeisgreat said.  The problem is it's running at 50Hz and not 75Hz.

[[IMG]http://img218.imageshack.us/img218/7023/screenshotzi9.th.png[/IMG]](http://img218.imageshack.us/my.php?image=screenshotzi9.png)[[IMG]http://img218.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

---

### Post by wolfen69 on 2008-09-30
> **Tony Williams said:**
> Right got it to run at 1280x1024 by doing what abeisgreat said.  The problem is it's running at 50Hz and not 75Hz.

[[IMG]http://img218.imageshack.us/img218/7023/screenshotzi9.th.png[/IMG]](http://img218.imageshack.us/my.php?image=screenshotzi9.png)[[IMG]http://img218.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

is the screen flickering? if not, don't worry about it.

---

### Post by Kellemora on 2008-09-30
Hi Tony

Give this a shot!

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

