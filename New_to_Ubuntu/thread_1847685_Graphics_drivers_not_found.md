---
title: "Graphics drivers not found"
date: 2011-09-21
forum: New to Ubuntu
---

### Post by Hannahsaurus on 2011-09-21
Hi, just installed ubuntu 11.04 as my laptop was collapsing under the weight of windows.

Everything runs much faster but I can't get it to recognise the monitor. 

I've downloaded the right drivers (I think) and put them in the drivers folder but it still isn't using them. 
Graphics card - SiS 771/671 Mirage.

Any help would be much appreciated. My computer's still usable but a 1280x800 screen is a little annoying in 1024x768 resolution.

Laptop - fujitsu esprimo modile V5515
Thanks.

---

### Post by realzippy on 2011-09-21
Welcome.
Which driver did you download?Have a link?

---

### Post by P05TMAN on 2011-09-21
> **Hannahsaurus said:**
> Hi, just installed ubuntu 11.04 as my laptop was collapsing under the weight of windows.

Everything runs much faster but I can't get it to recognise the monitor. 

I've downloaded the right drivers (I think) and put them in the drivers folder but it still isn't using them. 
Graphics card - SiS 771/671 Mirage.

Any help would be much appreciated. My computer's still usable but a 1280x800 screen is a little annoying in 1024x768 resolution.

Laptop - fujitsu esprimo modile V5515
Thanks.


To check drivers that are installed, open a terminal & type 

```

lspci

```

---

### Post by realzippy on 2011-09-21
```
[lspci]("http://manpages.ubuntu.com/manpages/intrepid/man8/lspci.8.html")
```
doesn't show any driver at all.
It lists pci devices....

---

### Post by P05TMAN on 2011-09-21
> **realzippy said:**
> ```
[lspci]("http://manpages.ubuntu.com/manpages/intrepid/man8/lspci.8.html")
```doesn't show any driver at all.
It lists pci devices....

*foot in mouth* O_o

sorry 'bout that. I thought it showed the drivers as well.

After some further research, and correct me if I'm wrong again, you may search your drivers with 

```

modprobe -l

```

---

### Post by realzippy on 2011-09-21
Don't want to derail this thread,but you asked for it:
*[modprobe]("http://linux.die.net/man/8/modprobe")* is...
..a program to add and remove modules from the Linux Kernel.
*modprobe -l* lists the currently inserted modules.
Not all drivers are kernel modules.
A manually installed SIS graphics driver is no such kernel module.

---

### Post by P05TMAN on 2011-09-21
> **realzippy said:**
> Don't want to derail this thread,but you asked for it:
*[modprobe]("http://linux.die.net/man/8/modprobe")* is...
..a program to add and remove modules from the Linux Kernel.
*modprobe -l* lists the currently inserted modules.
Not all drivers are kernel modules.
A manually installed SIS graphics driver is no such kernel module.

Ah...well then I'll go back to research. Thanks for clearing that up for me (and hopefully the OP). 

On the OP's issue though, could there be an adjustment made in etc/X11/xorg.conf to bypass a default setting the driver may already have, such as screen resolution?

---

### Post by realzippy on 2011-09-21
Btw,afaik there is no linux command that lists all device drivers if they are no modules....

..................................

You are right,editing xorg.conf probably will work.
Adding the correct Vrefresh/Hsync values in the monitor section usually
solves the problem of limited resolutions offered.

---

### Post by P05TMAN on 2011-09-21
> **realzippy said:**
> Btw,afaik there is no linux command that lists all device drivers if they are no modules....


I see.

> 
You are right,editing xorg.conf probably will work.
Adding the correct Vrefresh/Hsync values in the monitor section usually
solves the problem of limited resolutions offered.For the OP: I found a page with a little more info about what realzippy is talking about: 

[https://wiki.ubuntu.com/X/Troubleshooting/Resolution](https://wiki.ubuntu.com/X/Troubleshooting/Resolution)

specifically, realzippy's reference was to this section of the xorg.conf file (your values may differ): 

```

Section "Monitor"
        Identifier   "Monitor1"
        HorizSync    28.0 - 80.0
        VertRefresh  48.0 - 75.0
EndSection                

```

---

### Post by realzippy on 2011-09-21
Yes,exactly.
For 1280x800 a Hsync limit of 50 KHz is enough,so try:

```
Section "Monitor"
        ........................
        HorizSync    28.0 - 51.0
        VertRefresh  48.0 - 75.0
EndSection
```

---

### Post by Hannahsaurus on 2011-09-21
I downloaded the drivers from this link

[http://www.ubuntugeek.com/how-to-install-sis-771671-mirage-3-video-drivers-in-ubuntu-10-04-lucid.html](http://www.ubuntugeek.com/how-to-install-sis-771671-mirage-3-video-drivers-in-ubuntu-10-04-lucid.html)

Are they not right then? 

My xorg.config file doesn't have any values in for Monitor...

```
Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Monitor"
	Identifier   "Monitor1"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection
```

---

### Post by realzippy on 2011-09-21
Link seems to be pretty old...

Anyway,please show whole xorg.conf

```
cat /etc/X11/xorg.conf
```

---

### Post by Hannahsaurus on 2011-09-21
If I try to view it from terminal I get:


```
hannah@Hannah-Laptop:~$ cat /etc/X11/xorg.conf
cat: /etc/X11/xorg.conf: No such file or directory

```

Even if I run it as sudo.

But when I go to the folder and view the text file it's there... but I can only open it as read-only:

```
Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	Screen      1  "Screen1" RightOf "Screen0"
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "built-ins"
EndSection

Section "Module"
	Load  "record"
	Load  "dri2"
	Load  "dbe"
	Load  "dri"
	Load  "extmod"
	Load  "glx"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Monitor"
	Identifier   "Monitor1"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "ShadowFB"           	# [<bool>]
        #Option     "Rotate"             	# <str>
        #Option     "fbdev"              	# <str>
        #Option     "debug"              	# [<bool>]
	Identifier  "Card0"
	Driver      "fbdev"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "ShadowFB"           	# [<bool>]
        #Option     "DefaultRefresh"     	# [<bool>]
        #Option     "ModeSetClearScreen" 	# [<bool>]
	Identifier  "Card1"
	Driver      "vesa"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Screen"
	Identifier "Screen1"
	Device     "Card1"
	Monitor    "Monitor1"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection
```

---

### Post by realzippy on 2011-09-21
please show output from

```
ls /etc/X11
```

---

### Post by Hannahsaurus on 2011-09-21
```
hannah@Hannah-Laptop:~$ ls /etc/X11
app-defaults             X               Xreset      Xsession.options
cursors                  xinit           Xreset.d    Xwrapper.config
default-display-manager  xkb             Xresources
fonts                    xorg.config     Xsession
rgb.txt                  xorg.conf.save  Xsession.d
hannah@Hannah-Laptop:~$ 

```

---

### Post by realzippy on 2011-09-21
Ok,you saved your 
xorg.conf 
as
xorg.config
that's why cat didn't show file's content.

Anyway,the driver you tried to install is outdated (it is for Xserver 1.7 )
and your xorg.conf(ig) is a mess.
Run

```
gksudo gedit /etc/X11/xorg.conf
```

paste into empty file:

```
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "vesa"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync    28.0 - 51.0
        VertRefresh  48.0 - 75.0
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

```

close file saving changes.
reboot (or restart Xserver)

1280x800 now available?

---

### Post by Hannahsaurus on 2011-09-21
Wow, massive improvement!
I'm at 1280x768 now... 
Can I make it 800?

---

### Post by realzippy on 2011-09-21
Show output from

```
xrandr -q
```

---

### Post by Hannahsaurus on 2011-09-21
```
hannah@Hannah-Laptop:~$ xrandr -q
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 1280 x 768, maximum 1280 x 768
default connected 1280x768+0+0 0mm x 0mm
   1280x768        0.0* 
   1024x768       61.0  
   800x600        73.0  
   640x480        73.0  
hannah@Hannah-Laptop:~$ 

```

---

### Post by realzippy on 2011-09-21
Thanks,unfortunately screen maximum reported is 1280x768...

Again run

```
gksudo gedit /etc/X11/xorg.conf
```

change 51 to 60,so line is:

```
HorizSync    28.0 - 60.0
```
close,save,reboot.
Honestly I don't think it helps,since 51 should have been enough for
1280x800,but please try it.

---

### Post by Hannahsaurus on 2011-09-21
Gave it a go but nothing changed. 

Before I put your last fix in it was saying the maximum was 1024x768.

---

### Post by realzippy on 2011-09-21
```
xrandr -q
```
shows maximum screen...


................................................................

Googled a bit and found a SIS driver that should work in 11.04...
[http://ajoliveira.com/ajoliveira/uk/software/xorg.php](http://ajoliveira.com/ajoliveira/uk/software/xorg.php)
If you want help with this,tell me if you run 11.04 32 or 64 bit...

---

### Post by Hannahsaurus on 2011-09-21
I'm on 32 bit. 
I've downloaded the drivers and extracted them

---

### Post by realzippy on 2011-09-21
After extracting you have to copy the 2 files to their destinate location,
as described.If downloaded to /home/hannah/Downloads:

```
sudo cp ~/Downloads/32-bit/*.so /usr/lib/xorg/modules/drivers
```
```
sudo cp ~/Downloads/32-bit/*.la /usr/lib/xorg/modules/drivers
```
Then edit xorg.conf again:

```
gksudo gedit /etc/X11/xorg.conf
```

delete all,paste in:

```
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"sis671"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth 	24
EndSection
```

reboot

---

### Post by Hannahsaurus on 2011-09-21
You're a star! Thank you so much. All fixed :)

---

### Post by realzippy on 2011-10-01
Could you -if you still run that sis671 machine- post/attach content of
your 
var/log/Xorg.0.log
file ?

..only for my archive :p
thanks
have fun zippy

---

