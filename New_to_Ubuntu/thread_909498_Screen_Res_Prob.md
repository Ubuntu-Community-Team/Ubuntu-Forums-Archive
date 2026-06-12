---
title: "Screen Res Prob"
date: 2008-09-03
forum: New to Ubuntu
---

### Post by Mike.B on 2008-09-03
I'm a first time user of Linux. I installed kubuntu, everything seemed ok so I thought I'd have a look around. I changed the screen res to 1024 x 768 as it is in Windows. the next time I booted in, the res is stuck on 640 x 480 and will not let me change it back even tho I use as admin, the slider will NOT move.
What do I do.:oops:

---

### Post by bhadotia on 2008-09-03
In KDE (kubuntu) we have a graphical interface RandR (can't remember where its found- usually as an appelet in the system tray) you can try using that. 
Or use the command line . Open the terminal and type 'man randr' (without quotes) , this will give you the info you need to know regarding the command randr . Then use that command as required.

Heres a qoute from the [Comprehensive Video Howto]("http://ubuntuforums.org/showthread.php?t=766683")

> 
**[COLOR=DarkRed]Resolution:[/COLOR]** To enable the correct display resolution in Ubuntu, you have several options. First of all, there is the fairly useless tool in System > Preferences, the soon to be dead displayconfig-gtk tool, and finally, RandR - the newest method. There will be a graphical frontent (GUI) for RandR soon (keep an eye out for it in System > Administration), but for now you will need to use the command line. Let's say you wanted to change your resolution to 1280x800, you would need to execute the following command:

**sudo xrandr -s 1280x800**

If that fails, bring up a list of "supported" resolutions with this command:

**sudo xrandr -q**

Use the first command again and set the highest resolution that RandR claims is supported. Once that is set, try setting the resolution you know is correct, as it may now accept that resolution.

If you're still having issues, press Alt+F2 and type "gksudo displayconfig-gtk" (without "gtk" in Kubuntu), type your password and execute, then select the resolution you want from the list. Some of you may have to select a different screen/monitor in the list before you can successfully change the resolution. Reboot/logout if necessary, then go to [Launchpad]("http://launchpad.com/") and report a bug.


Also, try restarting the computer:)

---

### Post by jynyl on 2008-09-19
Are there any other options for changing screen resolution?

Running Kubuntu 8.04, new install, with ATI 9200 graphics card.  The live cd runs 1280x1024 fine, which is correct for the monitor.  But the installed system only gives 640x480.
In xrandr, displayconfig and System Settings, the 640x480 is the only option available.

Do I need to manually edit /etc/X11/xorg.conf ?  If so, how?

TIA

---

### Post by jynyl on 2008-09-19
In /etc/X11/ there was an older file xorg.conf.1 (which I didn't put there).  Moving this to xorg.conf and restarting xserver seems to fix things.  This conf file seems to have very little in it.

---

