---
title: "Settings resolution through Nvidia X Server Settings"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by rhc on 2008-10-31
I installed Ibex to my desktop today and i set resolution to 1152*864 and 75 hz with the Nvidia X server settings in system>administration.(i have Lg crt f700b). I applied it and click "save to x configuration file".

But when i log out or restart the system, it changes to default resolution.

I know i can set the resolution and refresh rate from xorg.conf but i want to know the problem and solution anyway.

Thanks for help.
----
Title:  "Set resolution through Nvidia X Server Settings  " : )))

---

### Post by taqkavar on 2008-10-31
try running it as root and then make the changes to the settings:
sudo nvidia-settings

---

### Post by rhc on 2008-10-31
> **taqkavar said:**
> try running it as root and then make the changes to the settings:
sudo nvidia-settings
The same thing happened. No change.

---

### Post by Kellemora on 2008-10-31
Hi RHC

I put together something for Hardy, don't see why it wouldn't work in the new release.

I'll add it here in case you want to give it a try.

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

### Post by aimpau on 2008-10-31
open up a terminal and type:

```

sudo nvidia-xconfig

```

then

```

gksu nvidia-settings

```

click autodetect display, change your modes then apply, then click save to configuration file WITH the merge checkbox checked.

---

### Post by Cowloon on 2008-11-01
Neither of those things work for me (starting with a fresh xorg.conf using nvidia-xconfig and then having nvidia-settings merge changes, or using the screens and graphics tool). As soon as I log out the resolution switches back to 1280x1024.

When I use nvidia-xconfig and nvidia-settings, my xorg.conf only has 1600x1200 as an entry, yet I get 1280x1024 as soon as I get back to gdm.

This is a worse problem for wmii, because after I run nvidia-settings, wmii still behaves as though my entire desktop is the upper left 1280x1024 of my 1600x1200 desktop.

This is with ubuntu 8.04

---

### Post by rhc on 2008-11-01
> **aimpau said:**
> open up a terminal and type:

```

sudo nvidia-xconfig

```

then

```

gksu nvidia-settings

```

click autodetect display, change your modes then apply, then click save to configuration file WITH the merge checkbox checked.

Except i didn't understand that "merge checkbox" -didn't see it either-, no it doesn't work.

And Kellemora; there is no "screen and grapichs" option in "other" menu. Also in edit menu screen. How can i find it in Synaptic?

---

### Post by Cowloon on 2008-11-01
The merge checkbox that I checked was in the dialog that appears when you click save.

Screens and Graphics was in the Applications menu unchecked, then after checking it, it moved to the "Other" menu.

In any case, neither  of those methods have fixed the problem for me.

---

### Post by rhc on 2008-11-03
Both of them did not work.
I think there's a bigger problem about that Nvidia settings and it's really important for average home user not to change an easy resolution setting from xorg.conf file.
Should be solved.

---

### Post by earthpigg on 2008-11-03
i have the same problem.

in 8.04, you click 'save' and another dialog box comes up asking you what file to save to and if you want to merge the files.

in 8.10, you click 'save' and the entire nvidia-settings program closes instantly (but your changes, if you clicked 'apply', remain for the rest of the x session).

is this the same thing that is happening to everyone?

---

### Post by dulence on 2008-12-09
I have similar problems. The graphics settings seem to work only after I start nvidia-settings and they're only enforced till the end of the session. After that the system reverts to default values.
Has this issue been resolved?

---

### Post by Tatty on 2008-12-09
I dont know if this is related (i only skimmed over the thread) but when I have used the nvidia-settings dialog before I found that if i press apply first, then it will not save the settings.

Click to save the settings without pressing apply.

---

### Post by dulence on 2008-12-09
Nope, didn't help.

---

### Post by dulence on 2008-12-10
Anyone?

---

### Post by m_l17 on 2008-12-10
Give this a try:

[http://ubuntuforums.org/showthread.php?t=975058]("http://ubuntuforums.org/showthread.php?t=975058")

---

