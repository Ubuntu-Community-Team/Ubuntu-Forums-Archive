---
title: "HowTo: Xinerara / Dual Head with two cards"
date: 2005-05-04
forum: Outdated Tutorials &amp; Tips
---

### Post by henriquemaia on 2005-05-04
**Disclaimer:** 

This worked for me. You should use it at your own risk. This only provides a rough guide, as you should attend to the differences of your own hardware.
This HowTo only covers xinerama/two desktops with TWO cards.

**Hardware:**
2 video cards. 2 monitors. Please make sure that everything is properly connected (cards in computer, monitors to the cards and monitors to the electricity).

**First things first - Backup your xorg.conf file:**

On a terminal (gnome-terminal, for instance), type:

```
cd /etc/X11/
sudo cp xorg.conf xorg.conf.backup
```
[note: if something goes wrong with your xorg setup, you just have to revert the last command to restore your xorg.conf file - eg:

```
cd /etc/X11/
sudo cp xorg.conf.backup xorg.conf
```]

**Editing/creating your xinerama xorg.conf file:**

Run:

```
sudo gedit /etc/X11/xorg.conf
```

Now you have to add the specific data for your second card. You use your xorg.conf file as basis because the data of your main card is already there. You don't have to worry about messing with xorg.conf because you have a backup copy ;)

Take a look at xorg.conf file. You're going add some bits to it, your secondary card info and your secondary monitor info. For that you're going use your main card and monitor info as basis, copying and pasting them, and then change this info to match the exact details of your secondary device.

You see something like this:

Section "Device"
        Identifier      "agp"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        Option          "RenderAccel"   "true"
        Option          "NvAGP"         "3"
EndSection

Just make a copy of that section just bellow that one. Now, change the Identifier field of both sections "Device" so that you can easily understand what they represent. In my case, I named the first device "primary" and "secondary". These names are just representative, so you can put whatever you want:

Section "Device"
        **Identifier      "primary"**
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        Option          "RenderAccel"   "true"
        Option          "NvAGP"         "3"
EndSection

Section "Device"
        **Identifier      "secondary"**
        Driver          "vesa"
        BusID   "PCI:0:13:0"
EndSection

My first card uses nvidia driver and as such uses nvidia driver specific Options. You can delete that on your secondary if it uses a different driver. 

Now you need the specific info of your secondary device, the driver and the BusID. First, to figure out the BusID, you have to run a specific X command: 

```
sudo X :1 -scanpci
```

this will give you something like this (my case):

Probing for PCI devices (Bus:Device:Function)

(0:0:0) Silicon Integrated Systems [SiS] 735 Host
(0:1:0) Silicon Integrated Systems [SiS] SiS 530 Virtual PCI-to-PCI bridge (AGP)(0:2:0) Silicon Integrated Systems [SiS] SiS85C503/5513 (LPC Bridge)
(0:2:1) unknown chip (DeviceId 0x0016) from Silicon Integrated Systems [SiS]
(0:2:2) unknown card (0x1019/0x0a14) using a Silicon Integrated Systems [SiS] USB 1.0 Controller
(0:2:3) unknown card (0x1019/0x0a14) using a Silicon Integrated Systems [SiS] USB 1.0 Controller
(0:2:5) unknown card (0x1039/0x5513) using a Silicon Integrated Systems [SiS] 5513 [IDE]
**(0:13:0) S3 Inc. 86c864 [Vision 864 DRAM] vers 1**
(0:15:0) unknown card (0x1102/0x8027) using a Creative Labs SB Live! EMU10k1
(0:15:1) unknown card (0x1102/0x0020) using a Creative Labs SB Live! MIDI/Game Port
(0:17:0) unknown card (0x10ec/0x8139) using a Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+
**(1:0:0) nVidia Corporation NV11 [GeForce2 MX/MX 400]**


Now, as you'll notice in bold, you see my main video card as well as my secondary one. You shall easily understand your own hardware as well. 
Between the first parenthesis you see some numbers in this format 0:13:0 - this indicates your BusID of your devices. (this is my secondary card BusID).
My secondary card is a S3 Inc. 86c864 [Vision 864 DRAM] vers 1. Its driver is vesa. How do I know this? On a terminal, if you type:
```
man xorg.conf
```
you'll see the manual page for this file. Scroll down to the bottom of this info and in the end of it you'll find this:

 Display  drivers:  apm(4x),  . chips(4x), cirrus(4x), cyrix(4x), fbdev(4x), glide(4x), glint(4x),   i128(4x),   i740(4x),  i810(4x), imstt(4x), mga(4x), neomagic(4x), nv(4x), r128(4x), endition(4x), savage(4x), s3virge(4x), siliconmotion(4x), sis(4x), sunbw2(4x), suncg14(4x), suncg3(4x), suncg6(4x), sunffb(4x), sunleo(4x), suntcx(4x), tdfx(4x), tga(4x), trident(4x),  tseng(4x), vesa(4x), vga(4x), via(4x), vmware(4x).

You just have to find out what driver suits your device best. You don't have to worry if you can't figure out what to use, as you'll shall have the opportunity to do some trial and error with your configuration until everything gets ok. If your card is an old one, use vesa or vga first, as these should work fine. 

So now you have your secondary device with something like this:

Section "Device"
        Identifier      "pci"
        Driver           "vesa"
        BusID           "PCI:0:13:0"
EndSection

Its now time to add your primary and secondary monitor info. Please attend to your hardware and monitor specs when configuring this part. Here's a sample Section "Monitor". This should go right after the last Section "Device" (your secondary card configuration).

Section "Monitor"
        **Identifier      "tft"**
        HorizSync       30-70
        VertRefresh     50-160
        Option          "DPMS"
EndSection

Section "Monitor"
        **Identifier      "crt"**
        HorizSync       30-70
        VertRefresh     50-160
        Option          "DPMS"
EndSection

Again, as before, change the Identifier entries to whatever you like, having in mind that you should use names that make you easily recognize. I used "tft" and "crt" because these are their main characteristic (mine are both from LG and both Flattron). You can put whatever you want (eg: their brands, for instance, or their positions, like "left" or "right"). This is important because you're going to tell in the next entry which monitor you're going to use for each screen X displays.

Please consult your monitor's manual when filling the values of HorizSync and VertRefresh. Option DPMS stands for Display Power Managment Signaling. Use it if your monitor is energy saving aware. There are more Options you can use here, but these are the same you would use in a normal xorg.conf configuration. You just have to remember that you have to fill each monitor Section with its appropriate features.

Now you have the Section "Screen". Just make a copy of that Section (from your original xorg.conf file) and put it just bellow. The Section "Screen" looks like this:

Section "Screen"
   Identifier        "first"
   Device           "primary"
   Monitor          "tft"
   DefaultDepth 16
      SubSection "Display"
        Depth  1
        Modes  "1280x1024" "1152x864" "1024x768"
   EndSubSection
   SubSection "Display"
        Depth  4
        Modes  "1280x1024" "1152x864" "1024x768"
   EndSubSection
   SubSection "Display"
        Depth  8
        Modes  "1280x1024" "1152x864" "1024x768"
   EndSubSection
   SubSection "Display"
        Depth  15
        Modes  "1280x1024" "1152x864" "1024x768"
   EndSubSection
   SubSection "Display"
        Depth  16
        Modes  "1280x1024" "1152x864" "1024x768"
   EndSubSection
   SubSection "Display"
        Depth  24
        Modes  "1280x1024" "1152x864" "1024x768"
    EndSubSection
EndSection

Again, change the names of the Identifier entries in a way that it is easily understandable for you. I named them "first" and "second". You can put whatever you want.

Please note that you have to edit both "Screen" sections if you changed the name of your primary device and the monitor name (the Identifier). Just as an example, I'm going to assume you used "primary" as the name of your primary device and "tft" as name of the first monitor. Remember to fill with YOUR appropriate names. Do the same with your secondary. Like this:

Section "Screen"
 Identifier "first"
 **Device  "primary"**
 ...

Section "Screen"
 Identifier "second"
 **Device  "secondary"**
 ...

Now change the monitor entries of both Section "Screen" with the names you chose. Like this:

Section "Screen"
 Identifier "first"
 Device  "primary"
 **Monitor "tft"**
 ...

Section "Screen"
 Identifier "second"
 Device  "secondary"
 **Monitor "crt"**
 ...

Now you have the DefaultDepth entry. If you're going to use xinerama (big desktop across both monitors), you have to use the same depth for both screens, otherwise it doesn't work (X limitation). If your secondary card is limited to some depth (like an old one, for instance) and can only display 8 or 15 of depth, you put both screen sections using the same value of the less powerful card (don't worry if you don't know this, as you can change these values later in a trial and error manner until you get things the way that best suits you. So now you'll have:

Section "Screen"
 Identifier "first"
 Device  "primary"
 Monitor "tft"
** DefaultDepth 16**
 ...

Section "Screen"
 Identifier  "second"
 Device  "secondary"
 Monitor  "crt"
 **DefaultDepth 16**
 ...

Now comes the resolutions part. You have to attend to the values your cards and monitor can support. In xinerama, only the depth must be the same, and you can use different resolutions for each monitor. I assume you have equally powerful monitors, so you leave both sections with the same resolutions values. If your monitors are different, you can edit the second screen part to match your second monitor specs. Again, you can find this by trial and error. We talk about this again later.

Now we're close to the end. You have to edit this part:

Section "ServerLayout"
 Identifier "Default Layout"
 Screen  "Default Screen"
 InputDevice "Generic Keyboard"
 InputDevice "Configured Mouse"
EndSection

to tell xorg.conf where to put the different screens and how to do it (Xinerama or non-Xinerarma). As such, you'll have:

Section "ServerLayout"
 Identifier      "Default Layout"
 Screen          "first"
 **Screen          "second" LeftOf "first"**
 **Option  "Xinerama"  "On"**
 InputDevice     "Generic Keyboard"
 InputDevice     "Configured Mouse"
EndSection

You have to adjust the entry Screen "second" LeftOf "first" to your own needs, according to the position of your monitors, It can be "second" RightOf "first", or Above or Bellow. In general, LeftOf and RightOf suits our needs best.
Option "Xinerama" "On" tells whether you want to use Xinerama or not (Xinerama - desktop stretched across both monitors). If you prefer, you can have two separate screens. To get that, just type "Off" after "Xinerama". This can have some advantages and disadvantages to Xinerama. It's totally up to you. If you want to know more about multiple screens vs Xinerama, please read this [page](http://da.gentoo-wiki.com/HOWTO_Dual_Monitors#Using_multiple_screens)

You've done it! (almost). Now we're going to test this configuration to see if it works. For that, you have to place your new xorg.conf file in its place, by running:

```
sudo cp ~/xorg.conf /etc/X11/xorg.conf
```

Now the test. Under a console -  Press  ctrl + alt + F1 , log in and run:

```
xinit -- :2
```
[note: to get back to your X session, just press ctrl + alt + F7 to get back to it - this is how you're going to fine tune your xorg.conf file, by jumping between X sessions. Your normal X session is under ctrl + alt + F7 . The new session will be on  ctrl + alt + F8 ]

This will start a new X session. Make sure that both monitors are on. Your screen is going to blank. Soon you'll see your second monitor displaying the secondary card bios info (this shows you that you have selected the correct driver). If everything is ok, a new session starts,  and you see a ugly greyish background and a terminal, but now with your desktop across both monitors. If the second monitor don't show up anything, the xorg.conf is not correct, so you have to correct it. Press ctrl + alt + F7 to get back to your session and fine tune the xorg.conf file. Verify if the BusID and the driver of the second card is ok. Press ctrl + alt + F1 to get back to the console, press ctrl + c to stop the second X session and rerun startx -- :2. Do this as many times as you need until you fine tune everything (resolution, colour depth, options)

[note: I use xinit because it just starts the basic X session without any desktop environment, which is much faster than startx. It's just for testing purposes.]


I hope this helps. As stated before, this is only a rough guide to get xinerama /dual head working. I like to thank everyone in #ubuntu at freenode that gave me valuable hints on how to get this xinerama working. Also, I have found this [site](http://da.gentoo-wiki.com/HOWTO_Dual_Monitors#Introduction) very useful. Many thanks to its authors.

[last note: if you find any mistake or want to add something that might be useful for this purpose, please send me a PM or post it on the thread.]

---

### Post by momo66 on 2005-05-04
Thank you very much for this great how to.  I had left a couple of posts to no avail of getting mine to work.  Cant wait to get home from work and set mine up.

---

### Post by henriquemaia on 2005-05-05
I have updated this HowTo. I forgot about the Section "Monitor" which is now added. My apologies, my mistake.

---

### Post by shakin on 2005-05-09
Excellent how-to! This is such a hard subject because hardware can vary so much and most tutorials focus on dual head cards. When I tried to get this working a month ago I came so close, but never quite there (the second monitor was usually a garbled mess). I used my broken dual monitor xorg.conf and made a couple small changes as per your instructions and now it works!

Thanks again.

---

### Post by oddabe19 on 2005-05-09
Suggestion:
Since not all people have 2 cards, but have 2 ports (DVI & VGA usually) on one card, why don't you do a how two on dual monitors with that setup.

other then that, great howto.

---

### Post by henriquemaia on 2005-05-24
[QUOTE=oddabe19]Suggestion:
Since not all people have 2 cards, but have 2 ports (DVI & VGA usually) on one card, why don't you do a how two on dual monitors with that setup.

other then that, great howto.[/QUOTE]

That would be great. I wrote this HowTo based on my hardware. I cannot test the 2 ports configuration, as such I don't think I'm the right person to do that. Maybe someone who has experience on this can make that HowTo. 

Both HowTos would make a nice pair, as (almost) everyone could find a solution to their hardware/configuration of xinerama/twinview.

---

### Post by Poul on 2005-05-24
[QUOTE=oddabe19]Suggestion:
Since not all people have 2 cards, but have 2 ports (DVI & VGA usually) on one card, why don't you do a how two on dual monitors with that setup.

other then that, great howto.[/QUOTE]

Unfortunatyly it is technicaly impossible as although card has two ports it doesn't have dual display support (unless stated). It might be possible to make it display same output signal on 2 screens but you'll newer get dual display  :-?

---

### Post by mikolajev on 2005-07-14
thanks for a very good howto...first one that I found that comprehensively seems to address configuration of two cards.  I also find the command lspci helpful, although the pci addresses are returned in hex.
-Mikolaj

---

### Post by huwshimi on 2005-07-18
[QUOTE=Poul]Unfortunatyly it is technicaly impossible as although card has two ports it doesn't have dual display support (unless stated). It might be possible to make it display same output signal on 2 screens but you'll newer get dual display  :-?[/QUOTE]
As far as I know it IS possible. I've set this up (one card two monitors) on a couple of computers and have not had a problem. Unless I have just been lucky with the cards I think that it IS possible (I am currently writing this from a computer with 2 monitors but only one card). If i'm incorrect then please let us all know before we buy the wrong graphics cards.

---

### Post by huwshimi on 2005-07-27
By the way to use this how to for a single card just change the following section so that the devices have the same drivers and BusIDs

> Section "Device"
Identifier "primary"
Driver "nvidia"
BusID "PCI:1:0:0"
Option "RenderAccel" "true"
Option "NvAGP" "3"
EndSection

Section "Device"
Identifier "secondary"
Driver "vesa"
BusID "PCI:0:13:0"
EndSection

the above would become something like the following

> Section "Device"
Identifier "primary"
Driver "nvidia"
BusID "PCI:1:0:0"
Option "RenderAccel" "true"
Option "NvAGP" "3"
EndSection

Section "Device"
Identifier "secondary"
Driver "nvidia"
BusID "PCI:1:0:0"
Option "RenderAccel" "true"
Option "NvAGP" "3"
EndSection

---

### Post by da_unruled on 2005-08-01
guys I have a problem,

I followed the guide completely, but then I got this

> 
unruled@unruled:/etc/X11$ sudo cp ~/xorg.conf /etc/X11/xorg.conf
cp: cannot stat `/home/unruled//xorg.conf': No such file or directory
unruled@unruled:/etc/X11$


oh well I skipped ahead without this step, then I got an error because I had a typo in my xorg.conf file...
now it starts my regular monitor (albeit at a resolution too high for comfort with bad refresh), but the other still doesnt start.

 I have attached my xorg.conf (just rename the .zip to .conf).

see, my setup is this:
gf3ti200 AGP on PHILIPS 107T5
riva tnt2 PCI on PHILIPS 107S
in the file I have added a -R and -L to indicate left and right.

what is wrong in my file?  ](*,)

guys??!?

---

### Post by da_unruled on 2005-08-08
[QUOTE=da_unruled]guys I have a problem,

I followed the guide completely, but then I got this



oh well I skipped ahead without this step, then I got an error because I had a typo in my xorg.conf file...
now it starts my regular monitor (albeit at a resolution too high for comfort with bad refresh), but the other still doesnt start.

 I have attached my xorg.conf (just rename the .zip to .conf).

see, my setup is this:
gf3ti200 AGP on PHILIPS 107T5
riva tnt2 PCI on PHILIPS 107S
in the file I have added a -R and -L to indicate left and right.

what is wrong in my file?  ](*,)

guys??!?[/QUOTE]
 guys? i need help with this

---

### Post by henriquemaia on 2005-09-17
Sorry for the loooooong delay in answering this, but I only saw your post today.

I think the problem with your xorg.conf file is this BusID line:

Section "Device"
[INDENT]Identifier "NVIDIA Corporation [TNT2]"
Driver  "vga"
**BusID  "PCI:(2:1:0)"**
Option  "NoLogo"[/INDENT]
EndSection

it should be:

**BusID  "PCI:2:1:0"**

Cannot guarantee, though.

---

### Post by modestmelody on 2005-09-19
I too followed this guide exactly but to no avail.  Here is my xorg.conf:

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
# again, run the following commands:
#
# cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
# sudo sh -c 'md5sum /etc/X11/xorg.conf >/var/lib/xfree86/xorg.conf.md5sum'
# sudo dpkg-reconfigure xserver-xorg

Section "Files"
FontPath "unix/:7100" # local font server
# if the local font server has problems, we can fall back on these
FontPath "/usr/lib/X11/fonts/misc"
FontPath "/usr/lib/X11/fonts/cyrillic"
FontPath "/usr/lib/X11/fonts/100dpi/:unscaled"
FontPath "/usr/lib/X11/fonts/75dpi/:unscaled"
FontPath "/usr/lib/X11/fonts/Type1"
FontPath "/usr/lib/X11/fonts/CID"
FontPath "/usr/lib/X11/fonts/100dpi"
FontPath "/usr/lib/X11/fonts/75dpi"
# paths to defoma fonts
FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
Load "bitmap"
Load "dbe"
Load "ddc"
Load "dri"
Load "extmod"
Load "freetype"
Load "glx"
Load "int10"
Load "record"
Load "type1"
Load "vbe"
EndSection

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "keyboard"
Option "CoreKeyboard"
Option "XkbRules" "xorg"
Option "XkbModel" "pc104"
Option "XkbLayout" "us"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ImPS/2"
Option "Emulate3Buttons" "true"
Option "ZAxisMapping" "4 5"
EndSection

Section "Device"
Identifier "Primary"
Driver "nvidia"
VendorName "nVidia Corporation"
BoardName "geForce 6800GT"
BusID "PCI:5:0:0"
Screen "First"
EndSection

Section "Device"
Identifier "Secondary"
Driver "nvidia"
VendorName "nVidia Corporation"
BoardName "geForce 6800GT"
BusID "PCI:5:0:0"
Screen "Second"
EndSection


Section "Monitor"
Identifier "SyncMaster"
Option "DPMS"
EndSection

Section "Monitor"
Identifier "Dell"
Option "DPMS"
EndSection

Section "Screen"
Identifier "First"
Device "Primary"
Monitor "Dell"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
EndSection

Section "Screen"
Identifier "Second"
Device "Secondary"
Monitor "SyncMaster"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
EndSection

Section "ServerLayout"
Identifier "Default Layout"
Screen "First"
Screen "Second" RightOf "First"
Option "Xinerama" "On"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
EndSection

Section "DRI"
Mode 0666
EndSection

---

### Post by digitalmouse on 2005-09-25
modestmelody - do you have a single geforce card with two video ports? or are you trying to use two separate video cards?  if the later, then i bet the BusID of those two cards are different - you have them listed as the same in both Monitor sections.  

follow the instructions in the Howto on how to scan the PCI bus, and note the different BusIDs for each card.  adjust your config accordingly.

---

### Post by digitalmouse on 2005-09-25
Henri - great tutorial!  almost got mine working (onboard card with 17" monitor for primary and S3 Trio64 with 15" generic monitor for secondary) with your tutorial.  I see the moire pattern on the right screen so I know that the X server has started it, but when testing with 'startx -- :2' or just rebooting the machine with the new config file, I do not get a background, nor can I see the mouse on the second screen.  I know it is going over there because the mouse disappears for a while (not moving up-n-down the right side of the primary), just cannot see it.

any tips?  the KDE Control Center *does* show a Screen 2 now, and at 1024x768, so it seems to be working- just no mouse/background. here is my config  (Kubuntu 5.04):

[PHP]Section "Files"
	FontPath	"unix/:7100"			# local font server
	# if the local font server has problems, we can fall back on these
	FontPath	"/usr/lib/X11/fonts/misc"
	FontPath	"/usr/lib/X11/fonts/cyrillic"
	FontPath	"/usr/lib/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/lib/X11/fonts/Type1"
	FontPath	"/usr/lib/X11/fonts/CID"
	FontPath	"/usr/lib/X11/fonts/100dpi"
	FontPath	"/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"de"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"Silicon Integrated Systems (SiS) 630/730 PCI/AGP VGA Display Adapter"
	Driver		"sis"
	BusID		"PCI:1:0:0"
EndSection

Section "Device"
	Identifier	"s3"
	Driver		"vesa"
	BusID		"PCI:0:11:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-65
	VertRefresh	50-75
EndSection

Section "Monitor"
	Identifier	"highscreen"
	HorizSync	30-69
	VertRefresh	47-120
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"primary"
	Device		"Silicon Integrated Systems (SiS) 630/730 PCI/AGP VGA Display Adapter"
	Monitor		"Generic Monitor"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"secondary"
	Device		"s3"
	Monitor		"highscreen"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600"
	EndSubSection
EndSection


Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"primary"
	Screen		"secondary" RightOf "primary"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666

EndSection[/PHP]
(edit)
added:  
	Option		"Xinerama" "true"
	Option		"Clone" "off"

...to the Server Layout section, and now the desktop background is stretched to apparently cover two screens, but i still do not see the second screen (mouse does still seem to disappear into it though) - maybe because they are of differing resolutions?

also, i noticed in other posts in this forum that the 
	Option		"Xinerama" "true"
appears in another section like so:
Section "ServerFlags"
  Option "Xinerama" "true"
EndSection

does anyone know where the Xinerama option should *really* go?

thanks!

---

### Post by henriquemaia on 2005-09-29
My xorg.conf uses this:

**Section "ServerLayout"**
Identifier "Default Layout"
Screen "first"
Screen "second" LeftOf "first"
Option "Xinerama" **"On"**
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
EndSection

The Option Xinerama "On" goes to **Section "ServerLayout"**. Mine works like a charm. I also use **"On"** instead of "True" but that probably doesn't matter.

Hope it helps.

---

### Post by digitalmouse on 2005-09-29
ok- here is the edited xorg.conf:

```

Section "ServerLayout"
  Identifier         "Default Layout"
  Screen           "primary"
  Screen           "secondary" RightOf "primary"
  Option           "Xinerama" "On"
  Option           "Clone" "off"
  InputDevice    "Generic Keyboard"
  InputDevice    "Configured Mouse"
EndSection

```

i restarted the session, and no change.  second monitor *is* active (with moire pattern), but no desktop, and no visible mouse in that screen.

any other suggestions?

---

### Post by henriquemaia on 2005-09-29
[QUOTE=digitalmouse]

i restarted the session, and no change.  second monitor *is* active (with moire pattern), but no desktop, and no visible mouse in that screen.

any other suggestions?[/QUOTE]

I think you can try other drivers for your card. I think I did that with my secondary one. Maybe another one will make it work.

Also, are you sure the card is ok? I had one card here that was not working, even though X -scanpci detected it. Check that, if you can.

---

### Post by Ricapar on 2005-10-01
I'm having problems with this as well.

First, here is my xorg.conf:

[php]# /etc/X11/xorg.conf (xorg X Window System server configuration file)
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
# again, run the following commands:
#
#   cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
#   sudo sh -c 'md5sum /etc/X11/xorg.conf >/var/lib/xfree86/xorg.conf.md5sum'
#   sudo dpkg-reconfigure xserver-xorg

Section "Files"
    FontPath    "unix/:7100"            # local font server
    # if the local font server has problems, we can fall back on these
    FontPath    "/usr/lib/X11/fonts/misc"
    FontPath    "/usr/lib/X11/fonts/cyrillic"
    FontPath    "/usr/lib/X11/fonts/100dpi/:unscaled"
    FontPath    "/usr/lib/X11/fonts/75dpi/:unscaled"
    FontPath    "/usr/lib/X11/fonts/Type1"
    FontPath    "/usr/lib/X11/fonts/CID"
    FontPath    "/usr/lib/X11/fonts/100dpi"
    FontPath    "/usr/lib/X11/fonts/75dpi"
        # paths to defoma fonts
    FontPath    "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath    "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
    Load    "bitmap"
    Load    "dbe"
    Load    "ddc"
#    Load    "dri"
    Load    "extmod"
    Load    "freetype"
    Load    "glx"
    Load    "int10"
    Load    "record"
    Load    "type1"
    Load    "vbe"
EndSection

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "keyboard"
    Option        "CoreKeyboard"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc104"
    Option        "XkbLayout"    "us"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"        "/dev/input/mice"
    Option        "Protocol"        "ImPS/2"
    Option        "Emulate3Buttons"    "false"
    Option        "ZAxisMapping"        "4 5"
EndSection

Section "Device"
    Identifier     "nvidiafx"
    Driver        "nvidia"
    BusID        "PCI:0:19:0"
    Option         "RenderAccel" "true"
    Option        "nologo" "true"
EndSection

Section "Device" 
    Driver         "via" 
    Identifier    "onboard"
    BusID          "PCI:1:0:0"
EndSection


Section "Monitor"
    Identifier    "vs90"
    Option        "DPMS"
EndSection

Section "Monitor" 
    Identifier "vs4x" 
    HorizSync 60 
    VertRefresh 30-150 
EndSection


Section "Screen"
    Identifier  "vsbig" 
    Device      "nvidiafx" 
    Monitor     "vs90" 
    
    DefaultDepth    24
    SubSection "Display"
        Depth        1
        Modes        "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        4
        Modes        "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        8
        Modes        "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        15
        Modes        "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        16
        Modes        "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        24
        Modes        "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

Section "Screen" 
    Device "onboard" 
    Identifier "vssmall" 
    Monitor "vs4x" 

    DefaultDepth 24 
    SubSection "Display" 
        Depth 24 
        Modes "800x600" "640x480"
    EndSubSection    
EndSection


Section "ServerLayout"
    Identifier "Default Layout"
    Screen "vsbig"
    Screen "vssmall" RightOf "vsbig"
    Option "Xinerama" "On"
    InputDevice "Generic Keyboard"
    InputDevice "Configured Mouse"
EndSection


#Section "DRI"
#    Mode    0666
#EndSection
[/php] 
When I start up X, I'll get the normal display on the first monitor, but nothing on the second.

I tried to troubleshoot it a bit by setting the 2nd monitor as the default, but then X gave me the "no screens found" error.

Any ideas?

In case it matters, here is the output of "sudo X :1 -scanpci":
```
richard@sparky:~$ sudo X :1 -scanpci
Probing for PCI devices (Bus:Device:Function)

(0:0:0) VIA Technologies, Inc. VT8363/8365 [KT133/KM133]
(0:1:0) VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP]
(0:7:0) unknown card (0x1106/0x0000) using a VIA Technologies, Inc. VT82C686 [Apollo Super South]
(0:7:1) unknown card (0x109f/0x315c) using a VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT8233/A/C/VT8235 PIPC Bus Master IDE
(0:7:2) unknown card (0x0925/0x1234) using a VIA Technologies, Inc. USB
(0:7:3) unknown card (0x0925/0x1234) using a VIA Technologies, Inc. USB
(0:7:4) VIA Technologies, Inc. VT82C686 [Apollo Super ACPI]
(0:7:5) unknown card (0x109f/0x315c) using a VIA Technologies, Inc. VT82C686 AC97 Audio Controller
(0:13:0) unknown card (0x109f/0x315c) using a Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+
(0:19:0) unknown card (0x3842/0xb309) using a nVidia Corporation NV34 [GeForce FX 5200]
(1:0:0) unknown card (0x109f/0x315c) using a S3 Inc. ProSavage KM133

```

---

### Post by henriquemaia on 2005-10-02
You have to correct the BusID of your second card.

On you xorg.conf, you have:

Section "Device" 
    Driver         "via" 
    Identifier    "onboard"
    **BusID          "PCI:1:0:0"**
EndSection

Where it should be:

Section "Device" 
    Driver         "via" 
    Identifier    "onboard"
   ** BusID          "PCI:0:1:0"**
EndSection

according to your "sudo X :1 -scanpci":

richard@sparky:~$ sudo X :1 -scanpci
Probing for PCI devices (Bus: Device:Function)

(0:0:0) VIA Technologies, Inc. VT8363/8365 [KT133/KM133]
**(0:1:0) VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP]**
(0:7:0) unknown card (0x1106/0x0000) using a VIA Technologies, Inc. VT82C686 [Apollo Super South]
(0:7:1) unknown card (0x109f/0x315c) using a VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT8233/A/C/VT8235 PIPC Bus Master IDE
(0:7:2) unknown card (0x0925/0x1234) using a VIA Technologies, Inc. USB
(0:7:3) unknown card (0x0925/0x1234) using a VIA Technologies, Inc. USB
(0:7:4) VIA Technologies, Inc. VT82C686 [Apollo Super ACPI]
(0:7:5) unknown card (0x109f/0x315c) using a VIA Technologies, Inc. VT82C686 AC97 Audio Controller
(0:13:0) unknown card (0x109f/0x315c) using a Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+
(0:19:0) unknown card (0x3842/0xb309) using a nVidia Corporation NV34 [GeForce FX 5200]
(1:0:0) unknown card (0x109f/0x315c) using a S3 Inc. ProSavage KM133

I think this will do the trick. ;)
I really hope so. Good luck

---

### Post by jaakko on 2005-10-02
Everything else seems to work perfectly with this Ubuntu 5.10 but I can't get my other monitor working. All day I have been searching tutorials from google and from this forum. I have found lots of guides on this matter but for some reason I haven't been able to get my xorg.conf configurated properly.

At the moment I'm using the Ati fglrx driver from Synaptic (version 8.16.20). I also downloaded Ati Control Panel software, but it seems pretty useless. There is options conserning dual monitors but it doesn't save the changes I've made. So in order to get two monitors working I guess I have to do configuration by editing the xorg.conf.

So the situation is this: I have a Ati Radeon 9700 graphics card, two monitors and I want to get **"intependent" desktops on each monitor** (two x servers?). The primary monitor is Samsung SyncMaster 710t (LCD) and the other one is Nokia 447Zi+ (CRT). LCD monitor uses 1280x1024 resolution and CRT monitor should use 1024x768. At the moment the secondary monitor is a clone (shows the same picture as the primary monitor).

If some one has got a xorg configuration that would work in my situation, I would really appreciate if I could see it. And I'm going to paste my latest (I have tried many) xorg.conf if some one could tell me what is wrong with it.

Thank you!

```


# /etc/X11/xorg.conf (xorg X Window System server configuration file)...

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "ServerFlags"
	Option	"Xinerama"
EndSection 

Section "Module"
	Load	"dbe" # Double-Buffering Extension
	Load	"v4l" # Video for Linux
	Load	"GLcore"
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
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"fi"
EndSection


########## Hiiren oletusasetukset
#Section "InputDevice"
#	Identifier	"Configured Mouse"
#	Driver		"mouse"
#	Option		"CorePointer"
#	Option		"Device"		"/dev/input/mice"
#	Option		"Protocol"		"ImPS/2"
#	Option		"Emulate3Buttons"	"true"
#	Option		"ZAxisMapping"		"4 5"
#EndSection

########## Hiirikonfiguraatio Logitechin MX510:lle
########## http://ubuntuforums.org/showthread.php?t=65471
Section "InputDevice"
Identifier	"Configured Mouse"
Driver		"mouse"
Option		"Protocol"		"evdev"
Option		"Dev Name"		"Logitech USB-PS/2 Optical Mouse"
Option		"Dev Phys"		"usb-*/input0"
#Option		"Dev Phys"		"usb-0000:00:02.1-2/input0"
Option		"Device"		"/dev/input/event1"
Option		"Buttons"		"10"
Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"device0"
	VendorName	"ATI"
	BoardName	"ATI Radeon"
	Driver		"radeon"
	BusID		"PCI:2:0:0"
	Option		"DDCMode" "on"
	Option		"DPMS"
	Screen 0
EndSection

Section "Device"
	Identifier	"device1"
	BoardName	"ATI Radeon"
	Driver		"radeon"
	BusID		"PCI:2:0:1"
	Option		"DDCMode" "on"
	Option		"DPMS"
	Screen 1
EndSection

Section "Monitor"
	Identifier	"monitor0"
	Option		"DPMS"
EndSection

Section "Monitor"
	Identifier	"monitor1"
	Option		"DPMS"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device "device0"
    Monitor "monitor0"
    DefaultColorDepth 24
    Subsection "Display"
        Depth 24
        Virtual 1024 768    
        Modes    "1024x768"
    EndSubsection
EndSection

Section "Screen"
    Identifier "Screen1
    Device "device1"
    Monitor "monitor1"
    DefaultColorDepth 24
    Subsection "Display"
        Depth 24
        Virtual 1024 768    
        Modes    "1024x768"
    EndSubsection    
EndSection

Section "ServerLayout"
	Identifier "Multihead layout"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	Screen  "Screen0" 0 0
	Screen  "Screen1" RightOf "Screen0" 
EndSection

Section "DRI"
	Mode	0666
EndSection


```

---

### Post by mellowdave on 2005-10-02
```
Section "ServerLayout"
	Identifier	"single head configuration"
	Screen		0	"Screen0" 0 0
	Screen		1	"Screen1" LeftOf "Screen0"
	InputDevice	"Mouse0" "CorePointer"
	InputDevice	"Keyboard0" "CoreKeyboard"
	Option		"Clone" "off"
#	Option		"Xinerama" "on"
EndSection

Section "ServerFlags"
#	Option		"Xinerama"
	Option		"MergedFB"
EndSection

Section 	"Files"
	RgbPath		"/usr/lib/X11/rgb"
	ModulePath	"/usr/X11R6/lib/modules"
#	FontPath "unix/:7100"
EndSection

Section	"Module"
	Load	"dbe"
	Load	"extmod"
	Load	"fbdevhw"
	Load	"glx"
	Load	"record"
	Load	"freetype"
	Load	"type1"
#	Load	"dri"
EndSection

Section	"Extensions"
	Option	"Composite" "Enable"
EndSection

Section	"InputDevice"
	Identifier	"KeyBoard0"
	Driver		"kbd"
	Option		"XkbModel" "pc105"
	Option		"Xkblayout" "us"
EndSection

Section	"InputDevice"
	Identifier	"Mouse0"
	Driver		"mouse"
	Option		"ButtonNumber"	"7"
	Option		"Buttons"	"7"
	Option		"Protocol" "ExplorerPS/2"
	Option		"Device" "/dev/input/mice"
	Option		"ZAxisMapping" "6 7"
	Option		"Emulate3Buttons" "yes"
EndSection

Section	"Monitor"
	Identifier	"Monitor0"
	VendorName	"Samsung"
	ModelName	"172T"
	HorizSync	30.0 - 67.0
	VertRefresh	56.0 - 75.0
EndSection


Section "Monitor"
	Identifier	"Monitor1"
	VendorName	"Samsung"
	ModelName	"172N"
	HorizSync	30.0 - 81.0
	VertRefresh	56.0 - 75.0
EndSection

Section	"Device"
	Identifier	"Videocard0"
	Driver		"radeon"
	VendorName	"ATI Technologies Inc"
	BoardName	"ATI Radeon 9500 Pro"
	BusID		"PCI:03:00:0"
#	Option		"AGPMode" "4"
	Screen		0
EndSection

Section	"Device"
	Identifier	"Videocard1"
	Driver		"radeon"
	VendorName	"ATI Technologies Inc"
	BoardName	"ATI Radeon 9500 Pro"
	BusID		"PCI:03:00:0"
#	Option		"AGPMode" "4"
	Screen		1
EndSection

Section	"Screen"
	Identifier	"Screen0"
	Device		"Videocard0"
	Monitor		"Monitor0"
	DefaultDepth	24
		SubSection "Display"
		Viewport	0 0
		Depth		24
		Modes		"1280x1024"
		EndSubSection
EndSection

Section "Screen"
	Identifier	"Screen1"
	Device		"Videocard1"
	Monitor		"Monitor1"
	DefaultDepth	24
	SubSection "Display"
		Viewport	0 0
		Depth		24
		Modes		"1280x1024"
	EndSubSection
EndSection

#Section "DRI"
#	Group	0
#	Mode	0666
#EndSection

```

This works for me. Dual head, no xinerama, no acceleration. I've been planning to try Merged FB but havent delved in. I'm pretty sure if I remove the second screen portion, and make a few other minor changes Merged FB will work, but I'm not sure I want a GARGANTUAN desktop.

Also note, the parts that mde the monitors stop mirrring each other is the "Device" Video card 0 and "Device" Video Card 1. 


I'm using a Radeon 9500 Pro, two LCD;s.

open to ideas if anyone sees areas for improvement...

---

### Post by jaakko on 2005-10-03
**mellowdave:** Thank you so much! I finally got it working! \\\\:D/ :D

---

### Post by Ricapar on 2005-10-03
I tried what you suggested, henriquemaia, but still no luck.
:(

---

### Post by henriquemaia on 2005-10-03
[QUOTE=Ricapar]I tried what you suggested, henriquemaia, but still no luck.
:([/QUOTE]

Try to get another secondary card, so you can troubleshoot better what's happening.  

If you do this, remember to run -scanpci to find out the correct BusID of that card. I had to try at least 3 until I could get one working (I was using some old cards my uncle had gave me).

Good luck.

---

### Post by kANDIs on 2005-10-17
Hi!

I've read your How-To and tried to do set up a second monitor, but failed.

I got an acer aspire notebook and when I plug in the second monitor to the vga-port before (!) booting the LCD stays black and everything's displayed on the second monitor. So, it's working at least...
The video-chip is on board (should be a Via, PCI 1.0.0).

This is what I tried:

[SIZE="1"]Section "Device"
	Identifier	"Primary"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
	Screen		0
EndSection

Section "Device"
	Identifier	"Secondary"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
	Screen		1
EndSection

Section "Monitor"
	Identifier	"Notebook"
	Option		"DPMS"
	HorizSync	30-85
	VertRefresh	55-160
EndSection

Section "Monitor"
	Identifier	"Eizo"
	Option		"DPMS"
	HorizSync	30-85
	VertRefresh	55-160
EndSection


Section "Screen"
	Identifier	"Default Screen"
	Device		"Primary"
	Monitor		"Notebook"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection


Section "Screen"
	Identifier	"Additional Screen"
	Device		"Secondary"
	Monitor		"Eizo"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	Screen		"Additional Screen" LeftOf "Default Screen"
	Option		"Xinerama" "Off"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection[/SIZE]

Running xinit -- :2 I get:
[SIZE="1"]Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_clip.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_norm.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_xform.o":  No symbols found

Fatal server error:
Requested Entity already in use![/SIZE]


So, what's wrong with my xorg.conf?

---

### Post by Stormy Eyes on 2005-10-17
[QUOTE=kANDIs]So, what's wrong with my xorg.conf?[/QUOTE]

It looks like you have a Xinerama-style setup, but you've disabled Xinerama. Try changing **Option "Xinerama" "Off"** to **Option "Xinerama" "On"**. I'll cross-post this in the other thread, OK?

---

### Post by kANDIs on 2005-10-17
No, sorry
same error

---

### Post by morticia on 2006-07-07
> **kANDIs said:**
> No, sorry
same error

Hi, I've been the same error, mas I've one video card nvidia GF6500 that work how dual head. Plis if someone find the solution tell me.


Thks,

Morticia

---

### Post by henriquemaia on 2006-07-07
> **morticia said:**
> Hi, I've been the same error, mas I've one video card nvidia GF6500 that work how dual head. Plis if someone find the solution tell me.


Thks,

Morticia

The previous post was posted long ago (almost a year). Maybe you can try elsewhere to try to find the solution. 

ps: mas... are you portuguese (or portuguese speaker)?

---

