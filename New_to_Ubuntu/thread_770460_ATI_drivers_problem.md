---
title: "ATI drivers problem"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by gerben1 on 2008-04-27
I just don't seem able to get the ATI proprietary drivers installed. I have tried this tutorial: [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

I followed it closely, and have tried multiple times, but it just won't work I keep getting this:

gerben@CC1184274-A:~$ fglrxinfo
display: :0.0 screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.3-rc2)

I also tried using envyNG but it gave me exactly the same result,
even though it did recognize my card and said it was supported by the driver, it is a ATI Mobility Radeon X700 card.

Anyways I had this working perfectly fine in Gutsy, so it must be possible to get it working again. Does anybody have some suggestions for things to check?

---

### Post by gerben1 on 2008-04-27
Oh common, does nobody know anything about this?

This looks like a very basic issue to me, somebody must be able to point me in the right direction?? I can go on googling for more different howto's/tutorials, but they all do bassically the same thing, sometimes the order is a bit different or they use a different text editor to edit xorg.conf but that can't make much of a difference I assume. 

There is no way I can solve this myself, as the normal way of doing this does not work in my case. I really need someone with knowledge of the operating system to help me a bit in order get any further.

---

### Post by gerben1 on 2008-04-27
anybody?

---

### Post by TechDragon on 2008-04-27
remove anything with "fglrx" in the title using synaptic.

Then try running envy from a terminal

sudo envyng -t

I had to do this, worked for me.

YRMV

---

### Post by Ub1476 on 2008-04-27
Make sure you remove every install driver (even though it does not work it did install), before using Envy, else that will probably fail too. There's an option to remove drivers in Envy, but I recommend you to double check they're gone.

---

### Post by aigelonic on 2008-04-27
When you say remove/uninstall everything with fglrx in it, do you also mean
linux-restricted-modules-2.6.24-16-generic ?
There is a module with fglrx in this package...

(Dunno if this was a stupid question or not :P, pretty new to this)

---

### Post by gerben1 on 2008-04-27
Alright let me try that,so only things with fglrx in the title right? not all things that synaptic finds when searching for fglrx. For example i should "mark for complete removal" xorg-driverfglrx-dev but not xserver-xorg-video-ati even though that one is also found when searching for fglrx in synaptic?

(I don't know how synaptic works but if i search for fglrx it finds 18 packages of which only 8 have fglrx in the package name.... very very weird and confusing search results... I assume it is clear to the initiated..., don't even try searching for ATI you'll get 1000's of packages, in my case 15782...)

---

### Post by forrestcupp on 2008-04-27
Just use EnvyNG to remove the drivers, then reinstall them with EnvyNG.  Yes, it may remove linux-restricted-modules, but it will reinstall it for you.  Then after you have installed the drivers through EnvyNG, you may have to go to System->Administration->Hardware Drivers (Restricted Drivers Manager in Gutsy) and enable the restricted drivers.

---

### Post by gerben1 on 2008-04-27
@TechDragon:
This did not work for me, unfortunately.

@Ub1476:
How can I check if they are really gone, mind you I do not know where the drivers are or what exactly the driver is and what the kernel module etc.

All I have been doing is following tutorials and they ussually go like:
- uninstall a bunch
- install restricted manager
- install some x-org packages (probably this the kernel module?)
- download ATI driver
- make .deb packages for driver
- install packkages just made

It is all easy enough, but it just does not work. So any ideas of things I could check that are supposed to be such or so in a healthy system would be very welcome. I think this would be much easier if I had at least a bit of an idea what I was doing instead of just installing and uninstalling different packages again and again....

---

### Post by gerben1 on 2008-04-27
@forrestcupp:
I just tried the method you propose, but with the same results....
It looks like nothing is changed at all, still:

gerben@CC1184274-A:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.3-rc2)

---

### Post by aigelonic on 2008-04-27
Thx!
I have a Asus A6V Laptop with an ATI X700 video card. I've been having trouble for some time now getting the 3d acceleration to work. And EnvyNG was the solution :)
Here is what I did:
Went to synaptic and searched for envy. 
Installed the envyng-gtk package.
Closed synaptic and started a terminal. Wrote "sudo envyng -t", as stated above.
EnvyNG started and I first chose the option to uninstall ATI-drivers. After this was done I chose the option to install ATI-drivers. After a few minutes of downloading and installing I had to reboot. And now everything works :) I checked that the drivers were in use under Hardware Drivers. 

(I did get a warning after the first reboot, Ubuntu complained about that the drivers were not supported, but I guess this is as should be :P )

Cheers

---

### Post by gerben1 on 2008-04-27
Well congratulations!

Although I have the same video card this does not work with my setup, for some unfanthomable reason. I do not even have a videocard driver in sytem->administration->hardware drivers.
There's only:
- Broadcom B43 wireless driver
- Software modem


and my card is recognized:

gerben@CC1184274-A:~$ lspci | grep X700
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X700 (PCIE)

---

### Post by forrestcupp on 2008-04-27
Well, if you're sure you properly reinstalled the drivers with EnvyNG after uninstalling them, go ahead and post the results of
```
cat /etc/X11/xorg.conf
```

Also, just to make sure, you did reboot, right?

---

### Post by TechDragon on 2008-04-27
I followed the instructions found here to remove everything

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

then installed envy through the terminal

sudo envyng -t

I hate to say this but as easy as it is to install ubuntu, you may need to re-install it, do all the updates first, then enable the required repositories, and I always include medibuntu's repo as well.  Then install envy.


I am pretty new to Linux but have fought this @!##@IU!Y ATI card from day ONE.

---

### Post by gerben1 on 2008-04-28
@TechDragon: Well, that will be my very very last resort. It has been pretty difficult to get internet working on this laptop, I do not really want to go through that again.

@forrestcupp:
Yes, i rebooted. First I uninstalled the ATI driver using EnvyNG, then I rebooted, then I installed the ATI driver using EnvyNG, and then I rebooted again and still found fglrxinfo reporting Mesa. 

I read things about XGL in some other thread somebody was suggesting that:
"you are both using the mesa GLX environment, instead of the fglrx GLX environment." 
Could that have anything to do with my problem too perhaps?

```

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

Section "Screen"
	Identifier	"aticonfig-Screen[0]"
	Device		"aticonfig-Device[0]"
	Monitor		"aticonfig-Monitor[0]"
	SubSection "Display"
		Viewport	0	0
		Depth	24
	EndSubSection
	Defaultdepth	24
EndSection

Section "Device"
	Identifier	"aticonfig-Device[0]"
	Driver		"fglrx"
	#	Driver		"ati"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"acer_ferrari4k"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	#	Driver		"mouse"
	#	Option		"Protocol"	"ImPS/2"
	#	Option		"ZAxisMapping"	"4 5"
	Identifier	"Configured Mouse <-- before Hardy Heron"
	Driver		"evdev"
	Option		"Name"	"Logitech USB Gaming Mouse"
	Option		"CorePointer"
	Option		"ZAxisMapping"	"4 5 6 7 8"
	Option		"Emulate3Buttons"	"true"
	#	Option		"Device"	"/dev/input/mice"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
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

Section "InputDevice"
	Identifier	"stylus"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier	"eraser"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Identifier	"cursor"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

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
	Option		"AIGLX"	"on"
EndSection

Section "Module"
	Load		"glx"
	Load		"dri"
EndSection

Section "Monitor"
	Identifier	"aticonfig-Monitor[0]"
	Option		"VendorName"	"ATI Proprietary Driver"
	Option		"ModelName"	"Generic Autodetecting Monitor"
	Option		"DPMS"	"true"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
	Option		"DAMAGE"	"Enable"
	Option		"RENDER"	"Enable"
	Option		"XVideo"	"Enable"
	Option		"Composite"	"Enable"
EndSection

```

---

### Post by forrestcupp on 2008-04-28
Well, you are using the fglrx driver.  Open a terminal and enter
```
glxinfo | grep direct
```
If it says yes, then you're ok.  But if you have Xgl installed, that is definitely your problem.  It's now possible with the latest drivers to run Compiz without Xgl, so you need to just uninstall it.  Xgl basically redraws everything about your desktop experience on an opengl screen so that you can use effects, where they aren't normally able to be used.  So it pretty much ties up your opengl which means that opengl apps don't work well with it.  To uninstall Xgl,
```
sudo apt-get remove xserver-xgl
```
Then reboot.  If your visual effects don't work, you may need to do some tweaking to get them to work.

Basically, ATI cards have always been a pain in the rear in Linux.  But gradually, they appear to be getting better.

---

### Post by gerben1 on 2008-04-28
Thanks for the info.

I just got it working. Unfortunately I do not know exactly why it is working again. Next Ubuntu upgrade I will log everything I do in order to get the hardware working, so that I can backtrack where (and possibly understand why) something went wrong.

All I know now about how I got it working is this: I was trying this method that seems to work for quite some people (but not for me initially):
[http://ubuntu-utah.ubuntuforums.org/showpost.php?p=4806574&postcount=4](http://ubuntu-utah.ubuntuforums.org/showpost.php?p=4806574&postcount=4)
and that in combination with aticonfig -f --initial seems to have done the trick of giving me back "ATI accelerated graphics driver" in "System->Administration->Hardware drivers". When I just checked this everything seems to be working fine. 

In order to get compiz working i had to do this:
[http://www.realistanew.com/2008/04/23/fglrx-breaking-upgrades-to-804/](http://www.realistanew.com/2008/04/23/fglrx-breaking-upgrades-to-804/)
but then it worked fine.

My feeling is that I got myself into trouble when trying to use Envy to get the ATI drivers working. Just after the upgrade I had the driver running in "System->Administration->Hardware drivers", but with strange effects, for example if I would move the cursor over text in a console the text would become garbled beyond recognition and scrolling was extremely slow. So I thought, ah well this must be because of that included video driver, I just need to use the one from ATI's website like I did in Gutsy. Then I noticed that Envy did not support Hardy, and downloaded EnvyNG which produced an error when I ran it. I asked in the EnvyNG forums and the maintainer of the package told me to download another (newer i guess) EnvyNG.deb package. I did that and installed it. After that I had lost the "ATI accelerated graphics driver" in "System->Administration->Hardware drivers", but I did not really care much as I did not want to use them anyways but wanted to use the drivers from the ATI site. Well, I never really succeeded at that, but now the packaged driver seems to be working fine.

Since I had the "ATI accelerated graphics driver" in "System->Administration->Hardware drivers" back, I thought let's try them again and see how bad it was, perhaps I can adjust their workings via xorg.conf. However, the xorg.conf  I have right now is the one generated by "aticonfig -f --initial" and is very different from the one I had initially after the upgrade to Hardy. Since everything seems to be working fine now I guess the original bad performance after the upgrade was not due to the packaged driver but due to settings in xorg.conf.

---

### Post by forrestcupp on 2008-04-28
Well, with the old Envy that was for Gutsy, the web site says that kernel upgrades will break your drivers.  So they said you need to uninstall your Envy installed drivers before upgrading to a new version, i.e. Hardy.  Then you were supposed to reinstall your drivers with the new EnvyNG for Hardy.  I guess you missed that step and it messed your system up.

The good thing is that EnvyNG now creates driver packages that are 100% compatible with Ubuntu, so kernel upgrades will no longer break your system.

---

### Post by gerben1 on 2008-04-29
> **forrestcupp said:**
> Well, with the old Envy that was for Gutsy, the web site says that kernel upgrades will break your drivers.  So they said you need to uninstall your Envy installed drivers before upgrading to a new version, i.e. Hardy.  Then you were supposed to reinstall your drivers with the new EnvyNG for Hardy.  I guess you missed that step and it messed your system up.

The good thing is that EnvyNG now creates driver packages that are 100% compatible with Ubuntu, so kernel upgrades will no longer break your system.

Yes that is correct, I did not uninstall the video drivers before doing the upgrade. Right now I don't even know if my install would count as an envyNg install or not, as I have ran envyNG many times, tried the manual install plenty of times, and ended up by just placing a check in the box after "ATI accelerated graphics driver" in "System->Administration->Hardware drivers", which made everything work properly. So it's good to know that it does not matter anymore for new upgrades.

---

