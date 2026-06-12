---
title: "Graphics Drivers + Low Resource Desktop (seperate questions)"
date: 2008-09-04
forum: New to Ubuntu
---

### Post by Tony_L on 2008-09-04
Its been at least 2 years since I last touched a *nix box (Slackware 8 I think it was), and I've just installed Ubuntu 8.04 to two boxes.

Here's my questions;

1st box:
Shuttle SN45G (nForce2 Ultra 400 SPP)
2500+ Barton
Generic 512mb ddr400 (2x 256)
Generic 64mb (I think) Geforce 4 MX440

I've just tried installing nvidia drivers via Envyng and I don't think it worked :confused:
It installed fine with no errors, but couldn't detect the monitor (Acer AC506) or specific video card. I've selected generic 1024x768 lcd and nv driver

How do I tell if it worked? The first reboot of Gnome only ran in 800x600 and wouldn't let me select higher in Monitor Resolution Settings

I rebooted again and its back to 1024x768; but it seems to me it might have just reverted back to generic drivers.

Is there a program to test 2d or 3d to see if its accelerated properly?
------------------------------------------------

2nd box:
Epia V (VIA PLE133 + VT8231; 533Mhz Samuel)
Generic 512mb pc133 (2x 256)
Integrated VGA, S3 Unichrome / Trident Cyberblade?

Its very slow with default Gnome so I'd like something like Fluxbox (as per [http://www.linux.com/feature/128940](http://www.linux.com/feature/128940) ); But I can't work out exactly how to set it up.
Fluxbox is installed (and fluxconf + xdm ?).

Or can someone tell me how to configure gnome to be a bit less fancy.

(Sorry about this last bit, lost my train of thought :( )
------------------------------------------------
EDIT: Also is there anything for downloading yahoo emails to evolution or similar (Without paying for Yahoo Plus) - I used YPops! for Windows
**Sorted: Webmail + Yahoo Extensions for Thunderbird**

---

### Post by maniheer on 2008-09-04
I think u could use thunderbird with the WebMail plugins

[http://webmail.mozdev.org/](http://webmail.mozdev.org/)

Don't know about ur driver thing

u could look in /etc/X11/xorg.conf and look at this part

```

Section "Device"
	Identifier  "Card0"
	**Driver      "via"**
	VendorName  "Unknown Vendor"
	BoardName   "Unknown Board"
	BusID       "PCI:1:0:0"
EndSection

```

My driver is the via one, I don't know if that how it works for nvidia though.

---

### Post by eriqjaffe on 2008-09-04
> **Tony_L said:**
> I've just tried installing nvidia drivers via Envyng and I don't think it worked :confused:
It installed fine with no errors, but couldn't detect the monitor (Acer AC506) or specific video card. I've selected generic 1024x768 lcd and nv driver

How do I tell if it worked?You should get an NVIDIA splash screen before the login screen comes up.

FWIW, I have an older nVidia card, and had to install an older set (IIRC, Envy gives you three to choose from) to make it work, you may want to give that a shot.

As to your second question, you could just install a command-line version of Ubuntu and add on the things you need.  It's what I did on my Pentium II laptop.

[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

---

### Post by Tony_L on 2008-09-04
> **maniheer said:**
> I think u could use thunderbird with the WebMail plugins

[http://webmail.mozdev.org/](http://webmail.mozdev.org/)

Don't know about ur driver thing

u could look in /etc/X11/xorg.conf and look at this part

```

Section "Device"
	Identifier  "Card0"
	**Driver      "via"**
	VendorName  "Unknown Vendor"
	BoardName   "Unknown Board"
	BusID       "PCI:1:0:0"
EndSection

```

My driver is the via one, I don't know if that how it works for nvidia though.



Ok, that file says driver is nv; that's the base 2d driver isn't it?

---

### Post by Tony_L on 2008-09-04
> **eriqjaffe said:**
> You should get an NVIDIA splash screen before the login screen comes up.

FWIW, I have an older nVidia card, and had to install an older set (IIRC, Envy gives you three to choose from) to make it work, you may want to give that a shot.

As to your second question, you could just install a command-line version of Ubuntu and add on the things you need.  It's what I did on my Pentium II laptop.

[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)



checked again
No splash screen, the login screen is in 640x480 :(, goes to 1024 for the desktop

I'll try the minimal install on the other box tomorrow as I need it to write this ;)

---

### Post by maniheer on 2008-09-04
Type in terminal

```

glxinfo | grep direct

```

The output should be

```

direct rendering: Yes

```


I think nv is the open source one.

---

### Post by Tony_L on 2008-09-04
> **maniheer said:**
> Type in terminal

```

glxinfo | grep direct

```

The output should be

```

direct rendering: Yes

```


I think nv is the open source one.

Xlib: extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX Visual

(via terminal while in desktop)

---

### Post by philinux on 2008-09-04
To see the logo you need to edit xorg.conf

```
gksudo gedit /etc/X11/xorg.conf

```


Look for this bit
```
Section "Device"
    Identifier    "Configured Video Device"
    Driver        "nvidia"
    Option        "NoLogo"    "True"
EndSection

```

Change True to False. Then save the file.

---

### Post by maniheer on 2008-09-04
```

Section "Module"
	Load  "extmod"
	Load  "dbe"
	**Load  "glx"**
	Load  "dri"
	Load  "record"
	Load  "xtrap"
	Load  "GLcore"
	Load  "freetype"
EndSection

```

ur xorg.conf wont be the same as mine but does urs say "glx" or "GLX". It should be "glx" (lowercase)

It looks like u definetly have the opensource drivers u might want to use envy to install the right ones

```

sudo apt-get install envyng-gtk

```

and select it from the system menu. U can set everything up from there

---

### Post by Tony_L on 2008-09-04
> **maniheer said:**
> ```

Section "Module"
	Load  "extmod"
	Load  "dbe"
	**Load  "glx"**
	Load  "dri"
	Load  "record"
	Load  "xtrap"
	Load  "GLcore"
	Load  "freetype"
EndSection

```

ur xorg.conf wont be the same as mine but does urs say "glx" or "GLX". It should be "glx" (lowercase)

It looks like u definetly have the opensource drivers u might want to use envy to install the right ones

```

sudo apt-get install envyng-gtk

```

and select it from the system menu. U can set everything up from there

load glx is there

I originally installed it using that command ^
I've tried the two older drivers from that install menu and both didn't detect the card properly

---

### Post by Tony_L on 2008-09-05
Progress!!

OK, not really :(
I've given up on the nvidia stuff, so I found my Powercolour ATI 9800pro and put that in. (I tried forcibly removing all nv and nvidia stuff last night to no avail)

The ati doesn't detect properly either :-k
Could it be something to do with plug n play settings in the bios?

---

### Post by maniheer on 2008-09-05
> **Tony_L said:**
> Progress!!

OK, not really :(
I've given up on the nvidia stuff, so I found my Powercolour ATI 9800pro and put that in. (I tried forcibly removing all nv and nvidia stuff last night to no avail)

The ati doesn't detect properly either :-k
Could it be something to do with plug n play settings in the bios?

I might be wrong but I thought ATI is worst than nvidia when its on Linux

```

sudo apt-get install xorg-driver-fglrx

```

Should install the ATI drivers (and remove the nv ones)

Then logout and in again and type

```

glxinfo | grep direct

```

to see if you have direct rendering

---

### Post by Tony_L on 2008-09-05
> **maniheer said:**
> I might be wrong but I thought ATI is worst than nvidia when its on Linux

```

sudo apt-get install xorg-driver-fglrx

```

Should install the ATI drivers (and remove the nv ones)

Then logout and in again and type

```

glxinfo | grep direct

```

to see if you have direct rendering
no luck with that one

tried method 1 from here - [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide) - didn't come up with a low quality dialog box like all the other times, is running 1024 - but still has the same errors in glxinfo
method 2 = low quality dialog box

---

### Post by Tony_L on 2008-09-05
How can I find out which xorg.conf my current session is using?

---

### Post by maniheer on 2008-09-05
Sorry for the late reply, had to go School

Have you already went to the restricted drivers manager and enabled ATI?

And it should use /etc/X11/xorg.conf by default.

Have you

```

sudo apt-get install xserver-xgl

```

That should give direct rendering

---

### Post by Tony_L on 2008-09-05
> **maniheer said:**
> Sorry for the late reply, had to go School

Have you already went to the restricted drivers manager and enabled ATI?

And it should use /etc/X11/xorg.conf by default.

Have you

```

sudo apt-get install xserver-xgl

```

That should give direct rendering
Haven't done that, will do it in a few mins.

I've honestly got no idea what I'm running currently lol
EDIT: ok, I'm running without a xorg.conf right now and its the right resolution.
System > Admin > Hardware Drivers is currently not listing anything
System > Prefs > Screen Resolution is correctly identifying my monitor

---

### Post by maniheer on 2008-09-05
can u run Compiz, even though u don't want to, it will make sure u have the right drivers. It looks like its getting better though :)

---

### Post by Tony_L on 2008-09-07
Well its fixed...
I reformatted and started again lol

Only problem there is at the moment is very very small font on the GDM login screen

---

### Post by Tony_L on 2008-09-09
Thanks for all your help people :)

I reckon I'll end up with XP on both boxes again soon though, just don't have the time to customise ubuntu to how I want it.

---

### Post by waltclay on 2008-09-09
I've done my best to understand this thread.
I'm trying to make GoogleEarth work and get a message about graphics driver, but their 'help' has nothing on Linux.

I find 
```
Section "Device"

	Identifier	"Generic Video Card"

	Driver		"vesa"

	BusID		"PCI:1:0:0"

EndSection



Section "Monitor"

	Identifier	"210T/MP/LXA"

	Option		"DPMS"

EndSection



Section "Screen"

	Identifier	"Default Screen"

	Device		"Generic Video Card"

	Monitor		"210T/MP/LXA"

	DefaultDepth	24

	SubSection "Display"

		Modes		"1600x1200" "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"

	EndSubSection


```

Should I update 'vesa?' How?

---

### Post by Vadi on 2008-09-19
"vesa" is a generic driver that really can't do much but at least it shows something. What graphics card are you using?

try going to system - administration - hardware drivers and enabling the video driver there.

---

### Post by Vadi on 2008-09-19
"vesa" is a generic driver that really can't do much but at least it shows something. What graphics card are you using?

try going to system - administration - hardware drivers and enabling the video driver there.

---

### Post by waltclay on 2008-09-29
system>administration>hardware_drivers says there are no proprietary drivers installed.

---

