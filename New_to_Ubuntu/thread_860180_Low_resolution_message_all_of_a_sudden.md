---
title: "Low resolution message all of a sudden"
date: 2008-07-15
forum: New to Ubuntu
---

### Post by jwlittle on 2008-07-15
I am an absolute newbie to Ubuntu. I have a Dell Dimmension 3000 with a built in video card. When I first cleared off the hard drive and put Ubuntu on it--no problems! My screen resolution was great! About 2 weeks ago I downloaded the updates and my screen resolution is stuck in low resolution mode. I tried the terminal procedure and used "gksudo displayconfig-gtk" I really don't know what I'm doing with it. I tried changing the display options and the graphics options in Administration but there is nothing there. This low res stuff is terrible. Can I remove the last two updates and go back to where this worked? My monitor is a HPw2207 LCD. Any help would be greatly appreciated. Thanks!

---

### Post by benfindlay on 2008-07-15
Try typing ```
sudo dpkg-reconfigure xserver-xorg
``` and follow the onscreen prompts. Choose "Medium" when given the simple, medium or advanced options and you can set which resolutions you want to have available and pick a default.

Hope this helps!

---

### Post by philinux on 2008-07-15
If he's using Hardy then that command no longer sets screen resolution.

What vid card is integrated?

lspci will show you.

---

### Post by benfindlay on 2008-07-15
Whats it been replaced with?

---

### Post by jwlittle on 2008-07-15
Thanks for the help.  After typing in the command line, the only on-screen prompts I got referred to the keyboard.  I did not see anything regarding Medium options?

---

### Post by jwlittle on 2008-07-15
I typed in lspci and this is what I have:
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:01.0 Modem: Intel Corporation FA82537EP 56K V.92 Data/Fax Modem PCI (rev 04)
01:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)

---

### Post by Heinzelotto on 2008-07-15
I am not exactly sure (I am not using Gnome) but I think somewhere in System Menu -> Administration -> Display you can change your screen resolution.

---

### Post by jwlittle on 2008-07-15
Unfortunately there are no options to change in System Preferences

---

### Post by larryfroot on 2008-07-15
Well, your right-ish...its in system > preferences but it may well be of no use at all. I found out the other day that my resolution was low on hardy, and adjusting the display was of limited value when I could either have it on at very low resolution, or switch it to stupidly low resolution. I went scouring the forum and came up with a couple of posts I copied into a text file...just haven't had the time to apply myself properly to the situation, but the following copy from two of the posts I found may be of use...unfortunately I cant remember who posted them, or I would credit them..

...and if you do decide to apply the following BE CAREFUL!!! CHECK AND DOUBLE CHECK as you go along. The advice to keep within the ranges declared is absolutely vital to keep your monitor working. 

I have carefully read through both of them beforehand, and they do proceed with adequate caution and common sense...if anyone else wants to do the same with a view to clear them, please do!

Find your monitors manual (manufacturers website and Google are useful).
Look for hozizontal sync and vertical refresh rates, also if bandwidth or maximum dot clock / pixel clock is mentioned, write it down.

Edit xorg.conf and put correct values to your xconf.org's Monitor section. Something like this:

Section "Monitor"
    Identifier "CM752ET"
    HorizSync 31-101
    VertRefresh 60-160
EndSection

Be sure that Identifier is same as the Monitor line in Screen section.

More info and a nice howto here:

[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

###############################

CUSTOM MODELINES:

If you know what your monitor can do, for example 1024x768@75Hz, you can use this page to generate a custom Modeline for you xorg.conf:

    [http://www.bohne-lang.de/spec/linux/modeline/](http://www.bohne-lang.de/spec/linux/modeline/)

Copy paste the new Modeline to Monitor section (for example):

Code:

 # 1024x768 @ 75.00 Hz (GTF) hsync: 60.15 kHz; pclk: 81.80 MHzModeline "1024x768_75.00"  81.80  1024 1080 1192 1360  768 769 772 802  -HSync +Vsync

Watch that the hsync is in range with the HorizSync on the same section (in this example the range is 31-101 and this modelines hsync is 60.15, so we're safe). Also the VertRefresh and the refresh rate you selected (75Hz in this example) should match - in this example VertRefresh is 60-160 and modeline is 75Hz, so that's all good.

Now you can select the default resolution and colordepth by tweaking the Screen section. It should look something like this:

Code:

Section "Screen"
    Identifier    "Default Screen"
    Device        "NVIDIA Corporation NV34 [GeForce FX 5200]"
    Monitor        "CM752ET"
    DefaultDepth    16
    SubSection "Display"
        Depth        16
        Modes      "1024x768_75.00"
    EndSubSection
EndSection

Monitor name here (CM752ET) matches the Identifier on your Monitor Section. Device line here matches the identifier on your Device section - you get the idea? It ties together some settings for your screen - the graphics card and your monitor. You may have more Subsections here, but only one is needed.

Change the DefaultDepth to what you would want it to be, 16 (65536 colors) or 24 (16M colors). Change the Modes line to match the resolutions you want to use - Depth must match DefaultDepth (here it's 16).

Save the config. If you're in X, hit CTRL+ALT+BACKSPACE to restart X (if you're running logon manager like xdm, kdm or gdm). Change between virtual consoles with CTRL + F1 F2 F3 and so on - your X should be on F7.

Starting the X:
startx OR sudo /etc/init.d/gdm start (in KDE it's kdm)

If that doesn't work, try fixing the xorg.conf or get back to your original by copying the backup over your changed one with:
Code:

sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf

---

### Post by PmDematagoda on 2008-07-15
Boot Ubuntu in Recovery Mode and use xfix to try and fix the X-Server configuration, after that is finished see if the resolution has now returned back to normal.

---

### Post by larryfroot on 2008-07-15
I booted into the failsafe terminal tried xfix and got an error message telling me it wasn't a command! Is recovery mode different from a failsafe terminal? If it is then the GDM options haven't got it available.

---

### Post by PmDematagoda on 2008-07-15
> **larryfroot said:**
> I booted into the failsafe terminal tried xfix and got an error message telling me it wasn't a command! Is recovery mode different from a failsafe terminal? If it is then the GDM options haven't got it available.

Are you running Ubuntu 8.04 by any chance?

---

### Post by jwlittle on 2008-07-15
How do I boot in Recovery mode?

---

### Post by jwlittle on 2008-07-15
Thanks to everyone for their help!! I'm back up and running! Yeehah.

---

### Post by sop408 on 2008-07-15
> **jwlittle said:**
> How do I boot in Recovery mode?
You can go to Recovery mode, by pressing 'Esc' button when the bootloader turns up, then you will see it.

---

