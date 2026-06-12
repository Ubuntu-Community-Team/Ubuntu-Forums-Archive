---
title: "How do you get a Geforce Video Card to work right??"
date: 2008-09-05
forum: New to Ubuntu
---

### Post by mastergunner on 2008-09-05
Guys I just did a fresh reinstall of the latest Kubuntu. How do you get the Geforce video cards to use the right nvidia drivers. I tried Envy as well as clicked the box that comes up when you do an install so it can use those drivers. Everytime it screws up and I only get a crappy resolution of 600x320 or so. If there is a guide that takes me through the process that would be great.

---

### Post by Lutin on 2008-09-05
Sorry to hear that you are having problems. Have a look here -

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

or maybe here -

[https://help.ubuntu.com/community/NvidiaManual](https://help.ubuntu.com/community/NvidiaManual)

Hope these help.

---

### Post by philinux on 2008-09-05
Not sure where it is in Kubuntu.

On gnome it's system>admin>hardware drivers.

All you have to do is tick the box.

Which gforce is it. Mine worked out the box after ticking the driver.

[edit] I do now. [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#Kubuntu%208.04%20Hardy%20Heron](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#Kubuntu%208.04%20Hardy%20Heron)

---

### Post by mastergunner on 2008-09-05
I didnt know I had to do the following after ticking the box:

Activating the driver

Once the driver is installed you need to set the system to use the driver. Open Konsole from K-Menu->System->Konsole and enter the command

sudo nvidia-xconfig

That will set the driver to be used from now on. To start using the driver you will need to logout and select Restart X Server from the menu, or press Alt+E


What happens if it doesnt work? How do I go back to the way it was before I ticked the box?

---

### Post by jolx on 2008-09-05
> **mastergunner said:**
> I didnt know I had to do the following after ticking the box:

Activating the driver

Once the driver is installed you need to set the system to use the driver. Open Konsole from K-Menu->System->Konsole and enter the command

sudo nvidia-xconfig

That will set the driver to be used from now on. To start using the driver you will need to logout and select Restart X Server from the menu, or press Alt+E


What happens if it doesnt work? How do I go back to the way it was before I ticked the box?

those instructions are for older versions of kubuntu

---

### Post by Darkade on 2008-09-05
Just download the driver from the official site here

[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

Go to a shell Alt+Ctrl+F1

and kill your X11, in gnome youdo
```
killall gdm
```
in kde i think it is
```
killall kdm
```

Now just install the file you've download it will patch your kernel and overwrite your xorg.conf ; any previous xorg.conf will be saved

Works like a charm

Check this thread [http://ubuntuforums.org/showthread.php?t=819043](http://ubuntuforums.org/showthread.php?t=819043)
Look at post #2 in that thread

**EDIT:** BTW you will need to repeat this process every time you upgrade your kernel. If you use the drivers provided by (K)Ubuntu you won't need to do this but those drivers are kind of... well not so good :lolflag:

---

### Post by mastergunner on 2008-09-05
Are you running Kubuntu? Doesnt Envy do this? I am new to Linux so it would help if someone could help me step by step.

Jolx if those comds are for older versions (pre-Hardy) what do I do then?


Philinux I have a Geforce 8500GT. Any issues with that card. I mean I can install the the nvidia drivers it just gives a low resolution with no way to go higher.

---

### Post by alienexplorers on 2008-09-05
Have you tried using nvidia-settings:
> gksudo nvidia-settings

---

### Post by jolx on 2008-09-05
> **mastergunner said:**
> Jolx if those comds are for older versions (pre-Hardy) what do I do then?

only the stuff under the heading "Kubuntu 8.04 Hardy Heron" are relavent to hardy. if u look you'll see that all the stuff other than checking the box is intended for older editions of Kubuntu (ie. "Kubuntu 7.10 Gutsy Gibbon" & "Kubuntu 7.04 Feisty Fawn")

---

### Post by mastergunner on 2008-09-05
Jolx what do you mean? Are you saying the only thing I have to do is click the box? If so that doesnt work for me cause it gives me only one resolution with is LOW.

---

### Post by mastergunner on 2008-09-05
> **alienexplorers said:**
> Have you tried using nvidia-settings:


When is this to be tried and how?

---

### Post by jolx on 2008-09-05
> **mastergunner said:**
> Jolx what do you mean? Are you saying the only thing I have to do is click the box? If so that doesnt work for me cause it gives me only one resolution with is LOW.

im saying that if ticking the box is'nt working then the problem is not going to be solved by doing any other stuff that is on that site. i think the problem might be the particular nvidia driver which you are using, you should go to their site and download the latest one and install it. there are heaps of guides on exactly how to install it.

---

### Post by anjilslaire on 2008-09-05
The specific location in Kubuntu Hardy is
System > Hardware Drivers Manager.

---

### Post by mastergunner on 2008-09-05
Jolx could you point me to those guides cause I havent seen any. According to the information given for those drivers that get downloaded when clicking the box they are the latest nvidia drivers.

---

### Post by jolx on 2008-09-05
> **Darkade said:**
> Go to a shell Alt+Ctrl+F1

and kill your X11, in gnome youdo

before killing X you must login as root

---

### Post by mastergunner on 2008-09-05
> **anjilslaire said:**
> The specific location in Kubuntu Hardy is
System > Hardware Drivers Manager.

I have tried that and I get only one resolution which is non adjustable and low.

---

### Post by mastergunner on 2008-09-05
> **jolx said:**
> before killing X you must login as root

How do you do that?

---

### Post by anjilslaire on 2008-09-05
you may need the nvidia-glx-new drivers from the repo's. I think I've heard somewhere that the 8500 has issues with the standard nvidia-glx driver...

---

### Post by anjilslaire on 2008-09-05
> **mastergunner said:**
> How do you do that?

reboot and select Recovery Mode is one way. You'll be on as Root, with a cli environment (no GUI, hence no X)

---

### Post by jolx on 2008-09-05
the link that darkade posted in [this]("http://ubuntuforums.org/showpost.php?p=5731955&postcount=6") post is pretty good

---

### Post by mastergunner on 2008-09-05
> **anjilslaire said:**
> you may need the nvidia-glx-new drivers from the repo's. I think I've heard somewhere that the 8500 has issues with the standard nvidia-glx driver...


That is where I downloaded the drivers the first time. There just needs to be a decent guide on how to install a geforce card into Hardy. Being a noob at linux is so painful.

---

### Post by anjilslaire on 2008-09-05
Weird that this is being so rough. I have an nvidia 6600 GT that behaves perfectly under Kubuntu Hardy.

Bummer :(

---

### Post by mastergunner on 2008-09-05
> **anjilslaire said:**
> Weird that this is being so rough. I have an nvidia 6600 GT that behaves perfectly under Kubuntu Hardy.

Bummer :(

Older card, better supported.

---

### Post by anjilslaire on 2008-09-05
I see you've found ElephantMan's thread

```

sudo dpkg-reconfigure xserver-xorg

```

will let you specify the driver, resolution, and monitor refresh rates, among other settings. Try it. Just follow along with the prompts.

---

### Post by mastergunner on 2008-09-05
> **anjilslaire said:**
> I see you've found ElephantMan's thread

```

sudo dpkg-reconfigure xserver-xorg

```

will let you specify the driver, resolution, and monitor refresh rates, among other settings. Try it. Just follow along with the prompts.

So should I have the drivers downloaded or will it download for me?

---

### Post by philinux on 2008-09-05
> **anjilslaire said:**
> I see you've found ElephantMan's thread

```

sudo dpkg-reconfigure xserver-xorg

```will let you specify the driver, resolution, and monitor refresh rates, among other settings. Try it. Just follow along with the prompts.

Not in 8.04. Only keyboard and mouse. Xorg.conf does not contain detailed video stuff anymore.
Here's mine.
```
# xorg.conf (X.Org X Window System server configuration file)
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

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "gb"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Driver        "nvidia"
    Option        "NoLogo"    "True"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    Defaultdepth    24
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
  screen "Default Screen"
EndSection
Section "Module"
    Load        "glx"
EndSection
```

---

### Post by anjilslaire on 2008-09-05
download them 1st, then run the above command from the konsole

---

### Post by knix on 2008-09-05
I recommend using the nvidia-glx-new-envy in the updates. the 169 series had some problems.After that, you can do wahtever to configure your xorg.conf (nvidia-xconfig works, or manually modify it so that it uses the nvidia driver)

---

### Post by anjilslaire on 2008-09-05
> **philinux said:**
> Not in 8.04. Only keyboard and mouse. Xorg.conf does not contain video stuff anymore.

That's funny:
```

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
	Option		"Protocol"	"ExplorerPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"ButtonMapping" "1 2 3 4 5"
	Option 		"Buttons" 	"5" 
	Option		"Emulate3Buttons"	"false"
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
	Identifier	"Nvidia GeForce 6600GT"
	Driver		"nvidia"
	Busid		"PCI:2:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"false"
EndSection

Section "Monitor"
	Identifier	"SCEPTRE P73V"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Nvidia GeForce 6600GT"
	Monitor		"SCEPTRE P73V"
	Defaultdepth	24
	SubSection "Display"
		Virtual 1024	768
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

```

---

### Post by mastergunner on 2008-09-05
WOW there isnt just one way to do this? You know this noob is totally confused and not wishing to screw up the freshly installed Kubuntu.

---

### Post by philinux on 2008-09-05
**anjilslaire**


That cannot be a clean install it must be an upgrade.

---

### Post by anjilslaire on 2008-09-05
I do clean installs every release. I do tweak some things here and there, but not monitor settings, just the mouse, video drivers, etc.

---

### Post by philinux on 2008-09-05
> **anjilslaire said:**
> I do clean installs every release. I do tweak some things here and there, but not monitor settings, just the mouse, video drivers, etc.

So how do we get this guys graphics driver going?

He should have had a green icon thing on the notification area which would have installed the proprietary driver. Mine's a 8600 i cant see why the 8500 should be that much different.

My choice would be to install nvidia-glx-new-envy from synaptic or terminal

sudo apt-get install nvidia-glx-new-envy

It's the newer driver for the  8 series.

---

### Post by mastergunner on 2008-09-05
> **philinux said:**
> So how do we get this guys graphics driver going?

He should have had a green icon thing on the notification area which would have installed the proprietary driver. Mine's a 8600 i cant see why the 8500 should be that much different.

My choice would be to install nvidia-glx-new-envy from synaptic or terminal

sudo apt-get install nvidia-glx-new-envy

It's the newer driver for the  8 series.

Yes there is as green icon thing in the notification area. How when I check the block and restart X I only have one resolution which is 640x320. So what is the problem and how should it be fixed?

---

### Post by philinux on 2008-09-05
KMenu->System->Hardware Drivers Manager

Does this show the driver enabled.

---

### Post by anjilslaire on 2008-09-05
Even though its nonstandard, he may need to force the resolution by manually specifying a resolution, by reconfiguring xorg.

I agree it shouldn't ***need*** to be done, but if it fixes him up...

---

### Post by mastergunner on 2008-09-05
The driver is not enable because it will only give me a resolution of 640x320 when X is restarted.

---

### Post by philinux on 2008-09-05
> **anjilslaire said:**
> Even though its nonstandard, he may need to force the resolution by manually specifying a resolution, by reconfiguring xorg.

I agree it shouldn't ***need*** to be done, but if it fixes him up...

I agree too. But as we move to intrepid and intrepid+1 xorg.conf will vanish completely. Better to get things sorted without editing xorg if we can.

---

### Post by philinux on 2008-09-05
> **mastergunner said:**
> The driver is not enable because it will only give me a resolution of 640x320 when X is restarted.

First thing.

Reboot and at the grub menu press esc and choose the recovery option using the up down keys. Then press enter. a load of text will fly by. ignore this. you will then see a menu.

Choose xfix then after thats finished choose continue to boot.

---

### Post by knix on 2008-09-05
and if it doesn't- go into recovery mode, type startx, and see what kind of output you get (anybody remember where the log goes)
This seems dumb, but you might make sure that you have linux-restricted-modules installed. Also, try using the most recent kernel, because the stock one's linux-restricted-modules only came with the kernel for the 169 series

---

### Post by mastergunner on 2008-09-05
> **philinux said:**
> First thing.

Reboot and at the grub menu press esc and choose the recovery option using the up down keys. Then press enter. a load of text will fly by. ignore this. you will then see a menu.

Choose xfix then after thats finished choose continue to boot.

I reloaded a fresh Hardy so as not to have any problems so I do not need to do this.

---

### Post by mastergunner on 2008-09-05
> **knix said:**
> and if it doesn't- go into recovery mode, type startx, and see what kind of output you get (anybody remember where the log goes)
This seems dumb, but you might make sure that you have linux-restricted-modules installed. Also, try using the most recent kernel, because the stock one's linux-restricted-modules only came with the kernel for the 169 series

As of now there are no nvidia drivers what so ever downloaded until I feel comfortable on the exact way this is suppose to work. I do know enabling the hardware manager causes issues.

---

### Post by knix on 2008-09-05
> **mastergunner said:**
> As of now there are no nvidia drivers what so ever downloaded until I feel comfortable on the exact way this is suppose to work. I do know enabling the hardware manager causes issues.

Agreed. Step by step:

A)use synaptic to
 1) completely remove all nvidia drivers.
 2)install latest kernel and linux-restricted-modules for this kernel
B)set xorg.conf driver line to nv
C)Reboot
D)install nvidia-glx-new-envy in synaptic
E)change driver to nvidia
F)Ctrl+Alt+Backspace to restart x

you should be fine with the default xorg.conf with different driver line. if not, I've been successful with nvidia-xconfig.

---

### Post by mastergunner on 2008-09-05
> **knix said:**
> Agreed. Step by step:

A)use synaptic to
 1) completely remove all nvidia drivers.
 2)install latest kernel and linux-restricted-modules for this kernel
B)set xorg.conf driver line to nv  [COLOR="Red"]How do you do this[/COLOR]
C)Reboot
D)install nvidia-glx-new-envy in synaptic
E)change driver to nvidia  [COLOR="Red"]How do you do this[/COLOR]
F)Ctrl+Alt+Backspace to restart x

you should be fine with the default xorg.conf with different driver line. if not, I've been successful with nvidia-xconfig.

See my posts in red above

---

### Post by knix on 2008-09-05
sudo gedit /etc/X11/xorg.conf

scroll down to section "Device"

Find line "Driver"

the driver value should be in quotes. it will either be vesa or nv, most likely.

change it to nvidia (or nv, the first time)

---

### Post by mastergunner on 2008-09-05
> **knix said:**
> sudo gedit /etc/X11/xorg.conf

scroll down to section "Device"

Find line "Driver"

the driver value should be in quotes. it will either be vesa or nv, most likely.

change it to nvidia (or nv, the first time)

I have done this before and had problems with the low resolution. Basically you are telling me to load envy and have it load the nvidia drivers.

---

### Post by anjilslaire on 2008-09-05
No, "nv" is the open source nvidia driver that has no hardware acceleration. It is not Envy.

Once you can get the standard "nv" driver working at a good resolution, then we can narrow down the accelerated driver...

---

### Post by mastergunner on 2008-09-05
nv is already there.

---

### Post by knix on 2008-09-05
nv because you need something to run while you don't have the restricted driver installed.

I don't use envy becuse it can mess up the xorg.conf.

Reaaly, what's worked best for me is sudo nvidia-xconfig AFTER installing the driver

nvidia-glx-new-envy is just a more up to date package

---

### Post by knix on 2008-09-05
> **mastergunner said:**
> nv is already there.

then skip to D (install nvidia-glx-new-envy)

I like to enable the logo to tell me if the driver is loading

in section "Screen"
  add line: Option    "NoLogo        "False"

---

### Post by knix on 2008-09-05
OK, I gotta go to class. I'll be back in an hour.

If you still have low resolution after setting the dirver to nvidia and rebooting, then add this lin to section "Screen" SubSection "Display": Modes     "1280x800" "1024x768@60" "800x600@60" "800x600@56" "640x480@60"

replace 1280x800 with your native resolution.

---

### Post by knix on 2008-09-05
just realized, you can't use gedit. I don't know what the command for kde's text editor is (I never could figure it out). however, you ca use nano. it's a relatively easy to use command line text editor

---

### Post by anjilslaire on 2008-09-05
kate, although my preference is leafpad

---

### Post by mastergunner on 2008-09-08
Knix I have the Nvidia drivers loaded but know my monitor says out of range. What do I do now? I cant even get into X cause of this.

---

### Post by knix on 2008-09-08
OK. You need to find the native resolution for your monitor, and add it here:Section "Screen" SubSection "Display": Modes "native res." "1024x768" "800x600" "800x600" "640x480" (in /etc/X11/xorg.conf)

If your monitor only supports 1024x768, or less, change appropriately.
replace "native res." with your monitors resolution.

Edit: the out of range is because your graphics card output is at a greater resolution than your monitor supports (or maybe wrong frequency). your monitor documentation may tell frequency. if it does, use something like "1024x768@75" where 75 is your frequency. depending on monitor type, it will probably be 75 or 60 (be careful here!).
you can change the driver line to nv to fix your settings (after you boot into x, type xfailsafedialog in the terminal)
You can boot into recovery mode and edit your xorg.conf with nano, then test it with startx. (ctrl+alt+backspace to restart x if you have problems)

---

### Post by mastergunner on 2008-09-08
Could you explain how to do this? Thanks.

---

### Post by fauzie on 2008-09-08
Sorry, I didn't read the whole thread, so I don't know your card. But for my card, GeForce FX5200, the latest driver won't work no matter what you do. So my solution is to install an older version of the nvidia driver with Envy (you have to install envy first). It works here.

---

### Post by knix on 2008-09-08
my recommendation:

boot into recovery mode (in Grub)
  You will boot to a command prompt
type "cd /etc/X11" and press enter
type "nano xorg.conf"
Find this Section:

```
Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

```


Note: if you have a manual for your monitor or it states resolution and refresh rate (frequency) then you can skip to the part where you add "Modes".

replace driver nvidia with driver nv. This is Temporary. use Ctrl+o to save and ctrl+x to exit
reboot into normal mode. open a terminal window and type "xfailsafedialog" and press enter. this will give you the window that ubuntu uses to warn you about low graphics mode. use it to pick monitor model, resolution. click "Test." click "keep settings." write down the  resolution and frequency somewhere. click "OK." Reboot into recovery mode. use "nano /etc/X11/xorg.conf" and check for a section like this:

```
Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1024x768@60" "800x600@60" "800x600@56" "640x480@60"
    EndSubSection
EndSection
```

the "Modes" line may not be there. you will have to add it if it isn't. Note: this is just a sample. use resolution and frequency info that you got to replace mine.

replace nv with nvidia.
 reboot into normal mode.

---

### Post by mastergunner on 2008-09-08
Thanks I will try that when I get home from work.

---

### Post by mastergunner on 2008-09-09
Knix I tried what you suggested and it didnt work. My monitor can handle 1400x1050@60. I put just that in and it said out of range. I then put in 800x600@60 and X didnt start. What gives?

---

### Post by knix on 2008-09-09
try booting into recovery mode, then typing "startx" and posting the output.
Or the contents of your Xorg.0.log.
What model is your monitor?

---

### Post by eragon100 on 2008-09-09
open a terminal and type: sudo displayconfig-gtk

Click on the place where it mentions the monitor make and model. Select your monitor make on model. Then select your monitor's max resolution and refresh rate, close the windows with ok, log out and log in. Problem should be solved.

This is offcourse only doable after you get a graphical interface running again, but then, it should work :wink:

---

### Post by mastergunner on 2008-09-09
Knix I have a 20.1" Westinghouse LCD Monitor.

Eragon I have Kubuntu running after running xfix which means I am on a nv driver. I do not understand what that is supposed to do. The problem is I cannot get a GUI running with the nvidia driver.

Was wondering for detection purposes would using a DVI cable be better than a standard vga cable?

---

### Post by knix on 2008-09-09
Basically, displayconf-gtk is a more direct rout than xfailsafedialog. I just didn't now about the command. can you see what it does when you try to set driver to nvidia?
But really, if you can run startx from recovery mode with nvidia enabled, it will give you an error message that we can interpret. I suspect that it has a problem with the nvidia kernel. You *may* have to install the driver form nvidia's script, but we don;t want to try that if we don't have to.

---

### Post by mastergunner on 2008-09-09
OK I finally got it to work and the only thing I did was hook up a DVI cable from card to monitor. Apparently the cable is needed so it can see the monitor and adjust from there. This is the only thing I did. I hooked it up turned on the computer went into Kubuntu and during boot up I saw the NVIDIA splash screen. After logging on I went to NVIDIA Settings and it was seeing everything. WOW I wished this was written somewhere that this cable is a must (at least for me).

---

### Post by anjilslaire on 2008-09-09
Cool. Now, the test:

Put the regular VGA back on & see if it works. If not, go back to DVI. I'd like to know the results.

---

### Post by mastergunner on 2008-09-09
Shoot no. I might screw something up after all of this. I might do it it down the road.

---

### Post by cprofitt on 2008-09-09
> **mastergunner said:**
> OK I finally got it to work and the only thing I did was hook up a DVI cable from card to monitor. Apparently the cable is needed so it can see the monitor and adjust from there. This is the only thing I did. I hooked it up turned on the computer went into Kubuntu and during boot up I saw the NVIDIA splash screen. After logging on I went to NVIDIA Settings and it was seeing everything. WOW I wished this was written somewhere that this cable is a must (at least for me).


To be honest it sounds as though the issue may have been related to:

A)  Your monitor
B)  The VGA cable

Most of the time when the wrong resolution is being used it is because the monitor was not being detected properly. I had a loose VGA cable that caused issues for me and when I reattached it and made sure it was really on the problem went away.

---

### Post by mastergunner on 2008-09-10
I believe it was because it was not name brand monitor that the driver needed a digital input to see it and get the info from it. The vga cable was attached properly and the screw were tight. In Windows once I attached the DVI cable the NVIDIA Manager actually got the resolution right as well as the monitor name.

---

### Post by knix on 2008-09-10
Honestly, I never would have guessed. I don't have DVI,so I've never tried it.
YOu'll notice that sometimes, getting stuff to work is a matter of experimentation (in X especially)

Quote from a section of the xorg.conf man page "VIDEOADAPTOR SECTION
       Nobody wants to say how this works.  Maybe nobody knows ..."

---

### Post by anjilslaire on 2008-09-10
Qft

---

