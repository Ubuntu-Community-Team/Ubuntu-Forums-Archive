---
title: "HOWTO: Gutsy Gibbon 7.10 + Xgl + ATI fglrx + Compiz Fusion"
date: 2007-10-19
forum: Outdated Tutorials &amp; Tips
---

### Post by michael37 on 2007-10-19
[SIZE="4"]This document is specific to proud owners of challenging ATI video cards and to the new release of Gutsy Gibbon 7.10.  The guide has two sections: instructions for the fresh Gutsy install and instructions for Feisty upgrade.
[/SIZE]

Note for Hardy Heron 8.04 and Intrepid Ibex 8.10 users.  The new ATI accelerated driver supports so called AIGLX so XGL is not required.  However, XGL still works, and is apparently a working strategy to address some video playback (choppy video, video tearing) problems with Compiz Fusion. 

This guide supersedes [thread=482773]Feisty guide[/thread].  The original location of this guide is [thread=569654]here[/thread].  I prefer that troubleshooting takes place on the "Desktop Effects" optimization forum in [thread=569654]the original thread[/thread] rather than here.

[SIZE="6"]If you are doing fresh install of Gutsy[/SIZE]

When using apt-get, please close Synaptic Package Manager or Update Manager.

[LIST=1]
[*]Enable fgrlx driver.

Install linux-restricted-modules and restricted-manager provided in the restricted repositories:
```

sudo apt-get update
sudo apt-get install linux-restricted-modules-generic restricted-manager

```
Open the restricted drivers manager in "System -> Administration -> Restricted Drivers Manager" and select "ATI accelerated graphics driver".


[*]Install xserver-xgl package
```

sudo apt-get install xserver-xgl

```
[*]Install compiz
```
sudo apt-get install compizconfig-settings-manager compiz compiz-core compiz-fusion-plugins-main compiz-fusion-plugins-extra compiz-gnome compiz-plugins libcompizconfig-backend-gconf libcompizconfig0

```
[*]Reboot
[*]Log in.  3D effects should be enabled!
[/LIST]

[SIZE="6"]If you are upgrading from Feisty 7.04 or earlier versions and you have run Xgl before.[/SIZE]

When upgrading, you may experience blank screen, a screen with no windows and toolbars, a screen with only a background, or any other mess.  It is caused by the customized scripts for Xgl which do not work with Gutsy.  So, we need to clean up.  We will end up wiping your custom Compiz settings -- but this may be required since some customizations applicable to early alpha versions of Compiz Fusion in Feisty are incompatible to more mature Compiz Fusion version in Gutsy.

If you really can't log into a working X session and open a terminal, simply press "Ctrl-Alt-F1" to get into the text prompt and follow the removal steps (1-4) from the text interface.  After a reboot, the graphics should work better.

When using apt-get, please close Synaptic Package Manager or Update Manager.

[LIST=2]
[*]Remove compiz
```

sudo echo "activate sudo"
sudo apt-get --purge remove compiz*
sudo apt-get --purge remove libcompiz*
sudo apt-get --purge remove libdecoration0
sudo apt-get --purge remove compizconfig-settings-manager 
sudo apt-get --purge remove python-compizconfig

```
[*]Remove Xgl
```

sudo apt-get --purge remove xserver-xgl

```
[*]Clean up
```

sudo apt-get autoremove

```
[*]Remove customizations
```

rm -rf ~/.compiz
rm -rf ~/.config/compiz
rm -rf ~/.gconf/apps/compiz
sudo rm -i /usr/local/bin/startxgl.sh
sudo rm -i /usr/share/xsessions/xgl.desktop

```
When asked to remove the files, type YES.  If the files were present and you removed them, proceed to the next item.  Otherwise, undo customizations to /etc/gdm/gdm.conf and /etc/gdm/gdm.conf-custom that you have made from [ this section of the guide](https://help.ubuntu.com/community/CompositeManager/Xgl#head-0e4ffce2a76cdb03b8dbd57642f13fac385afef0)
[*]Reboot
[*]Login back in and find yourself in a 3D effect devoid session.  You may not even be running a windows manager.  If you can't move windows and don't see window decorations, press "Alt-F2" and type ```
metacity --replace
```
[*]Verify that everything else is working properly, e.g. Firefox opens, Wired and/or Wireless Network connects, etc.  This is the best time to troubleshoot everything else until we enable 3D effects.
[*]Enable fgrlx driver.

Install linux-restricted-modules and restricted-manager provided in the restricted repositories:
```

sudo apt-get update
sudo apt-get install linux-restricted-modules-generic restricted-manager

```
Open the restricted drivers manager in "System -> Administration -> Restricted Drivers Manager" and select "ATI accelerated graphics driver".
[*]Reboot if necessary.
[*]After reboot, log back in.
Open terminal and run
```

fglrxinfo -display :0

```
and verify that you see something like this:
```

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400
OpenGL version string: 2.0.6473 (8.37.6)

```
[IMG]https://help.ubuntu.com/htdocs/ubuntu/img/attention.png[/IMG]If you don't have command fglrxinfo, you either don't have a supported ATI card or you missed a step or two.  Go back through all steps.  If unsure, post your /etc/X11/xorg.conf in this thread.
[*]=================================
[*]Are you ready to get back into the wobbly windows and Desktop Cube?
[*]=================================
[*]Install Xgl.
```
sudo apt-get install xserver-xgl
```
[*]Install compiz
```
sudo apt-get install compizconfig-settings-manager compiz compiz-core compiz-fusion-plugins-main compiz-fusion-plugins-extra compiz-gnome compiz-plugins libcompizconfig-backend-gconf libcompizconfig0

```
[*] Reboot
[*] Log in. 3D effects should be enabled!  You no longer need to select a special Xgl session.
[/LIST]

[SIZE="4"]Troubleshooting[/SIZE]

A common problem in step 10 is fgrlxinfo output like this:
```

# fglrxinfo -display :0
display: :0.0 screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)

```.
That means you are not using the restricted driver.  Enable it via Restricted Driver Manager -- see step 8.  Just in case, run command 
```

sudo aticonfig --initial

```
then reboot (that's step 9).

-----------
If you have a laptop, suspect and hibernate will not work until ATI fixes a bug in the driver.  More details at [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/121653](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/121653)
-----------

If you have any questions, please post output of commands
fglrxinfo -display :0
fglrxinfo -display :1
as well as contents of your /etc/X11/xorg.conf file in  [thread=569654]the original thread[/thread]

[SIZE="4"]References[/SIZE]
[SIZE="5"]DO NOT FOLLOW THESE LINKS BLINDLY.  MOST ARE WRITTEN FOR FEISTY AND THIS GUIDE UNDOES WHAT IS SUGGESTED IN THESE GUIDES.
[/SIZE]
[http://ubuntuforums.org/showpost.php?p=3285132&postcount=217](http://ubuntuforums.org/showpost.php?p=3285132&postcount=217)
[http://ubuntuforums.org/showthread.php?t=488385](http://ubuntuforums.org/showthread.php?t=488385)
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
[https://help.ubuntu.com/community/RestrictedDrivers/ATI](https://help.ubuntu.com/community/RestrictedDrivers/ATI)
[https://help.ubuntu.com/community/CompositeManager/Xgl](https://help.ubuntu.com/community/CompositeManager/Xgl)

---

### Post by seasom on 2007-11-23
so after going through half a dozen installation guides on this site & the wiki and being unsuccessful, this worked for me.  thank you so so much!

---

### Post by [ajax] on 2007-11-25
Well, I'll concede that this worked better for me than anything else so far.

However, Compiz Fusion is quite slow, esp. compared to my old Beryl Install.

"fglrxinfo -display :0"
> 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1950 Series
OpenGL version string: 2.0.6958 Release


"fglrxinfo -display :1"
> 
display: :1.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (2.1 Mesa 7.0.1)


"xorg.conf"> # xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver	"fglrx"
	Option	"VideoOverlay" "on"
	Option	"OpenGLOverlay" "off"
	BusID		"PCI:6:0:0"
EndSection


Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"SyncMaster"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1440x1440" "1440x900" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "Extensions"
	Option "Composite" "Disable"
EndSection


---

### Post by keithk on 2007-11-25
Just thought I'd chime in also. This worked for me after a long series of disaoopointments. thanks!

---

### Post by [ajax] on 2007-11-25
Fixed the problem.  Word of warning: the ATI 42.x.3 (whatever the latest one is as of 11/25/07) sucks.  I downgraded the driver to get things to run smoothly.

---

### Post by adrianmak on 2007-11-27
Does this guide applicable on new ati display like ati 2400, 2600, 2900, 3850, 3870 card ?

---

### Post by accog on 2007-11-27
when i attempt to install the xserver-xgl i get this from the terminal:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
anyone got any ideas?

---

### Post by olskar on 2007-11-28
> **accog said:**
> when i attempt to install the xserver-xgl i get this from the terminal:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
anyone got any ideas?

Run "sudo dpkg --configure -a" as it tells you :)

---

### Post by accog on 2007-11-28
Thanks a bunch! (D'oh!)

But now when i try to install the xserver-xgl package its telling me it cannot find it. Does it no longer exist?!?

accog@accog-desktop:~$ sudo apt-get install xserver-xgl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package xserver-xgl
accog@accog-desktop:~$

---

### Post by flipfone on 2007-12-01
i followed this tutorial however i get the same problem as all other tries. i will bootup to the login screen then ill login after about 20 seconds of blank screen the screen goes black then back to the login screen? any ideas? im using an ati x1650


 fglrxinfo -display :0
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1650 Series
OpenGL version string: 2.1.7059 Release

---

### Post by Escipion on 2007-12-03
> **accog said:**
> Thanks a bunch! (D'oh!)

But now when i try to install the xserver-xgl package its telling me it cannot find it. Does it no longer exist?!?

accog@accog-desktop:~$ sudo apt-get install xserver-xgl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package xserver-xgl
accog@accog-desktop:~$

Do you have all the extra repositories??

---

### Post by Rheicide on 2007-12-07
Hi, I've followed your instructions and everything works fine; I can use all effects of CompizFusion. However, today it takes longer to load the X session, so I open the terminal to check up and here's what I got:
```
fglrxinfo -display :0
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)
```
```
fglrxinfo -display :1
display: :1.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon 9550 / X1050 Series
OpenGL version string: 1.2 (2.0.6473 (8.37.6))
```
When I completed your how-to, the output of "fglrxinfo -display :0" was what is now the output of "fglrxinfo -display :1".
My /etc/X11/xorg.conf file:
```

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc RV350 AS [Radeon 9550]"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"ViewSonic P95f+"
	Option		"DPMS"
	Horizsync	30-110
	Vertrefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV350 AS [Radeon 9550]"
	Monitor		"ViewSonic P95f+"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Modes	"1280x1024"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  	Screen 		"Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
Section "Module"
	Load		"glx"
EndSection
Section "Extensions"
	Option		"Composite"	"0"
EndSection
```
Then I use the "sudo aticonfig --initial" command but it says:
```
Found fglrx primary device section
Nothing to do, terminating.
```
I can still use all CompizFusion's effects, so is there something wrong or not?
(My English isn't good, I'm sorry if there're any mistakes)

---

### Post by anthonie on 2007-12-07
Would this tutorial also apply to a AGP 9250 card with 256Mb of memory?

---

### Post by Teknyk on 2007-12-09
This worked great!
I did have some problems when I upgraded from Feisty to Gutsy so I had already reinstalled shortly afterwards.

I just followed your example for a fresh install and now I have my eye candy! Works pretty good on this poor thing too.

Gateway MX6441
AMD Turion 64 1.8GHz
ATI Radeon Xpress 200M
Broadcom BCM4318 Wifi
512MB RAM

*EDIT*
I am using the 32bit Ubuntu though.

---

### Post by Zarneth on 2007-12-11
> **adrianmak said:**
> Does this guide applicable on new ati display like ati 2400, 2600, 2900, 3850, 3870 card ?
I got it to work on my HD 3850.
But as Ubuntu doesn't have a driver yet you need to download the driver for the HD2900 from ati.com. It's a tad glitchy as the 38's aren't officially supported yet. But still usable if you can't live with out features such as scale. I hear ati are supposed to be bringing out a new driver in a month or so.

You may also need to do a "sudo dpkg-reconfigure xserver-xorg" to setup the fglxr driver.

---

### Post by Pronco on 2007-12-12
Here's the output of fglrxinfo displays

```

Pronco::~$ fglrxinfo -display :0
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (2.1 Mesa 7.0.1)

&

Pronco::~$ fglrxinfo -display :1
Error: unable to open display :1

```

My VGA is X1600 and it does't work properly

---

### Post by cptjaben on 2007-12-13
After following the guide for upgrading from fiesty and rebooting, everything seems to be in order except that compiz simply won't run. running in the terminal produces this result:

```
compiz (core) - Fatal: GLX_EXT_texture_from_pixmap is missing
compiz (core) - Error: Failed to manage screen: 0


```

Anyone have any ideas? Thanks

---

### Post by gibby213 on 2007-12-15
Moved it to the proper thread

---

### Post by ShAdEd_PaSt on 2007-12-20
nice and easy, good to go on first try. Thanks Ubuntu

---

### Post by darkeale on 2007-12-21
ive got a problem after doing this. the compiz effects work fine, but now my panels dont match my theme. i use the ubuntu studio theme but my panels are the standard grey ubuntu ones. anyone know why?

thanks

alex

---

### Post by liam.dunn144 on 2007-12-25
Thx, except, when I try to install xserver-xgl, I get this: l

Reading package lists ... Done
Building dependency tree
Reading state information
E: Couldn't find package xserver-xgl

:confused: Can anyone help?

---

### Post by ugm6hr on 2007-12-26
> **liam.dunn144 said:**
> Thx, except, when I try to install xserver-xgl, I get this: l

Reading package lists ... Done
Building dependency tree
Reading state information
E: Couldn't find package xserver-xgl

:confused: Can anyone help?

Make sure your Ubuntu is updated first.

Have you tried searching for it in Synaptic and installing from there?

---

### Post by wiiittttt on 2007-12-27
wow, i have been trying to get my x1650 Pro card to work for 2 days until i found this...thanks

---

### Post by yasashii_gogo on 2007-12-28
Ehh, i;m a complete newbie in using Linux, so i'm gonna ask a dumb qn, how do you enable fgrlx driver?

---

### Post by underwog on 2007-12-31
I followed this and when I rebooted the screen resolution wasn't correct. So I went to System -> Admin -> Screens and Resolutions and configured the monitor for widescreen and 1900x1200. Message said I needed to reboot. Now I get a blank screen when X starts. I can log in blindly and it hits the HD like it is logging in, but no screen. I have a 1950XTX. Help?

---

### Post by ruark1 on 2008-01-10
hello
i'm new to ubuntu so please bear with me.
i wanted to post my xorg.conig but when i typed into the terminal
sudo gedit /etc/X11/xorg.conf all i got was a blank page
my problem is when i verify i get

# fglrxinfo -display :0
display: :0.0 screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)

and ubuntu tells me my hardware doesn't need any restricted drivers
i ran this thing -sudo aticonfig --initial- and got a long list and then it said aborted now when i run it it says it can't find the configuration line
i've got an ati 2400hd pro
any help would be awesome
sorry about sounding like an idiot

---

### Post by ugm6hr on 2008-01-16
While this works OK, I would now recommend using the latest ATI driver with AIGLX (no need to install) for Compiz instead of XGL (needs to be uninstalled).

For how this worked on my laptop: [http://ubuntuforums.org/showpost.php?p=3950616&postcount=3](http://ubuntuforums.org/showpost.php?p=3950616&postcount=3)

---

### Post by zasf on 2008-01-18
> **ugm6hr said:**
> While this works OK, I would now recommend using the latest ATI driver with AIGLX (no need to install) for Compiz instead of XGL (needs to be uninstalled).

For how this worked on my laptop: [http://ubuntuforums.org/showpost.php?p=3950616&postcount=3](http://ubuntuforums.org/showpost.php?p=3950616&postcount=3)

I have a x700 and latest fglrx driver with aiglx performs poorly, is fglrx + xgl faster? I used it when compiz came out, but then I haven't used it for a while.

---

### Post by ugm6hr on 2008-01-18
> **zasf said:**
> I have a x700 and latest fglrx driver with aiglx performs poorly, is fglrx + xgl faster? I used it when compiz came out, but then I haven't used it for a while.

I couldn't get xgl to work with fglrx properly at all.  aiglx works just fine for me (but I don't play games - just for Compiz).

---

### Post by B3N on 2008-01-25
Hey guy and gals, great looking forum you got here. I want to stop by and ask a couple of things, I'm a soldier and I'm currently in Iraq. My biggest problem is that I can't plug my laptop into the internet here, I can only download anything onto the computers in the internet cafe and put them on my computer via a jump drive. So now for the question, Is there a way for me to do what you have described above without aptget? Is there a way to DL this stuff onto my jump drive and install from it or CD? Thanks guys,
Ben

Sorry I meant to put this here..  [http://ubuntuforums.org/showthread.php?t=580748](http://ubuntuforums.org/showthread.php?t=580748)

---

### Post by ugm6hr on 2008-01-25
> **B3N said:**
> My biggest problem is that I can't plug my laptop into the internet here, I can only download anything onto the computers in the internet cafe and put them on my computer via a jump drive. So now for the question, Is there a way for me to do what you have described above without aptget? Is there a way to DL this stuff onto my jump drive and install from it or CD?

This might help you: [http://nonetdebs.homeip.net/](http://nonetdebs.homeip.net/)

Otherwise, you can manually search for the files here:
[http://packages.ubuntu.com/gutsy/](http://packages.ubuntu.com/gutsy/)

Or, as long as you have updated your sources online at some point, you can use the download script option in Synaptic Package Manager (System-> Admin-> Synaptic Package Manager):
Mark the packages mentioned in the thread for installation, then go to File-> *Generate Package download script*
To install, use *Add downloaded package*s in the same menu

---

### Post by B3N on 2008-01-25
All right thhanks mate for getting back so quickly. I think that the nonetdebs will work out nicely. I'm going to give it a go now and see what happends. Thanks again!
Ben

---

### Post by Deuz Ex Machina on 2008-01-25
All of this worked, I have wobbly windows, can install my AWN dock, and have my cube effect @.@ I praise thee! \\:D/

---

### Post by OneSeventeen on 2008-01-26
This guide worked GREAT on my HP Pavilion zv6000 laptop which has an ATI Radeon Xpress 200M chip.

The only thing I'm left wondering now is how to use Emerald after following these instructions.  (Many tutorials on getting Emerald to work mention modifying a script that you make when manually installing compiz-fusion as per the old feisty fawn instructions.)

Any tips?

---

### Post by College_Trained on 2008-02-01
The Xgl part makes my desktop cube work in gusty but when I try to boot into my windows partition, I get a BSOD about my ATI graphics card every time.
Anyone know if I can run both the desktop cube and windows or if it's one or the other?

---

### Post by StampU on 2008-02-02
fglrx seems to be working ok for me (no mention of mesa drivers at all), but compiz fails on start up for me.  In terminal window, this is what I get:

Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with fglrx ATi drivers...
/usr/bin/compiz: 378: /usr/local/bin/compiz: not found

Any suggestions?

---

### Post by StampU on 2008-02-05
I got mine fixed.  Upgrading from feisty to gutsy must have left some different file structures than expected.  I had to edit /usr/bin/compiz.

Here is the post that helped me.
[http://ubuntuforums.org/showthread.php?p=4260181](http://ubuntuforums.org/showthread.php?p=4260181)

"change lines 30 and 31 to:
COMPIZ_BIN_PATH="/usr/bin/" # For window decorators and compiz
PLUGIN_PATH="/usr/lib/compiz/"

and then a few lines down, change to:
COMPIZ_NAME="compiz.real" # Final name for compiz (compiz.real)

Before, these lines said:
COMPIZ_BIN_PATH="/usr/local/bin/" # For window decorators and compiz
PLUGIN_PATH="/usr/local/lib/compiz/"
...
COMPIZ_NAME="compiz" # Final name for compiz (compiz.real)"

---

### Post by SexyStud on 2008-02-08
First of all, thanks for this guide. It's by far the best one I've found, after previous unsuccessful tries in the past, this one works.

I have a doubt - or two - though.
My compiz seems a little slow and pulls a bit of my CPU. I noticed that I have the "Direct Rendering: no" line. Could turning this ON make it faster? If so, how can I do it? I'm on ATI Mobility Radeon 9700 + P4 3.4 + 1Gb RAM.

My 2nd question lies on themes. I remember having Emerald as my wannabe-theme manager, but following this tutorial I won't have it installed. Does compiz handles themes with another method now, do I need to install anything? If so, what/how?


Thanks in advance!

---

### Post by jamespickles on 2008-02-08
Yes, This guide is what i used im now happily running Compiz fusion with an Ati radeon x1550 :)

Its awesome, and it isnt slow at all it runs as smooth as i possibly can :)

---

### Post by Lazeballz on 2008-02-10
Hello all -
Ive just installed Gutsy Gibbons...and wow im impressed.  Switching from Windows to this was a snap for me.  The only real issue i have is Drivers. (but then again if you have Vista ((64 bit flavors)) then your in the same boat regardless).

Heres my setup:  MSI board using it as a HTPC.  Im switching from MCE to this sweet looking Myth TV.  My mobo has the ATI 1250 Radeon IGP integrated into it with HDMI output.

I am able to do all the cube shifting and wobbly windows, however here is my issue:
When i go to the GL desktop options - it reads my card as a Generic video card - am i the only one like this?

:~$ fglrxinfo -display :0
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon X1200 Series
OpenGL version string: 2.1.7276 Release

l:~$ fglrxinfo -display :1
display: :1.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (2.1 Mesa 7.0.1)

Also - for display :1 is that normal for me to see Mesa 3d?/

---

### Post by Lazeballz on 2008-02-11
Bump*

---

### Post by sythe on 2008-02-12
This worked great for me. Thanks a lot!

---

### Post by Enissay on 2008-02-15
Hi, after folowing all the tutorial, it seems that my card was successefully installed:

> # fglrxinfo -display :0
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1650 Series
OpenGL version string: 2.0.6473 (8.37.6)

# fglrxinfo -display :1
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :1.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1650 Series
OpenGL version string: 1.2 (2.0.6473 (8.37.6))


But when i tried to enable effects it said:
> Desctop effects could not be enablad

My xorg.conf is :

> # xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"be"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"fglrx"
	Busid		"PCI:2:0:0"
EndSection

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"SyncMaster"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1280x1024"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
Section "Module"
	Load		"glx"
EndSection
Section "Extensions"
	Option		"Composite"	"0"
EndSection

I spent much time trying to install my card withaout any result !
Ready to follow any suggestions.

---

### Post by scrhoads800 on 2008-02-17
This is how I was able to get everything to work (I don't play games on the computer, so I'm not sure how they work):

My setup dell 9400, ati x1400, gutsy (upgrade not a fresh install), fglrx (8.45.5), compiz-fusion, and I'm running aiglx now (disabled xgl  and it's not showing up in the System Monitor's process list).  

If you don't want to install the driver below, that's fine. I'm just writing what worked for me (granted it took about 24 hours, but it's working now)

I installled the ati fglrx driver with this how to : [[COLOR="Blue"]http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide[/COLOR]]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide")

( Installs Catalyst 8.2 – ati changed the way the drivers are listed – whatever, something about windows I think. The driver version that gets installed is 8.45.5)

Followed the upgrade section of the how-to on the first page of  this thread, and changed the lines in /usr/bin/compiz that StampU mentioned on page 4 of this thread ([[COLOR="Blue"]http://ubuntuforums.org/showthread.php?t=580748&page=4[/COLOR]]("http://ubuntuforums.org/showthread.php?t=580748&page=4")) . 

The other things I did were:
[LIST]
[*]Changed WHITELIST var from “nivdia intel ati radeon i810” to “fglrx nvidia intel ati radeo i810” in /usr/bin/compiz file (should be around line 58 or so)
[*]Created empty file 'disable' (no quotes when creating it though) in ~/.config/xserver-xgl/ directory. If the directory isn't there, make it.
[*]Modified my xorg.conf w/ the suggestions in this post: [http://forum.compiz-fusion.org/showthread.php?t=6794](http://forum.compiz-fusion.org/showthread.php?t=6794)
[*]Put 'compiz --replace'   in the startup programs: System->Preferences->Session->Startup Programs (once again, no quotes when you actually put the command in).
[/LIST]

Various bits of info: 

Before I did the extra steps, my fglrxinfo looked correct, but when I ran glxinfo, direct rendering was off and the OpenGL vendor sections still referenced the Mesa driver.  After direct rendering was on and the OpenGL stuff referenced ATI driver.

If you have multiple “Device” sections w/ the fglrx driver in them, check the /var/log/Xorg.0.log file to see which one is actually being used ( make sure the options are being set in that section).

Warning I did have a problem w/ playing video (flickers), read somewhere that disabling compiz fixes this issue. Running 'metacity --replace' ( no quotes ) in the command line is my workaround for now.

After playing around w/ my xorg.conf I saw that turning TexturedVideo off fixes the video problem.  I don't know what TexturedVideo does or was doing, but I think I' pretty happy now.

Good Luck.

---

### Post by Thug14 on 2008-02-20
thnx a lot

---

### Post by UncleBark on 2008-02-20
New to Linux and Ubuntu.  I have an ATI Radeon 9550.  After following these instructions it seems to have worked properly first time.  Thanks for the post.

---

### Post by Chris Morin on 2008-02-22
I followed your steps and I got this:

display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)

my xorg.conf :

# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Identifier	"Default Layout"
  screen 0 "aticonfig-Screen[0]" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"Synaptics Touchpad"
EndSection

Section "Files"
EndSection

Section "Module"
	Load		"glx"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

---

### Post by granjerox on 2008-02-24
Hi folks,

I have an Dell Inspiron 6400 with ati x1400 and a 1680x1050 display. I've always had problems with compiz, fglrx and 3d acceleration. I've just done a fresh install of Ubuntu Hardy Heron alpha 5 and all work like a sharm.

Compiz, graphic resolution, video playback with totem or Videolan ......

I recomend you all to do that. I had only to activate de fglrx driver in restricted hardware manager.

---

### Post by tardpicard on 2008-02-28
> **granjerox said:**
> Hi folks,

I have an Dell Inspiron 6400 with ati x1400 and a 1680x1050 display. I've always had problems with compiz, fglrx and 3d acceleration. I've just done a fresh install of Ubuntu Hardy Heron alpha 5 and all work like a sharm.

Compiz, graphic resolution, video playback with totem or Videolan ......

I recomend you all to do that. I had only to activate de fglrx driver in restricted hardware manager.

What version of fglrx is included in Hardy's restricted manager?

This will be the best news I've heard in a while if the fglrx version in restricted drivers includes amd's aiglx implementation.  I've struggled with this issue for some time now, and just can't seem to strike the perfect combo.

Right now, the only thing that holds be back from using the newest ati drivers is this video problem, as most everything else with them seems sufficient atm.

---

### Post by midboe on 2008-02-28
Thanks, works great on my hp nc6400 with ati x1300.

---

### Post by granjerox on 2008-02-29
> **tardpicard said:**
> What version of fglrx is included in Hardy's restricted manager?

This will be the best news I've heard in a while if the fglrx version in restricted drivers includes amd's aiglx implementation.  I've struggled with this issue for some time now, and just can't seem to strike the perfect combo.

Right now, the only thing that holds be back from using the newest ati drivers is this video problem, as most everything else with them seems sufficient atm.


Ati 8.45.5 says the amdccc Catalyst Panel. I have to say that hardy is not yet free from bugs, some apps crash usually, specially emerald .... but anyway I'm happy with it.

---

### Post by General_Ts0 on 2008-03-03
Ya know, I took a break from ubuntu because of dam ATI frustration, I'm back now in time for Hardy.  This works great so far, seems so easy.  What gives ?

---

### Post by Kivech on 2008-03-05
> **batis610 said:**
> Hi, after folowing all the tutorial, it seems that my card was successefully installed:

But when i tried to enable effects it said:

My xorg.conf is :

I spent much time trying to install my card withaout any result !
Ready to follow any suggestions.

Ok for some reason I cannot multi quote, but here goes.

I have a similar issue. My fglrxinfo output is similar as well as my xorg.conf. Here is the first

> display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1900 Series
OpenGL version string: 2.0.6473 (8.37.6)

> Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :1.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1900 Series
OpenGL version string: 1.2 (2.0.6473 (8.37.6))


Now everything works in my case. I have xserver-xgl installed which makes all desktop effects work. However, direct rendering doesn't work.

I get this output when querying direct rendering:
> Xlib:  extension "XFree86-DRI" missing on display ":1.0".
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)


This I think is related to the message on fglrxinfo -display :1. So my question would be, for a first step, how do I get DRI enabled on display 1.0?

My xorg.conf looks like this:
> # xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"SyncMaster"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1280x1024"	"1280x960"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
Section "Module"
	Load		"glx"
EndSection
Section "Extensions"
	Option		"Composite"	"0"
EndSection

# To prevent Blank Screen from popping up every 10 minutes
# when xgl is run as a session on display :1,
# when all the power management settings
# you normally find only concerns display :0
Section "ServerFlags"
	Option "blank time" "0"
	Option "standby time" "0"
	Option "suspend time" "0"
	Option "off time" "0"
EndSection

So far I followed several advices on this matter, but none had me get my direct rendering to be enabled. I really need this, so some help would be very much appreciated.

Or is it really as simple as hooking up my monitor on the other port of my gfx card?

Kivech

---

### Post by BooBooNTZU on 2008-03-05
HERE IS A RECAP OF EVERYTHING I KNOW SO FAR: 

1. If you want Compiz to work with the restricted ati driver and restricted packages you have to install the xserver-xgl package and direct rendering will not be available when the xgl is active. As soon as you turn off the XGL you get your direct rendering back but you can't run Compiz anymore. 

2. If you want to use the ATI driver from ATI's website , that one works with direct rendering while Compiz is enabled but you have to remove / uninstall all the restricted packages and all the restricted drivers + restricted manager + xserver-xgl package before you install it.

3. The rest depends on how new is your videocard. Newer videocards use the 'aiglx' driver while older videocards use the 'fglrx' driver. Use the following to configure :

sudo dpkg-reconfigure xserver-xorg
sudo aticonfig --initial -f

---

### Post by iheartubuntu on 2008-03-05
Ive followed the instructions, everything went well, but the compiz eye candy just doesnt work. This laptop has a ATI Radeon X1200. I would think it should work as I have read some people have World of Warcraft working on a computer with an ATI X1200 vid card.

Any tips? Thanks!

---

### Post by BooBooNTZU on 2008-03-06
Try running the :

sudo dpkg-reconfigure xserver-xorg 

And from that list of videocards try the 'FGLRX' option instead of 'ati'.

You have to uninstall all the restricted packages if you want the ATI driver to work. I'm talking about the latest ATI driver from their website.

---

### Post by Thug14 on 2008-03-10
thnx a ton mate

---

### Post by muddletupper on 2008-03-14
I've been having a heck of a time trying to get my ATI graphics card to work correctly, perhaps someone else has had a similar issue or can offer some advice?

I'm using an AMD 64-bit CPU system, 1G of RAM
trying to get an ATI Radeon HD 2600 XT graphics card with 512M RAM to run

I have a fresh install of Ubuntu 7.10.  In fact I've done fresh reinstalls multiple times which has really slowed things down.  I've gone through multiple guides for ATI install and others people have posted and most ask to make sure all other drivers are removed and since I'm not sure how to ensure I have a clean build without extraneous drivers my response has to be a fresh rebuild every attempt.  The only thing I do after that is allow the system to download the most recent security updates as well.

The problems I've run in to...

[LIST]
[*]The steps on this walkthrough run without error giving the expected responses right up through the reboot.  It even tells me that xgl will automatically load after the next reboot without me having to make changes.  Once I log back in though things are running just as before.  I'm not sure exactly how you "enable 3D effects" but I assume the Appearance Preferences options for None, Normal, Extra, and Custom switched to Extra should be an indicator that 3D effects are now working or at least that I've properly enabled my graphics card.  When I attempt to switch it from None to Normal or Extra I still always get a pop up error telling me that desktop effects could not be enabled and it goes right back to None.

[*]I have no restricted drivers listed under System > Administration > Restricted Drivers Manager.  It tells me my hardware does not need any restricted drivers.  I do wonder if there had been updates to the drivers making them no longer restricted.

[*]I did run through some commands (I forget which exactly) to check if the system is seeing my ATI graphics card, and it does see it.  It's listed in the devices and everything from command line.

[*]I even tried the install of the ATI drivers themselves where you download them from ATI and jump through some hoops via command line to install it.  Those run flawlessly, right until I get to a step where I have to run "sudo aticonfig --initial" at which point I'm told that there isn't a file for that.  There's an alternative method that says to update /etc/X11/xorg.conf but that file doesn't exist either.  It's odd that every other command runs flawlessly with expected results but two files that you'd expect to be there just plain aren't.  Again I have to wonder if this is due to changes in either the restricted files or the latest ATI drivers you download.
[/LIST]

Anyone have any similar issues that they managed to resolve?
Any thoughts on something I've obviously overlooked somewhere?

Any help would be appreciated.  I have some experience with Linux (used to run RedHat long before Fedora, did a little work with Fedora and more recently Kubuntu.  Command line work doesn't worry me at all, I'm just fairly rusty at recalling some of the commands and some things are new enough for me that I'm still learning them.  (Synaptic package manager, aptitude, and apt-get are wonderful things)

---

### Post by quddusaliquddus on 2008-03-28
OK. I've followed the instructions for "If you are doing fresh install of Gutsy" but i didnt enable fgrlx driver. Is that the reason why the application names are now giant as well as the minimise maximise and close buttons are giant for every application i open. How do i fix that? Also - how do i enable fgrlx driver?

Any help is much apprecited - its become impossible for me to use ubuntu now.

Thanks

Regards

Q

---

### Post by martin saint martin on 2008-04-07
thanks, worked like a charm.  i thought the lack of a vid card (on board ATI Readeon)was holding me back, stumbled onto this thread and thought why not try it out?  i'm glad i gave it a shot.

---

### Post by Treeckcold57 on 2008-04-14
```
treeck57@Treeck57-linux:~$ sudo apt-get update
[sudo] password for treeck57:
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Reading package lists... Done
treeck57@Treeck57-linux:~$ sudo apt-get install linux-restricted-modules-generic restricted-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-restricted-modules-generic is already the newest version.
restricted-manager is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
treeck57@Treeck57-linux:~$ sudo apt-get install xserver-xgl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package xserver-xgl
treeck57@Treeck57-linux:~$ sudo apt-get install xserver-xgl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package xserver-xgl
treeck57@Treeck57-linux:~$ 

```

How do suppose I fix it? :(

---

### Post by zad_sida on 2008-05-29
hey i try this for my ati 9200 se vga its works but slow when moving the window or else resizing can any one help me for this

---

### Post by michael37 on 2008-11-30
An update -- I no longer run Xgl since ATI supports AIGLX in the 8.04 and 8.10 versions, but the principles still apply for those who want to use Xgl.

---

### Post by fickusowsky on 2009-01-26
hi
I try to install like you sed but i have problem in firs step. howe i can fix it? the error message is:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
sale@sale-laptop:~$ y
bash: y: command not found
sale@sale-laptop:~$ 

howe I can oppen it!?

sorry about my english & if my question is stupid.

thanx

---

### Post by fickusowsky on 2009-01-26
ok, nobody wants to halp me..:(
and I try to do somethig alone and have new sitution! here it is:

sale@sale-laptop:~$ sudo apt-get update
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Translation-en_US                     
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [189B]             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US     
Get:3 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg [189B]                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release                          
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_US               
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy Release                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages                        
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Sources                         
Get:4 [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release.gpg [197B]                   
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Translation-en_US                 
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Translation-en_US             
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release                                
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release                                
  
Get:5 [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release [11.7kB]                     
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release                                
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Packages                          
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Packages                      
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Sources                           
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Sources                   
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_US             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Translation-en_US               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Translation-en_US               
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release.gpg [189B]               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Translation-en_US     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Translation-en_US             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources
99% [Waiting for headers]                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Translation-en_US
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed Release.gpg [189B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/restricted Translation-en_US
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports Release.gpg [189B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/universe Translation-en_US       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/multiverse Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/restricted Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed Release                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports Release                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Sources     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-backports/restricted Sources
Fetched 11.9kB in 8m25s (24B/s)
Reading package lists... Done
[B]W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems[/B]
sale@sale-laptop:~$ 
sale@sale-laptop:~$ 

what I gonna do now!?

---

### Post by fickusowsky on 2009-01-26
how i can delete message!?

---

