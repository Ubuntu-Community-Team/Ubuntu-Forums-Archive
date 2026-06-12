---
title: "ATI settings manager?"
date: 2008-09-14
forum: New to Ubuntu
---

### Post by Zopiac on 2008-09-14
so i got an ATI Radeon x1650PRO video card, and after a few months, got it working hardware-wise, and now im stuck in 640x480 or something, and have the drivers, but i have no idea what program to use/install to change resolution, etc.

I WAS using an nVidia 6100 onboard, and don't know how ATI works in comparison to nVidia

---

### Post by bobnutfield on 2008-09-14
Under Applications>Other, do you have a listing for ATI Catalyst Control Center?  If you have the restricted driver installed, you can change resolution there.

---

### Post by Zopiac on 2008-09-14
ok i installed that, didnt realize it was under other, though, (didnt even read your post but found it :P ) but it only lists that i can only handle up to 640x480 :(

---

### Post by bobnutfield on 2008-09-14
Hmm..That is odd.  The slider bar on the GUI should allow you to set the resolution higher (it does on my ATI laptop.)  Have you checked in your /etc/X11/xorg.conf file to see what entries are listed in "Device" or "Monitor"?  The driver, of course, should say "fglrx".  There may be a list of resolution choices and if there xorg uses the first entry as the default.  If you are going to edit xorg, I would surely recommend a backup first.

---

### Post by Zopiac on 2008-09-14
OK what do i change?

```
Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"vesa"
	Busid		"PCI:2:0:0"
	Driver		"fglrx"
	Screen	0
	Option		"MergedFB"	"off"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
	Gamma	1.0
EndSection
```

---

### Post by bobnutfield on 2008-09-14
Well, I see why you are stuck in 640X480 as it is the first option.  I am always a little gunshy about advising people to edit their xorg file as it could keep you out of X if you get it wrong.  First, boot into safe graphics mode, open a terminal, and type:

> sudo dpkg-reconfigure -phigh -xserver-xorg

This will reconfigure xorg for you and should give you some choices on resolution.  There are a number of posts on the forum about this issue.  I will try to find a pertinent one for you,

---

### Post by Zopiac on 2008-09-14
> **bobnutfield said:**
> Well, I see why you are stuck in 640X480 as it is the first option.  I am always a little gunshy about advising people to edit their xorg file as it could keep you out of X if you get it wrong.  First, boot into safe graphics mode, open a terminal, and type:



This will reconfigure xorg for you and should give you some choices on resolution.  There are a number of posts on the forum about this issue.  I will try to find a pertinent one for you,

```
Unknown option: x
Unknown option: s
Unknown option: e
Unknown option: r
Unknown option: v
Unknown option: e
Unknown option: r
Unknown option: xorg
Usage: dpkg-reconfigure [options] packages
  -a,  --all			Reconfigure all packages.
  -u,  --unseen-only		Show only not yet seen questions.
       --default-priority	Use default priority instead of low.
       --force			Force reconfiguration of broken packages.
  -f,  --frontend		Specify debconf frontend to use.
  -p,  --priority		Specify minimum priority question to show.
       --terse			Enable terse mode.

```

---

### Post by R_T_H on 2008-09-14
Run the cli code again, but without the "-" before xserver-xorg

i.e. > sudo dpkg -phigh xserver-xorg

---

### Post by Zopiac on 2008-09-14
```
zopiac@Zopiac:~$ sudo dpkg-reconfigure -phigh xserver-xorg
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080914161351
zopiac@Zopiac:~$ 
```

does this mean it worked? if so, what do i do now?

---

### Post by bobnutfield on 2008-09-14
Did you type it exactly as shown?

> sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by R_T_H on 2008-09-14
> **bobnutfield said:**
> Did you type it exactly as shown?

Yes, he did.

---

### Post by bobnutfield on 2008-09-14
It means that it has reconfigured your xorg file.  Hit Ctrl+Alt+Bspce to close down X and then log back in to restart x

---

### Post by Zopiac on 2008-09-14
ok, i did so, and it was in a better resolution, but when i tried to open gnome-do (the only way to do anything, for me) it logged out again? also, the background image was just plain white; had to load into failsafe gnome to do anything.

edit: ok i lied, i also have super+t bound to open terminal, but that did same thing. i cant do anything, or else i will be logged out :(

---

### Post by Zopiac on 2008-09-14
in failsafe mode, i get an error opening the catalyst settings manager. is it just because its in failsafe gnome? the error staes that there is no ATI driver installed; i could open it earlier, though, when i wasnt in failsafe.

---

### Post by bobnutfield on 2008-09-14
The command you ran created a backup file of xorg.conf.  You can revert back to it if the new one does not work you.  This is behaviour I am not familiar with when running that command.  To revert back to your old xorg file, just rename it to xorg.conf and rename the current (the one created by the command) one to xorg.conf.bkp,  That will at least get you back to where you were.  The reconfigure command may have altered your driver.  I would recommend installing Envyng to install your driver.  It will correctly identify your card, and install the correct driver as well as configuring you xorg file.

---

### Post by Zopiac on 2008-09-14
> **bobnutfield said:**
> The command you ran created a backup file of xorg.conf.  You can revert back to it if the new one does not work you.  This is behaviour I am not familiar with when running that command.  To revert back to your old xorg file, just rename it to xorg.conf and rename the current (the one created by the command) one to xorg.conf.bkp,  That will at least get you back to where you were.  The reconfigure command may have altered your driver.  I would recommend installing Envyng to install your driver.  It will correctly identify your card, and install the correct driver as well as configuring you xorg file.

and which one is the backup of the 'original' file?

---

### Post by bobnutfield on 2008-09-14
The command created this file:

> /etc/X11/xorg.conf.20080914161351


This is the backup file.  Just rename this to xorg.conf.

---

### Post by Zopiac on 2008-09-14
i renamed xorg.conf to xorg.conf.bkp, and xorg.conf.backup to xorg.conf, and tried to relogin, but instead of going to the login screen it displayed the logout CLI output over and over for about a minute, then the screen went plack with various, i dont know, lines and dots of varying colors. i restarted the computer, and after a confusing mess of graphics, got to the login screen, logged in, in safe graphics mode, and here i am now. its all very confusing :(

edit: ok, just read your post, didnt think of that as the backup. will change them now.

---

### Post by Zopiac on 2008-09-14
ok, the 'real' backup file is now xorg.conf, i smoothly relogged, and now im at 16bit color, 1024x768 (not optimum) and the catalyst settings manager is telling me it has no drivers.

---

### Post by bobnutfield on 2008-09-14
OK, you fglrx driver was replaced with the -reconfigure command.  I did not think it would remove the driver.  I have ATI, Nvidia and Intel graphics on 3 different machines, and I install the graphics drivers for both Nvidia and ATI with EnvyNG and it worked flawlessly for me.  If you want to try EnvyNG, just install with:

> sudo apt-get install envyng-gtk

This will put the program in the Applications>System>EnvyNG location.  As I said, it worked flawlessly for me on more than one occassion, but you can also reinstall the ATI driver the original way you installed.

---

### Post by Zopiac on 2008-09-14
i see no EnvyNG, and the catalyst program still says theres no driver...i installed the driver before with the in safe graphics mode, which it booted into automatically. how do i boot into it manually?

the hardware drivers program says that the/a driver is enabled, but it isnt in use.

edit: ok, in gnome-do i found envyng.

---

### Post by bobnutfield on 2008-09-14
Did you reboot after you restored the original xorg.conf file?  Also, just make sure in xorg.conf it still says that the driver is fglrx (dont edit anything, just check it).

EnvyNG is in the Synaptic Package Manager and can be installed that way, but it appears you still have the drvier installed, so rebooting should put it in use if it is showing as enable in the Hardware Drivers.

---

### Post by Zopiac on 2008-09-14
i used envyng, and im EXACTLY back to where i started. everything works perfectly, but im stuck in 640x480 resolution D:

---

### Post by bobnutfield on 2008-09-14
Well, I have to admit I am stumped.  Everything I know about xorg should have worked with the proper drivers installed.  I will do a little research on this forum and elsewhere for you and see what I can find.  I will post back.

---

### Post by Zopiac on 2008-09-14
> **bobnutfield said:**
> Well, I have to admit I am stumped.  Everything I know about xorg should have worked with the proper drivers installed.  I will do a little research on this forum and elsewhere for you and see what I can find.  I will post back.

all right, thanks for your help so far :)

---

### Post by Zopiac on 2008-09-14
WOW. THAT WAS EASY.

i tried a little experimentation.....

```
Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	SubSection "Display"
		Depth	24
		Virtual	640	480
		Modes		"640x480@60"
	EndSubSection
	Defaultdepth	24
EndSection
```

all i did was change the 640x480 to 1280x1024, and POOF i have the res. thx all for the help, and if i missed a step where one of you told me to do this, sorry(?)

---

### Post by bobnutfield on 2008-09-14
That's great!  Glad you got it working.  I was going to suggest a direct edit of xorg.conf, but did not want to bork your whole desktop with a bad suggesttion.  Just for future note, I did find a thread which seems to mirror your problem, so you might want to bookmark for any future probs.

[http://ubuntuforums.org/showthread.php?t=834528&highlight=ATI+Screen+resolution]("http://ubuntuforums.org/showthread.php?t=834528&highlight=ATI+Screen+resolution")

---

### Post by Zopiac on 2008-09-15
Well it turns out that i cannot use the drivers....when i enable them, it brings me to safe graphics mode, which disables the driver. i have no idea what is going on anymore :confused: is there a specific driver i need for the ATI Radeon x1650PRO video card, or what? i would think the one in Hardware Drivers would be it, and that it would work!

---

### Post by Zopiac on 2008-09-15
well i try to go to the ATI Catalyst manager, but it tells me i do not have a driver. i installed the 8.8 drivers from the ATI site, enabled them, and restarted my computer. it says they are enabled and working, but im still being told that i have no drivers by the Catalyst Manager!

---

### Post by Zopiac on 2008-09-15
Bump.

---

### Post by Zopiac on 2008-09-15
now the OS isnt even READING xorg.conf...the data in there is way off from what is being shown. I have no eyecandy, no res. above 640x480, and i cant do anything involving 3D or else my computer crashes. Im about to scrap ubuntu if i canf fix this soon :mad::mad:

---

### Post by dwarx on 2008-09-16
What does your fglrxinfo show? (in terminal write that) you might have to reboot and clear the x-conf and re-install from scratch. 

It took me 5 hours and 4 different drivers to get my Ati card up and running, and it's still not 100%... I had the same resolution problem that you have, it means you are basically still running with Mesa drivers... double check!

---

### Post by Zopiac on 2008-09-16
```
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.3-rc2)

```

well, whenever i try to load a different driver, and restart, it brings me to safe graphics mode, where it resets the driver to, as t seems, Mesa.

how do i reset xorg.conf?

---

