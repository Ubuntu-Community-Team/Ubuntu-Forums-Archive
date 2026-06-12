---
title: "Increasing screen resolution in Ubuntu 8.04 LTS"
date: 2008-10-01
forum: New to Ubuntu
---

### Post by sumithaswar on 2008-10-01
I have a HP Pavilion dv2945se Notebook PC with AMD Turion Machine(64-bit) and have an NVIDIA GeForce Go 7150M (UMA) graphics with 1071MB

After successfully installing Ubuntu 8.04 the resolutions is set to 800x600
I want to set it to 1024 x 768

Can anybody provide me any clue..

---

### Post by wolfen69 on 2008-10-01
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` then restart x or reboot.

---

### Post by cam381 on 2008-10-01
Unclear on whether or not you don't know how, or you physically can't. It's under System->Preferences->System Resolution

---

### Post by SiHa on 2008-10-01
...and don't foget that to do either of the above, you need first to enable restricted drivers. System > Administration > Hardware drivers.
There should be 'Nvidia Accelerated Graphics Drivers with a checkbox next to it. Tick the box. You will need a reboot, but the system should then automatically restart at the highest resolution it detects the monitor can display.

---

### Post by Henner on 2008-10-01
You might want to give this a try, you can find it under System>Administration>Nvidia X server settings after you install it.

```
sudo apt-get install nvidia-settings
```

---

### Post by Kellemora on 2008-10-01
Hi S

I see this is your first post!  Welcome to Ubuntu!

I'm a Noob two and had those same problems, so I wrote an article as simply and completely as possible on how I fixed it, and tested it on several machines.

Hope it works for you!

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

### Post by sumithaswar on 2008-10-02
Gary/aka Kellemora...
I tried the same walkthrough as suggested by you and after finding the manufacturer as in my case Hawlett packard I selected the 1024x768 resolution and restarted the PC but my screen got screwed up badly and is all smugged... I am seeing a tiled sort of ghost pictures....
How do I revert back the changes??

---

### Post by Kellemora on 2008-10-02
Hi Sumithaswar

Ctrl-Alt Backspace a few times will keep stepping it back until it hits one that works.  Just don't select OK if it's still flashy.  You can do this like 3 to 5 times, then it will revert back to the original default setting.

TTUL
Gary

---

### Post by sailor2001 on 2008-10-02
I think that after you select your resolution as per kellermora, ctrl/alt/backspace and select "options" at the bottom and click gnome, not the default gnome.  This rewrites your config file.

---

### Post by Dave Otter on 2008-10-02
alt + F2 >> sudo displayconfig-gtk 


This should allow you to set reolution

---

