---
title: "How to set you monitor resolution"
date: 2006-10-01
forum: Outdated Tutorials &amp; Tips
---

### Post by bodhi.zazen on 2006-10-01
[img]http://metaphysicsforchristians.org/Yin-Yang.JPG[/img]

[size=6]**How to Monitor resolution**[/size]

[size=2]**Major Edit October 29, 2006**: Updated 915 resolution[/size]
[size=2]**Minor Edit December 20, 2006**: Added information on xorg-edit[/size]

[color=blue]_**Thanks to everyone for your patience, feedback, and assistance with this thread._**[/color]:
[color=green][list][*]ebutton
[*]guitara
[*]k94382
[*]Krisz
[*]lucis
[*]Pablasso
[*]pastashop
[*]UnknownVariable[/list][/color]

[size=2]**_Major Sections_:**[/size]
[list=number][*]Introduction.
[*]GUI tool to configure X
[*]Quick fix ?
[*]Collect information on your monitor and video card.
[indent]Google ?[/indent]
[*]Edit /etc/X11/xorg.conf 
[indent]_Note_: That is a capital "X" in "X11"[/indent]
[*]Stuck with a small screen?
[indent][list][*]On laptops
[*]Are you stuck with a small screen, that will not enlarge, centered on your screen?[/list][/indent]
[*]Videocard
[indent]Nvidia, ATI, Intel[indent]
[*]Further troubleshooting.
[*]Tips & tricks
[*]Referances[/list] 

[size=2][b]_Introduction_:
This post is _not_ intended to be a definitive guide to xorg.conf or monitor resolutions. It is intended to guide new users on a few "easy" fixes for their potential resolution problems and point to further information as needed.[/b][/size]

[size=4]**See References section for more detailed guides and some information for Laptops**[/size]


[b]First, just in case, make a back up of you current file:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.org
```
.org for origional file. This may be of help in the future as a referance.[/b]

[color=red]**If you ever get a working copy, save a back up**:[/color]
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```
.bak for backup.

[size=2]***You can restore from back up at any time with:[/size]***```
sudo cp /etc/X11/xorg.conf.org /etc/X11/xorg.conf
```

===================================


[size=2]_**GUI Tool_.**[/size]

[color=blue]Thanks to guitara[/color]

> **guitara said:**
> you should add info about xorg-edit. a GUI for editing your xorg config. Maybe not newbie friendly, but it does have a modeline generator 

There is a GUI tool called **[color=blue]Xorg-Edit[/color]**

Found here: [Xorg-Edit v06.11.12](http://www.cyskat.de/dee/progxorg.htm)

I have not used this but have heard good reviews. You may find it is easier to use this tool.

Features:
> Because I found it very complex to edit the XServer config file (xorg.conf in Ubuntu) manually to add my monitor refresh rates and some users from the German forum Ubuntuusers.de had the same issues I want to build a GUI so that editing this file becomes much easier. 

Apparently this tool will also calculate modlines as well.


===================================


[size=2]1. _First, try a quick fix_. It may not work, but if is does you are done.[/size]
	
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
[list][*]The -phigh option selects the defaults for everything but the screen resolution.
[*]To select a resolution, use the arrow keys to move up and down, hit the "Space bar" to select/unselect a resolution.
[*]You will recieve a message indication your old file was backed up.
_Note_: This often shakes the confidence of "noobs", but it is normal. :-&[/list]

===================================

[size=2]2. _If that fails you will need to know the specifications of your monitor and video card_.[/size]

**It is helpful, critical in fact, if you include this information if you post on the forums.** :?:

_**Monitor information_**- Google search your monitor by make and model. You are looking for the technical specifications for the horizontal and vertical refresh rates.

_**Videocard information_**- In a terminal run this command:```
lspci | grep VGA
``` 

===================================

[size=4]Manual edit(s) to /etc/X11/xorg.conf[/size]

[size=2]3a. _Monitor section- You need to know the horizontal and vertical refresh rates_.[/size]

Edit /etc/X11/xorg.conf

_If you have Gnome running_:
```
sudo gedit /etc/X11/xorg.conf
```

_If you have no video and are stuck at the CLI_:
```
sudo nano /etc/X11/xorg.conf
```
_With nano_: Ctrl-X to exit, type Y to save your edit, N to close without changing.

You are looking for the following sections:

_Monitor_:> Section "Monitor"
	Identifier	"Monitor1"
	VendorName	"DEL"
	ModelName	"DELL P1110"
[b]	HorizSync	29-121
	VertRefresh	50-180[/b]
EndSection

Enter you monitors horizontal and vertical refresh rates:
If you do not know what they are, google search for your monitor.
I put an entry in my xorg.conf with my monitors web site for reference:
```
##############################################################################################
#
# DELL P110 = Monitor 1
#
**# sepcs at http://www.dealtime.com/xPF-Dell_DELL_P1110_Tinitron_21_Monitor_walt_91MCW**
#
##############################################################################################

Section "Monitor"
	Identifier	"Monitor1"
	VendorName	"DEL"
	ModelName	"DELL P1110"
	HorizSync	29-121
	VertRefresh	50-180
EndSection
```


[size=2]*After editing your xorg.conf you need to re-start X*:[/size] [-o<
Use the three finger salute: Ctrl-Alt-Backspace
This will bring you to the log-in screen (GDM).

-----------------------------------------

[size=2]3b. _Screen section_. If this fails, next reduce the color depth:[/size]

Again open xorg.conf with an editor (vi, nano, gedit)

This time you are looking for the _"Screen" section_:
> Section "Screen"
	Identifier	"twinviewscreen"
	Device		"twinview"
	Monitor		"Monitor1"
 
   **DefaultDepth 24**
   
    Subsection "Display"
        Depth       8
        Modes "1280x1024" "1024x768" "800x600" "640x480"
    EndSubsection
    [b]Subsection "Display"
        Depth       16
        Modes "1280x1024" "1024x768" "800x600" "640x480"
    EndSubsection[/b]
    Subsection "Display"
        Depth       24
        Modes "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubsection
    Subsection "Display"
        Depth       32
        Modes "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubsection
EndSection

[list=number][*]Reduce the DefaultDepth (this is color depth, 16 is more then adequate for most people and 24 may be excessive).

Change it to 16:```
[b]DefaultDepth 16

    Subsection "Display"
        Depth       16
        Modes "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubsection[/b]
```
[*]Make sure the Subsection "Display" lists your desired resolution.
On occasion I have "fooled" X into giving me my desired resolution by setting the resolution 1 step higher.

If you are not sure, you can use "1600x1200" and reduce it later.[/list]

[size=2]*After editing your xorg.conf you need to re-start X*:[/size] [-o<
Use the three finger salute: Ctrl-Alt-Backspace
This will bring you to the log-in screen (GDM).

===================================

[size=2]4. _Small screen_.[/size]
I recently installed onto a laptop and the display was small, low resolution, and centered on the screen.

The fix was to edit xorg.conf and add a line:
```
Option "UseEdidFreqs" "1"
```As well as HorizSync and VertRefresh rates. I obtained these rates from another live CD (in my case Zenwalk Live 3.0).

The final monitor section looks like this:
> Section "Monitor"
Identifier "Generic Monitor"
HorizSync 31.5 - 50.0
VertRefresh 40-90
Option "UseEdidFreqs" "1"
# Option "DPMS"
EndSection

You may also need to update your BIOS.

===================================

[size=2]5. _Videocard_.[/size]

UPDATE 2/12/07: You can install EITHER the ATI or Nvidia drivers with the Envy script.

[indent][list][*]Use with the "generic kernel".
[*]The envy script will automate updating your drivers and kernel.[/list]

[**Envy**](http://albertomilone.com/nvidia_scripts1.html)[/indent]


[list][color=brown][*]Do you have an ATI card?[/color]
	Try the ATI drivers
	[[color=blue]ATI How-to[/color]](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

[color=brown][*]Do you have a Nvidia card?[/color]
	Try the nVidia drivers
	[[color=blue]nVidia How-to[/color]](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

I prefer method 2 in both the nVidia and ATI how-to's.

If you get stuck, post on the forums.

To stop X (you may need to stop X to install the driver):
```
sudo /etc/init.d/gdm stop
```

To start X:
```
sudo gdm
```

[color=brown][*]Do you have an Intel card?[/color]

[color=brown][size=2]Intel[/size][/color]: There have been numerous posts re: intel drivers. I have limited experience with these but here are some potential solutions I have come across.[/list]

[color=brown][list=number][*]Update i810[/color]

_Personal experience_: I have had success with this video card by reducing the Color depth, as above, to 16 and adding a resolution line of 1600x1200, again as above.

There is a new driver available for the i810 chip. I have not tried this, but this is how to update your driver: *(Note: ~ is shorthand for /home/user_name)*

```
mkdir ~/src
mkdir ~/src/i810
cd ~/src/i810
wget http://www.fairlite.demon.co.uk/i810_drv.so
cd /usr/lib/xorg/modules/drivers
sudo mv i810_drv.so i810_drv.so.old
sudo cp ~/src/i810/i810_drv.so .
```
Further information: [[color=blue]i810_drv.o[/color]](http://www.fairlite.demon.co.uk/intel.html)

After installing i810_drv.so you need to re-start X:
Use the three finger salute: Ctrl-Alt-Backspace
This will bring you to the log-in screen (GDM) or
```
sudo /etc/init.d/gdm restart
```

-----------------------------------------

[color=brown][*]915Resolution: Intel Video BIOS Hack[/color]
_Note_: 915resolution replaces 855resolution.

**Use for the following chip sets: Intel 855 / 865 / 915 / 845G / 855G / 865G / 915G / 915GM / and 945G**

There is apparently a problem selection resolutions on the display. This is apparently a problem with the BIOS.

> 915resolution is a tool to modify the video BIOS of the 800 and 900 series Intel graphics chipsets. This includes the 845G, 855G, and 865G chipsets, as well as 915G, 
915GM, and 945G chipsets. This modification is necessary to allow the display of certain graphics resolutions for an Xorg or XFree86 graphics server.

915resolution's modifications of the BIOS are transient. There is no risk of permanent modification of the BIOS. This also means that 915resolution must be run every time the 
computer boots in order for it's changes to take effect.

915resolution has been reported to work with the following systems. It should, however, work with any system with an Intel 800 or 900 series graphics chipset. 
Further information: [[color=blue]915resolution[/color]](http://www.geocities.com/stomljen/).[/list]

915resolution is in the Ubuntu repositories.
[Enable Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu)

Either install it with Synaptic or;
```
sudo aptitude install 915resolution
```

_Configuration_:

See also the Unofficial Ubuntu Guide: [915resolution](http://ubuntuguide.org/wiki/Dapper#How_to_Correct_the_Graphics_Resolution_.28Intel.29)

[list=number][*]To list available resolution "modes":```
915resolution -l
```
_Note_: That is a small "L" and not the number 1.


[*]To use: If the resolution you desire is not listed you will need to edit one of the existing resolutions.
For example (using mode 5c (1920x1440):

```
sudo 915resolution [color=green]5c[/color] [color=red]1280 800[/color] [color=blue]24[/color]
```
[color=green]Mode to be changed[/color]
[color=red]Desired resolution[/color]
[color=blue]Desired color depth[/color]

Thus the Mode "5c" will be changed from the default resolution of 1920x1440 to the desired resolution of 1280x800 and a color depth of 24 bits.


[*]Additional examples:
> sudo 915resolution 3a 1440 900 24
sudo 915resolution 50 1280 768

[*]After configuring 915resolution and setting your new resolution mode, you need to re-start X:
Use the three finger salute: Ctrl-Alt-Backspace
This will bring you to the log-in screen (GDM) or
```
sudo /etc/init.d/gdm restart
```
[*]If gnome does not start at you new resolution, choose the resolution from the gnome menu.
[indent]From the gnome menu choose "System>Preferences>Screen Resolution" and change to your new resolution.[/indent]

[*]Your new resolution should work when you reboot as well. If your resolution reverts to an undesired, lower resolution on reboot:

```
sudo gedit /etc/rc.local
```

Add the desired 915resolution {sudo 915resolution [color=green]5c[/color] [color=red]1280 800[/color] [color=blue]24[/color]} above the "exit 0" line.

Save /etc/rc.local and exit gedit.


[*]The last potential tip I am aware of comes form [color=blue]Krisz[/color]:
> In my bios for some reason i only had 1Mb set for my video adapter's memory. I changed it to 8Mb and now i can change my screen resolution to higher. Although i still can not go up to 1600x1200 but at least i can use 1280 x 1024 which is the one i wanted to use anyways.[/list]

[More Detailed Example](http://ubuntuforums.org/showpost.php?p=1465348&postcount=10)

[915resolution README](http://www.geocities.com/stomljen/readme.html)

===================================

[size=2]_Troubble shooting 101_:[/size] ](*,)
[list=number][*]Confirm your monitor section still has the correct horizontal and vertical refresh rate.
[*]If you installed the ATI or nVidia driver with method 1, try method 2[/list]


[size=2]5. _Is your video card supprted by Ubuntu_?[/size]

[Supported video cards](http://doc.gwos.org/index.php/VideoCard)

[Hardware support](http://doc.gwos.org/index.php/HCL)

[Laptop support](https://wiki.ubuntu.com/HardwareSupportMachinesLaptops)
	

[size=2]6. _Is you video card supported by another version of Linux or Unix_?[/size] :-({|=


===================================

[size=2]**Tips**[/size]

Once you are up and running.....

1. _Change resolution on the fly_
Ctrl-Alt-+ (Control and Alt and the + on the numeric pad) cycles through available resolutions for our monitor.

2. _Change the font resolution in firefox_
Put the mouse in Firefox (so the firefox window is active)
Ctrl-= (Control and the = key, which I remember because it has a "+" on it)
Increases font size

Ctrl-- (Control and the - key, it has a -) reduces fornt size.

_Note_: You can use the + and - keys on the numeric pad as well.

_Note_: You can also do this with the mouse. Hold down the Ctrl key, scroll the [color=blue]mouse wheel[/color] up and down to change font size.

===================================

[size=2]_References_:[/size]

Where to go from here: This was intended a a brief how-to. Below are two more detailed explanations for all your resolution needs.

[Change Resolution](http://doc.gwos.org/index.php/ChangeResolution)
[How to fix video resolution](https://help.ubuntu.com/community/FixVideoResolutionHowto)

[Change resolution/refresh rate in Xorg](http://www.ubuntuforums.org/showthread.php?t=83973&)

Dual monitor:
[list=number][*][How to Twinview](http://www.ubuntuforums.org/showthread.php?t=221174&highlight=twinview)

[*][How to Xinerama](https://help.ubuntu.com/community/XineramaHowTo)

[*][Dual Monitor](http://ubuntuforums.org/showthread.php?t=240150)
[*][Dual Monitor 2](http://doc.gwos.org/index.php/DualMonitors)[/list]

Laptop external monitor:
[list=number][*][How to Laptop external monitor](http://ozlabs.org/~jk/docs/mergefb/)
[*][Laptop external monitor; SAMPLE xorg.conf](http://www.linux-on-laptops.com/forum/showthread.php?p=1253)
[*][Laptop external monitor for presentations](http://www.astro.umd.edu/~teuben/linux/laptop-display.html)[/list]

[img]http://www.laiwa.com/cache/3/1/531045_70x70.gif[/img] [color=navy]bodhi.[/color][color=darkgray]zazen[/color]

---

### Post by UnknownVariable on 2006-10-02
The one part I was interested in this HOWTO was the following:

> If this new resolution fits the bill, you need to make a script to run 855resolution when you boot.
Code:

sudo touch /etc/init.d/resolution sudo gedit /etc/init.d/resolution

Insert the following lines (or what resolution you would like):
Quote:
#/bin/sh ** <-- Shouldn't there be a bang (!) after the initial sharp?**
855resolution 5c 1400 1050
Save and exit.

Make it executable:
Code:

sudo chmod a+x /etc/init.d/resolution

Symlink it to /etc/rc2.d/90resolution: ** <-- Also needs a capital S before "90"**
Code:

sudo ln -s /etc/rc2.d/S90resolution /etc/init.d/resolution

This resolution should be good to go on re-boot.

(Small note for you, I bolded it in the quote.)

I followed the commands just as written (replacing 915resolution & pixel dimensions instead of 855, as I'm using the 915 version, as well as adding in the sharp to the above file), and upon bootup I still booted into a low-res system, and I have to run my command manually to get my good resolution back. I assume it'd be a good idea to revert the changes we made during this process, to try something else, yes? How would I go about reverting the symlink?

**edit:** Without reverting the symlink, I opened up a terminal in my lowres system and performed my normal 915resolution command. After that, I pressed **ctrl alt backspace** to restart X... And now I have a blank black screen. What went wrong?

**edit 2:** I rebooted improperly (bad, I know) but now I have X. I think I'll attempt to remove the symlink and the file before resetting my resolution this time, lol.

---

### Post by Pablasso on 2006-10-15
thanks for the guide! the correct link for the i810 driver is:
[http://www.fairlite.demon.co.uk/i810_drv.so](http://www.fairlite.demon.co.uk/i810_drv.so)

*trying the driver right now*

---

### Post by Aualin on 2006-10-15
i always use
sudo dpkg-reconfigure xserver-xorg
it always works and is easy!

---

### Post by bodhi.zazen on 2006-10-15
> **Aualin said:**
> i always use
sudo dpkg-reconfigure xserver-xorg
it always works and is easy!

```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Is the same thing. The option **-phigh** selects the defaults for everything except resolution.

---

### Post by indigoshift on 2006-10-15
Thanks for these tips!

I had a strange problem:  I set up a KVM switch so I could switch between my Windows box and my Ubuntu box, and all I could get was the 640x480/60Hz option.

I tried a couple of the things you suggested, but what ended up working was manually entering the vertical and horizontal from my monitor type and then rebooting.

Once it came back up, it worked.  :cool:

---

### Post by Pablasso on 2006-10-15
i just solved my problem, it was a little different since it was on a widescreen lcd and with a 865G chipset

[http://ubuntuforums.org/showthread.php?p=1465348#post1465348](http://ubuntuforums.org/showthread.php?p=1465348#post1465348)

edit: oh yeah.. i didnt tried the i810 driver that you posted

---

### Post by lucis on 2006-10-15
Regarding the alternative i810 driver, /usr/X11R6/lib/modules/drivers doesn't exist on my system.

Edit: I think I found it: /usr/lib/xorg/modules/drivers

Just in case I'm not the only one... :)

Also, if a user pasted the commands into the terminal it wouldn't work as the filename (I presume) is incorrect. The file extension is "so", and the one in the command is "o" :)


```
mkdir ~/src/i810
cd ~/src/i810
wget http://www.fairlite.demon.co.uk/i810_drv.so
cd /usr/X11R6/lib/modules/drivers/   OR   /usr/lib/xorg/modules/drivers
sudo mv i810_drv.so i810_drv.so.old
sudo cp ~/src/i810/i810_drv.so
```

And one last thing... what benefits does the new i810 driver have over the default? Thanks! :)

---

### Post by Aualin on 2006-10-16
> **bodhi.zazen said:**
> ```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Is the same thing. The option **-phigh** selects the defaults for everything except resolution.


But, i always use dpkg-reconfigure xserver-xorg.
Its easy! And the phigh takes longer time...

---

### Post by balloons on 2006-12-19
you should add info about xorg-edit. a GUI for editing your xorg config. Maybe not newbie friendly, but it does have a modeline generator :-)

 [http://www.cyskat.de/dee/progxorg.htm](http://www.cyskat.de/dee/progxorg.htm)

---

### Post by maechler on 2007-01-01
I have a slightly different *big* problem which I'm pretty sure is not so easily solved
(since I've already spent a dozen hours ... of course I'm gladly proven wrong by a solution!  ;)) 
Upgrading (aptitude dist-upgrade after editing /etc/apt/sources.list) from dapper to edgy 
after Christmas unfortunately "broke" my X setup:
To say: My graphic card is a "good old" reliable 
            Matrox MGA 200 AGP Rev.3 with only 8192 kB VideoRam
but it has worked flawlessly for years, providing 1024x768 TrueColor in many incantations of Linux, including Ubuntu Hoary, Warty and Dapper.
Now with the upgrade to Edgy (which meant an upgrade from X windows 6.8.2 to 7.1.1 and actually I believe the bug is there and not with ubuntu proper)

  The monitor (17'' LCD "Philips 170S") refused to show anything on the graphic console but displayed
   ATTENTION:  Cannot display this video mode,
                      change computer display 
                      output to 1280x1024@60Hz.
I started editing /etc/X11/xorg.conf (in a text console of course); trying many different things including those proposed in this thread,
and eventually go to a mode where the monitor did

    ATTENTION:  This is 85Hz overdrive, change computer display 
  output to 1280x1024@60Hz.

As said, I've tried many versions of xorg.conf and I have also saved the corresponding
/var/log/Xorg.0.log files. I have uploaded some of them to [http://stat.ethz.ch/~maechler/ubuntu/xorg-woes/](http://stat.ethz.ch/~maechler/ubuntu/xorg-woes/)
Always a matching pair of  xorg.conf_FOO  and  Xorg.0.log_FOO

Note that I also used the exact correct xorg.conf file that works fine with the ubuntu dapper Live CD (the only dapper I can still easily run on that machine) but gives the above "cannot display ..." message with edgy.

As said, I'm very glad for help --- I hope you see that I've tried a lot already,
and I'm sure this needs some expert insight.
All I need is to be able to tweak 'xserver' (or the mga driver module) to behave as it did by default in Dapper...

(Sorry if this is in the wrong thread; probably should have started a new one;
 I'm more used to mailing lists than such forums)

Martin Maechler, 
ETH Zurich

---

### Post by leradard on 2007-02-10
Thanks a lot for the guide!
I've tried to fix a screen resolution problem for weeks... and this is the page that gave me the answer. Or at least one solution to the problem. (Haven't yet found the way to keep the resolution after restarting my laptop...)

For other users: I have a Fujitsu-Siemens, Amilo M6450G; Screen: 14.0" LCD WXGA, Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04), which looks best with 1280x768 resolution. (I was stuck with the flat 1024x768 )
I use Ubuntu 6.10 *Edgy Eft*

What worked for me was to:
1. install "915resolution",
and
2. to type:
sudo 915resolution 50 1280 768
in a terminal window.

Thanks a lot to the Ubuntu community.

---

### Post by kumarnarain on 2007-07-07
Hai
I have a different problem,,,,

I bought a viewsonic lcd display and a gforce 5200 recently...I have been able to upgrade display settings to 1440X900 by editing my Xorg.conf and restarting the Xserver..but my lcd screen has a blank(black)  left hand side...I have fiddled around with the display adjuster buttons on the lcd panel with no luck...the display does not cover the whole screen...

any help

(sure I am missing the obvious)

---

### Post by iiaiiappa on 2007-09-10
If you are running ubuntu with Intel 800/900 series and not full resolution

follow instructions of:

[https://wiki.ubuntu.com/i915Driver](https://wiki.ubuntu.com/i915Driver)

---

### Post by anselm on 2010-03-01
I was able to get rid of using the nvidia driver and using just xorg.conf file.

Works great on 8.04:p

---

### Post by El3mentGamer on 2010-05-05
How am i supposed to do this when my resolution is so screwed up to where i cant even log in?

---

### Post by bodhi.zazen on 2010-05-06
> **El3mentGamer said:**
> How am i supposed to do this when my resolution is so screwed up to where i cant even log in?

This is somewhat of an old post and you should start a new thread in the support section if you need assistance.

Be sure to tell us what video card you have.

---

### Post by crazytrini on 2010-08-08
i have looked everywhere for the xorg.conf file but i cant find it. i go into etc/x11 and its not there. please help me.

---

### Post by bodhi.zazen on 2010-08-09
> **crazytrini said:**
> i have looked everywhere for the xorg.conf file but i cant find it. i go into etc/x11 and its not there. please help me.

This thread is almost 4 years old =)

xorg.conf has been depreciated , and thus does not exist.

You can write on if you wish, but you are probably better off starting a new thread asking for assistance. Be sure to include a description of your hardware and your problem.

If you wish, write a file with this command:

```
gksu gedit /etc/X11/xorg.conf
```

Write the file and then save it. Then log off and log back in.

Just be sure you know what you are doing or X (your graphical system) may fail outright.

---

### Post by geoffree on 2010-11-27
I have not found xorg.conf file on my computer. I am running Ubuntu 10.04.  
What is the problem?

Geoff

---

### Post by bodhi.zazen on 2010-11-27
> **geoffree said:**
> I have not found xorg.conf file on my computer. I am running Ubuntu 10.04.  
What is the problem?

Geoff

xorg.conf is depreciated, read the post right above yours.

If you are having a problem best to start a new thread and tell us more information. What monitor ? Videocard ? What is the problem ?

With that I am going to close this thread now.

---

