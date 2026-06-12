---
title: "HOWTO:  Enabling Accelerated 3D for a Virtual Machine in VMWare 5.0"
date: 2005-10-30
forum: Outdated Tutorials &amp; Tips
---

### Post by sizzam on 2005-10-30
This is from the [VMWare manual]("http://www.vmware.com/support/ws5/doc/ws_vidsound_d3d_enabling_vm.html"):

To enable a virtual machine for accelerated 3-D

1. Choose a virtual machine with Windows 2000 or XP guest operating system.

Note: Do not enable Direct3D on a virtual machine that is powered on or suspended.

2. Add the following to the configuration (.vmx) file for the virtual machine:

mks.enable3d = TRUE

This line enables accelerated 3-D on the host. It is required to support accelerated 3-D in the guest and also enables the host to accelerate 2-D portions of the guest display.

3. You may also add one or both of the following optional lines:

svga.vramSize = 67108864

This line increases the amount of VRAM on the virtual display card to 64 MB. Adding more VRAM helps to reduce thrashing in the guest. The maximum value is 128 MB.

vmmouse.present = FALSE

This line disables the absolute pointing device in the guest. Applications which require DirectInput relative mode need to turn off the absolute pointing device in the guest. In practice, this is only required for a certain class of full screen 3-D applications (for example, real-time games like first-person shooters).

Note: If you set the vmmouse.present option, you should also turn off the preference for motion ungrabbing in the Input tab of the Preferences settings dialog.

To turn off ungrabbing for vmouse.present:

a. Choose Edit > Preferences.

b. Click Input.

c. Deselect Ungrab when cursor leaves window.

*****EDIT - More info ******
Not all aspects of 3-D acceleration are enabled. The following 3-D features are not accelerated:
# Pixel and vertex shaders
# Multiple vertex streams
# Hardware bump-mapping, environment mapping
# Projected textures
# Textures with one, three, or four dimensions

---

### Post by krye on 2005-10-30
Excellent! When i've just installed vmware5 on my machine, only to avoid rebooting to windows when I need to use photoshop and dreamweaver :D

Thanks!

---

### Post by greythorne on 2005-10-31
so now if i want to put the vid memory to 128mb then what the value will be?

thnx

---

### Post by krye on 2005-10-31
That would be... 128 megabytes = 134 217 728 bytes

---

### Post by kakashi on 2006-04-17
does this work for the new beta vmware server (its free so i only use it)

---

### Post by Stormbringer on 2006-04-18
Well ... here's a possible showstopper on **AMD64** systems with NVIDIA graphic cards (I'm running VMware Wks 5.5.1 build 19175 on Breezy AMD64).

You added the following lines to your <virtualmachine>.vmx file:

mks.enable3d = "TRUE"
svga.vramSize = "67108864" (or "134217728")

As soon as you start the VM you get an error saying the 3d acceleration cannot be used because of a problem with libnvidia-tls.so.1

Reason: unknown (only Nvidia may know the answer)
Source: VMware opens the 32-Bit TLS library (instead of the 64-Bit one) ... and here seems to be a catch.

Open a terminal and type ...

# sudo mv /usr/lib32/tls/libnvidia-tls.so.1.0.<version> /usr/lib32/tls/libnvidia-tls.so.1.0.<version>.backup
# sudo cp /usr/lib32/libnvidia-tls.so.1.0.<version> /usr/lib32/tls

Replace <version> with the version number of the Nvidia driver that's installed on your box ... here's an example for v87.56 ...

# sudo mv /usr/lib32/tls/libnvidia-tls.so.1.0.8756 /usr/lib32/tls/libnvidia-tls.so.1.0.8756.backup
# sudo cp /usr/lib32/libnvidia-tls.so.1.0.8756 /usr/lib32/tls

That's it ... exit the terminal, fire up VMware, start the VM ... the error should be gone and 3d acceleration should be available.

Hope this information is useful ...

Storm.

---

### Post by imagine on 2006-04-19
[QUOTE=kakashi]does this work for the new beta vmware server (its free so i only use it)[/QUOTE]Not really, because VMware Server uses a remote console to access the virtual machine. Servers don't need 3D acceleration.

---

### Post by MASTERTUHO on 2006-10-24
:) GUYS YOUR AMAZING!!!!!!!! :) 
now i can game at school :mrgreen: 

now school is more fun ;);) 

but i have 1 question.
How can i calculate the code foor more MB for the VM graphic :-k 

if you can tell me then post it here pls

me beg you :p 

SIGNED BY MASTERTUHO

---

### Post by Crashmaxx on 2006-10-24
Anyway to get this to work with vmware server? It says "3d back-end not enabled" or something like that. Don't see why it won't work, basically the same as vmware, but with more.

---

### Post by aroswald1977 on 2006-11-02
> **Crashmaxx said:**
> Anyway to get this to work with vmware server? It says "3d back-end not enabled" or something like that. Don't see why it won't work, basically the same as vmware, but with more.

same here:

Direct rendering is not available.
Failed to construct 3-D rendering backend.  The 3-D features of the display card will be disabled.

---

### Post by closey on 2006-11-03
> **MASTERTUHO said:**
> :) GUYS YOUR AMAZING!!!!!!!! :) 
now i can game at school :mrgreen: 

now school is more fun ;);) 

but i have 1 question.
How can i calculate the code foor more MB for the VM graphic :-k 

if you can tell me then post it here pls

me beg you :p 

SIGNED BY MASTERTUHO

Multiple the number by 1024 and then 1024 again.

---

### Post by ashmew2 on 2006-12-29
> **MASTERTUHO said:**
> :) GUYS YOUR AMAZING!!!!!!!! :) 
now i can game at school :mrgreen: 

now school is more fun ;);) 

but i have 1 question.
How can i calculate the code foor more MB for the VM graphic :-k 

if you can tell me then post it here pls

me beg you :p 

SIGNED BY MASTERTUHO

Hey , you need to know that
1 MegaByte (MB) = 1024 KB(KiloBytes)
I KB = 1024 Bytes

so Ultimately 1 MB = 1024 Multiplied by 1024 Bytes
or 64 MB = 64 Multiplied by 1024 multiplied by 1024.! :P

---

### Post by ashmew2 on 2006-12-31
Direct rendering is not available.
Failed to construct 3-D rendering backend.  The 3-D features of the display card will be disabled.

I get that error as soon as the WinXP VM is  powered on.
By the way , SIzzam and others , shouldnt there be quotes in the options that Sizzam told us
For Example :
mks.enable3d = "TRUE" instead of mks.enable3d = TRUE
svga.vramSize = "67108864" instead of svga.vramSize = 67108864
vmmouse.present = "FALSE" instead of vmmouse.present = FALSE
 ?

---

### Post by baldercm on 2007-01-12
Hello!

I'm running Kubuntu Edgy on a laptop with Intel i835 graphics. I've installed VMWare Server 1.0.1 and a WinXP guest. I've tried to setup 3D acceleration with and without the quotes ashmew2 talk about in the previous post. When I power on the virtual machine I get a
```
Failed to construct rendering backend
```
error.

Can someone help me?

---

### Post by tlacuache on 2007-01-12
For those of you trying this in VMWare server, you need to understand that there's a difference in the way VMWare server displays its guests' screens vs. the way VMWare Workstation and VMWare Player do it. 

VMWare workstation and player render the screen directly. VMWare server uses a remote console to display your screen. It's sort of akin to trying to use 3d acceleration over a protocol like vnc or remote desktop.

In other words, you aren't going to be able to use 3d acceleration with VMWare server.

---

### Post by chandoug on 2007-01-27
when i add the line

mks.enable3d = "TRUE" 

the display is blank and i dont know why
my pc seems to be happy with the other two lines, 
when i take a snapshot i see everything on my desktop

mygraphics card is 
INTEL GMA 950

does anybody know how to solve this problem?

thanks

---

### Post by euthyfro on 2007-02-06
I got the same error message using vmware server, but when i ran the Sims 2 in the virtual machine it worked perfectly w/all it's 3-d elements

---

### Post by demonhunter on 2007-02-06
does anyone got success on enabling 3d acceleration using ATI cards??

thnx, ):P

---

### Post by basse1989 on 2007-02-08
Ok, now on to the important question... does WoW work?

---

### Post by Valehru on 2007-02-12
Hey guys.  

Everything seems to be working in VMware player apart from the 3D acceleration.  I get the error:
"Failed to construct 3-D rendering backend.  The 3-D features of the display card will be disabled."

I've tried the Direct 3d tests in dxdiag and they fail, also I've tried the 3d screensavers and they also fail.  My vmx file is as follows.  Could this have something to do with my xorg.conf file?  I'm running a nvidia 6600GT

_**Windows XP Professional.vmx**_
```

#!/usr/bin/vmware
config.version = "8"
virtualHW.version = "4"
scsi0.present = "TRUE"
memsize = "256"
MemAllowAutoScaleDown = "FALSE"
ide0:0.present = "TRUE"
ide0:0.fileName = "Windows XP Professional.vmdk"
ide0:0.writeThrough = "TRUE"
ide1:0.present = "TRUE"
ide1:0.fileName = "/media/backup1/Games/Lego.Star.Wars.2.The.Original.Trilogy-RELOADED/rld-lsw2.iso01.iso"
ide1:0.deviceType = "cdrom-image"
floppy0.fileName = "Auto detect"
ethernet0.present = "TRUE"
usb.present = "TRUE"
sound.present = "TRUE"
sound.virtualDev = "es1371"
displayName = "Windows XP Professional"
guestOS = "winxppro"
nvram = "Windows XP Professional.nvram"

ide0:0.redo = ""
ide1:0.startConnected = "TRUE"
ethernet0.addressType = "generated"
uuid.location = "56 4d 4d f9 45 cf 94 ae-66 e4 57 9f 15 4f 89 db"
uuid.bios = "56 4d 4d f9 45 cf 94 ae-66 e4 57 9f 15 4f 89 db"
ethernet0.generatedAddress = "00:0c:29:4f:89:db"
ethernet0.generatedAddressOffset = "0"

floppy0.autodetect = "TRUE"
sound.fileName = "-1"
sound.autodetect = "TRUE"
mouse.fileName = "/dev/mouse"

tools.remindInstall = "FALSE"

floppy0.startConnected = "FALSE"

tools.syncTime = "FALSE"
ethernet0.connectionType = "bridged"
mks.enable3d = "TRUE"
svga.vramSize = "67108864" 
vmmouse.present = "FALSE"

sharedFolder.maxNum = "1"
sharedFolder0.present = "TRUE"
sharedFolder0.enabled = "TRUE"
sharedFolder0.readAccess = "TRUE"
sharedFolder0.hostPath = "/media/backup1"
sharedFolder0.guestName = "Backup1"
sharedFolder0.expiration = "never"
sharedFolder1.present = "TRUE"
sharedFolder1.enabled = "TRUE"
sharedFolder1.readAccess = "TRUE"
sharedFolder1.hostPath = "/media/backup1"
sharedFolder1.guestName = "Backup1"
sharedFolder1.expiration = "never"

checkpoint.vmState = ""


```

_**XORG.CONF**_
```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
#	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV43 [GeForce 6600 GT]"
	Driver		"nvidia"
	BusID		"PCI:5:0:0"
EndSection

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV43 [GeForce 6600 GT]"
	Monitor		"SyncMaster"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "ServerFlags"
   Option "BlankTime" "0"
   Option "StandbyTime" "0"
   Option "SuspendTime" "0"
   Option "OffTime" "0"
EndSection

Section "DRI"
	Mode	0666
EndSection


```

---

### Post by Neo40 on 2007-02-13
Does this thing also work with Windows98?

---

### Post by Valehru on 2007-02-13
I realized why it didn't work.  There was a kernel upgrade that screwed up my Nvidia driver.  A quick re-install of the driver solved it for me.

Oh and I'm pretty sure that it does work with Windows 98, which reminds me that it might be a good time to break out that old daggerfall CD for a bit of Elder scrolls nostalgia...

---

### Post by Neo40 on 2007-02-13
Ok, So it would be possible to play Civilization III? I have Cedega, but Civ3 is to much slow and unplayable....That's why I'd like to know if I could play it with vmware...?

Thanks!

---

### Post by SarahKH on 2007-03-01
> **Neo40 said:**
> Ok, So it would be possible to play Civilization III? I have Cedega, but Civ3 is to much slow and unplayable....That's why I'd like to know if I could play it with vmware...?

Thanks!

[http://appdb.winehq.com/appview.php?iVersionId=6130](http://appdb.winehq.com/appview.php?iVersionId=6130)

Seems Wine is playable... possibly more so than Cedega... perhaps worth a shot?

---

### Post by Corvo78 on 2007-03-07
> **basse1989 said:**
> Ok, now on to the important question... does WoW work?

Allthough I'm very sceptic of it, I'm also very curious as to whether I'll be capable of running World of Warcraft.

So far I'm still fiddling with Wine+WoW, but most of the time I simply dual-boot into Windows.

---

### Post by Kastang on 2007-03-07
> **Corvo78 said:**
> Allthough I'm very sceptic of it, I'm also very curious as to whether I'll be capable of running World of Warcraft.

So far I'm still fiddling with Wine+WoW, but most of the time I simply dual-boot into Windows.

Interesting that you brought that up, I was just on the IRC and a person said there that VMWARE was working on 3d accel, so I was looking it up on google and found this thread. I am also attempting to run WoW on Ubuntu. It is one of three programs that I need before I can fully move over to the wonderful world of linux!

---

### Post by BatPenguin on 2007-03-12
Hi everybody,

Just found this thread: I've never tried VMWare (yet) myself but I'm curious now: Has anybody had any success in running games with this experimental 3D support? Please post what you've exactly been able to do with it, I'm sure others reading this would be interested too.

Like many others (I suppose), I'm using Cedega at the moment for gaming and I'm not too happy with it. OK for Civ IV but "fast" 3D games like Battlefield 2 and Oblivion aren't really working that great so it'd be great to hear if others have had success playing games in Ubuntu with some other solution. So please let us know what you've been able to accomplish (gaming-wise) with VMWare - thanks!

---

### Post by el sleepy on 2007-03-13
civ 1, 2 and 3 work in vmware 5.0 . civ 4 does not beacouse of no full 3d support.

---

### Post by Anolis on 2007-03-13
what about old games like Falcon 4.0
and the new Falcon AF

---

### Post by M$LOL on 2007-04-08
[Vmware 6.0 beta is out.]("http://www.vmware.com/products/beta/ws/")
It's a free download ATM, so you can try your games in it for nothing.

---

### Post by uubuuntuu on 2007-05-12
Hi,

I'm running Ubuntu in a virtual machine with VMWare under Windows XP. Following this thread I enabled a grafic device in my virtual Ubuntu. Now I'd like to activate the desktop-effects in Ubuntu which didn't work until now (because there wasn't a 3d-device). But somehow my X-Server still crashes when I ienable the effects. Do I really have to download directx (I dont think so, I guess this is only the other way round - using a virtual windows os).
Would you please help me?

---

### Post by kilou on 2007-05-12
I understand this 3d acceleration doesn't work in VMWare server but does it work in VMWare Player (version 2.0) or is it only a feature of the non-free VMWare Workstation???

---

### Post by BIGtrouble77 on 2007-05-12
Is there any way to have both server and player installed at the same time?  Only reason I run server is because I have to create VM's every so often.  Player is much better for actually using VM's locally.  

Couple things... Cedega and Wine play WoW and CivIV nearly perfectly, so you wouldn't want to play them in VMWare.  Civ III has got to play well in Cedega, if you're having issues then you are probably not using the correct profile.  Try out transgaming's forum for setting.

And to the guy who said vmware server is only for remote VM's, you are wrong.  It works just fine as a player.  Also, in my testing I've found win98 to run MUCH faster than XP or 2000.  I try and use 98 whenever possible.  I REALLY don't think games like WoW will work.  Maybe Halflife 1, but nothing modern.

---

### Post by inoxllor on 2007-05-15
I am using Windows XP with VMWARE 6.0 Workstation. 
Ubuntu 7.04 running in a virtual machine.
I tried to use the "experimental feature" stated here but having no success so far.

My video card is an ATI XT1600, but the Ubuntu vmware client only detects a standard svga card, and when I try to enable the "special effects" it simply reboots to login. Damn.

I am now trying other types of virtual machines software.
Ex.: LIVEPC Engine claims to have 3D Acceleration Features (and they have Ubuntu 7.04 available).
[http://www.moka5.com/node/536](http://www.moka5.com/node/536)
Lets see if they can bypass this problem.

If not, I have to return to the old dual boot system...

Maybe next version of VMWARE will bring a 3D Card virtual device ???

---

### Post by scraff on 2007-05-20
[QUOTE=sizzam;456224]This is from the [VMWare manual]("http://www.vmware.com/support/ws5/doc/ws_vidsound_d3d_enabling_vm.html"):

2. Add the following to the configuration (.vmx) file for the virtual machine:

mks.enable3d = TRUE

This line enables accelerated 3-D on the host. It is required to support accelerated 3-D in the guest and also enables the host to accelerate 2-D portions of the guest display.

3. You may also add one or both of the following optional lines:

svga.vramSize = 67108864
~~~~~~~~~~~~~~~~~~~~~~~~~~~

this may be a stupid question, but were exactly do you add these lines in the code of the vmx file?

---

### Post by Maniax2 on 2007-05-22
i have a host operating system of windows xp sp2 in a pc that has a nvidia 7900 gt  , amd 64 3700 and 1gb of ram.

Recently i made a guest operating system of windows 98 SE , i installed vmware tools , direct x 9c and typed the things to enable d3d on the vmx file of the guest operating system folder.

so... then i enter in vmware using windows 98 i check using dxdiag and i found out that d3d cant be enabled :( , can you guys think of anything wrong i did?

---

### Post by Ferrat on 2007-05-24
It's far from perfect but it works, I get some grafic errors after awhile, like the cache clearing isn't working as it should or something but that could be the beta game Im running as well. 

Im using VMware Player to run a WinXP SP2 on my Ubuntu install, 
AMD64 3200+ 
1500+ RAM
X800 ATi 

First of 

1. Why install WoW via VMware? wine runs WoW more or less flawless now adays and with almoste the same preformance as Windows almoste out of the box? besides WoW maybe will work but not well if at all since no shaders ect works.

2. To get 3d acc. you need to have it up and running on your back system so that your guest system can find it and use it. 

3. Install VMware tools to get SVGA drivers, that will make it better 


Easiest way to install on Ubuntu

Program >> Add/remove >> Install VMware Player

make a vmx file ect with [http://www.easyvmx.com](http://www.easyvmx.com)

install Windows via a normal install CD


Tweaking:

make sure that you give VMware sufficient RAM but not more than 50% of your acctuall amount since giving it to much slows down Ubuntu that needs to use a swap file instead = making both Ubuntu and VMware slow.

Strip down Windows as much as you can 

Get more RAM  ;)

---

### Post by elnur on 2007-05-31
> **inoxllor said:**
> I am using Windows XP with VMWARE 6.0 Workstation. 
Ubuntu 7.04 running in a virtual machine.
I tried to use the "experimental feature" stated here but having no success so far.


Try to type 
```
mks.enable3d = "TRUE" 
```
I mean with quotes

---

### Post by scrop on 2008-02-25
I've been adding 

mks.enable3d = "TRUE"
svga.vramSize = "67108864"
vmmouse.present = "FALSE"

to my vmx file w/ vmware off. As soon as I start up the VM that uses that file, the mks.enable3d option is reverted to 

mks.enable3d = "FALSE"

No obvious error in the logs. Any idea what this is?

---

### Post by scrop on 2008-02-28
The VMWare forums have been having some issues for a few days. Users can't login w/o being taken to the registration screen in an endless loop. I even called them and they had the same issue on their end.

Anyway, after experimentation, I found that VMWare will silently disable 3d support if you don't specify this parameter correctly.

svga.vramSize = "67108864"

If this works out to be anything other than the exact size of the memory your graphics card has then w/o warning or errors being logged you just get reverted to no 3d.

---

### Post by DoDoENT on 2008-03-19
Hello!

I'm using VMware workstation 6.0.1 on Ubuntu gutsy with XP Pro SP2 guest. If I enable 3d acceleration in virtual machine, as soon as I power on the virtual machine, X server crashes and returns me to the login screen. This happens no matter if the compiz effects are on or off.

My graphic card: ATI Mobility Radeon X1600 on HP nx9420 laptop.

I need guest 3d acceleration to gain better performance in AutoCAD Map 3D 2008.

---

### Post by DoDoENT on 2008-04-12
Same with hardy beta :(:(:(.

---

