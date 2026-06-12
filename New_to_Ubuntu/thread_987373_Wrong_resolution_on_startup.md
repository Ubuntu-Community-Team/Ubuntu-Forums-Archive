---
title: "Wrong resolution on startup"
date: 2008-11-19
forum: New to Ubuntu
---

### Post by dazwest on 2008-11-19
After successfully installing Ubuntu I stupidly decided to try to get a higher resolution and after applying it my monitor went blank and the popped up a message saying:

'Signal frequency is out of range. Please change signal timing'

Basically I guess I've chosen a resolution too high for my screen or video card.
Now whenever I boot up I just go straight to that black screen and that message.
How can I get the resolution back to 1280x1024?

thanks in advance
Darren

---

### Post by MasterSander on 2008-11-19
No it's probably your refresh rate that is too high, should be 60 Hz, dunno how to edit it from terminal though

---

### Post by CLomax on 2008-11-19
You can try this:
[B]
> CTRL + ALT + F1
> sudo nano /etc/X11/xorg.conf
> Scroll down until you see the "Screen" section
```
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
      [COLOR="Red"]SubSection "Display"
            Modes	"1440 900"
	    Virtual      1440 900
      EndSubSection[/COLOR]
EndSection
```
That's what mine looks like, try it yourself with your appropriate resolutions and...

```
sudo reboot now
```[/B]
Hope that helps :)
.
.

---

### Post by MasterSander on 2008-11-19
does that still work in 8.10, cause I saw multiple posts mentioning the fact they had an empty xorg.conf

---

### Post by w4ett on 2008-11-19
You can always boot into recovery mode and try using the xfix option

---

### Post by icanfly0307 on 2008-11-19
Hi,
   When you get the GRUB Boot Menu, boot into "Recovery Mode" instead of the normal mode. This should drop you down to a blue screen with several options, one of which is "Fix X Server" (the first option.) Select that, press enter and after its done, reboot into normal mode. This should get you back to your "working" resolution. If this works, post a reply and I'll help you get your monitor to optimal resolution.

Good Luck! :)

---

### Post by CLomax on 2008-11-19
I concur with doing xfix, ignore my previous post.

However, if your login screen resolution is a bit too high... refer back to it :)

---

### Post by dazwest on 2008-11-19
Thanks all for the replies.

I tried the Xfix via recovery mode but when i continued into normal boot I got the same thing happening :(

At that point I followed CLomax's advice and tried the 'sudo gedit' command.
I got the following error: (gedit:6775): Gtk-WARNING **: cannot open display

Any ideas?

---

### Post by wolfen69 on 2008-11-19
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` then reboot.

---

### Post by icanfly0307 on 2008-11-19
> **dazwest said:**
> Thanks all for the replies.

I tried the Xfix via recovery mode but when i continued into normal boot I got the same thing happening :(

At that point I followed CLomax's advice and tried the 'sudo gedit' command.
I got the following error: (gedit:6775): Gtk-WARNING **: cannot open display

Any ideas?

Try hitting Ctrl + Alt + F1 when you get the error message. Then, try following CLomax's idea. However, gedit works ONLY IN GNOME. As you cannot login to GNOME, you have to use nano.

sudo apt-get install nano.

Then, replace CLomax's code with *nano* instead of *gedit*.

---

### Post by dazwest on 2008-11-19
> **wolfen69 said:**
> ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` then reboot.

Thanks. Unfortunately I got the same thing.

---

### Post by dazwest on 2008-11-19
> **icanfly0307 said:**
> Try hitting Ctrl + Alt + F1 when you get the error message. Then, try following CLomax's idea. However, gedit works ONLY IN GNOME. As you cannot login to GNOME, you have to use nano.

sudo apt-get install nano.

Then, replace CLomax's code with *nano* instead of *gedit*.

Thanks. That certainly seemed to work and I was able to edit my xorg.conf
Unfortunately the xorg.conf file seems to be empty though!:confused:

---

### Post by icanfly0307 on 2008-11-19
Could you please post your graphics card model and the maximum resolution of your monitor? This will help a lot.

What do you mean by an empty xorg.conf? Is there nothing in there or does it have something that you can't understand?

---

### Post by dazwest on 2008-11-19
> **icanfly0307 said:**
> Could you please post your graphics card model and the maximum resolution of your monitor? This will help a lot.

Card is a ATI Radeon X1300
Monitor is a 19" running at 1280x1024 in Windows. Not sure if thats its maximum....


> **icanfly0307 said:**
> What do you mean by an empty xorg.conf? Is there nothing in there or does it have something that you can't understand?

Theres nothing in there - its blank.

---

### Post by icanfly0307 on 2008-11-19
Are you sure that you typed in: sudo nano /etc/X11/xorg.conf? If it's still empty, copy and paste this into the empty file.

Section "Files"
FontPath	"/usr/share/fonts/X11/misc"
FontPath	"/usr/X11R6/lib/X11/fonts/misc"
FontPath	"/usr/share/fonts/X11/cyrillic"
FontPath	"/usr/X11R6/lib/X11/fonts/cyrillic"
FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
FontPath	"/usr/X11R6/lib/X11/fonts/100dpi/:unscaled"
FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
FontPath	"/usr/X11R6/lib/X11/fonts/75dpi/:unscaled"
FontPath	"/usr/share/fonts/X11/Type1"
FontPath	"/usr/X11R6/lib/X11/fonts/Type1"
FontPath	"/usr/share/fonts/X11/100dpi"
FontPath	"/usr/X11R6/lib/X11/fonts/100dpi"
FontPath	"/usr/share/fonts/X11/75dpi"
FontPath	"/usr/X11R6/lib/X11/fonts/75dpi"
# path to defoma fonts
FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
Load	"i2c"
Load	"bitmap"
Load	"ddc"
Load	"dri"
Load	"extmod"
Load	"freetype"
Load	"glx"
Load	"int10"
Load	"type1"
Load	"vbe"
EndSection

Section "InputDevice"
Identifier	"Generic Keyboard"
Driver	 "kbd"
Option	 "CoreKeyboard"
Option	 "XkbRules"	"xorg"
Option	 "XkbModel"	"pc105"
Option	 "XkbLayout"	"de"
EndSection

Section "InputDevice"
Identifier	"Configured Mouse"
Driver	 "mouse"
Option	 "CorePointer"
Option	 "Device"	 "/dev/input/mice"
Option	 "Protocol"	 "ExplorerPS/2"
Option	 "Emulate3Buttons"	"true"
EndSection

#Section "Device"
#	Identifier	"ATI Technologies, Inc. ATI Default Card"
#	Driver	 "radeon"
#	BusID	 "PCI:3:0:0"
#EndSection

Section "Device"
Identifier	"ATI Technologies, Inc. ATI Default Card"
Driver	 "radeon"
BusID	 "PCI:3:0:1"
EndSection


Section "Monitor"
Identifier	"Standardbildschirm"
Option	 "DPMS"
HorizSync	28-51
VertRefresh	43-60
EndSection

Section "Screen"
Identifier	"Default Screen"
Device	 "ATI Technologies, Inc. ATI Default Card"
Monitor	 "Standardbildschirm"
DefaultDepth 16	
SubSection "Display"
Depth	 1
Modes	 "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth	 4
Modes	 "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth	 8
Modes	 "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth	 15
Modes	 "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth	 16
Modes	 "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth	 24
Modes	 "1024x768" "800x600" "640x480"
EndSubSection
EndSection

Section "ServerLayout"
Identifier	"Default Layout"
Screen	 "Default Screen"
InputDevice	"Generic Keyboard"
InputDevice	"Configured Mouse"
EndSection

Section "DRI"
Mode	0666
EndSection

If it still doesn't work, give us a shout. :)

---

### Post by CLomax on 2008-11-19
> **icanfly0307 said:**
> Try hitting Ctrl + Alt + F1 when you get the error message. Then, try following CLomax's idea. However, gedit works ONLY IN GNOME. As you cannot login to GNOME, you have to use nano.

sudo apt-get install nano.

Then, replace CLomax's code with *nano* instead of *gedit*.

Such a silly mistake to make.

---

### Post by dazwest on 2008-11-23
Many thanks for your help.
I'm making progress :)
I've pasted in the contents of the xorg.conf file that icanfly0305 recommended above and I'm now getting an error message when loading as follows:
'Ubuntu is running in low-graphics mode
The following error was encountered
(EE) Failed to load module 'type1'(module does not exist, 0)
(EE) No devices detected'

When I ok that another box pops up asking if i want to run in low graphics mode, reconfigure graphics or troubleshoot the error.
If I choose to run in low graphics mode then boot up continues successfully and Ubuntu loads with a resolution of 1280x1024 but doesn't seem to identify my graphics card or monitor.

Have I misidentified my graphics card?

---

### Post by icanfly0307 on 2008-11-23
When you say that Ubuntu continues successfully, do you mean that you are able to log on and access the menus and everything like normal? If so, open your home folder. In the address bar, type:

*/usr/share/applications/*

Scroll down and there should be an icon,"Screens and Graphics" or something like that. Clicking on it should open up a dialog where you can configure your monitor with the correct screen resolution and your correct graphics driver. Let me know what happens.

Good Luck! :)

**PS.** After trying the suggestion that I posted above, try removing everything in the modules section except for "dri" and "glx".

So you should replace this in the xorg.conf:

[I]Section "Module"
Load "i2c"
Load "bitmap"
Load "ddc"
Load "dri"
Load "extmod"
Load "freetype"
Load "glx"
Load "int10"
Load "type1"
Load "vbe"
EndSection[/I]

With this:

[I]Section "Module"
Load "dri"
Load "glx"
EndSection[/I]

---

### Post by dazwest on 2008-11-24
Thanks again for the help.

Yes I can indeed log in and access menus etc. through the GUI (how do you refer to it?).
I can access the Screen Resolution application but within it it says Unknown for monitor type and if I click Detect Displays nothing happens. I can select a resolution and it is already set at 1280x1024 which is what I want.
So all seems good except I still get that error message on startup. I changed the xorg.conf as per your instructions above and that seems to have got rid of the '(EE) Failed to load module 'type1'(module does not exist, 0)' error but not the '(EE) No devices detected' error.
I'm guessing its still not recognising my graphics card somehow?

---

### Post by dazwest on 2008-11-24
An update....
I got rid of the error message by changing 'BusID "PCI:3:0:1"' to 'BusID "PCI:1:0:0"
TBH I've absolutely no idea what that does - it was just a case of trial and error!
What does it do?

Anyway, I've got rid of that error but now it defaults to 1024x768 and I don't get the option of 1280x1024 in the Screen Resolution app.
How can I get that?

---

### Post by icanfly0307 on 2008-11-24
Guess what? I got rid of Hardy last night and installed Intrepid. Unfortunately, my screen resolution was stuck at 800x600 instead of 1024x768!!! Yeah, its a real coincidence, but, I've posted a new thread so it should help you out.

[http://ubuntuforums.org/showthread.php?t=980983&highlight=displayconfig-gtk](http://ubuntuforums.org/showthread.php?t=980983&highlight=displayconfig-gtk)

Let me know if it works. I'll try it out myself once I get back home from school. :)

---

