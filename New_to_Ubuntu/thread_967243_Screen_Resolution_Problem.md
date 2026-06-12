---
title: "Screen Resolution Problem"
date: 2008-11-01
forum: New to Ubuntu
---

### Post by ultblad1 on 2008-11-01
Hello all, I'm very much new to Ubuntu, having just installed it today. The first thing I noticed about this is... how horrible the screen resolution is. I'm running a desktop and flat panel LCD, both from acer. I just switched from Windows Vista, which runs on 1440 by some something resolution, and now Ubuntu has me running at 800 by 600. As you might guess, this is obviously not small enough, so I can't really fit much on my screen.

Does anyone have any ideas on how to fix my screen resolution?

P.S. I read some forum about fixing this, and the sudo command they gave me wasn't helpful at all. It didn't change anything.

Any help would be greatly appreciated!

-Toby

---

### Post by Kellemora on 2008-11-01
Hi Toby

Here is something I put together that might help you!

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

### Post by ultblad1 on 2008-11-02
I believe that I forgot to mention that I installed Ubuntu 8.10 (Intrepid Ibex), not the Hardy Heron. Hence, when I tried to get the application Screens and Graphics, it was not there. I tried to find it under the Other section of the edit menus thing, but it was not there.

The instructions were:
To get started we need the Tool called Screens and Graphics.
If it is not available under Applications/Other, then RIGHT CLICK on Applications, select Edit Menu (left click) and wait for the Main Menu screen to open. From the Main Menu, left column (Menus) select 'Other' and a new list of text will appear in the right screen (items).

Instead of seeing Screens and Graphics appear when I click 'Other', I see ten options, from 'Archive Mounter' to 'Verify Signature'.

Does anyone know where Screens and Graphics went?

-Toby

---

### Post by taurus on 2008-11-02
What graphic card does your machine have and have you installed any driver for it?

---

### Post by diablo75 on 2008-11-02
Screens and Graphics has never been in the Applications menu.

It's located at System>Preferences>Screen Resolution.

---

### Post by ultblad1 on 2008-11-02
I believe I have a NVIDA Geforce graphics card, and the driver for it was installed within Windows. Also, I have an acer X193W LCD monitor, but I don't think it came with any special software.

-Toby

---

