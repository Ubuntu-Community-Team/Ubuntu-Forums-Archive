---
title: "Newbie needs help with dual monitors"
date: 2008-10-24
forum: New to Ubuntu
---

### Post by hatrack on 2008-10-24
Hi all !

Although I have a fair experience of computers stretching back over 20+ years (back to DOS 3.1 !) all my experience has been with MS products. Now at the age of 75, I'm trying to set up my first Linux system and finding it has a steep learning curve.

I have so far got a dual boot system (Ubuntu 8.04/Win XP) and this works fine. I mainly do photo-processing and need Win XP to drive my film scanner. PhotoShop runs just fine under Ubuntu/Wine ... so far so good. Now I am trying to set up a dual monitor system.

My main graphics controller is on the motherboard and is an Intel 82945G/GL. I have added a Radeon 7000-series PCI card and hooked my second monitor to this. Under Win XP, this works without a problem. However, under Ubuntu, the graphics display originally defaulted to this card, not the on-board controller. I have found and fixed this particular problem by altering a BIOS setting but still can't get a twin-display under Ubuntu. I understand that I need to modify xorg.conf and have searched this forum but the information found so far doesn't quite seem to match what I am trying to do. I then found a book ("Ubuntu Hacks" by Oxer, Rankin & Childers) which gave pretty detailed instructions and have followed these to produce the file that I have appended below :-

[NB preamble to this file deleted ...]

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Intel 82945G Main Monitor"
	Driver		"Intel 82945G/GL"
	BusID		"PCI:00:02:0
EndSection

Section "Device"
	Identifier	"Radeon 7000 Series CRT Monitor"
	Driver		"Radeon 7000 Series"
	BusID		"PCI:00:02:1
EndSection

Section "Monitor"
	Identifier	"Main Monitor"
	Option 		"DPMS"
	HorizSync	28-80
	VertRefresh	43-75
EndSection

Section "Monitor"
	Identifier	"CRT Monitor"
	Option 		"DPMS"
	HorizSync	28-80
	VertRefresh	43-75
EndSection


Section "Screen"
	Identifier 	"Default Screen"
	Monitor		"Main Monitor"
	Device		"Intel 82945G Main Monitor"
	DefaultDepth	32

#Additional info added as instruction	
	SubSection "Display"	
		Depth	32
		Modes	"1152x864"
	End Subsection
#End additional info

EndSection

Section "Screen"
	Identifier	"Second Screen"
	Monitor		"CRT Monitor"
	Device		"Radeon 7000 Series"
	DefaultDepth	32
	
	SubSection "Display"	
		Depth	32
		Modes	"1152x864"
	End Subsection
EndSection

# Additional info added as recommended
Section "ServerFlags"
	Option "Xinerama" "true"
EndSection
# End additional info

Section "ServerLayout"
	Identifier	"Twin Head"
	Screen		"Default Screen"
	Screen		"Second Screen" LeftOf "Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection


When I try to boot with this xorg.conf, the system protests that it cannot set up the monitors and then defaults to a low-res (800x600) display ... which allows me to recover the situation (Nice design feature !)

Can anyone please either provide an edit of my file or point me towards a GOOD source of information. I know that I am asking a bit much here but I well and truly stuck.

Many thanks to those who read this lengthy post and may I offer my apologies for raising what I am sure is a very simple problem.

Regards to all ...

---

### Post by hatrack on 2008-10-26
Thank you for your good wishes

---

### Post by drtre on 2008-10-26
Don't know if this helps, but I had the same problem back then. Hopefully I had nVidia graphic card which is pretty compatible with Linux system. ATI as far as I know doesn't disclose it's sources for open source projects, so it has some difficulties in Linux. The best and most efficient way that keeps you a lot of a headache is to use your card driver which is downloadable via synaptic. I think for ATI is Catalyst Control or something like that. Try installing that. If that didn't help you're going to have a lot more problem manipulating xorg.conf for your ATI Card. Just my experience though. Perhaps others can help more. Good Luck. :popcorn:

---

### Post by nick_h on 2008-10-26
This is not a simple problem.  You seem to be progressing in the right direction though.

You have two device sections to define your graphics cards but the drivers don't look correct.  The Radeon 7000 should specify a driver like "ati", "radeon" or "fglrx".  Your Intel driver also looks like it needs changing.  You should also check your BusID with the *lspci* command.

Have a look at [https://help.ubuntu.com/community/Video](https://help.ubuntu.com/community/Video)

The identifiers in your device sections need to match the drivers in your screen section.  In the radeon case it doesn't.

Otherwise I think it looks good.

Have a look in your /var/log/Xorg.0.log file to see what errors you are getting.  Type:
```
less /var/log/Xorg.0.log
```
or use System->Administration->System Log

For more information:
```
man xorg.conf
```
[https://help.ubuntu.com/community/Video#ATI](https://help.ubuntu.com/community/Video#ATI)

---

### Post by hatrack on 2008-10-26
My thanks to all who replied to my post.

I agree that "this is not a simple problem" (LOL !) and also with the suggestions that I should look both at BUSID info and also the drivers. I had a feeling that the problem was essentially a combination of some fairly simple errors. I have already gathered BUSID info but now, developing the solution, is going to be a matter of  "change the conf file ... boot ... recover ... change the conf file, etc. ... etc." 

I repeat my thanks and promise to post my findings when (or "If") I manage to crack the problem.

Best regards to all ...

---

### Post by nick_h on 2008-10-26
> developing the solution, is going to be a matter of "change the conf file ... boot ... recover ... change the conf file, etc. ...

Hopefully you won't need to reboot, just restart the X server.

Make a backup of a working single screen xorg.conf file so that you can restore a working copy when you need to.

To backup:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.single
```
To restore:
```
sudo cp /etc/X11/xorg.conf.single /etc/X11/xorg.conf
```

Don't forget that you can use Ctl-Alt-F1 to get to a virtual terminal to restore the file.  Also Ctl-Alt-Backspace will kill an X session.

Try the open source drivers "radeon" and "intel" to begin with.

Post the error section [entries prefixed with (EE)] of your /var/log/Xorg.0.log file if you need any help.

---

### Post by hatrack on 2008-10-26
Thanks Nick !

So far today, I've been on to the ATI Web site and found a suitable Linux-compatible driver for my obsolescent Series 7000 card.

This took a bit of searching but the site is very helpful and provides links to various sources of information.

I've now down-loaded this and installed it apparently without any trouble. As it is now 0130hrs locally, I'm going to stop for tonight and think about the next step (modifying the xorg.conf file) tomorrow !

Thanks again !

---

### Post by nick_h on 2008-10-27
> I've been on to the ATI Web site and found a suitable Linux-compatible driver

OK.  I think you will need "fglrx" for the proprietary driver, not "radeon" as I suggested earlier.

---

### Post by hatrack on 2008-10-27
Hi All !

The saga of the dual monitors continues ...

Following on from the helpful advice I have so far received, I have been onto the forum [https://help.ubuntu.com/community/Video](https://help.ubuntu.com/community/Video) and read all the stuff there. I think I've understood it and incorporated the information into the new xorg.conf file set out below. I've actually produced and tested two versions using the strings "ati" and "fglrx" to describe the drivers for the Radeon card.

Both versions fail to set up the monitors correctly and crash out into low-res mode. However, I have the impression that this is happening slightly later in the boot process ... rather as though the boot fails at the last moment.

Following on from Nick's suggestion, I have checked the log file ( /var/log/Xorg.0.log) after the last failure. The occurred when I was using the version of xorg.conf set out below and I can only find one error message:-

(EE) intel(0): [dri] I830CheckDRIAvailable failed because of a version mismatch.
[dri] libDRI version is 5.0.0 but version 5.4.x is needed.
[dri] Disabling DRI.

I have had a look on this forum for references to "DRI" but I'm not at all sure that I understand what I am reading so once again, I shall be very grateful to receive any suggestions that readers can offer.

Thanks in advance and my best regards to all ...


Latest copy of xorg.conf appended ---

#  xorg.conf to drive twin monitors -- Created 27.10.2008/2000

# For Ubuntu Ver: 8.04, running on Dell GX-520: IGb RAM.
# Main monitor - TFL 19" connected to Intel 82945G on motherboard
# Second monitor - 17" CRT connected to Radeon 7000-series grahics card in PCI slot

# Ver No.2 -- strng "fglrx" replaces "ati" as device driver for 2nd monitor


# Standard info ---
Section "InputDevice"
	Identifier		"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
EndSection

Section "InputDevice"
	Identifier		"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

# Identifying & setting up dual monitors
Section "Device"
	Identifier		"Main Monitor"
	Driver		"Intel 82945G/GZ"
	BusID		"PCI: 0:2:0
EndSection

Section "Device"
	Identifier		"Second Monitor"
	Driver		"fglrx"
	BusID		"PCI:0:2:1
EndSection
# Note that cmd "lspci -b" returns BusID values in hex --- these must be converted to denary notation, as above


Section "Monitor"
	Identifier		"Main Monitor"
	Option 		"DPMS"
	HorizSync	28-80
	VertRefresh	43-75
EndSection

Section "Monitor"
	Identifier		"Second Monitor"
	Option 		"DPMS"
	HorizSync	28-80
	VertRefresh	43-75
EndSection

# Info for Main monitor
Section "Screen"
	Identifier 	"Default Screen"
	Monitor		"Main Monitor"
	Device		"Intel 82945G/GZ"
	DefaultDepth	24

		SubSection "Display"	
			Depth	24
			Modes	"1152x864","1024x768"
		End Subsection
EndSection

# Info for Second monitor
Section "Screen"
	Identifier		"Second Screen"
	Monitor		"Second Monitor"
	Device		"fglrx"
	DefaultDepth	24
	
		SubSection "Display"	
			Depth	24
			Modes	"1152x864", "1024x768"
	End Subsection
EndSection

# Additional info --
Section "ServerFlags"
	Option "Xinerama" "true"
EndSection

# Specify position of two monitors relative to each other
Section "ServerLayout"
	Identifier		"Twin Head"
	Screen		"Default Screen"
	Screen		"Second Screen" LeftOf  "Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

---

### Post by nick_h on 2008-10-29
The driver line for your intel card still looks wrong. Your indeftifiers are also the same for the monitors as the drivers which may be a little confusing. Try:
```

Section "Device"
Identifier "Intel 82945G"
Driver "intel"
BusID "PCI: 0:2:0
EndSection

Section "Device"
Identifier "Radeon 7000"
Driver "fglrx"
BusID "PCI:0:2:1
EndSection

```

The monitor sections look OK.

The device and monitor lines in the screen section should then be made to match the identifiers in the ealier device and monitor sections.

```

# Info for Main screen
Section "Screen"
Identifier "Default Screen"
Monitor "Main Monitor"
Device "Intel 82945G"
DefaultDepth 24

SubSection "Display"
Depth 24
Modes "1152x864","1024x768"
End Subsection
EndSection

# Info for Second screen
Section "Screen"
Identifier "Second Screen"
Monitor "Second Monitor"
Device "Radeon 7000"
DefaultDepth 24

SubSection "Display"
Depth 24
Modes "1152x864", "1024x768"
End Subsection
EndSection

```

You can also look in the same log file to check what drivers are being used and what the system is detecting automatically.

---

### Post by hatrack on 2008-10-29
Hi Nick !

Thank you very much for your further efforts in trying to deal with my problem.

I have most carefully incorporated the changes that you suggest into a new version of xorg.conf but, I am sorry to report that the system again crashes out into Low-res mode on a single monitor.

Whilst there (and before resetting back to the original file) I captured the log file into a text editor and have spent some time looking at this ... all 1700+ lines !

The system is correctly seeing both chip-sets (on the motherboard and the Radeon card) and is recognizing the "Monitor" commands. However, it is insisting on defaulting to the 800x600 resolution. There are no errors reported.

I think that we are being forced to the conclusion that Ubuntu 8.04 just wont see and set up a dual-monitor system using this particular Radeon card. After all, it is now over four years old and is officially obsolete so far as ATI are concerned. This view is supported by the fact that I have a dual-boot system with Win XP in my other partition.  In this environment, the two monitors are set up perfectly but ... Win XP is an older Op Sys,  was that for which the card was designed and, was current when the card was manufactured.

Naturally, I am disappointed for I wanted to go over to Ubuntu 100% but I think we must accept the realities of the situation. I DO have a perfectly viable environment in which to do my photo-processing. By simply re-booting, I can use Ubuntu for all my other tasks and also enjoy the enhanced security aspects of a "proper" Op Sys !

I repeat my thanks to you for all the time and effort you have expended on my behalf and regret that in the end, they have come to naught. 

Very best regards

---

### Post by nick_h on 2008-10-29
> I think that we are being forced to the conclusion that Ubuntu 8.04 just wont see and set up a dual-monitor system using this particular Radeon card. After all, it is now over four years old and is officially obsolete so far as ATI are concerned.
I run a dual monitor system on a 5 year-old laptop.  Linux is normally very good at supporting old hardware.

> Whilst there (and before resetting back to the original file) I captured the log file into a text editor and have spent some time looking at this ... all 1700+ lines !
Mine is only 530 lines but I only have one video card.  You probably aren't getting any errors because the system can find a working configuration.  There may be useful information in the warnings though.  If you post your log file I'll have a look at it for you.  You should enclose it in CODE tags though.

---

### Post by tuxxy on 2008-10-29
I know this isnt a solution to the problem but if you could upgrade to an nVidia card with dual DVI out, this process would take only a couple of minutes making use of the **nvidia-settings** package, which provides a graphical display of your twin setup and allows you position them amongst other options.

---

### Post by nick_h on 2008-10-29
> I know this isnt a solution to the problem but if you could upgrade to an nVidia card with dual DVI out, this process would take only a couple of minutes making use of the nvidia-settings package
Yes, I have an nVidia card and setting up twinview is very easy.

I still think that it should be possible with a Radeon 7000 though with the xinerama approach.

---

### Post by hatrack on 2008-10-29
My thanks to both of you ...

In reply to your suggestion Nick ... I've searched all over these forums but I'm blowed if I can find how to format the information you need between "Code" tags.  I guess it's something to do with HTML but I've never studied this and haven't a clue how to do as you ask.

Since you have raised the matter, I guess it's important that I mark the info properly so I am holding up posting until I get some guidance.

I've cut out what I assume is irrelevant material ("Mode" lines for example). If you want these, I can put them back but this'll then be a very big file ... is it OK to send something like 1700 lines to this this Forum ... the cut-down version is about 200 lines ?

I'll discuss the nVidia a bit later on if I may.

Regards to all ...

---

### Post by nick_h on 2008-10-30
> In reply to your suggestion Nick ... I've searched all over these forums but I'm blowed if I can find how to format the information you need between "Code" tags. I guess it's something to do with HTML but I've never studied this and haven't a clue how to do as you ask.
Sorry, I forgot that you were a newbie.  You can find details on how to use the code tags [here](http://ubuntuforums.org/misc.php?do=bbcode#code).  You can write them in yourself or use the "#" button in the advanced posting screen.  Your log file will then be placed in a scrollable box with an easy to read monospace font.

> Since you have raised the matter, I guess it's important that I mark the info properly so I am holding up posting until I get some guidance.
It just makes it easier for people to read.  It is always a good idea to ask if you are unsure though.

> I've cut out what I assume is irrelevant material ("Mode" lines for example). If you want these, I can put them back but this'll then be a very big file ... is it OK to send something like 1700 lines to this this Forum ... the cut-down version is about 200 lines ?
As far as the file size is concerned I think you should be OK.  The limit on file attachments, for example, is about 1M for images and I expect that your file will only be about 100K.

It is quite common for people to post long log files, but it can also be useful to cut out long reprtative sections.

---

### Post by peakshysteria on 2008-10-30
Migh be stupid, but I would concentrate on getting the driver to work and then try to give dual monitor a shot. Have you looked at: [Ubuntu Hardy Installation Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide")? [**Method 2: Manual Install Method**]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Install_Method") is the approach that seems to work for most people (including myself).

And check out: [Will It Work On Your Card?]("https://help.ubuntu.com/community/RadeonDriver") (dual monitor)
And most important: [*BinaryDriverHowto* ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")(but i guess you've been there already)

Happy hunting

---

### Post by hatrack on 2008-10-30
G'day Nick !

I'm learning something new everyday ! ... although  things don't always work for me as the "literature" says they should. :(

The following is the log file cut down to a reasonable size. I have the original saved and I've marked my deletions very clearly so, if you should perhaps need some additional info later, I can supply this extra bit without undue hassle.

I have been thinking about the suggestion to up-grade to a double-head nVidia card and this is a possibility I can explore, if necessary. The point that I am trying to make here is that I am very much aware of the scale of your efforts on my behalf so far and I don't wish to impose upon your kindness. If up-grading really is the better route to a solution, please let me know and I can see what's involved.

Rgds for now ...
Eric.


Edited copy of log file ---
```

This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at http://bugs.freedesktop.org/.
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See http://wiki.x.org/wiki/GitPage for git access instructions.

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9.2)
Current Operating System: Linux beric 2.6.24-21-generic #1 SMP Tue Oct 21 23:43:45 UTC 2008 i686
Build Date: 13 June 2008  01:08:21AM
 
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Oct 29 19:34:21 2008
(==) Using config file: "/etc/X11/xorg.conf.failsafe"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.
(==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(==) |-->Input Device "Configured Mouse"
(==) |-->Input Device "Generic Keyboard"
(==) The core pointer device wasn't specified explicitly in the layout.
    Using the first mouse device.
(==) The core keyboard device wasn't specified explicitly in the layout.
    Using the first keyboard device.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81dc500
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.3
    X.Org Video Driver: 2.0
    X.Org XInput driver : 2.0
    X.Org Server Extension : 0.3
    X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 1.0.0
    ABI class: X.Org Video Driver, version 2.0
(++) using VT number 9

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,2770 card 1028,01ad rev 02 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,2771 card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:02:0: chip 8086,2772 card 1028,01ad rev 02 class 03,00,00 hdr 80
(II) PCI: 00:02:1: chip 8086,2776 card 1028,01ad rev 02 class 03,80,00 hdr 80
(II) PCI: 00:1c:0: chip 8086,27d0 card 0000,0000 rev 01 class 06,04,00 hdr 81
(II) PCI: 00:1c:1: chip 8086,27d2 card 0000,0000 rev 01 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,27c8 card 1028,01ad rev 01 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,27c9 card 1028,01ad rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,27ca card 1028,01ad rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,27cb card 1028,01ad rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,27cc card 1028,01ad rev 01 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev e1 class 06,04,01 hdr 81
(II) PCI: 00:1e:2: chip 8086,27de card 1028,01ad rev 01 class 04,01,00 hdr 00
(II) PCI: 00:1f:0: chip 8086,27b8 card 0000,0000 rev 01 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,27df card 1028,01ad rev 01 class 01,01,8a hdr 00
(II) PCI: 00:1f:2: chip 8086,27c0 card 1028,01ad rev 01 class 01,01,8f hdr 00
(II) PCI: 00:1f:3: chip 8086,27da card 1028,01ad rev 01 class 0c,05,00 hdr 00
(II) PCI: 02:00:0: chip 14e4,1677 card 1028,01ad rev 01 class 02,00,00 hdr 00
(II) PCI: 04:00:0: chip 1002,5159 card 174b,7c02 rev 00 class 03,00,00 hdr 00
(II) PCI: 04:02:0: chip 1106,3038 card 0925,1234 rev 50 class 0c,03,00 hdr 80
(II) PCI: 04:02:1: chip 1106,3038 card 0925,1234 rev 50 class 0c,03,00 hdr 80
(II) PCI: 04:02:2: chip 1106,3104 card 0925,1234 rev 51 class 0c,03,20 hdr 80
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,4), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
    [0] -1    0    0x00000000 - 0x0000ffff (0x10000) IX[b]
(II) Bus 0 non-prefetchable memory range:
    [0] -1    0    0x00000000 - 0xffffffff (0x0) MX[b]
(II) Bus 0 prefetchable memory range:
    [0] -1    0    0x00000000 - 0xffffffff (0x0) MX[b]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 1 non-prefetchable memory range:
    [0] -1    0    0xfe900000 - 0xfe9fffff (0x100000) MX[b]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:28:0), (0,2,2), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 2 non-prefetchable memory range:
    [0] -1    0    0xfe800000 - 0xfe8fffff (0x100000) MX[b]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:28:1), (0,3,3), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 3 non-prefetchable memory range:
    [0] -1    0    0xfe700000 - 0xfe7fffff (0x100000) MX[b]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:30:0), (0,4,4), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 4 I/O range:
    [0] -1    0    0x0000d000 - 0x0000dfff (0x1000) IX[b]
(II) Bus 4 non-prefetchable memory range:
    [0] -1    0    0xfe500000 - 0xfe6fffff (0x200000) MX[b]
(II) Bus 4 prefetchable memory range:
    [0] -1    0    0xf0000000 - 0xf7ffffff (0x8000000) MX[b]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(0:2:0) Intel Corporation 82945G/GZ Integrated Graphics Controller rev 2, Mem @ 0xfeb00000/19, 0xe0000000/28, 0xfeac0000/18, I/O @ 0xe898/3
(--) PCI: (0:2:1) Intel Corporation 82945G/GZ Integrated Graphics Controller rev 2, Mem @ 0xfeb80000/19
(--) PCI: (4:0:0) ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE] rev 0, Mem @ 0xf0000000/27, 0xfe5f0000/16, I/O @ 0xdc00/8, BIOS @ 0xfe600000/17
(II) Addressable bus resource ranges are
                    DELETED
(II) OS-reported resource ranges:
                    DELETED
(II) Active PCI resource ranges:
                    DELETED
(II) Inactive PCI resource ranges:
                    DELETED
(II) Active PCI resource ranges after removing overlaps:
                    DELETED
(II) Inactive PCI resource ranges after removing overlaps:
                    DELETED
(II) OS-reported resource ranges after removing overlaps with PCI:
                    DELETED
(II) All system resource ranges:
                    DELETED
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 1.0.0
    ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
    compiled for 1.4.0.90, module version = 2.1.0
    Module class: X.Org Font Renderer
    ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 7.1.0, module version = 1.0.0
    ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers//vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 1.3.0
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 2.0
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
    compiled for 1.4.0, module version = 1.2.3
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
    compiled for 1.4.0, module version = 1.2.2
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 2.0
(II) VESA: driver for VESA chipsets: vesa
(II) Primary Device is: PCI 00:02:0
(--) Assigning device section with no busID to primary device
(WW) VESA: No matching Device section for instance (BusID PCI:4:0:0) found
(--) Chipset vesa found
(II) resource ranges after xf86ClaimFixedResources() call:
                    DELETED
(II) resource ranges after probing:
                    DELETED
(II) Setting vga for screen 0.
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 1.1.0
    ABI class: X.Org Video Driver, version 2.0
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 1.0.0
    ABI class: X.Org Video Driver, version 2.0
(II) VESA(0): initializing int10
(WW) VESA(0): Bad V_BIOS checksum
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 7872 kB
(II) VESA(0): VESA VBE OEM: Intel(r)Lakeport-G Graphics Chip Accelerated VGA BIOS
(II) VESA(0): VESA VBE OEM Software Rev: 1.0
(II) VESA(0): VESA VBE OEM Vendor: Intel Corporation
(II) VESA(0): VESA VBE OEM Product: Intel(r)Lakeport-G Graphics Controller
(II) VESA(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(==) VESA(0): Depth 16, (--) framebuffer bpp 16
(==) VESA(0): RGB weight 565
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) VESA(0): VESA VBE DDC supported
(II) VESA(0): VESA VBE DDC Level none
(II) VESA(0): VESA VBE DDC transfer in appr. 0 sec.
(II) VESA(0): VESA VBE DDC read failed
(II) VESA(0): Searching for matching VESA mode(s):
Mode: 160 (0x0)
                    DELETED    
Mode: 161 (0x0)
                    DELETED    
Mode: 162 (0x0)
                    DELETED    
Mode: 163 (0x0)
                    DELETED
Mode: 164 (0x0)
                    DELETED    
Mode: 165 (0x0)
                    DELETED    
Mode: 166 (0x0)
                    DELETED    
Mode: 167 (0x0)
                    DELETED    
Mode: 168 (0x0)
                    DELETED    
Mode: 13c (0x0)
                    DELETED
Mode: 14d (0x0)
                    DELETED    
Mode: 15c (0x0)
                    DELETED    
Mode: 13a (1600x1200)
                    DELETED    
*Mode: 14b (1600x1200)
                    DELETED
Mode: 15a (1600x1200)
                    DELETED
Mode: 107 (1280x1024)
                    DELETED    
*Mode: 11a (1280x1024)
                    DELETED    
Mode: 11b (1280x1024)
                    DELETED
Mode: 105 (1024x768)
                    DELETED
*Mode: 117 (1024x768)
                    DELETED    
Mode: 118 (1024x768)
                    DELETED    
Mode: 112 (640x480)
                    DELETED    
*Mode: 114 (800x600)
                    DELETED    
Mode: 115 (800x600)
                    DELETED    
Mode: 101 (640x480)
                    DELETED    
Mode: 103 (800x600)
                    DELETED    
*Mode: 111 (640x480)
                    DELETED    
(II) VESA(0): Total Memory: 123 64KB banks (7872kB)
(II) VESA(0): Configured Monitor: Using default hsync range of 31.50-37.90 kHz
(II) VESA(0): Configured Monitor: Using default vrefresh range of 50.00-70.00 Hz
(II) VESA(0): Not using built-in mode "1600x1200" (width too large for virtual size)
(II) VESA(0): Not using built-in mode "1280x1024" (width too large for virtual size)
(II) VESA(0): Not using built-in mode "1024x768" (width too large for virtual size)
(--) VESA(0): Virtual size is 800x600 (pitch 800)
(**) VESA(0): *Built-in mode "800x600"
(**) VESA(0):  Built-in mode "640x480"
(==) VESA(0): DPI set to (96, 96)
(II) VESA(0): Attempting to use 60Hz refresh for mode "800x600" (114)
(II) VESA(0): Attempting to use 60Hz refresh for mode "640x480" (111)
(**) VESA(0): Using "Shadow Framebuffer"
(II) Loading sub module "shadow"
(II) LoadModule: "shadow"
(II) Loading /usr/lib/xorg/modules//libshadow.so
(II) Module shadow: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 1.1.0
    ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.3
(II) do I need RAC?  No, I don't.

(II) resource ranges after preInit:
                    DELETED

(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) VESA(0): initializing int10
(WW) VESA(0): Bad V_BIOS checksum
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 7872 kB
(II) VESA(0): VESA VBE OEM: Intel(r)Lakeport-G Graphics Chip Accelerated VGA BIOS
(II) VESA(0): VESA VBE OEM Software Rev: 1.0
(II) VESA(0): VESA VBE OEM Vendor: Intel Corporation
(II) VESA(0): VESA VBE OEM Product: Intel(r)Lakeport-G Graphics Controller
(II) VESA(0): VESA VBE OEM Product Rev: Hardware Version 0.0
(II) VESA(0): Splitting WC range: base: 0xe0000000, size: 0x7b0000
(II) VESA(0): Splitting WC range: base: 0xe0400000, size: 0x3b0000
(II) VESA(0): Splitting WC range: base: 0xe0600000, size: 0x1b0000
(II) VESA(0): Splitting WC range: base: 0xe0700000, size: 0xb0000
(II) VESA(0): Splitting WC range: base: 0xe0780000, size: 0x30000
(==) VESA(0): Write-combining range (0xe07a0000,0x10000)
(==) VESA(0): Write-combining range (0xe0780000,0x30000)
(==) VESA(0): Write-combining range (0xe0700000,0xb0000)
(==) VESA(0): Write-combining range (0xe0600000,0x1b0000)
(==) VESA(0): Write-combining range (0xe0400000,0x3b0000)
(WW) VESA(0): Failed to set up write-combining range (0xe0000000,0x7b0000)
(II) VESA(0): virtual address = 0xb7214000,
    physical address = 0xe0000000, size = 8060928
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Backing store disabled
(II) VESA(0): DPMS enabled
(==) RandR enabled
(II) Setting vga for screen 0.
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) AIGLX: Screen 0 is not DRI capable
(II) Loading sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 1.0.0
    ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
(WW) Configured Mouse: No Device specified, looking for one...
(II) Configured Mouse: Setting Device option to "/dev/input/mice"
(--) Configured Mouse: Device: "/dev/input/mice"
(==) Configured Mouse: Protocol: "Auto"
(**) Option "CorePointer"
(**) Configured Mouse: always reports core events
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(**) Option "CoreKeyboard"
(**) Generic Keyboard: always reports core events
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(--) Configured Mouse: PnP-detected protocol: "ExplorerPS/2"
(II) Configured Mouse: ps2EnableDataReporting: succeeded

```

---

### Post by hatrack on 2008-10-30
To "peakhysteria"

G'day and thanks for your suggestions.

I think (with all respect) that perhaps you may have misunderstood the situation I am trying to solve with Nick's help ?

I have a dual-boot system (Win XP/Ubuntu) and I get a dual-monitor configuration under Win XP without problems. I have also previously plugged my main monitor into the Radeon card and this works just fine ... in fact, during earlier experiments, the system would default to the monitor connected to this card, rather than use the graphics chip on the motherboard. I think this demonstrates that the system can handle the Radeon card but ... for some silly reason we can't explain ... it wont set up dual-monitor mode.

With that said, I had not seen the URLs you posted so I shall go and have a look at these.

I thank you very much for posting on this matter ... this is a big help to a newbie like myself and I assure you that it is very much appreciated.

Best regards ...

---

### Post by peakshysteria on 2008-10-30
[https://support.ati.com/ics/support/KBAnswer.asp?questionID=1105](https://support.ati.com/ics/support/KBAnswer.asp?questionID=1105)

---

### Post by nick_h on 2008-10-30
This log file has been generated from a failsafe configuration, not the one that you posted.  You can see this from the following lines:
```
(==) Using config file: "/etc/X11/xorg.conf.failsafe"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"

```
I would expect to see the file /etc/X11/xorg.conf and the identifiers for the devices and monitors that you defined.

The next interesting bit is the PCI probe.  Both of the video cards are detected.
```
(--) PCI:*(0:2:0) Intel Corporation 82945G/GZ Integrated Graphics Controller rev 2, Mem @ 0xfeb00000/19, 0xe0000000/28, 0xfeac0000/18, I/O @ 0xe898/3
(--) PCI: (0:2:1) Intel Corporation 82945G/GZ Integrated Graphics Controller rev 2, Mem @ 0xfeb80000/19
(--) PCI: (4:0:0) ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE] rev 0, Mem @ 0xf0000000/27, 0xfe5f0000/16, I/O @ 0xdc00/8, BIOS @ 0xfe600000/17

```

The section where the driver is assigned uses the VESA driver as a failsafe driver.  The primary device is your Intel card and in the failsafe configuration there is no busID specified.  The primary device gets assigned a VESA driver and a warning is given that the Radeon card has no device section (and hence will be ignored).
```
(II) VESA: driver for VESA chipsets: vesa
(II) Primary Device is: PCI 00:02:0
(--) Assigning device section with no busID to primary device
(WW) VESA: No matching Device section for instance (BusID PCI:4:0:0) found
(--) Chipset vesa found

```

Have a look in your /var/log directory to see if there any other log files that were generated from the /etc/X11/xorg.conf configuration file.

Try:
```
ls -al /var/log/X*
```

EDIT: Check the BusID you specified for the Radeon card.

---

### Post by hatrack on 2008-10-30
Thanks Nick !

I'm just on my way to eat dinner right now but I'll look into the points you raise and hopefully will be able to post a proper reply within an hour or so ...

Cheers !

---

### Post by hatrack on 2008-10-30
OK ... back again after more experiments ...

Before I report on these, however, I'll deal with a couple of points from your post --

You say "This log file has been generated from a failsafe configuration, not the one that you posted. You can see this from the following lines"

This was the log file that was available to me immediately after the boot, when the system had set up low-res mode. I have had another look at the log files but, so far as I can see, a new one is produced at each boot. So ... the file I sent reflects what the system actually did, rather than what we wanted it to do !  I've had a look in the /var/logs dir and there are indeed several log files there with extra characters appended to their names, suggesting to me that these are previously-created versions. If you can please tell me what to look for, I can send any of these to you.

As to the matter of the BusID being wrong, I don't know how I missed this ... perhaps a case of seeing what you expect to see, rather than what is there ? ... Sorry !

Anyway ... moving on ...

The BusID was the easiest thing to change first so that is where I started my experiments this evening. I corrected the info in xorg.conf but, when I re-booted, the system again just failed into the low-res mode. So ... this alone is clearly not the cause of the problem.

I was interested in your comment that after the pci probe; the system shows two addresses being used for the controller on the mother-board (0:2:0 and 0:2:1) with the Radeon card on 4:0:0. This observation lead me to think back over what has been done during the two weeks or so that I have been messing with this problem.

When I first got this computer, it had one monitor (connected to the Intel 82945G chip). This ran both Win XP and Ubuntu without problems. I then added the old Radeon 7000 card and connected my CRT monotor to this. This set-up also ran Win XP without problems and (using the Win procedure) I created a dual-monotor configuration. The monitor on the Intel controller remained the primary display and my CRT became the secondary one. So far so good.

When, however, I booted into Ubuntu [a] there was only one monitor and [b] the display was on the CRT screen ... the system was defaulting to the Radeon card. I frigged around with this for a while and then thought to look at the BIOS settings.

These offer "Primary Video" and "Memory" sections only. In the Primary Monitor section, there are the options of selecting either "Auto" (which is the factory default) and "PEG/Onboard". The text explains that this later choice selects which video controller will become the primary one when two controllers are available.

Since I now had two controllers, I selected "PEG". Now, my TFL monitor on the on-board chip became the primary display in both Win XP and Ubuntu with a dual display under Win XP but ... I only had one display under Ubuntu (albeit now on the right monitor ! ). All the subsequent testing has been done with the "PEG" BIOS setting selected.

However ... thinking about the duplicated BiosID for the Intel chip, I came to wondering if this was being provoked by my chice of BIOS setting. So ...  I have tried using both "Auto" and "PEG" BIOS settings with both the latest version of xorg.conf (BiosID set to 4:0:0 for the Radeon card) and with the original simple xorg.conf file generated during the original installation of Ubuntu.

I am sorry to report that only the simple *.conf gives a workable system with correct resolution and dual monitors under Win XP ... and correctly-selected single monitor under Ubuntu using the "PEG" choice in the BIOS settings.

So ... that is the situation ... seemingly not one step nearer finding a solution.

I am getting embarrassed about all this effort on your part so I'm simply going to shut up for tonight !

Best Regards ...

---

### Post by nick_h on 2008-10-31
> This was the log file that was available to me immediately after the boot, when the system had set up low-res mode. I have had another look at the log files but, so far as I can see, a new one is produced at each boot.
What I think is happening is that when the Gnome Display Manager (gdm) detects that the X server has failed to start it runs a failsafe configuration.  I found a link about [BulletProofX](https://wiki.ubuntu.com/BulletProofX) with some information.  What then happens is that the log from the failsafe configuration gets written where we expect to find the log from the failed session.

The original log may be just renamed.  You should look for any Xorg log file that uses the /etc/X11/xorg.conf file and not the failsafe version.  A quick way to do this is to use *grep* to search the files:
```
grep "Using config file" /var/log/X*
```

If you can't find one then you could try stopping gdm and then starting X with the *startx* command.  Switch to a virtual terminal using Ctl-Alt-F1 and stop gdm with:
```
sudo /etc/init.d/gdm stop
```

Then you can try to start X with:
```
startx
```
but prepare for it to fail - and create a log file which you can look at (and copy).

Finally you can restart gdm with the following:
```
sudo /etc/init.d/gdm start
```

> I am getting embarrassed about all this effort on your part so I'm simply going to shut up for tonight !
People on these forums help because they want to.  I find that it is also a useful way to learn a little more about the system myself.  Keep asking the questions; there are plenty of forum users who are willing to help.

---

### Post by hatrack on 2008-10-31
Hi Nick !

Thank you for your helpful and encouraging post !

I'll try the ideas you suggest and post again as soon as I have the results ... probably late tonight or tomorrow AM.

Rgds,
Eric

---

### Post by hatrack on 2008-10-31
Hi Nick !

Following on from your earlier post, I have searched in /var/log and found a copy of Xorg.0.log with the extension "old" which I submit below --

```

This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at http://bugs.freedesktop.org/.
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See http://wiki.x.org/wiki/GitPage for git access instructions.

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9.2)
Current Operating System: Linux beric 2.6.24-21-generic #1 SMP Tue Oct 21 23:43:45 UTC 2008 i686
Build Date: 13 June 2008  01:08:21AM
 
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Oct 31 21:08:44 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.
(==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(==) |-->Input Device "Configured Mouse"
(==) |-->Input Device "Generic Keyboard"
(==) The core pointer device wasn't specified explicitly in the layout.
    Using the first core pointer device.
(==) The core keyboard device wasn't specified explicitly in the layout.
    Using the first keyboard device.
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81dc500
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.3
    X.Org Video Driver: 2.0
    X.Org XInput driver : 2.0
    X.Org Server Extension : 0.3
    X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 1.0.0
    ABI class: X.Org Video Driver, version 2.0
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,2770 card 1028,01ad rev 02 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,2771 card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:02:0: chip 8086,2772 card 1028,01ad rev 02 class 03,00,00 hdr 80
(II) PCI: 00:02:1: chip 8086,2776 card 1028,01ad rev 02 class 03,80,00 hdr 80
(II) PCI: 00:1c:0: chip 8086,27d0 card 0000,0000 rev 01 class 06,04,00 hdr 81
(II) PCI: 00:1c:1: chip 8086,27d2 card 0000,0000 rev 01 class 06,04,00 hdr 81
(II) PCI: 00:1d:0: chip 8086,27c8 card 1028,01ad rev 01 class 0c,03,00 hdr 80
(II) PCI: 00:1d:1: chip 8086,27c9 card 1028,01ad rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:2: chip 8086,27ca card 1028,01ad rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:3: chip 8086,27cb card 1028,01ad rev 01 class 0c,03,00 hdr 00
(II) PCI: 00:1d:7: chip 8086,27cc card 1028,01ad rev 01 class 0c,03,20 hdr 00
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev e1 class 06,04,01 hdr 81
(II) PCI: 00:1e:2: chip 8086,27de card 1028,01ad rev 01 class 04,01,00 hdr 00
(II) PCI: 00:1f:0: chip 8086,27b8 card 0000,0000 rev 01 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,27df card 1028,01ad rev 01 class 01,01,8a hdr 00
(II) PCI: 00:1f:2: chip 8086,27c0 card 1028,01ad rev 01 class 01,01,8f hdr 00
(II) PCI: 00:1f:3: chip 8086,27da card 1028,01ad rev 01 class 0c,05,00 hdr 00
(II) PCI: 02:00:0: chip 14e4,1677 card 1028,01ad rev 01 class 02,00,00 hdr 00
(II) PCI: 04:00:0: chip 1002,5159 card 174b,7c02 rev 00 class 03,00,00 hdr 00
(II) PCI: 04:02:0: chip 1106,3038 card 0925,1234 rev 50 class 0c,03,00 hdr 80
(II) PCI: 04:02:1: chip 1106,3038 card 0925,1234 rev 50 class 0c,03,00 hdr 80
(II) PCI: 04:02:2: chip 1106,3104 card 0925,1234 rev 51 class 0c,03,20 hdr 80
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,4), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
    [0] -1    0    0x00000000 - 0x0000ffff (0x10000) IX[b]
(II) Bus 0 non-prefetchable memory range:
    [0] -1    0    0x00000000 - 0xffffffff (0x0) MX[b]
(II) Bus 0 prefetchable memory range:
    [0] -1    0    0x00000000 - 0xffffffff (0x0) MX[b]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 1 non-prefetchable memory range:
    [0] -1    0    0xfe900000 - 0xfe9fffff (0x100000) MX[b]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:28:0), (0,2,2), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 2 non-prefetchable memory range:
    [0] -1    0    0xfe800000 - 0xfe8fffff (0x100000) MX[b]
(II) PCI-to-PCI bridge:
(II) Bus 3: bridge is at (0:28:1), (0,3,3), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 3 non-prefetchable memory range:
    [0] -1    0    0xfe700000 - 0xfe7fffff (0x100000) MX[b]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 4: bridge is at (0:30:0), (0,4,4), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 4 I/O range:
    [0] -1    0    0x0000d000 - 0x0000dfff (0x1000) IX[b]
(II) Bus 4 non-prefetchable memory range:
    [0] -1    0    0xfe500000 - 0xfe6fffff (0x200000) MX[b]
(II) Bus 4 prefetchable memory range:
    [0] -1    0    0xf0000000 - 0xf7ffffff (0x8000000) MX[b]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(0:2:0) Intel Corporation 82945G/GZ Integrated Graphics Controller rev 2, Mem @ 0xfeb00000/19, 0xe0000000/28, 0xfeac0000/18, I/O @ 0xe898/3
(--) PCI: (0:2:1) Intel Corporation 82945G/GZ Integrated Graphics Controller rev 2, Mem @ 0xfeb80000/19
(--) PCI: (4:0:0) ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE] rev 0, Mem @ 0xf0000000/27, 0xfe5f0000/16, I/O @ 0xdc00/8, BIOS @ 0xfe600000/17
(II) Addressable bus resource ranges are
    [0] -1    0    0x00000000 - 0xffffffff (0x0) MX[b]
    [1] -1    0    0x00000000 - 0x0000ffff (0x10000) IX[b]
(II) OS-reported resource ranges:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[b]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [5] -1    0    0x00000000 - 0x000000ff (0x100) IX[b]
(II) Active PCI resource ranges:
    [0] -1    0    0xfe5eff00 - 0xfe5effff (0x100) MX[b]
    [1] -1    0    0xfe8f0000 - 0xfe8fffff (0x10000) MX[b]
    [2] -1    0    0xfeabf900 - 0xfeabf9ff (0x100) MX[b]
    [3] -1    0    0xfeabfa00 - 0xfeabfbff (0x200) MX[b]
    [4] -1    0    0xffa80800 - 0xffa80bff (0x400) MX[b]
    [5] -1    0    0xfeb80000 - 0xfebfffff (0x80000) MX[b](B)
    [6] -1    0    0xfeac0000 - 0xfeafffff (0x40000) MX[b](B)
    [7] -1    0    0xe0000000 - 0xefffffff (0x10000000) MX[b](B)
    [8] -1    0    0xfeb00000 - 0xfeb7ffff (0x80000) MX[b](B)
    [9] -1    0    0x0000d8e0 - 0x0000d8ff (0x20) IX[b]
    [10] -1    0    0x0000d8c0 - 0x0000d8df (0x20) IX[b]
    [11] -1    0    0x0000e8a0 - 0x0000e8bf (0x20) IX[b]
    [12] -1    0    0x0000fea0 - 0x0000feaf (0x10) IX[b]
    [13] -1    0    0x0000fe30 - 0x0000fe33 (0x4) IX[b]
    [14] -1    0    0x0000fe20 - 0x0000fe27 (0x8) IX[b]
    [15] -1    0    0x0000fe10 - 0x0000fe13 (0x4) IX[b]
    [16] -1    0    0x0000fe00 - 0x0000fe07 (0x8) IX[b]
    [17] -1    0    0x0000ffa0 - 0x0000ffaf (0x10) IX[b]
    [18] -1    0    0x00000374 - 0x00000374 (0x1) IX[b]
    [19] -1    0    0x00000170 - 0x00000177 (0x8) IX[b]
    [20] -1    0    0x000003f4 - 0x000003f4 (0x1) IX[b]
    [21] -1    0    0x000001f0 - 0x000001f7 (0x8) IX[b]
    [22] -1    0    0x0000e8c0 - 0x0000e8ff (0x40) IX[b]
    [23] -1    0    0x0000ec00 - 0x0000ecff (0x100) IX[b]
    [24] -1    0    0x0000ff20 - 0x0000ff3f (0x20) IX[b]
    [25] -1    0    0x0000ff40 - 0x0000ff5f (0x20) IX[b]
    [26] -1    0    0x0000ff60 - 0x0000ff7f (0x20) IX[b]
    [27] -1    0    0x0000ff80 - 0x0000ff9f (0x20) IX[b]
    [28] -1    0    0x0000e898 - 0x0000e89f (0x8) IX[b](B)
(II) Inactive PCI resource ranges:
    [0] -1    0    0xfe500000 - 0xfe51ffff (0x20000) MX[b](B)
    [1] -1    0    0xfe5f0000 - 0xfe5fffff (0x10000) MX[b](B)
    [2] -1    0    0xf0000000 - 0xf7ffffff (0x8000000) MX[b](B)
    [3] -1    0    0x0000dc00 - 0x0000dcff (0x100) IX[b](B)
(II) Active PCI resource ranges after removing overlaps:
    [0] -1    0    0xfe5eff00 - 0xfe5effff (0x100) MX[b]
    [1] -1    0    0xfe8f0000 - 0xfe8fffff (0x10000) MX[b]
    [2] -1    0    0xfeabf900 - 0xfeabf9ff (0x100) MX[b]
    [3] -1    0    0xfeabfa00 - 0xfeabfbff (0x200) MX[b]
    [4] -1    0    0xffa80800 - 0xffa80bff (0x400) MX[b]
    [5] -1    0    0xfeb80000 - 0xfebfffff (0x80000) MX[b](B)
    [6] -1    0    0xfeac0000 - 0xfeafffff (0x40000) MX[b](B)
    [7] -1    0    0xe0000000 - 0xefffffff (0x10000000) MX[b](B)
    [8] -1    0    0xfeb00000 - 0xfeb7ffff (0x80000) MX[b](B)
    [9] -1    0    0x0000d8e0 - 0x0000d8ff (0x20) IX[b]
    [10] -1    0    0x0000d8c0 - 0x0000d8df (0x20) IX[b]
    [11] -1    0    0x0000e8a0 - 0x0000e8bf (0x20) IX[b]
    [12] -1    0    0x0000fea0 - 0x0000feaf (0x10) IX[b]
    [13] -1    0    0x0000fe30 - 0x0000fe33 (0x4) IX[b]
    [14] -1    0    0x0000fe20 - 0x0000fe27 (0x8) IX[b]
    [15] -1    0    0x0000fe10 - 0x0000fe13 (0x4) IX[b]
    [16] -1    0    0x0000fe00 - 0x0000fe07 (0x8) IX[b]
    [17] -1    0    0x0000ffa0 - 0x0000ffaf (0x10) IX[b]
    [18] -1    0    0x00000374 - 0x00000374 (0x1) IX[b]
    [19] -1    0    0x00000170 - 0x00000177 (0x8) IX[b]
    [20] -1    0    0x000003f4 - 0x000003f4 (0x1) IX[b]
    [21] -1    0    0x000001f0 - 0x000001f7 (0x8) IX[b]
    [22] -1    0    0x0000e8c0 - 0x0000e8ff (0x40) IX[b]
    [23] -1    0    0x0000ec00 - 0x0000ecff (0x100) IX[b]
    [24] -1    0    0x0000ff20 - 0x0000ff3f (0x20) IX[b]
    [25] -1    0    0x0000ff40 - 0x0000ff5f (0x20) IX[b]
    [26] -1    0    0x0000ff60 - 0x0000ff7f (0x20) IX[b]
    [27] -1    0    0x0000ff80 - 0x0000ff9f (0x20) IX[b]
    [28] -1    0    0x0000e898 - 0x0000e89f (0x8) IX[b](B)
(II) Inactive PCI resource ranges after removing overlaps:
    [0] -1    0    0xfe500000 - 0xfe51ffff (0x20000) MX[b](B)
    [1] -1    0    0xfe5f0000 - 0xfe5fffff (0x10000) MX[b](B)
    [2] -1    0    0xf0000000 - 0xf7ffffff (0x8000000) MX[b](B)
    [3] -1    0    0x0000dc00 - 0x0000dcff (0x100) IX[b](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[b]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [5] -1    0    0x00000000 - 0x000000ff (0x100) IX[b]
(II) All system resource ranges:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[b]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0xfe5eff00 - 0xfe5effff (0x100) MX[b]
    [5] -1    0    0xfe8f0000 - 0xfe8fffff (0x10000) MX[b]
    [6] -1    0    0xfeabf900 - 0xfeabf9ff (0x100) MX[b]
    [7] -1    0    0xfeabfa00 - 0xfeabfbff (0x200) MX[b]
    [8] -1    0    0xffa80800 - 0xffa80bff (0x400) MX[b]
    [9] -1    0    0xfeb80000 - 0xfebfffff (0x80000) MX[b](B)
    [10] -1    0    0xfeac0000 - 0xfeafffff (0x40000) MX[b](B)
    [11] -1    0    0xe0000000 - 0xefffffff (0x10000000) MX[b](B)
    [12] -1    0    0xfeb00000 - 0xfeb7ffff (0x80000) MX[b](B)
    [13] -1    0    0xfe500000 - 0xfe51ffff (0x20000) MX[b](B)
    [14] -1    0    0xfe5f0000 - 0xfe5fffff (0x10000) MX[b](B)
    [15] -1    0    0xf0000000 - 0xf7ffffff (0x8000000) MX[b](B)
    [16] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [17] -1    0    0x00000000 - 0x000000ff (0x100) IX[b]
    [18] -1    0    0x0000d8e0 - 0x0000d8ff (0x20) IX[b]
    [19] -1    0    0x0000d8c0 - 0x0000d8df (0x20) IX[b]
    [20] -1    0    0x0000e8a0 - 0x0000e8bf (0x20) IX[b]
    [21] -1    0    0x0000fea0 - 0x0000feaf (0x10) IX[b]
    [22] -1    0    0x0000fe30 - 0x0000fe33 (0x4) IX[b]
    [23] -1    0    0x0000fe20 - 0x0000fe27 (0x8) IX[b]
    [24] -1    0    0x0000fe10 - 0x0000fe13 (0x4) IX[b]
    [25] -1    0    0x0000fe00 - 0x0000fe07 (0x8) IX[b]
    [26] -1    0    0x0000ffa0 - 0x0000ffaf (0x10) IX[b]
    [27] -1    0    0x00000374 - 0x00000374 (0x1) IX[b]
    [28] -1    0    0x00000170 - 0x00000177 (0x8) IX[b]
    [29] -1    0    0x000003f4 - 0x000003f4 (0x1) IX[b]
    [30] -1    0    0x000001f0 - 0x000001f7 (0x8) IX[b]
    [31] -1    0    0x0000e8c0 - 0x0000e8ff (0x40) IX[b]
    [32] -1    0    0x0000ec00 - 0x0000ecff (0x100) IX[b]
    [33] -1    0    0x0000ff20 - 0x0000ff3f (0x20) IX[b]
    [34] -1    0    0x0000ff40 - 0x0000ff5f (0x20) IX[b]
    [35] -1    0    0x0000ff60 - 0x0000ff7f (0x20) IX[b]
    [36] -1    0    0x0000ff80 - 0x0000ff9f (0x20) IX[b]
    [37] -1    0    0x0000e898 - 0x0000e89f (0x8) IX[b](B)
    [38] -1    0    0x0000dc00 - 0x0000dcff (0x100) IX[b](B)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 1.0.0
    ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
    compiled for 1.4.0.90, module version = 2.1.0
    Module class: X.Org Font Renderer
    ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 7.1.0, module version = 1.0.0
    ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) Matched intel from file name intel.ids in autoconfig
(==) Matched intel for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 2.2.1
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 2.0
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
    compiled for 1.4.0, module version = 1.2.3
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 2.0
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
    compiled for 1.4.0, module version = 1.2.2
    Module class: X.Org XInput Driver
    ABI class: X.Org XInput driver, version 2.0
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, 965G, G35, 965Q, 946GZ,
    965GM, 965GME/GLE, G33, Q35, Q33, Intel Integrated Graphics Device
(II) Primary Device is: PCI 00:02:0
(--) Assigning device section with no busID to primary device
(WW) intel: No matching Device section for instance (BusID PCI:0:2:1) found
(--) Chipset 945G found
(II) resource ranges after xf86ClaimFixedResources() call:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[b]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0xfe5eff00 - 0xfe5effff (0x100) MX[b]
    [5] -1    0    0xfe8f0000 - 0xfe8fffff (0x10000) MX[b]
    [6] -1    0    0xfeabf900 - 0xfeabf9ff (0x100) MX[b]
    [7] -1    0    0xfeabfa00 - 0xfeabfbff (0x200) MX[b]
    [8] -1    0    0xffa80800 - 0xffa80bff (0x400) MX[b]
    [9] -1    0    0xfeb80000 - 0xfebfffff (0x80000) MX[b](B)
    [10] -1    0    0xfeac0000 - 0xfeafffff (0x40000) MX[b](B)
    [11] -1    0    0xe0000000 - 0xefffffff (0x10000000) MX[b](B)
    [12] -1    0    0xfeb00000 - 0xfeb7ffff (0x80000) MX[b](B)
    [13] -1    0    0xfe500000 - 0xfe51ffff (0x20000) MX[b](B)
    [14] -1    0    0xfe5f0000 - 0xfe5fffff (0x10000) MX[b](B)
    [15] -1    0    0xf0000000 - 0xf7ffffff (0x8000000) MX[b](B)
    [16] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [17] -1    0    0x00000000 - 0x000000ff (0x100) IX[b]
    [18] -1    0    0x0000d8e0 - 0x0000d8ff (0x20) IX[b]
    [19] -1    0    0x0000d8c0 - 0x0000d8df (0x20) IX[b]
    [20] -1    0    0x0000e8a0 - 0x0000e8bf (0x20) IX[b]
    [21] -1    0    0x0000fea0 - 0x0000feaf (0x10) IX[b]
    [22] -1    0    0x0000fe30 - 0x0000fe33 (0x4) IX[b]
    [23] -1    0    0x0000fe20 - 0x0000fe27 (0x8) IX[b]
    [24] -1    0    0x0000fe10 - 0x0000fe13 (0x4) IX[b]
    [25] -1    0    0x0000fe00 - 0x0000fe07 (0x8) IX[b]
    [26] -1    0    0x0000ffa0 - 0x0000ffaf (0x10) IX[b]
    [27] -1    0    0x00000374 - 0x00000374 (0x1) IX[b]
    [28] -1    0    0x00000170 - 0x00000177 (0x8) IX[b]
    [29] -1    0    0x000003f4 - 0x000003f4 (0x1) IX[b]
    [30] -1    0    0x000001f0 - 0x000001f7 (0x8) IX[b]
    [31] -1    0    0x0000e8c0 - 0x0000e8ff (0x40) IX[b]
    [32] -1    0    0x0000ec00 - 0x0000ecff (0x100) IX[b]
    [33] -1    0    0x0000ff20 - 0x0000ff3f (0x20) IX[b]
    [34] -1    0    0x0000ff40 - 0x0000ff5f (0x20) IX[b]
    [35] -1    0    0x0000ff60 - 0x0000ff7f (0x20) IX[b]
    [36] -1    0    0x0000ff80 - 0x0000ff9f (0x20) IX[b]
    [37] -1    0    0x0000e898 - 0x0000e89f (0x8) IX[b](B)
    [38] -1    0    0x0000dc00 - 0x0000dcff (0x100) IX[b](B)
(II) resource ranges after probing:
    [0] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[b]E(B)
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0xfe5eff00 - 0xfe5effff (0x100) MX[b]
    [5] -1    0    0xfe8f0000 - 0xfe8fffff (0x10000) MX[b]
    [6] -1    0    0xfeabf900 - 0xfeabf9ff (0x100) MX[b]
    [7] -1    0    0xfeabfa00 - 0xfeabfbff (0x200) MX[b]
    [8] -1    0    0xffa80800 - 0xffa80bff (0x400) MX[b]
    [9] -1    0    0xfeb80000 - 0xfebfffff (0x80000) MX[b](B)
    [10] -1    0    0xfeac0000 - 0xfeafffff (0x40000) MX[b](B)
    [11] -1    0    0xe0000000 - 0xefffffff (0x10000000) MX[b](B)
    [12] -1    0    0xfeb00000 - 0xfeb7ffff (0x80000) MX[b](B)
    [13] -1    0    0xfe500000 - 0xfe51ffff (0x20000) MX[b](B)
    [14] -1    0    0xfe5f0000 - 0xfe5fffff (0x10000) MX[b](B)
    [15] -1    0    0xf0000000 - 0xf7ffffff (0x8000000) MX[b](B)
    [16] 0    0    0x000a0000 - 0x000affff (0x10000) MS[b]
    [17] 0    0    0x000b0000 - 0x000b7fff (0x8000) MS[b]
    [18] 0    0    0x000b8000 - 0x000bffff (0x8000) MS[b]
    [19] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [20] -1    0    0x00000000 - 0x000000ff (0x100) IX[b]
    [21] -1    0    0x0000d8e0 - 0x0000d8ff (0x20) IX[b]
    [22] -1    0    0x0000d8c0 - 0x0000d8df (0x20) IX[b]
    [23] -1    0    0x0000e8a0 - 0x0000e8bf (0x20) IX[b]
    [24] -1    0    0x0000fea0 - 0x0000feaf (0x10) IX[b]
    [25] -1    0    0x0000fe30 - 0x0000fe33 (0x4) IX[b]
    [26] -1    0    0x0000fe20 - 0x0000fe27 (0x8) IX[b]
    [27] -1    0    0x0000fe10 - 0x0000fe13 (0x4) IX[b]
    [28] -1    0    0x0000fe00 - 0x0000fe07 (0x8) IX[b]
    [29] -1    0    0x0000ffa0 - 0x0000ffaf (0x10) IX[b]
    [30] -1    0    0x00000374 - 0x00000374 (0x1) IX[b]
    [31] -1    0    0x00000170 - 0x00000177 (0x8) IX[b]
    [32] -1    0    0x000003f4 - 0x000003f4 (0x1) IX[b]
    [33] -1    0    0x000001f0 - 0x000001f7 (0x8) IX[b]
    [34] -1    0    0x0000e8c0 - 0x0000e8ff (0x40) IX[b]
    [35] -1    0    0x0000ec00 - 0x0000ecff (0x100) IX[b]
    [36] -1    0    0x0000ff20 - 0x0000ff3f (0x20) IX[b]
    [37] -1    0    0x0000ff40 - 0x0000ff5f (0x20) IX[b]
    [38] -1    0    0x0000ff60 - 0x0000ff7f (0x20) IX[b]
    [39] -1    0    0x0000ff80 - 0x0000ff9f (0x20) IX[b]
    [40] -1    0    0x0000e898 - 0x0000e89f (0x8) IX[b](B)
    [41] -1    0    0x0000dc00 - 0x0000dcff (0x100) IX[b](B)
    [42] 0    0    0x000003b0 - 0x000003bb (0xc) IS[b]
    [43] 0    0    0x000003c0 - 0x000003df (0x20) IS[b]
(II) Setting vga for screen 0.
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 1.0.0
    ABI class: X.Org Video Driver, version 2.0
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 1.1.0
    ABI class: X.Org Video Driver, version 2.0
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 0.1.0
    ABI class: X.Org Video Driver, version 2.0
(II) intel(0): Creating default Display subsection in Screen section
    "Default Screen" for depth/fbbpp 24/32
(==) intel(0): Depth 24, (==) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) 945G
(--) intel(0): Chipset: "945G"
(--) intel(0): Linear framebuffer at 0xE0000000
(--) intel(0): IO registers at addr 0xFEB00000
(II) intel(0): 2 display pipes available.
(==) intel(0): Using EXA for acceleration
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"(II) Module "i2c" already built-in
(II) intel(0): Output VGA using monitor section Configured Monitor
(II) intel(0): I2C bus "CRTDDC_A" initialized.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOB" initialized.
(II) intel(0): I2C device "SDVOCTRL_E for SDVOB:SDVO Controller B" registered at address 0x70.
(II) intel(0): No SDVO device found on SDVOB
(II) intel(0): I2C device "SDVOCTRL_E for SDVOB:SDVO Controller B" removed.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOB" removed.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOC" initialized.
(II) intel(0): I2C device "SDVOCTRL_E for SDVOC:SDVO Controller C" registered at address 0x72.
(II) intel(0): No SDVO device found on SDVOC
(II) intel(0): I2C device "SDVOCTRL_E for SDVOC:SDVO Controller C" removed.
(II) intel(0): I2C bus "SDVOCTRL_E for SDVOC" removed.
(II) intel(0): I2C device "CRTDDC_A:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "CRTDDC_A:ddc2" removed.
(II) intel(0): Output VGA connected
(II) intel(0): Output VGA using initial mode 1280x768
(II) intel(0): detected 256 kB GTT.
(II) intel(0): detected 7932 kB stolen memory.
(==) intel(0): video overlay key set to 0x101fe
(==) intel(0): Will not try to enable page flipping
(==) intel(0): Triple buffering disabled
(==) intel(0): Using gamma correction (1.0, 1.0, 1.0)
(==) intel(0): DPI set to (96, 96)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "exa"
(II) LoadModule: "exa"
(II) Loading /usr/lib/xorg/modules//libexa.so
(II) Module exa: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 2.2.0
    ABI class: X.Org Video Driver, version 2.0
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module "ramdac" already built-in
(II) intel(0): Comparing regs from server start up to After PreInit
(WW) intel(0): Register 0x61114 (PORT_HOTPLUG_STAT) changed from 0x00000000 to 0x00000b00
(==) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
    [0] 0    0    0xfeac0000 - 0xfeafffff (0x40000) MS[b]
    [1] 0    0    0xe0000000 - 0xefffffff (0x10000000) MS[b]
    [2] 0    0    0xfeb00000 - 0xfeb7ffff (0x80000) MS[b]
    [3] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[b]E(B)
    [4] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [5] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [6] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [7] -1    0    0xfe5eff00 - 0xfe5effff (0x100) MX[b]
    [8] -1    0    0xfe8f0000 - 0xfe8fffff (0x10000) MX[b]
    [9] -1    0    0xfeabf900 - 0xfeabf9ff (0x100) MX[b]
    [10] -1    0    0xfeabfa00 - 0xfeabfbff (0x200) MX[b]
    [11] -1    0    0xffa80800 - 0xffa80bff (0x400) MX[b]
    [12] -1    0    0xfeb80000 - 0xfebfffff (0x80000) MX[b](B)
    [13] -1    0    0xfeac0000 - 0xfeafffff (0x40000) MX[b](B)
    [14] -1    0    0xe0000000 - 0xefffffff (0x10000000) MX[b](B)
    [15] -1    0    0xfeb00000 - 0xfeb7ffff (0x80000) MX[b](B)
    [16] -1    0    0xfe500000 - 0xfe51ffff (0x20000) MX[b](B)
    [17] -1    0    0xfe5f0000 - 0xfe5fffff (0x10000) MX[b](B)
    [18] -1    0    0xf0000000 - 0xf7ffffff (0x8000000) MX[b](B)
    [19] 0    0    0x000a0000 - 0x000affff (0x10000) MS[b](OprD)
    [20] 0    0    0x000b0000 - 0x000b7fff (0x8000) MS[b](OprD)
    [21] 0    0    0x000b8000 - 0x000bffff (0x8000) MS[b](OprD)
    [22] 0    0    0x0000e898 - 0x0000e89f (0x8) IS[b]
    [23] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [24] -1    0    0x00000000 - 0x000000ff (0x100) IX[b]
    [25] -1    0    0x0000d8e0 - 0x0000d8ff (0x20) IX[b]
    [26] -1    0    0x0000d8c0 - 0x0000d8df (0x20) IX[b]
    [27] -1    0    0x0000e8a0 - 0x0000e8bf (0x20) IX[b]
    [28] -1    0    0x0000fea0 - 0x0000feaf (0x10) IX[b]
    [29] -1    0    0x0000fe30 - 0x0000fe33 (0x4) IX[b]
    [30] -1    0    0x0000fe20 - 0x0000fe27 (0x8) IX[b]
    [31] -1    0    0x0000fe10 - 0x0000fe13 (0x4) IX[b]
    [32] -1    0    0x0000fe00 - 0x0000fe07 (0x8) IX[b]
    [33] -1    0    0x0000ffa0 - 0x0000ffaf (0x10) IX[b]
    [34] -1    0    0x00000374 - 0x00000374 (0x1) IX[b]
    [35] -1    0    0x00000170 - 0x00000177 (0x8) IX[b]
    [36] -1    0    0x000003f4 - 0x000003f4 (0x1) IX[b]
    [37] -1    0    0x000001f0 - 0x000001f7 (0x8) IX[b]
    [38] -1    0    0x0000e8c0 - 0x0000e8ff (0x40) IX[b]
    [39] -1    0    0x0000ec00 - 0x0000ecff (0x100) IX[b]
    [40] -1    0    0x0000ff20 - 0x0000ff3f (0x20) IX[b]
    [41] -1    0    0x0000ff40 - 0x0000ff5f (0x20) IX[b]
    [42] -1    0    0x0000ff60 - 0x0000ff7f (0x20) IX[b]
    [43] -1    0    0x0000ff80 - 0x0000ff9f (0x20) IX[b]
    [44] -1    0    0x0000e898 - 0x0000e89f (0x8) IX[b](B)
    [45] -1    0    0x0000dc00 - 0x0000dcff (0x100) IX[b](B)
    [46] 0    0    0x000003b0 - 0x000003bb (0xc) IS[b](OprU)
    [47] 0    0    0x000003c0 - 0x000003df (0x20) IS[b](OprU)
(II) intel(0): Kernel reported 238592 total, 1 used
(II) intel(0): I830CheckAvailableMemory: 954364 kB available
(EE) intel(0): [dri] I830CheckDRIAvailable failed because of a version mismatch.
[dri] libDRI version is 5.0.0 but version 5.4.x is needed.
[dri] Disabling DRI.
(==) intel(0): VideoRam: 262144 KB
(**) intel(0): Framebuffer compression disabled
(**) intel(0): Tiling enabled
(II) intel(0): Page Flipping disabled
(==) intel(0): Write-combining range (0xe0000000,0x10000000)
(II) intel(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(WW) intel(0): EXA greedy migration mode enabled.
(II) EXA(0): Forcing greedy migration option
(II) EXA(0): Offscreen pixmap area of 19660800 bytes
(II) EXA(0): Driver registered support for the following operations:
(II)         Solid
(II)         Copy
(II)         Composite (RENDER acceleration)
(==) intel(0): Backing store disabled
(==) intel(0): Silken mouse enabled
(II) intel(0): Initializing HW Cursor
(II) intel(0): xf86BindGARTMemory: bind key 0 at 0x007bf000 (pgoffset 1983)
(II) intel(0): Fixed memory allocation layout:
(II) intel(0): 0x00000000-0x0001ffff: ring buffer (128 kB)
(II) intel(0): 0x00020000-0x00029fff: HW cursors (40 kB, 0x000000003f820000 physical
)
(II) intel(0): 0x0002a000-0x00031fff: logical 3D context (32 kB)
(II) intel(0): 0x00032000-0x00032fff: overlay registers (4 kB, 0x000000003f832000 physical
)
(II) intel(0): 0x00040000-0x0067ffff: front buffer (6400 kB)
(II) intel(0): 0x00680000-0x0193ffff: exa offscreen (19200 kB)
(II) intel(0): 0x10000000:            end of aperture
(II) intel(0): Output configuration:
(II) intel(0):   Pipe A is on
(II) intel(0):   Display plane A is now enabled and connected to pipe A.
(II) intel(0):   Pipe B is off
(II) intel(0):   Display plane B is now disabled and connected to pipe B.
(II) intel(0):   Output VGA is connected to pipe A
(II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(II) intel(0): DPMS enabled
(II) intel(0): Set up overlay video
(II) intel(0): direct rendering: Disabled
(--) RandR disabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) AIGLX: Screen 0 is not DRI capable
(II) Loading sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
    compiled for 1.4.0.90, module version = 1.0.0
    ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
(II) intel(0): Setting screen physical size to 338 x 203
(WW) Configured Mouse: No Device specified, looking for one...
(II) Configured Mouse: Setting Device option to "/dev/input/mice"
(--) Configured Mouse: Device: "/dev/input/mice"
(==) Configured Mouse: Protocol: "Auto"
(**) Option "CorePointer"
(**) Configured Mouse: always reports core events
(**) Option "Device" "/dev/input/mice"
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(**) Option "CoreKeyboard"
(**) Generic Keyboard: always reports core events
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "gb"
(**) Generic Keyboard: XkbLayout: "gb"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(--) Configured Mouse: PnP-detected protocol: "ExplorerPS/2"
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(II) intel(0): I2C device "CRTDDC_A:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "CRTDDC_A:ddc2" removed.
(II) intel(0): I2C device "CRTDDC_A:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "CRTDDC_A:ddc2" removed.
(II) intel(0): I2C device "CRTDDC_A:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "CRTDDC_A:ddc2" removed.
(II) intel(0): I2C device "CRTDDC_A:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "CRTDDC_A:ddc2" removed.
(II) intel(0): I2C device "CRTDDC_A:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "CRTDDC_A:ddc2" removed.
(II) intel(0): I2C device "CRTDDC_A:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "CRTDDC_A:ddc2" removed.
(II) intel(0): I2C device "CRTDDC_A:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "CRTDDC_A:ddc2" removed.
(II) intel(0): I2C device "CRTDDC_A:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "CRTDDC_A:ddc2" removed.
(II) intel(0): I2C device "CRTDDC_A:ddc2" registered at address 0xA0.
(II) intel(0): I2C device "CRTDDC_A:ddc2" removed.
(II) intel(0): xf86UnbindGARTMemory: unbind key 0

```Thinking around the problem, however, I reasoned that essentially, we have two situations --
[1] booting with the default xorg.conf ... which gives a good display on the Main monitor
but without the 2nd monitor on the Radeon card being seen
[2] booting with a modified xorg.conf ... which causes the Main monitor to show a low-res display ... the 2nd monitor still not being seen

In addition, I mentioned last night that I had experimented changing the BIOS settings and so I wondered just what (if anything) this changed.

I therefore did two clean re-boots (using the default xorg.conf file created during installation) but with the BIOS video settings at "Auto" and "PEG", respectively. Much to my surprise, when the BIOS setting was "Auto", the system crashed out into low-res mode. It didn't do this when I began all this experimentation a couple of weeks ago !
I could switch between "Auto" and "PEG" settings and all that happened was that either the monitor on the on-board card or the one on the Radeon card became "Main" ... with the other monitor simply not being recognised.

I made this change of BIOS setting early on in my experiments (before starting this thread) so all our work has been done with the BIOS set to "PEG". (The experiments last night showed this to be the right choice and tonight's test confirms this). However ... what has changed since I began this work to so drastically alter the behaviour of the monitors ?

Then I realised ... BEFORE I switched the BIOS settings, I was using the system defaults.

AFTER I had changed them and found that this didn't fix my problem, I down-loaded and MANUALLY (!)  installed a driver from the ATI site !

It does seem possible to me now that in my ignorance, I somehow made a mess of this operation and that we have been trying to fix a system that has a broken ATI driver !

So ... I think that before we go any further with this problem, the first thing to do is to completely de-install the exisitng ATI driver and then do a clean re-install.

To that end, I wonder if you can be so kind as to tell me (preferrably in VERY simple words :confused:) how I should go about these tasks ...

I feel an absolute fool but ... this has been a complex problem on part of what has been a steep learning curve ... at least, that's my excuse and I'm sticking to it !

Best regards ...

---

### Post by fooey on 2008-11-01
> **earthpigg said:**
> sir,

holy fcuking siht that is awesome.

i hope i am pushing the limits and installing operating systems on unfamiliar hardware at the age of 75.

unfortunately, i am to drunk to help you with your problem.

but, again, that is badass that you are throwing the theory that 'older people don't learn as fast/much' out the window.

you have my admiration and my intent is to be much like you in 5 decades.

hahahahaha :lolflag:

---

### Post by hatrack on 2008-11-01
> **fooey said:**
> hahahahaha :lolflag:

What does that mean ? ... How is it significant to the discussion in hand ?

---

### Post by nick_h on 2008-11-01
Your latest log uses the config file /etc/X11/xorg.conf but it doesn't seem to be the one you posted.  I would expect to see the identifiers you defined.  This log contains default ones.  For example, the section in my log reads:
```
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor1"
(**) |   |-->Device "Videocard0"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
(**) |-->Input Device "Touchpad0"

```
The lines correspond to the identifiers that I have used.

The complication is that X configures itself not only from information supplied in the log file but also from default values and data obtained by probing the hardware.  The system tries to get something working.

You have an example of a log in which the intel card was used to produce a display.  (I don't know why there are two BusIDs.)  The default display when one is not defined in the config file is probably taken from the BIOS but I am not sure.

I think your next step is to write two config files and try to see if you can get both cards to work in single display mode.  When this works you can combine the files to try the dual display configuration.

There is no need to uninstall the ATI driver to use the open source version.  You could just use "ati" as the driver rather than "fglrx".  (I can switch back to "nv" from  "nvidia" without uninstalling the proprietary driver).  If you installed the driver manually then I will have to know how what instructions you followed before I can suggest how you re-install it.

For the Radeon try:
```

Section "Device"
Identifier "Radeon 7000"
Driver "ati"
BusID "PCI:4:0:0"
EndSection

Section "Monitor"
Identifier "Second Monitor"
Option "DPMS"
HorizSync 28-80
VertRefresh 43-75
EndSection

Section "Screen"
Identifier "Second Screen"
Monitor "Second Monitor"
Device "Radeon 7000"
DefaultDepth 24

SubSection "Display"
Depth 24
Modes "1152x864", "1024x768"
End Subsection
EndSection

Section "ServerLayout"
Identifier "Single Radeon"
Screen "Second Screen"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
EndSection

```

Then you can try another version for the Intel card.

---

### Post by hatrack on 2008-11-01
Hi Nick !

Sorry, but I've been tied up all day and only had time 'til now to electronically-acknowledge your post.

You say >  Your latest log uses the config file /etc/X11/xorg.conf but it doesn't seem to be the one you posted. I would expect to see the identifiers you defined. This log contains default ones This doesn't surprise me too much ... it appears that at each boot a new log-file is created and that the one from the previous invocation is renamed "* old". At the next boot, "*old" disappears and the previous log-file is  now renamed to become the current  " *old". After the last series of tests of xorg.conf files, naturally, I rebooted using my default version (so as to get a fully-working system with correct display) and I'm not at all sure how many times I rebooted after that.

The trick, of course, is to interrupt the boot process before it gets too far along automatically-creating a "Safe Mode" set-up but to not do this too soon !   I understand your instructions in the Post of 31/10 on how to attempt this and I'll try this tomorrow. I also understand your instructions to create a number of log-files reflecting differing versions of xorg.conf. 

In my previous post, I raised my concerns that the ATI driver may be corrupted. Looking around this evening whilst reflecting on this whole matter, I found to my surprise that a new pair of items relating to ATI had been added to the "Applications" menu (I don't routinely use this, so I have not had cause to look there recently). 

These items are --

"ATI Catalyst Control Centre" and "ATI Catalyst Control Centre (Super-user)". When I click on either (and enter my password, if required) a splash-screen is presented with the following ---
```

"There is a problem initialising the Catalyst Control Centre Linux edition. It could be caused by the following -
No ATI driver is installed or the driver is not functioning properly. Please install .... etc., etc.."

```Sadly, I think that that is pretty-solid evidence that my suspicions regarding installation errors on my part are correct. I wish I'd noticed this a week ago !  Further, I think I must get rid of these before trying other experiments. I take your point that you cannot advise me how to de-instal these drivers unless you know exactly how I installed them in the first place. Sadly, after all the many experiments of the past days, I can't remember how I did this ... and I didn't make any notes at the time ...instead, merrily going along following the screen prompts (I thought). Another newbie blunder ... experience in Windows is no help under Linux !

OK ... I think another route that I can follow is to search the file system for the ATI drivers ... possibly hiding in a sub-directory, someplace ... and then to disable them by renaming the folders. If I remove the Radeon card and disconnect the second monitor, I know I can boot up using just the on-board chip. With these drivers disabled, I  can then down-load a new set, using Synaptic, thus restoring the system to the same state as it was in when I began all this work. Then I can start again.

I have never used the ATI Catalyst Control Centre when running under Windows, relying instead on the set-up available from the "Display" options  in "Control Centre". I don't know whether or not I shall need this under Linux, since all I want is to do is drive the card ... I'm not concerned about all the extra "Bells and Whistles" features. It seems to me from what I have read recently that the Open Source drivers will probably prove adequate for this simple need.

So ... tomorrow I shall hunt for and disable the existing ATI drivers (I hope ! ). Once I've got the system back into its original configuration, I will start all over again and will report back to you on my progress.

In the meantime ... before I get too far along the road, can you please make any comments on my proposed method of disabling drivers and then re-installing via Synaptic ?

Many thanks for your efforts and your interest in this problem ...

Best regards,

---

### Post by nick_h on 2008-11-02
> OK ... I think another route that I can follow is to search the file system for the ATI drivers ... possibly hiding in a sub-directory, someplace ... and then to disable them by renaming the folders.
You probably installed some packages and it would be better to remove them using a package manager like Synaptic or apt from the command line.

There are a few ways could could have installed the driver:

1. The Hardware Drivers tool
You may have seen a green icon in your top panel which said that new drivers were available for your system.  If you clicked on this then it would be the same as going to System->Administration->Hardware Drivers.  Have a look in there.

2. You installed a helper program called envy
I'm sure you would remember if you did this.
Look in the package manager for the packages xorg-driver-fglrx-envy and fglrx-control-envy

3. You manually installed some packages the Ubuntu way
Look in the package manager for the packages xorg-driver-fglrx and fglrx-control

4. You downloaded a script from the ATI site and ran it.
Here is a link to an [installation guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide).

From the command line you could type:
```
aptitude search fglrx
```
Installed packages will have "i" as the first character in the line.

---

### Post by hatrack on 2008-11-02
Hi Nick !

Once again, thanks for your reply.

In view of the "dog's-breakfast mess" of an installation that I appear to have created, I decided to wait for your comments on my last post before continuing.

Considering the installation options you list, it was in fact No.4 that I chose and I attempted to follow Method 1. detailed in the installation guide. After visiting this site to confirm this, I ran --
```

aptitude search fglrx

```and got the following output --
```

p   fglrx-amdcccle                  - Dummy package for easy transition         
p   fglrx-amdcccle-envy             - Dummy package for easy transition         
p   fglrx-control                   - Control panel for the ATI graphics acceler
p   fglrx-control-envy              - Control panel for the ATI graphics acceler
v   fglrx-driver                    -                                           
v   fglrx-driver-dev                -                                           
p   fglrx-kernel-source             - ATI binary kernel module source           
p   fglrx-kernel-source-envy        - ATI binary kernel module source           
p   xorg-driver-fglrx               - Video driver for ATI graphics accelerators
p   xorg-driver-fglrx-dev           - Video driver for ATI graphics accelerators
p   xorg-driver-fglrx-dev-envy      - Video driver for ATI graphics accelerators
p   xorg-driver-fglrx-envy          - Video driver for ATI graphics accelerators

```I take it that this listing shows that the various items are either "packages" or are "void" and that none are installed. I have also looked in Synaptic for xorg-driver-fglrx and fglrx-control. These are listed but are shown as not being installed. The two which are installed are -- "radeon tool", to control the back-light in laptops and "xserver-xorg-video-ati, which is descibed as being the  "X Org X Server ATI display driver".

Being of an inquisitive nature, I then ran a search for "ati" under Nautilus. This showed SIX directories of this name, as follows --

/etc/ati
usr/share/ati  --- ATI license, etc and assorted files
/usr.share/doc/ati --- files plus sub-dirs "Articles", "Examples" and "User Manual" plus assorted  files
/usr/source/ati --- sub-dir "fglrx-sample-source-tgz"

src/linux-headers-2.6.24.19 - generic            Header files
 --------- ditto -------  ditto ----- generic-include            ditto

Now ... the interesting point is that all of the first four listed above contained files/dirs with the Date/Time-stamp of 27.10.2008/0044hrs whilst the last two were stamped much earlier in the year. Clearly, therefore, those four directories were created/modified during my abortive installation attempt and the implication is that this has somehow scrambled the original basic set-up.

I'm beginning to wonder if it would not be simpler and easier to just re-install "Hardy" !

I presume that I could remove the Radeon card and second monitor and just re-run the DVD to produce a "clean" basic set-up ?   I haven't got a lot of data to back up and it would take perhaps 1/2 a day to re-create my desktop, re-install "Wine", etc.. The merit of the idea is that we would then be working with a known stable and correctly-configured system. What I am concerned about is whether or not this will also scramble my WinXP partition. Again, I can fix that too but, of course, it complicates the job considerably.

Can one get a "clean" re-install of a Linux system this way ?

I await your further comments/advice in due course ...

Rgds,

---

### Post by nick_h on 2008-11-03
> Considering the installation options you list, it was in fact No.4 that I chose and I attempted to follow Method 1. detailed in the installation guide.
Since the package xorg-driver-fglrx is not installed something must have gone wrong.

From the aptitude man page:
> The first character of each line indicates the current state of the package:
the most common states are p, meaning that no trace of the package exists on the system, c, meaning that the package was deleted but its configuration  files remain on the system, i, meaning that the package is installed, and v, meaning that the package is virtual.

> Being of an inquisitive nature, I then ran a search for "ati" under Nautilus.
Good idea.  There are a few other commands which maybe useful.  If you want to find out if a given file is part of an installed package you can use the *dpkg* command.
```
dpkg -S /usr/bin/lspci
```

If you have installed a package and want to know where it put the files, use:
```
dpkg -L pciutils
```

From the command line, *find* is a very powerful command.
If you have installed a program without using the package management system, then you could use the following to find all files modified within the last 5 minutes:
```
sudo find / -mmin -5 -print
```
(The / is where it starts the search.  You make find it more useful to search from /usr or /etc)

Your first choice for installing software should be the package management system. Firstly check that the software you need is in a repository.  Then check to see if a .deb file is available.  There are can be some occasions though when you will need to use other methods.

Some scripts that install software also have an uninstall facility.  So if you installed with a script then checking the help would be a good idea.
```
script.sh --help
```

You will have needed to have run the script using *sudo* so it will be recorded in your /var/log/auth.log (or one of the archived versions).

> I'm beginning to wonder if it would not be simpler and easier to just re-install "Hardy" !
Not a bad idea.  If you think you need to re-install it shouldn't take too long.  Here are a few tips.

1. Backup your personal data.

2. Make a backup of packages you have installed.  Generate a list with:
```
dpkg --get-selections > packages.txt
```
If you want to save bandwidth and not download the packages again they are stored in /var/cache/apt/archives/ - make a backup.

3. Backup your user settings.  They are in the hidden files under your home directory. (use ls -a from the command line or Ctrl-H in Nautilus to view them.)
I tend to make a tar archive for this.
```
cd /home
tar cvzf backup.tgz *username*/
```
(replace *username* with your account name)
If you remove any large files first it will make the process quicker.
Then you can view the contents with:
```
tar tvzf backup.tgz
```
and restore with:
```
tar xvzf backup.tgz
```

4. Backup system-wide settings.  These will be under the /etc directory.  You probably haven't changed many of these files - except xorg.conf a few times :)

5. When you re-install select manual partitioning not guided.  You will need to select the root (/) partition and possibly the swap partition.  You can set these to be formatted.  Make sure that you don't select any other partitions to be formatted and you should be OK.  I assume you have 1 partition for Windows, 1 for Ubuntu + 1 swap for Ubuntu and probably a shared partition for your data.

---

### Post by hatrack on 2008-11-03
Hi Nick !

Thanks again for your really helpful and informative post.

> 
Since the package xorg-driver-fglrx is not installed something must have gone wrong.
Yeah ! ... Right ! ... Understatement of the year !    I once read that the most fallible part of any computer system is located beween the keyboard and the chair seat.

> 
Your first choice for installing software should be the package management system
Again ... Yeah ! ... Right ! ... However, the best way to learn any lesson is to "Try" and then make mistakes. I've leaned this one all right ! ... as "they" are supposed to say, "No pain, no gain"

So ... I'm going to do a re-install. I have a DVD of "Hardy" and will use that, following your advice precisely. 

> 
 When you re-install select manual partitioning not guided. You will need to select the root (/) partition and possibly the swap partition. You can set these to be formatted. Make sure that you don't select any other partitions to be formatted and you should be OK. I assume you have 1 partition for Windows, 1 for Ubuntu + 1 swap for Ubuntu and probably a shared partition for your data.
Simpler than that ... my partitions are --- one for Win XP, one for Ubuntu and one swap.

The only reason that I have Win XP is so that I can drive my film-scanner. I have tried but, this definitely will not run under Wine, it is now officially "obsolete" and, there are no Linux drivers for it. Not a big deal in the grand scheme of things. Each scan produces a *.tif file of >50Mb, which I consider to be the digital equivalent of a film negative. After scanning a batch of images, I immediately burn the resulting files to CD/DVD and then empty out the HD space, ready for the next batch.

When I'm ready to process the images in PhotoShop, I load a selection from these back into a working dir.. In due course, these are output to one of my two printers. Again, I have special driver files for these produced by the ink manufacturers so ... output will be done under Win XP yet again. I have already confirmed that Ubuntu can "look over the wall" into the Win XP partition and both pick up and put back files from there, as well as read my old CDs.

Given this capability of Ubuntu to pick up files that are in cross-platform formats, I can't see a need (for me ! ) to have a "shared" partition.  Of course, Win XP is no where near so clever as is Ubuntu and can neither see nor write to partitions other than its own without aditional help. 

So ... that's it ... Now that I have your detailed advice, I shall start again tomorrow to re-install "Hardy" and then, I'll try to get a dual-monitor configuration without modifying anything ... I promise !  

I have all your replies archived away for future reference and I feel that over these past days, I have both learned a lot and also, now have some pretty clear ideas on how to create the configuration I require.

Many thanks ... I'll put up another post as soon as I have some further news.

Best regards,

---

### Post by hatrack on 2008-11-07
Hi All !

I have been trying for some two weeks to set up a simple dual-monitor configuartion on a dual-boot machine running Win XP/Ubuntu 8.04. 

After many abortive attempts, I decided to completely re-install Ubuntu so that the drivers available were known to be free from corruption. Even after all this work, it is absolutely impossible to get a dual-monitor set-up running. When a dual-monitor set-up is specified in xorg.cong., the machine fails at boot and defaults into a low-res mode. An example of the xorg.conf. files used is  --

```

# xorg.conf to drive twin monitors -- Originally created 27.10.2008
# Modified 05.11.2008

# For Ubuntu Ver: 8.04, running on Dell GX-520: IGb RAM.
# Main monitor - TFL 19" connected to Intel 82945G on motherboard
# Second monitor - 17" CRT connected to Radeon 7000-series grahics card in PCI slot

# Standard info ---
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

# Identifying & setting up dual monitors -- Modified
# Device No.1
Section "Device"
    Identifier    "Intel 82945G"
    Driver        "Intel"
    BusID        "PCI: 0:2:0"
EndSection

# Device No.2
Section "Device"
    Identifier    "Radeon 7000"
    Driver        "ati"
    BusID        "PCI: "4:0:0"
EndSection
# Note that cmd "lspci -b" returns BusID values in hex --- these must be converted to denary notation, as above
# Note -- Various names have been tried to identify the driver native to Ubuntu - the above is one example.

# Monitor No.1
Section "Monitor"
    Identifier    "Main Monitor"
    Option         "DPMS"
    HorizSync    28-80
    VertRefresh    43-75
EndSection

# Monotor No.2
Section "Monitor"
    Identifier    "Second Monitor"
    Option         "DPMS"
    HorizSync    28-80
    VertRefresh    43-75
EndSection

# Info for First monitor --
# Screen No.1
Section "Screen"
    Identifier     "Default Screen"
    Monitor        "Main Monitor"
    Device        "Intel 82945G"
    DefaultDepth    24

        SubSection "Display"    
            Depth    24
            Modes    "1024x768"
        End Subsection
EndSection

# Info for Second monitor --
# Screen No.2
Section "Screen"
    Identifier    "Second Screen"
    Monitor        "Second Monitor"
    Device        "Radeon 7000"
    DefaultDepth    24
    
        SubSection "Display"    
            Depth    24
            Modes    "1024x768"
    End Subsection
EndSection

# Additional info --
Section "ServerFlags"
    Option "Xinerama" "true"
EndSection

# Specify position of two monitors relative to each other
Section "ServerLayout"
    Identifier    "Twin Head"
    Screen        "Default Screen"
    Screen        "Second Screen" LeftOf  "Default Screen"
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

```During one of my last runs, I noticed that when I start Nautilus, it throws up the following message, although it subsequently starts and runs satifactorily --

```

** (nautilus:6122): WARNING **: Unable to add monitor: Operation not supported
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

```Questions ---
[1]  Is this relevant to my problem ?
[2]  Can anyone please tell me how to enable sharing ? I do not actually need to share files on my stand-alone computer but, if it is indeed needed to allow dual monitors to work, then I need to know how to enable it. I have searched this forum and the three books on Ubuntu that I have but (in my ignorance ! ) nothing seems relevant.

I am getting thoroughly frustrated by this whole business, so any advice will be most gratefully received.

Best regards to all ...

---

### Post by enystrom on 2008-11-08
Hello,

I'm not sure if this will actually solve your problem or not, but I've noticed a possible error or two in your xorg.conf -- in the file you posted originally, the BusID line was missing an end-quote.  That got me to thinking about the importance of the quotes and formatting -- if you were missing an end quote, the rest of the file would be included in the literal string, meaning that the rest of the information wasn't processed.  Since that post, you've reinstalled Hardy, but I notice again that there might be an error in the new version of the file.  In the second Device section, it says:

```
    BusID        "PCI: "4:0:0"

```

Notice the extra quote?  So the X server might be reading that as simply

```
    BusID        "PCI: "

```

Because the close-quote was received and thus the expression was over.  

Again, this is a very minor point, but sometimes this kind of thing can make all the difference.  Just for reference, I took a look at my own xorg.conf (single monitor), and it also does not have the spaces that you've inserted into the BusID line.  Mine looks like so:

```
        BusID           "PCI:0:2:0"

```

I rather doubt the spaces make a lot of difference, but since they are inside quotes, they may have to be exactly right so it might be worth changing those as well.

These minor points may not prove to have been your problem, but the opening/closing of quotes is one of the things that I always look for first when I have hand-edited something and it's not behaving as I expect.  Some text editors will do special tricks like highlighting pairs of quotes to help you figure these sorts of things out.

Good luck!

-Eric

---

### Post by hatrack on 2008-11-09
Thank you very much for your post.

I have enough experience to know that simple syntactical errors like these can play absolute havoc, so it does seem possible that you are on the right track. Later today I'll sit down quietly and go through the *.conf file with the proverbial "fine toothed comb". 

I'll put up a post later, reporting my findings.

I don't know how many times I've checked/re-written those damn' files so I have no idea why I didn't spot the glaringly-obvious ... "too close to the wood to see the trees", perhaps ?

Many thanks for your fresh pair of eyes !

Best regards,
Eric  (my name too !)

---

### Post by hatrack on 2008-11-09
Hi !

As promised, I have carefully checked and corrected the syntax of my xorg.conf file but ... sadly, this does not fix the problem !

I am getting very frustrated with this whole matter. All the posts seem to say that it is possible to have a dual-monitor setup. My Radeon card isn't "strange" or particularly old. Not only have I followed all the kind advice that I have received but also, I have done a complete re-install of Ubuntu. Yet, still no sign of success ... the system simply defaults to low-res mode.

To my mind, the only thing not resolved is the matter of "sharing" which I mentioned in my other thread "Not possible to set up dual monitors". If no one spots and comments upon this latest post, I shall try starting a new thread on this subject because I can't find anything on the subject of enabling sharing.

My thanks to all who have read this lengthy thread and offered their suggestions.

Best regards ...

---

