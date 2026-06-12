---
title: "HOWTO: change resolution/refresh rate in Xorg"
date: 2005-10-30
forum: Outdated Tutorials &amp; Tips
---

### Post by heimo on 2005-10-30
[B][SIZE=5]IMPORTANT: [SIZE=3]This is a very old howto (2005), please check more recent documentation for your version of Ubuntu if you need assistance with setting up Xorg, display resolution or anything like that. This howto is not up to date.  [/SIZE][/SIZE]
------------------------------------------------------------------------------------------------------------------------------------
[SIZE=3]Howto: change resolution/refresh rate in Xorg[/SIZE]
[/B][SIZE=3][SIZE=1][SIZE=2]If you can't change your display resolution or refresh rate (no desired option available) these instructions may help.[/SIZE][/SIZE][/SIZE][SIZE=2][B]

Backup your configuration file[/B][/SIZE]
 ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```[B][SIZE=2]
How to reconfigure Xorg
[/SIZE][/B][SIZE=2]Notice that auto detection of devices works best if Xorg is not running. Therefore it's recommended to stop X before reconfiguring [COLOR=Red]this will put you to text only mode / command line[/COLOR]:
[/SIZE]```
sudo /etc/init.d/gdm stop (or kdm for KDE)
``` You can do the whole X configuration process by entering:
```
  sudo dpkg-reconfigure xserver-xorg
```To start Gnome/KDE again:
```
sudo /etc/init.d/gdm start (or kdm for KDE)
```[SIZE=2][B]How to test configuration without restarting X?
[/B]See this [excellent tip]("http://www.ubuntuforums.org/showpost.php?p=679706&postcount=23") from [/SIZE]henriquemaia (Thanks!) 
[SIZE=2]
** How to edit xorg.conf file**[/SIZE]
  Run in terminal or console:
  ```
sudo nano /etc/X11/xorg.conf
``` online help in nano: ctrl+g (ctrl+x exits)
 
[B][SIZE=2]Where is the log file, how to debug?
[/SIZE][/B]File:
```
 /var/log/Xorg.0.log
```contains lots of invaluable debugging information about what's going on as Xorg starts. Watch for lines with EE (errors) and WW (warnings).
  
**[SIZE=2]How to edit or add HorizSync and VertRefresh lines[/SIZE]**
Find your monitors manual (manufacturers website and Google are useful). 
Look for hozizontal sync and vertical refresh rates, also if bandwidth or maximum dot clock / pixel clock is mentioned, write it down.

Edit xorg.conf and put correct values to your xconf.org's *Monitor section*. Something like this:
```
Section "Monitor"
    Identifier    "CM752ET"
    HorizSync     31-101
    VertRefresh    60-160
EndSection

``` Be sure that Identifier is same as the Monitor line in *Screen section*.


**[SIZE=3][SIZE=2]Adding custom modeline[/SIZE][/SIZE]**
If you know what your monitor can do, for example 1024x768@75Hz, you can use this page to generate a custom Modeline for you xorg.conf:
[LIST]
[*]     [online modeline generator]("http://www.dkfz-heidelberg.de/spec/linux/modeline/")
[/LIST]
Copy paste the new Modeline to *Monitor section* (for example):

```
 # 1024x768 @ 75.00 Hz (GTF) hsync: 60.15 kHz; pclk: 81.80 MHzModeline "1024x768_75.00"  81.80  1024 1080 1192 1360  768 769 772 802  -HSync +Vsync
```Watch that the hsync is in range with the HorizSync on the same section (in this example the range is 31-101 and this modelines hsync is 60.15, so we're safe). Also the VertRefresh and the refresh rate you selected (75Hz in this example) should match - in this example VertRefresh is 60-160 and modeline is 75Hz, so that's all good.

Now you can select the default resolution and colordepth by tweaking the *Screen section*. It should look something like this:

```
Section "Screen"
    Identifier    "Default Screen"
    Device        "NVIDIA Corporation NV34 [GeForce FX 5200]"
    Monitor        "CM752ET"
    DefaultDepth    16
    SubSection "Display"
        Depth        16
        Modes      "1024x768_75.00"
    EndSubSection
EndSection

```Monitor name here (CM752ET) matches the Identifier on your Monitor Section. Device line here matches the identifier on your Device section - you get the idea? :) It ties together some settings for your screen - the graphics card and your monitor. You may have more Subsections here, but only one is needed.

Change the DefaultDepth to what you would want it to be, 16 (65536 colors) or 24 (16M colors). Change the Modes line to match the resolutions you want to use - Depth must match DefaultDepth (here it's 16).

Save the config. If you're in X, hit CTRL+ALT+BACKSPACE to restart X (if you're running logon manager like xdm, kdm or gdm). Change between virtual consoles with CTRL + F1 F2 F3 and so on - your X should be on F7. 

Starting the X:
*startx* OR *sudo /etc/init.d/gdm start* (in KDE it's kdm)

If that doesn't work, try fixing the xorg.conf or get back to your original by copying the backup over your changed one with:
```
sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
```When you're back in X, you can cycle through different modes by pressing CTRL+ALT++ (plus sign on numpad), or go to System->Preferences->Screen Resolution.

[B]How to adjust position of your screen?
[/B][SIZE=2]open terminal[/SIZE](Applications->Accessories->Terminal), run xvidtune (type: "xvidtune"), adjust the screen and hit Show-button. You'll see a line with something like this on the terminal screen:
```
"1280x1024"   157.50   1280 1332 1492 1728   1024 1025 1028 1072 +hsync +vsync
```Next you should:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo nano /etc/X11/xorg.conf

``` In Monitor section, add the above line with a prefix "Modeline", like this:
```
Modeline "1280x1024"   157.50   1280 1332 1492 1728   1024 1025 1028 1072 +hsync +vsync
```That should do it. There should be no need to restart X if you did make the change (hit Apply in xvidtune), but you should test that this new change works. Hit ctrl+alt+backspace to restart X. If it doesn't work, you can copy back the old configuration file using:
```
sudo /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
``` and restart X using:
```
sudo /etc/init.d/gdm start

```**[SIZE=3][SIZE=2]:!: Problems? [/SIZE][/SIZE]**[SIZE=2]**Things to try:**[/SIZE]
[LIST]
[*]Check notes concerning your video card in Ubuntu wiki [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCards](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCards)
[*]Check BIOS settings - eg. amount of shared memory
[*]Add to your monitor section line ```
Option "DDC" "False"
```
[*]if you're using kvm (keyboard/video/mouse-switch), try reconfiguring without
[*]try vesa driver instead of your graphics card specific driver
[*]try nv instead of nvidia
[*]try ati instead of fglrx
[*]try intel instead of i810
[*]try 16-bits colors instead of 24-colors
[/LIST]

[LIST]
[*]adding HorizSync and VertRefresh line in Monitor section with correct values from monitors specification
[*]adding custom modeline for your monitor in Monitor section
[LIST]
[*][online modeline generator]("http://www.dkfz-heidelberg.de/spec/linux/modeline/")
[*]gtf generator online: [http://www.sh.nu/nvidia/gtf.php](http://www.sh.nu/nvidia/gtf.php)
[/LIST]

[*]reconfiguring Xorg
[LIST]
[*]```
sudo dpkg-reconfigure xserver-xorg
```
[/LIST]

[*]if you have Intel graphics chip, try installing [855resolution,]("https://wiki.ubuntu.com/FixVideoResolutionHowto") or 915resolution
[*]if having problems to get very high resolution working with nvidia drivers, try adding some or all of these **at your own risk** (some of these may be driver specific - check other documentation before using)>          Option "UseEDIDFreqs" "FALSE"
        Option      "NoBandWidthTest" "TRUE"
        Option "ExactModeTimingsDVI" "TRUE"
        Option "ModeValidation" "NoEdidModes, NoMaxPClkCheck, NoVertRefreshCheck, NoHorizSyncCheck, NoEdidMaxPClkCheck"
[*]Which driver should I use? Is my card supported? See [list of supported cards / chipsets.]("http://xorg.freedesktop.org/wiki/Projects/Drivers?action=show")
[*][Advanced X11 configuration in FreeBSD handbook]("http://www.freebsd.org/doc/en_US.ISO8859-1/books/handbook/x-config.html")
[*]If you're using nvidia driver, try gksudo nvidia-settings
[*]Try booting from Live-CD, if that works, copy /etc/X11/xorg.conf from there
[*]Tips and tricks in this howto: [http://ubuntuforums.org/showthread.php?t=269052](http://ubuntuforums.org/showthread.php?t=269052)
[/LIST]
[B][SIZE=3][SIZE=1][SIZE=2]
Check[/SIZE][/SIZE][/SIZE][/B][SIZE=2] FixVideoResolutionHowto
[/SIZE][[SIZE=3][SIZE=2]https://wiki.ubuntu.com/FixVideoResolutionHowto[/SIZE][/SIZE]]("https://wiki.ubuntu.com/FixVideoResolutionHowto")
 [https://wiki.ubuntu.com/DebuggingXAutoconfiguration](https://wiki.ubuntu.com/DebuggingXAutoconfiguration)
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)


 **[SIZE=2][SIZE=3]Miscellaneous resources[/SIZE] [/SIZE]**[SIZE=2](may contain outdated information)[/SIZE][B][SIZE=2]

Integrated Intel graphics card?
[/SIZE][/B][SIZE=2][http://ubuntuforums.org/showthread.php?t=24923](http://ubuntuforums.org/showthread.php?t=24923) (855resolution, hoary)
[/SIZE]  [http://www.x.org/X11R6.8.2/doc/i810.html](http://www.x.org/X11R6.8.2/doc/i810.html)

** Laptop with Intel graphics and widescreen**
[http://ubuntuforums.org/showthread.php?t=351647](http://ubuntuforums.org/showthread.php?t=351647)

[B]Widescreen
[/B] [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_enable_Large_Widescreen_Support](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_enable_Large_Widescreen_Support)
[B][SIZE=2]
Useful command line tools
[/SIZE][/B]
[LIST]
[*]xresprobe [driver=vesa,ati,nv,nvidia,i810]
[*]  ddcprobe
[/LIST]
[B]Why must I set the correct screen resolution on every startup?
[/B][http://www.ubuntuforums.org/showpost.php?p=248755&postcount=5](http://www.ubuntuforums.org/showpost.php?p=248755&postcount=5)

[B] Online modeline generators:
[/B][ http://sh.nu/nvidia/gtf.php]("http://sh.nu/nvidia/gtf.php")
 [http://www.dkfz-heidelberg.de/spec/linux/modeline/](http://www.dkfz-heidelberg.de/spec/linux/modeline/)
[http://xtiming.sourceforge.net/cgi-bin/xtiming.pl](http://xtiming.sourceforge.net/cgi-bin/xtiming.pl)
[http://koala.ilog.fr/cgi-bin/nph-colas-modelines](http://koala.ilog.fr/cgi-bin/nph-colas-modelines)
[http://zaph.com/Modeline/](http://zaph.com/Modeline/)

**Complete xorg.conf files:**
[http://aleks.vigio.pl/](http://aleks.vigio.pl/)

**What all those options do?**
[http://xorg.freedesktop.org/archive/X11R7.0/doc/html/xorg.conf.5.html](http://xorg.freedesktop.org/archive/X11R7.0/doc/html/xorg.conf.5.html)

Some random links I may need to sort later (mainly about setting widescreen resolution):
[https://bugs.launchpad.net/ubuntu/+s...org/+bug/67369]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/67369")
[http://gentoo-wiki.com/HOWTO_Widescr...lutions_(WSXGA]("http://gentoo-wiki.com/HOWTO_Widescreen_Resolutions_%28WSXGA"))
[http://thoughtworker.in/2007/04/24/k...ht-resolution/]("http://thoughtworker.in/2007/04/24/kubuntu-704-feisty-fawn-getting-right-resolution/")
[https://bugs.launchpad.net/ubuntu/+s...69/comments/21]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/67369/comments/21")

**Installing proprietary drivers**
Envy, Unofficial installer for ati and nvidia drivers:
[http://www.albertomilone.com/nvidia_scripts1.html]("https://launchpad.net/envy")



If anyone wants to copy this guide to Ubuntus wikipages, please feel free to do so.

---

### Post by frodon on 2005-10-30
Hi heimo, nice guide ... really complete

The first 2 links under **Integrated Intel graphics card?** and the link under **Problems with login screen refresh rate?** are broken.

---

### Post by heimo on 2005-10-30
[quote=frodon]Hi heimo, nice guide ... really complete[/quote] 
Thanks! :) There are lots of tips and tricks from all over Ubuntuforums and I've just collected some of those together in one post. I'm quite happy to see that there's not so much need for this guide anymore, Xorg configuration in Breezy is working better than it was in Hoary.

[quote=frodon]
The first 2 links under **Integrated Intel graphics card?** and the link under **Problems with login screen refresh rate?** are broken.[/quote]

Thanks for noticing! (removed/updated)

---

### Post by ubuntuzilla on 2005-11-07
OOPS,  i cut and pasted 
sudo /etc/init.d/gdm stop into the terminal.  

My computer starts but nothing is displayed.  I hear the hard drive spinning but my bios doesn't even display.  The monitor says it's working properly and to check my cables and computer. I can't boot anything on cd either.  

i did sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup first though but still.  With nothing displaying i can't really reset the backup.  Any and all help would be great.  I'm a newbie so i should have known better that to make changed in the terminal but i'm still stuck anyway.  Any help or should i just throw it away.  Sony Viao p2 400mgz, 128mb ram, 10gig hd:(

---

### Post by tseliot on 2005-11-07
[QUOTE=ubuntuzilla]OOPS,  i cut and pasted 
sudo /etc/init.d/gdm stop into the terminal.  

My computer starts but nothing is displayed.  I hear the hard drive spinning but my bios doesn't even display.  The monitor says it's working properly and to check my cables and computer. I can't boot anything on cd either.  

i did sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup first though but still.  With nothing displaying i can't really reset the backup.  Any and all help would be great.  I'm a newbie so i should have known better that to make changed in the terminal but i'm still stuck anyway.  Any help or should i just throw it away.  Sony Viao p2 400mgz, 128mb ram, 10gig hd:([/QUOTE]

Ok, you shouldn't have put that command into the terminal but the problems you describe sound to me as a hardware problem, a coincidence perhaps. The same fact it doesn't display your bios can't be caused by your operative system.

Either the monitor or the graphic card might have stopped working. If you have another monitor (if your notebook has a VGA port) you can try to connect it to your notebook.

---

### Post by ubuntuzilla on 2005-11-10
thanks for the response.  Someone suggested i unplug all pci cards then reboot and that worked.  Now how do i change resolution without destroying my computer again... hmmmmm.

---

### Post by pbb on 2005-11-15
Heimo, thanks for a great howto. I haven't tried it out yet, but it reads easily and seems very complete.
One thing however. Since this guide seems mostly for beginners, I suggest updating the guide with the remark tseliot made ("Ok, you shouldn't have put that command into the terminal..."). Beginners do make beginnner's mistakes, and this saves them from having to read through the comments.

---

### Post by saivert on 2005-12-06
I have nVidia GeForce Go 6600 GPU on my Zepto Znote 6515WD notebook computer.

I want to be able to connect an external monitor and use it to extend my desktop. The monitor will be running at 1280x1024 @ 60Hz (what it supports) and my notebook screen runs natively at 1280x800 (15,4 inch panel) also @ 60 Hz.

Should I use nVidia's TwinView option, the xinerama option or two separate X screens?

I know I have to define two Devices (with same Bus ID) when using two screens, but is TwinView dependant on two Monitor sections or does it simply detect the other monitor and configure it internally using the Option stements in the Device section for my graphics card?

---

### Post by briancurtin on 2005-12-26
[QUOTE=heimo][B]
**[SIZE=3][SIZE=2]:!: Problems? [/SIZE][/SIZE]**[SIZE=2]**Things to try:**[/SIZE][LIST]
[*]vesa driver instead of your graphics card specific driver
[/LIST] 
[/QUOTE]
how would one go about removing the nvidia drivers and returning to the original, or VESA driver?

---

### Post by heimo on 2005-12-27
[quote=briancurtin]how would one go about removing the nvidia drivers and returning to the original, or VESA driver?[/quote]

Choosing vesa / nv / nvidia during reconfiguration or setting Driver line by editin xorg.conf. As far as I know, nv supports 2D acceleration, but you need  [nvidia-glx]("http://packages.ubuntu.com/breezy/x11/nvidia-glx") from repositories or directly from [Nvidia]("http://www.nvidia.com/") for 3D acceleration.

I'm not confident at all here, but I believe the nvidia driver in repository is binary only (not Free), just an older version of the one available directly from Nvidia. I don't know how to change between these too versions "properly", but I've never had any problems. I think you can uninstall nvidia-glx and then install the latest from Nvidia and to change back to older version run the setup program (from Nvidia) to uninstall and then reinstall from Ubuntu repository.

Other drivers, vesa, nv and so on, can coexist without problems and you can change between those just by editing Driver line in xorg.conf

Hopefully this cleared something, I welcome all the comments and corrections. :)

---

### Post by artnay on 2005-12-27
You could use "nano -w" instead of plain nano. If I remember correctly, default installation doesn't bring that as an alias. That way lines won't get messed up.  If you want to tweak xorg.conf using a graphical text editor, remember to replace sudo with gksudo (GNOME) or kdesu (in KDE).

---

### Post by mrhaffer on 2005-12-30
Love you, Heimo

Great guide - Couldn't change resolution.  did reconfigure and all the right numbers were there but then added horizSync and vsync to xorg.conf and Voila!! Boots in 1024X768 with other available modes shown in screen resolution menu.  Been working on this and stumbling around in google until I found your guide.  Have you one on network cards, wireless and ISA?  When I did the expert install I got the ISA but the default seems to recognize the wireless but I can't make it happen.

Thanks again :p :KS :KS :KS :KS :KS

---

### Post by heimo on 2005-12-30
[quote=mrhaffer]Love you, Heimo
Have you one on network cards, wireless and ISA?
[/quote] 
Unfortunately this is my only howto, but there are many more on these forums. And you can always start a new thread and ask specific help to your problems. :)

[quote=mrhaffer]Thanks again :p :KS :KS :KS :KS :KS[/quote] 
Glad it helped you! :) Thanks goes to many helpful fellows on these forums. My howto is based on advice from various sources.

Cheers!

---

### Post by Gustav on 2006-01-02
This is the most useful howto I've found for me. Now I'm blazing away in 1600x1200 (85 Hz) :-D.

I'm linking this post to people with resolution problems at least twice a week.

---

### Post by phil.stone on 2006-01-04
Technically this is dealing with changing screen Dimensions,
not screen Resolution.  Bring up, say, KInfoCenter and 
look at the details for the X-Server, the term Dimensions is
for the 640x480 values or 1600x1200 values.  The Resolution is
different, typically 75 dpi, but can go much higher on modern
displays.

If you have, say, a laptop with a 1600x1200 screen that is only
15 inches across you need to edit the section dealing with the monitor
in order to set the "DisplaySize" to the millimeters of the width 
and height of your screen.

The following is a typical result of the editing, in this case a 
1600x1200 laptop display...

Section "Monitor"
   DisplaySize  305 229
   HorizSync    30-95
   Identifier   "Generic Monitor"
   ModelName    "1600X1200@75HZ"
   Option       "DPMS"
   VendorName   "--> LCD"
  VertRefresh  58-78
EndSection

(Mostly copied from a working SuSE 10.0 system, which can
change these values graphically, without the need for an
editor.)

Note also this is exact for a Thinkpad A31p 1600x1200 
display, some values, like HorizSync may be different for
different systems.  The 305 and 229 are the mm's of the
screen.  You can use a ruler if you don't know your values.

Good Luck changing the Resolution of your display.

Phil

---

### Post by MetalMusicAddict on 2006-01-20
So Im trying to get 100hz refresh on my Dell 2405 widescreen LCD. I do this in windows and it gets rid of the little bit of ghosting that there is.

What should the **HorizSync** and **VertRefresh** be?

```
Section "Monitor"
    Identifier     "DELL 2405FPW"
    Option         "DPMS"
    HorizSync     **?**-**?**
    VertRefresh    **?**-**?**
EndSection
```

---

### Post by heimo on 2006-01-21
[quote=MetalMusicAddict]So Im trying to get 100hz refresh on my Dell 2405 widescreen LCD. I do this in windows and it gets rid of the little bit of ghosting that there is.

What should the **HorizSync** and **VertRefresh** be?

```
Section "Monitor"
    Identifier     "DELL 2405FPW"
    Option         "DPMS"
    HorizSync     **?**-**?**
    VertRefresh    **?**-**?**
EndSection
```[/quote] 
According to [this]("http://support.dell.com/support/edocs/monitors/2405fpw/English/about.htm#Specifioications"):

```
     
HorizSync     30-81
VertRefresh   56-76

``` But 
```
     
HorizSync     30-81
VertRefresh   60

``` for highest resolutions. I don't think it's designed to run at 100Hz (TFTs rarely are, CRTs need higher refresh rates). Try values above first and see if you get rid of the ghosting. Are you using analog cable? If you're, you should probably try DVI / digital.

---

### Post by MetalMusicAddict on 2006-01-21
Naa. With this awesome monitor Im definitely using a DVI. On some gaming fourms is where I found the 100Hz info. A good amount of people mentioned using it so hopefully Ill have no problems. I did it on the win side no problems so far. Ill see how this goes. Thanx man.

---

### Post by eprebys on 2006-01-23
Hi!

I have a T42p, with the ATI card:

0000:01:00.0 VGA compatible controller: ATI Technologies Inc M10 NT [FireGL Mobility T2] (rev 80)

I have it working with the current ATI driver (I think):

eric@communitize:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY FIREGL T2 Pentium 4 (SSE2) (FireGL) (GNU_ICD)
OpenGL version string: 2.0.5582 (8.21.7)

display: :0.0  screen: 1
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY FIREGL T2 Pentium 4 (SSE2) (FireGL) (GNU_ICD)
OpenGL version string: 2.0.5582 (8.21.7)

I used this FAQ for installing this driver:
[http://ubuntuforums.org/showthread.php?t=78466](http://ubuntuforums.org/showthread.php?t=78466)

I have included my dmesg output below.

Now I want to get my Samsung SyncMaster 997DF to display at 1400x1050. I had this working with no problem when the laptop was running Windows, so I know the card/monitor can do it. It appears that the EDID from the monitor doesn't included 1400x1050, and I can't get the IgnoreEDID or NoDDC options to work with this driver. Does anyone have any suggestions?

Relevant sections from /etc/X11/xorg.conf:

Section "ServerLayout"
        Identifier     "Default Layout"
        Screen      0  "aticonfig Screen 0" 0 0
        Screen         "aticonfig Screen 1" RightOf "aticonfig Screen 0"
        InputDevice    "Generic Keyboard"
        InputDevice    "Configured Mouse"
        InputDevice    "Synaptics Touchpad"
EndSection

Section "Monitor"
        Identifier   "aticonfig Monitor 0"
EndSection

Section "Monitor"
        Identifier   "aticonfig Monitor 1"
EndSection

Section "Device"
        Identifier  "ATI Graphics Adapter 0"
        Option      "NoDDC"
        Driver      "fglrx"
        BusID       "PCI:1:0:0"
        Option      "IgnoreEDID"        "on"
EndSection

Section "Device"
        Identifier  "ATI Graphics Adapter 1"
        Option      "NoDDC"
        Driver      "fglrx"
        BusID       "PCI:1:0:0"
        Screen      1
        Option      "IgnoreEDID"        "on"
EndSection


Section "Screen"
        Identifier "aticonfig Screen 0"
        Device     "ATI Graphics Adapter 0"
        Monitor    "aticonfig Monitor 0"
        DefaultDepth     24
        SubSection "Display"
                Modes    "1400x1050"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

Section "Screen"
        Identifier "aticonfig Screen 1"
        Device     "ATI Graphics Adapter 1"
        Monitor    "aticonfig Monitor 1"
        DefaultDepth     24
        SubSection "Display"
                Modes    "1400x1050"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

Section "DRI"
        Mode         0666
EndSection

eric@communitize:~$ cat /var/log/Xorg.0.log | grep WW
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
(WW) The directory "/usr/share/X11/fonts/CID" does not exist.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID".
(WW) Open APM failed (/dev/apm_bios) (No such file or directory)
(WW) Ignoring request to load module GLcore
(WW) fglrx(0): board is an unknown third party board, chipset is supported
(WW) fglrx(1): board is an unknown third party board, chipset is supported
(WW) fglrx(0): Option "NoDDC" is not used
(WW) fglrx(0): Option "IgnoreEDID" is not used
(WW) Open APM failed (/dev/apm_bios) (No such file or directory)
(WW) Open APM failed (/dev/apm_bios) (No such file or directory)


eric@communitize:~$ dmesg | grep fglrx
[4294718.578000] [fglrx] Internal AGP support requested, but kernel AGP support active.
[4294718.578000] [fglrx] Have to use kernel AGP support to avoid conflicts.
[4294718.578000] [fglrx] Kernel AGP support doesn't provide agplock functionalit y.
[4294718.578000] [fglrx] AGP detected, AgpState   = 0x1f000217 (hardware caps of  chipset)
[4294718.579000] [fglrx] AGP enabled,  AgpCommand = 0x1f000314 (selected caps)
[4294718.785000] [fglrx] free  AGP = 252440576
[4294718.785000] [fglrx] max   AGP = 252440576
[4294718.785000] [fglrx] free  LFB = 114274304
[4294718.785000] [fglrx] max   LFB = 114274304
[4294718.785000] [fglrx] free  Inv = 0
[4294718.785000] [fglrx] max   Inv = 0
[4294718.785000] [fglrx] total Inv = 0
[4294718.785000] [fglrx] total TIM = 0
[4294718.785000] [fglrx] total FB  = 0
[4294718.785000] [fglrx] total AGP = 65536
[4294718.896000] [fglrx] free  AGP = 252440576
[4294718.896000] [fglrx] max   AGP = 252440576
[4294718.896000] [fglrx] free  LFB = 74424320
[4294718.896000] [fglrx] max   LFB = 74424320
[4294718.896000] [fglrx] free  Inv = 0
[4294718.896000] [fglrx] max   Inv = 0
[4294718.896000] [fglrx] total Inv = 0
[4294718.896000] [fglrx] total TIM = 0
[4294718.896000] [fglrx] total FB  = 0
[4294718.896000] [fglrx] total AGP = 65536

---

### Post by heimo on 2006-01-23
[quote=eprebys]
I have a T42p, with the ATI card:
[/quote]

Hi!

Have you tried adding custom modeline? (see first post on this thread)

---

### Post by eprebys on 2006-01-24
I did try a custom modeline. My xorg.conf included this:

Section "Monitor"
        Identifier   "aticonfig Monitor 0"
        HorizSync       31-101
        VertRefresh     60-160
        # V-freq: 85.00 Hz  // h-freq: 94.05 KHz
        Modeline "1400x1050" 211.42  1400 1512 1768 2248  1050 1050 1054 1106
EndSection

Section "Monitor"
        Identifier   "aticonfig Monitor 1"
        HorizSync       31-101
        VertRefresh     60-160
        # V-freq: 85.00 Hz  // h-freq: 94.05 KHz
        Modeline "1400x1050" 211.42  1400 1512 1768 2248  1050 1050 1054 1106
EndSection

I saw no difference with this configuration.

The thing that looks wrong to me is that the NoDDC and IgnoreEDID options are being ignored by the ATI driver. Is the syntax different? Is there some other way to get the driver to ignore the EDID?

---

### Post by heimo on 2006-01-25
Just a guess, but you could try:
```
Option "UseEdidFreqs" "0"

```

---

### Post by henriquemaia on 2006-01-25
Hi,

Very nice guide. I just want to make a small suggestion. In the end, instead of restarting gdm, one should first test if the configuration is right. As most newbies wouldn't know what to do if their X is lost, it's better to do

```
sudo xinit -- :2
```

where one can see the result on a new X (ctrl+alt+F9) without losing the first. If something goes wrong, one can easily use the backup configuration under their surviving X (ctrl+alt+F7).

---

### Post by eprebys on 2006-01-25
I tried this, and got the same message in /var/log/Xorg.0.log indicating that the setting was not used/recognized:

(WW) fglrx(0): Option "UseEdidFreqs" is not used

Is this the right place to be asking this question or should I be trying to ask someone at ATI?

---

### Post by Rellik on 2006-01-25
[QUOTE=henriquemaia]Hi,

Very nice guide. I just want to make a small suggestion. In the end, instead of restarting gdm, one should first test if the configuration is right. As most newbies wouldn't know what to do if their X is lost, it's better to do

```
sudo xinit -- :2
```

where one can see the result on a new X (ctrl+alt+F9) without losing the first. If something goes wrong, one can easily use the backup configuration under their surviving X (ctrl+alt+F7).[/QUOTE]

Great tip :D thanks!  Would anyone mind telling me, though, how to stop that secondary X once it's started?  Very useful, not having to restart the computer and all :P could have saved me half an hour at least as I'm working with this xorg stuff

---

### Post by eprebys on 2006-01-30
No one out there has any ideas?

Thanks for anything!

---

### Post by eprebys on 2006-01-30
This is the crummy response I got from ATI:

"
ATI does not provide direct technical support for laptops/notebooks at this current time (telephone or email). If you require direct technical support please contact the system manufacturer of your laptop/notebook.
"

ugh... i'm out of leads on this. i am afraid that i'm going to have to give up on ubuntu. i have had *constant* problems with the wireless and video card drivers. Basic functionality doesn't work well: vpn, docking, hibernation. I can't easily install current versions of core software: firefox. And the desktop search is still mediocre and broken: beagle.

The tools that I'm using linux for (emacs, ethereal, apache, gimp and a good terminal) have major problems running on windows, but I can use cygwin and run them on a server.

I had high hopes for ubuntu but when current off the shelf hardware requires many hours of tinkering, and even then you don't end up with a robust system, what's the benefit? I've had ubuntu crash on me and demonstrate more instability than any windows installation i've ever used.

---

### Post by Berdobenz on 2006-02-03
Im very new to linux as well as ubuntu I was trying to edit the resolution so 
I made a backup file for xorg.conf

then I typed sudo /etc/init.d/gdm stop (or kdm for KDE)
my computer restarted and now I cant get on the internet 

I tryed to sudo /etc/init.d/gdm start 

help lol

---

### Post by tseliot on 2006-02-03
[QUOTE=Berdobenz]Im very new to linux as well as ubuntu I was trying to edit the resolution so 
I made a backup file for xorg.conf

then I typed sudo /etc/init.d/gdm stop (or kdm for KDE)
my computer restarted and now I cant get on the internet 

I tryed to sudo /etc/init.d/gdm start 

help lol[/QUOTE]
The command "sudo /etc/init.d/gdm stop" should only get you to the command line (you won't see the Desktop Environment GNOME or KDE). Are you sure it restarted you computer?

---

### Post by Berdobenz on 2006-02-03
your right i restarted it... the gui comes back on but I cant get on the net the error message says i to recheck the web site name.


thanks for helping

---

### Post by tseliot on 2006-02-03
[QUOTE=Berdobenz]your right i restarted it... the gui comes back on but I cant get on the net the error message says i to recheck the web site name.


thanks for helping[/QUOTE]
Ok, click on System/Administration/Networking (in the GNOME panel)

If you use an ethernet connection you will see something like:
```
Ethernet Connection
The interface eth0 is active
```

Tell me what you see.

---

### Post by geearf on 2006-02-05
Hello,
I have a little problem now, the resolution / refresh rate is okay, but I have to set it back everytime I start KDE.
And I tick the little "set it up at next boot" thing, but it does not work :(

If you have any idea on this thanks.

---

### Post by fangorious on 2006-02-14
I'm having trouble getting refresh rates above 60 Hz, and some widescreen resolutions seem to be unavailable. I have an HP Compaw nw8240 laptop with an Ati Mobility FireGL V5000. I'm using the latest drivers (8.22.5 [1]) installed according to the HOWTO on this forum [2]. I have configured the refresh rate according to the only documentation I could find, a pdf file on HP's forums [3]. 

Under Windows, I have a very wide range of resolutions available, from 1920-1200 down to 640x480. I primarily use the widescreen resolution of 1680x1050. All resolutions seem to be supported up to 100 Hz refresh rate. 

So now on to the Linux supported resolutions and refresh rates. After installing the Ati driver and rebooting into single user mode, I ran 'sudo dpkg-reconfigure xserver-xorg' and specified the HorizSync and VertRefresh from the linked pdf, and selected these resolutions: 1920x1200; 1680x1050; 1600x1200; 1440x900; 1400x1050; 1280x1024; 1280x960; 1280x864; 1280x800; 1152x864; 1152x768; 1024x768; 800x600; 640x480. The xserver-xorg reconfigure generated this one Modeline ```
        Modeline        "1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
```

After booting all the way into gdm and logging in, I go to System->Preferences->Screen Resolution and am presented with the following resolutions (in this order): 1920x1200; 1600x1200; 1280x1024; 1280x800; 1152x864; 1024x768; 800x600; 1920x1080. I have no choice for refresh rate, only 60 Hz is available. So used one of the modeline generators [4] and create these modelines

```

        Modeline        "1920x1200@75i" 114.37 1920 1952 2384 2416 1200 1226 1234 1261 interlace
        Modeline        "1680x1050@75" 210.42 1680 1712 2504 2536 1050 1070 1083 1103
        Modeline        "1440x900@75" 146.10 1440 1472 2024 2056 900 917 928 946

```

and restart X (System->Logout, <ctrl>+<alt>+<del> at the login screen, then login) and find they had no effect. First off I would really like to get 75 Hz (or better) refresh rate, and secondary I would like to have the resolutions 1680x1050 and 1440x900 supported (at 75 Hz or better).

[1] [https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=300](https://support.ati.com/ics/support/default.asp?deptID=894&task=knowledge&folderID=300)
[2] [http://ubuntuforums.org/showpost.php?p=423584](http://ubuntuforums.org/showpost.php?p=423584)
[3] [http://h10018.www1.hp.com/wwsolutions/linux/products/clients/HP_whitepaper_Mobiles_Linux_062205.pdf](http://h10018.www1.hp.com/wwsolutions/linux/products/clients/HP_whitepaper_Mobiles_Linux_062205.pdf)
[4] [http://xtiming.sourceforge.net/cgi-bin/xtiming.pl](http://xtiming.sourceforge.net/cgi-bin/xtiming.pl)

Here's my xorg.conf

```
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

Section "Module"
	Load	"GLcore"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"v4l"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. FireGL v5000"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Samsung LCD"
	Option		"DPMS"
	HorizSync	31.5-91.1
	VertRefresh	60-100
	Modeline	"1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
        Modeline	"1920x1200@75i" 114.37 1920 1952 2384 2416 1200 1226 1234 1261 interlace
        Modeline	"1680x1050@75" 210.42 1680 1712 2504 2536 1050 1070 1083 1103
        Modeline	"1440x900@75" 146.10 1440 1472 2024 2056 900 917 928 946

EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. FireGL v5000"
	Monitor		"Samsung LCD"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1920x1200" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1920x1200" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1920x1200" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1920x1200" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1920x1200" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1920x1200" "1680x1050" "1600x1200" "1440x900" "1400x1050" "1280x1024" "1280x960" "1280x854" "1280x800" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by heimo on 2006-02-14
[quote=fangorious]I'm having trouble getting refresh rates above 60 Hz, and some widescreen resolutions seem to be unavailable.[/quote] 
Excellent post. :KS I hope I can help, but am not sure. Let's try.

Do you have fglrxconfig available? I don't know if the ati drivers you've installed included this, but it seems to be also in package fglrx-control. Make a backup copy of your xorg.conf and run this tool. Also check your log file and if possible, attach it your post. 

Good luck.

EDIT: I must add that I have zero experience using current ati graphics cards.

---

### Post by Screaming Monkey on 2006-02-15
Heimo, thanks for this very helpful how-to...I've been having a beach of a time with the resolution problem on my computer with an older video card (Cirrus Logic GD5446) and hadn't been able to get it past 640x480.  Thanks to some little things in your how-to I got it up to 800x600, a manageable resolution.  Thanks.\\:D/

---

### Post by fangorious on 2006-02-15
[QUOTE=heimo]Excellent post. :KS I hope I can help, but am not sure. Let's try.

Do you have fglrxconfig available? I don't know if the ati drivers you've installed included this, but it seems to be also in package fglrx-control. 
[/QUOTE]

fglrxconfig has been superceded by aticonfig. I ran this

```

sudo aticonfig --effective=startup --resolution=1920x1200,1680x1050,1600x1200,1440x900,1280x1024,1280x960,1152x864,1152x768,1024x768,800x600,640x480 --hsync=31.5-91.1 --vrefresh=60-100 --lcd full --fsaa=on -fs 4 -fsg on

```

and it generated the xorg.conf pasted below. But it didn't have any effect. Still stuck at 60 Hz. The Modelines were, I believe just preserved from the old config, rather than generated by aticonfg. I've attached a bzip'ed copy of my /var/log/Xorg.0.log

xorg.conf:

```

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"

        # paths to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/CID"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load  "GLcore"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "v4l"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc104"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ImPS/2"
	Option	    "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
	Identifier  "Synaptics Touchpad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizScrollDelta" "0"
EndSection

Section "Monitor"
	Identifier   "Samsung LCD"
	HorizSync    31.5 - 91.1
	VertRefresh  60.0 - 100.0
	Option	    "DPMS"
	ModeLine     "1920x1200@75i" 114.4 1920 1952 2384 2416 1200 1226 1234 1261 interlace
	ModeLine     "1680x1050@75" 210.4 1680 1712 2504 2536 1050 1070 1083 1103
	ModeLine     "1440x900@75" 146.1 1440 1472 2024 2056 900 917 928 946
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. FireGL v5000"
	Driver      "fglrx"
	Option	    "(null)"
	Option	    "Centermode" "off"
	Option	    "FSAAEnable" "on"
	Option	    "FSAAScale" "4"
	Option	    "FSAADisableGamma" "off"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. FireGL v5000"
	Monitor    "Samsung LCD"
	DefaultDepth     24
	SubSection "Display"
		Depth     8
		Modes    "1920x1200" "1680x1050" "1600x1200" "1440x900" "1280x1024" "1280x960" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1920x1200" "1680x1050" "1600x1200" "1440x900" "1280x1024" "1280x960" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1920x1200" "1680x1050" "1600x1200" "1440x900" "1280x1024" "1280x960" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

```

---

### Post by fangorious on 2006-02-18
In an effort to force X to use one of the custom Modelines, I changed to only include those resolutions. My expectation was that it would either run at 75 Hz or not even load X. But I was wrong, xvidtune confirms that even with only the 75 Hz resolutions configured, I'm still only getting 60 Hz. This is really irritating.

```

Section "Monitor"
	Identifier	"Samsung LCD"
	Option		"DPMS"
	HorizSync	31.5-91.1
	VertRefresh	60-100
	Modeline	"1920x1200@75i" 114.37 1920 1952 2384 2416 1200 1226 1234 1261 interlace
	Modeline	"1680x1050@75" 210.42 1680 1712 2504 2536 1050 1070 1083 1103
	Modeline	"1440x900@75" 146.10 1440 1472 2024 2056 900 917 928 946
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. RaMobility FireGL v5000"
	Monitor		"Samsung LCD"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1920x1200@75i" "1680x1050@75" "1440x900@75"
	EndSubSection
EndSection

```

---

### Post by smokinfish on 2006-02-19
This is a bit too involved for me. I can only select 1024x768 -

I know I prefer things on my screen to be a bit smaller, (the resolution higher?) but have no idea of what the actual resolution I prefer is. 

I've looked in the dvices list and can't even anything that resembles my laptop screen, but then I thought this was supposed to be a competitor for windows? I didn't need a minor degree in computer science to change the resolution in that! 

Can't all this stuff be put into some sort of generic app that changes the screen resolution for you? It seems to be a common problem and would therefore warrant some development imho - I'd ofer to do it but I have no idea what I'm doing!

I just want to select the different screen resolutions, without having to spend an age learning programming code, it should come as standard, I mean, it's one of the basics surely!?

I hope someone can help cos this is the only real thing that's spoiling my Ubuntu experience so far..

:-?

---

### Post by heimo on 2006-02-19
[quote=smokinfish]This is a bit too involved for me. I can only select 1024x768 -[/quote] 

```
sudo dpkg-reconfigure xserver-xorg
```

When it asks your monitor specification, use expert/advanced option and enter the horizsync and vertrefresh values from your monitors manual. WIthout further information  I can't help better and strongly recommend you to open a new thread so that it'll get more attention (please feel free to post a link to that thread in this thread). You can also try [another Linux distribution]("http://distrowatch.com/") if Ubuntu won't work for you. I've heart that [Linspire]("http://www.linspire.com/") is trying to be a Windows competitor.

---

### Post by smokinfish on 2006-02-20
But I don't know all that stuff about my monitor - it's just the screen attached to my laptop - which is a Sony Vaio PCG-R600HMPD - I'm sorry, I don't want to stop using Ubuntu, I'm just frustrated as I've been trying to fix this for some days now with no avail :(

The one thing that I LOVE about it is the fact that it's held together by people who can help make it work - my point was, if it was possible to put this entire thread into an app, that would make it a much easier experience for new peeps like me - and therefore would help spread the Ubuntu word a bit further!

:-#

---

### Post by heimo on 2006-02-20
[quote=smokinfish]But I don't know all that stuff about my monitor - it's just the screen attached to my laptop - which is a Sony Vaio PCG-R600HMPD [/quote] 
Find your laptops manual in Sonys support pages, check the specification sheet / page for details of display.
[http://esupport.sony.com/perl/select-system.pl?DIRECTOR=DOCS]("http://esupport.sony.com/perl/select-system.pl?DIRECTOR=DOCS")

Alternatively you can try to run *sudo ddcprobe* and *sudo xresprobe vesa *to get more information. Also command *lspci | grep -i vga *may reveal some useful information.

If I'd have to guess, your problem with resolution is driver related, not about monitor setting (vertrefresh/horizsync). In my experience that's more common with CTR monitors.

It's not really that difficult to tweak xorg.conf file, lots of Linux newbies have succeeded. Yes, it's a shame that autodetection fails every now and then, but making a tool to guess some settings and correcting xorg.conf would be fixing the problem at the wrong end and it would never be ready. 

A howto page and helpful community forum is a more flexible (even though burdensome) solution until the problem has been fixed by time (old monitors do not autodetect) and programmers. Some distributions make it easier. Buying a preinstalled computer with Linux on it, makes it a non-problem. If this discussion needs to be continued, let's move it to more appropriate forum and prevent cluttering this thread, which is more about getting the first aid, collecting all the tips&tricks to make Xorg.conf resolution/refresh-rate related settings in Ubuntu. Thank you very much. :)

---

### Post by fangorious on 2006-03-01
I added some Modelines for 1680x1050 and 1440x900 at 60 Hz, and I can at least get those resolutions now. Someone on the HP forums said Linux seems to require 60 Hz for LCD displays, seems silly. Anyhow At both those resolutions I have line of white pixels about 1 pixel high at the bottom of the screen. Is there a tool to adjust the geometry of the displayed image on the physical screen?

---

### Post by ahh_dee on 2006-03-02
I just made a new install great

---

### Post by henriquemaia on 2006-03-10
[QUOTE=fangorious]I added some Modelines for 1680x1050 and 1440x900 at 60 Hz, and I can at least get those resolutions now. Someone on the HP forums said Linux seems to require 60 Hz for LCD displays, seems silly.[/QUOTE]

I used to think that too, as I couldn't get my LG L1750S (LCD) to display its full 1280x1024@75 Hz. But I found that the only modeline configurators that worked for me were the [http://sh.nu/nvidia/gtf.php](http://sh.nu/nvidia/gtf.php) and [http://zaph.com/Modeline/](http://zaph.com/Modeline/) . this last one generates a XFree line, but it works as fine as the normal modeline.

Now my monitor is working right @75 Hz.

Try for yourself different modeline calculators and see if any of them works.

---

### Post by henriquemaia on 2006-03-10
[QUOTE=Rellik]Great tip :D thanks!  Would anyone mind telling me, though, how to stop that secondary X once it's started?  Very useful, not having to restart the computer and all :P could have saved me half an hour at least as I'm working with this xorg stuff[/QUOTE]

On that secondary X, press CTRL+ALT+Backspace. That will terminate the X server and return you to the remainder X. Tested.

---

### Post by vincent orange on 2006-03-10
excellent thread it helped me with my monitor problems, thank you

---

### Post by biguns on 2006-03-15
A great thread like this is like a gift that keeps on giving.  I just got a 24 " Dell 2405FPW and I can at least get 1600x1200 instead of 800x600. Thank you. Thank you. Thank you.

---

### Post by Ancalagon on 2006-03-15
[QUOTE=pbb]
Since this guide seems mostly for beginners, I suggest updating the guide with the remark tseliot made ("Ok, you shouldn't have put that command into the terminal..."). Beginners do make beginnner's mistakes, and this saves them from having to read through the comments.[/QUOTE]

As a super-noob, I have a really dumb question.  Where (if not in a terminal window) should I enter the following command to close Xorg?

sudo /etc/init.d/gdm stop

Thanks!

---

### Post by Christopher on 2006-03-15
Im NEW to Linux and i edited my xorg.conf & I was wondering if someone can take a look at it and tell me if i did it correctly. I got the Horizontal Freq & Vertical Freq from my monitor manual, Here's my xorg.conf:


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
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
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
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
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
	Identifier	"NVIDIA Corporation NV40 [GeForce 6800 GT]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	VideoRam	256
EndSection

Section "Monitor"
	Identifier	"NEC MultiSync FE992"
	Option		"DPMS"
	HorizSync	30-98
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV40 [GeForce 6800 GT]"
	Monitor		"NEC MultiSync FE992"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection


Thankyou in advance.

---

### Post by Ancalagon on 2006-03-15
Hey Christopher,

Before you edited your xorg.conf, did you close Xorg?  If so, where did you type sudo /etc/init.d/gdm stop?

Thanks

---

### Post by Christopher on 2006-03-15
[QUOTE=Ancalagon]Hey Christopher,

Before you edited your xorg.conf, did you close Xorg?  If so, where did you type sudo /etc/init.d/gdm stop?

Thanks[/QUOTE]

Well what happened was I edited my xorg.conf manually using this [http://www.ubuntuforums.org/showthread.php?t=75610&highlight=click+root+trick](http://www.ubuntuforums.org/showthread.php?t=75610&highlight=click+root+trick)    
 then saved it and hit control-alt-backspace and I got a  black screen with a login prompt. So I logged in with username and password and typed the command sudo dpkg-reconfigure xserver-xorg and it manually took me through it and then i copied and pasted my xorg.conf here.  Is there something wrong with it? Thank you in advance.

---

### Post by Christopher on 2006-03-17
Can someone tell me if my Xorg.conf looks ok, thank you in advance.

---

### Post by henriquemaia on 2006-03-18
[QUOTE=Christopher]Can someone tell me if my Xorg.conf looks ok, thank you in advance.[/QUOTE]

Hi, as stated here:

[http://ubuntuforums.org/showthread.php?t=75074](http://ubuntuforums.org/showthread.php?t=75074)

You have to comment out the options marked in red (adding a # before it, like I did).

Section "Module"
[COLOR="Red"]**#**Load "GLcore"[/COLOR]
Load "bitmap"
Load "ddc"
[COLOR="Red"]**#**Load "dri"[/COLOR]
Load "extmod"
Load "freetype"
Load "glx"
Load "int10"
Load "type1"
Load "vbe"
EndSection

Other thing, if you're using Nvidia proprietary driver, you'll have to follow that other HowTo to make it work. Your xorg.conf file looks ok, but it won't work unless you load the Nvidia driver onto the kernel.

---

### Post by Christopher on 2006-03-18
[QUOTE=henriquemaia]Hi, as stated here:

[http://ubuntuforums.org/showthread.php?t=75074](http://ubuntuforums.org/showthread.php?t=75074)

You have to comment out the options marked in red (adding a # before it, like I did).

Section "Module"
[COLOR="Red"]**#**Load "GLcore"[/COLOR]
Load "bitmap"
Load "ddc"
[COLOR="Red"]**#**Load "dri"[/COLOR]
Load "extmod"
Load "freetype"
Load "glx"
Load "int10"
Load "type1"
Load "vbe"
EndSection

Other thing, if you're using Nvidia proprietary driver, you'll have to follow that other HowTo to make it work. Your xorg.conf file looks ok, but it won't work unless you load the Nvidia driver onto the kernel.[/QUOTE]

Ok I commented out those lines you listed above & im using Nvidia's latest drivers as of 3 days ago. I used Method 2 to install my Nvidia divers and I get the nvidia splash screen on boot up. Here my xorg.conf now:

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
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	#Load	"GLcore"
	Load	"bitmap"
	Load	"ddc"
	#Load	"dri"
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
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
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
	Identifier	"NVIDIA Corporation NV40 [GeForce 6800 GT]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	VideoRam	256
EndSection

Section "Monitor"
	Identifier	"NEC MultiSync FE992"
	Option		"DPMS"
	HorizSync	30-98
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV40 [GeForce 6800 GT]"
	Monitor		"NEC MultiSync FE992"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

Is there a command I can use in terminal to test them? Sorry im NEW to linux..hehe. How do I know the Nvidia driver is loaded onto the kernel? Thank you in advance. ;)

---

### Post by henriquemaia on 2006-03-18
Hi,

You have the Nvidia driver loaded, since you get the Nvidia logo at X startup. 

To test your modifications to your xorg.conf file without loosing your present X, open a terminal and type: 

```
sudo xinit -- :1
```

where **:1** can be any number greater than 0 (by default, Xserver opens on :0, so to open another, use :1, :2, and so on).

If everything is ok, it will open a new X screen and jump automaticaly to it. To stop it, when you are already in it, press CONTROL+ALT+BACKSPACE. 

If anything is wrong with your configuration, you'll get the error printed out on the terminal.

---

### Post by Christopher on 2006-03-19
[QUOTE=henriquemaia]Hi,

You have the Nvidia driver loaded, since you get the Nvidia logo at X startup. 

To test your modifications to your xorg.conf file without loosing your present X, open a terminal and type: 

```
sudo xinit -- :1
```

where **:1** can be any number greater than 0 (by default, Xserver opens on :0, so to open another, use :1, :2, and so on).

If everything is ok, it will open a new X screen and jump automaticaly to it. To stop it, when you are already in it, press CONTROL+ALT+BACKSPACE. 

If anything is wrong with your configuration, you'll get the error printed out on the terminal.[/QUOTE]

Nope no errors at all printed out in my terminal. :D

---

### Post by henriquemaia on 2006-03-28
[QUOTE=heimo]

[ http://sh.nu/nvidia/gtf.php]("http://sh.nu/nvidia/gtf.php")
[http://www.dkfz-heidelberg.de/spec/linux/modeline/]("http://www.dkfz-heidelberg.de/spec/linux/modeline/")
[http://xtiming.sourceforge.net/cgi-bin/xtiming.pl]("http://xtiming.sourceforge.net/cgi-bin/xtiming.pl")
[http://koala.ilog.fr/cgi-bin/nph-colas-modelines]("http://koala.ilog.fr/cgi-bin/nph-colas-modelines")
[http://zaph.com/Modeline/](http://zaph.com/Modeline/)


If anyone wants to copy this guide to Ubuntus wikipages, please feel free to do so.[/QUOTE]

I was configuring a Samsung SyncMaster 204B and I was not getting its refresh rate properly configured. I've tested each one of that online modeline generators but I had no luck with any of them. Even though I selected 1600x1200@60hz, I was always getting 1600x1200@65hz. Then I googled a bit and found this one:

[http://www.tkk.fi/Misc/Electronics/faq/vga2rgb/calc.html](http://www.tkk.fi/Misc/Electronics/faq/vga2rgb/calc.html)

It worked. As stated before, anyone with problems when trying to configure the proper refresh rate for your TFT/LCD display, do no just try a single modeline generator. Try each one until you get the result you expect. I have configured correctly a LG1750S and a Samsung, but for each one I had to use a different modeline generator.

Also, try to get as much information about your monitor as possible (horizontal and vertical maximum and minumum refresh rates, maximum pixel clock and so on as stated on the manual). This info might help you in getting the proper result.

Hope this helps someone.

---

### Post by nemiroff on 2006-04-22
[QUOTE=henriquemaia]Hi,

Very nice guide. I just want to make a small suggestion. In the end, instead of restarting gdm, one should first test if the configuration is right. As most newbies wouldn't know what to do if their X is lost, it's better to do

```
sudo xinit -- :2
```

where one can see the result on a new X (ctrl+alt+F9) without losing the first. If something goes wrong, one can easily use the backup configuration under their surviving X (ctrl+alt+F7).[/QUOTE]


yess!!, it is really a perfect idea for new users. But, if something goes wrong on new X server, how can we stop it and try again ?

I am receiving below error when I turn back to old-server and try to start the new-server, 

[COLOR="Navy"]Fatal server error:
Server is already active for display 2
        If this server is no longer running, remove /tmp/.X2-lock
        and start again.


Please consult the The X.Org Foundation support
         at [http://wiki.X.Org](http://wiki.X.Org)
 for help.


Xlib: connection to ":2.0" refused by server
Xlib: No protocol specified

giving up.
xinit:  unable to connect to X server
xinit:  No such process (errno 3):  unexpected signal 2.[/COLOR]

I see there is something to stop but I don't know how to do!
Or each time, I need to wait some.. I couldn't figure out

Thanks, waiting another perfect tip](*,)

---

### Post by henriquemaia on 2006-04-22
[QUOTE=nemiroff]yess!!, it is really a perfect idea for new users. But, if something goes wrong on new X server, how can we stop it and try again ?

I am receiving below error when I turn back to old-server and try to start the new-server, 

[COLOR="Navy"]Fatal server error:
Server is already active for display 2
        If this server is no longer running, remove /tmp/.X2-lock
        and start again.


Please consult the The X.Org Foundation support
         at [http://wiki.X.Org](http://wiki.X.Org)
 for help.


Xlib: connection to ":2.0" refused by server
Xlib: No protocol specified

giving up.
xinit:  unable to connect to X server
xinit:  No such process (errno 3):  unexpected signal 2.[/COLOR]

I see there is something to stop but I don't know how to do!
Or each time, I need to wait some.. I couldn't figure out

Thanks, waiting another perfect tip](*,)[/QUOTE]

To stop the new X server, just press ctrl+alt+backspace when you're in it. 

The error you are getting is due to the fact that X is already (or still, if you prefer) running on that display (:2).

---

### Post by unfnknblvbl on 2006-07-08
Hi all, first post here

I'm having some trouble with getting my resolution right under Ubuntu 6.06 - with the "nvidia" driver, it just wants to run in 800x600, no matter what I edit the xorg.conf file to say. Even if I delete all the resolutions other than 1280x1024, it still insists in booting in 800x600.

It *was* working at 1280x1024 with XGL/compiz and everything, but earlier this evening I booted into Windows to use one of those annoyingly Windows-only apps that forces you to lose all that space to Windows, and then when I tried starting up Ubuntu again, it just gave me a rude look, so to speak.

I don't get it? :confused: 
This has happened before, too, and I don't know how I fixed it, because my guitar fell on the computer and reset it... when it booted up, it was working perfectly, so I didn't touch anything.

Also, if I boot up using the install disc, the LiveCD boots into 800x600 too! WTF? :confused: 

anyway, what follows is my xorg.conf file as it is now, with bits commented out and changed to make it work:

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
#	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
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
	Driver		"nv"
#	Driver		"nvidia"
	BusID		"PCI:1:0:0"
#	Option 		"RenderAccel" 		"true"
#	Option		"AllowGLXWithComposite" "true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
# 	V-freq: 60.00 Hz  // h-freq: 63.73 KHz
	Modeline "1280x1024" 109.62  1280 1336 1472 1720  1024 1024 1026 1062 
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV43 [GeForce 6600 GT]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
#	DefaultMode	"1280x1024"
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
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

Section "DRI"
	Mode	0666
EndSection

#Section "Extensions"
#          Option  "Composite" "Enable"
#EndSection

```

...Xorg doesn't spit out any errors, either....

EDIT: I'm using this monitor: [http://www.mitsubishielectric.com.au/PRODUCTS/COMPP/MONITORS/DV1772FD.htm](http://www.mitsubishielectric.com.au/PRODUCTS/COMPP/MONITORS/DV1772FD.htm)

---

### Post by jan on 2006-07-08
This thread is a straight shot on Ubuntu - I've got these problems since my beginning with it. ](*,)

---

### Post by PingunZ on 2006-07-08
Is it usefull to follow this guide when the resolution and refresh rates are fine atm ?
I had my nvidia drivers installed by automatix

edit :: nice guide ;)

Grtz PingunZ

---

### Post by unfnknblvbl on 2006-07-09
Well, I fixed it by completely uninstalling XGL, Compiz, and the nVidia drivers, then reinstalling them all from scratch.

sigh

---

### Post by kevanf1 on 2006-07-10
Strange one, possibly, here.  Can anybody give a me a pointer on how I go about changing the resolution of the graphical log in page?  Once I have logged in the resolution is fine but in the actual GUI log in screen it is something like 600x400.

Cheers.

---

### Post by usp8riot on 2006-07-12
Forget all the other examples and just go here: [http://www.ubuntuforums.org/archive/index.php/t-186021.html](http://www.ubuntuforums.org/archive/index.php/t-186021.html)

Do it just as tseliot says except use the underscore after every resolution number. No tinkering with the modeline generators. Apparently x does that automatically given the input from the hardware. I've been messing with it for hours and none worked and none are as simple as this.

Kevanf1: I believe the login uses the first specified resolution in your x config file from what I've read. I was wondering the same thing.

---

### Post by kevanf1 on 2006-07-12
> **usp8riot said:**
> 
Kevanf1: I believe the login uses the first specified resolution in your x config file from what I've read. I was wondering the same thing.

Ah, I'll check in the file.  I certainly don't want 600x400 as I am never likely to need it.

Cheers for that.

---

### Post by vlastikw on 2006-07-17
> **henriquemaia said:**
> Hi,

Very nice guide. I just want to make a small suggestion. In the end, instead of restarting gdm, one should first test if the configuration is right. As most newbies wouldn't know what to do if their X is lost, it's better to do

```
sudo xinit -- :2
```

where one can see the result on a new X (ctrl+alt+F9) without losing the first. If something goes wrong, one can easily use the backup configuration under their surviving X (ctrl+alt+F7).


or try
```
$ startx -- :2
```

---

### Post by keltong on 2006-08-12
> **heimo said:**
> 

[B][SIZE=2]How to adjust position of your screen?
[/SIZE]
[/B][SIZE=2]open terminal[/SIZE](Applications->Accessories->Terminal), run xvidtune (type: "xvidtune"), adjust the screen and hit Show-button. You'll see a line with something like this on the terminal screen:
```
"1280x1024"   157.50   1280 1332 1492 1728   1024 1025 1028 1072 +hsync +vsync
``` 
Next you should:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo nano /etc/X11/xorg.conf

``` In Monitor section, add the above line with a prefix "Modeline", like this:
```
Modeline "1280x1024"   157.50   1280 1332 1492 1728   1024 1025 1028 1072 +hsync +vsync
``` 
That should do it. There should be no need to restart X if you did make the change (hit Apply in xvidtune), but you should test that this new change works. Hit ctrl+alt+backspace to restart X. If it doesn't work, you can copy back the old configuration file using:
```
sudo /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
``` and restart X using:
```
sudo /etc/init.d/gdm start

``` 


Hi,

I am using Dapper and Omnibook 500 (ATI Mobility M1). As the default settings have the top part of the screen cut off and bottom part showing a bit more, I used xvidtune as suggested here to adjust. When I adjusted to the right settings, I added the Modeline to my xorg.conf file and restarted. But while it correctly shows the screen in when I use the xvidtune program (when I do a test or apply). Copying the details to my xorg.conf file with Modeline, then restarting it has no effect at all. Am I missing something? Now instead or having many different refresh rate (use to be 59, 61, 63, 65), I only have 62.

The 'show' from xvidtune shows "1024x768" 65.15  1024 1040 1130 1312  768 768 771 803 +hsync +vsync

Please help. Thanks.

---

### Post by keltong on 2006-08-20
Still hopin someone can help me with my problem as stated above. Thanks.

---

### Post by keltong on 2006-08-20
YES, I found the solution! Thanks to BitTorrentBuddha from this forum. Just a simple Fn+F5 amazingly does the trick. Hurray!

---

### Post by XProgrammer on 2006-08-21
Hi Friends,

I'm owning Dell Inspiron 6000 Laptop. After installing Dapper, default resolution is set to 1680x???? some.. I want to change it to 1024x768..I tried changing xorg.conf and 915resolution util, editing bootmisc.sh Nothing helped me out.. Then I tried configuring using below command.
'sudo dpkg-reconfigure xserver-xorg'

It worked charmly and got to my resolution of 1024x768..

Regards,
Xprogrammer.

---

### Post by dbw on 2006-08-21
seems like the easiest way to get an appropriate modeline is:
```
gtf 1680 1050 60
```
Where I want a 1680x1050 resolution monitor at 60hz

---

### Post by mrcdan on 2006-10-22
lol sorry wrong thread

---

### Post by DraeLee on 2006-10-23
great guide got a question tho.  ok i did eerything as you said to do.  I do have multiple resolutions to choose from but I dont have multiple refresh rates.  my monitor supports 75hz and lower.  but everytime i goot into ubuntu it only shows 85hz and its stuck there.

I did use custom modlines and all but yet in still i only get one refresh rate and thts the 86hz which my monitor doesnt support any ideas?

Section "Monitor"
        Identifier      "Rosewill R913j"
        Option          "DPMS"
        HorizSync       30-79
        VertRefresh     50-75
 # V-freq: 75.00 Hz  // h-freq: 60.31 KHz
 Modeline "1024x768" 75.00  1024 1064 1168 1352   768  768  770  804
 # V-freq: 75.00 Hz  // h-freq: 79.00 KHz
 Modeline "1280x1024" 75.83  1280 1360 1544 1888  1024 1024 1027 1072
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV34 [GeForce FX 5200]"
        Monitor         "Rosewill R913j"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1280x960" "1280x800" "1280x768" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "1280x960" "1280x800" "1280x768" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024" "1280x960" "1280x800" "1280x768" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "1280x960" "1280x800" "1280x768" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1280x960" "1280x800" "1280x768" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1280x960" "1280x800" "1280x768" "1024x768" "800x600" "640x480"
        EndSubSection

---

### Post by hype on 2006-10-23
Big thanks for that guide.
Well done and well documented !

---

### Post by porrelaar on 2006-10-25
For DraeLee:

Solution: see the first post in this thread (from Heimo): "Be sure that Identifier is same as the Monitor line in *Screen section*." Reread his post please.

So you have to do this: in Section Screen replace (after Identifier) "Default Screen" through "Rosewill R913j"

That will do the trick.
I followed Heimo's Guide yesterday with excellent result. I had before only one refresh rate of 60 Hz on a 15 inch CRT monitor, which gave me an awfull headache because of the flimmering. Now I can choose between 60, 70 or 75 Hz, with a resolution of 1024 x 768. Or at a resolution of 800 x 600, I can even choose from 5 different refresh rates.

Good luck!

---

### Post by QuacoreZX on 2006-10-29
Hey, this has probably been answered before (forgive me, it's late), but I seem to be having a problem with getting xorg to recognize the higher frequencies my monitor is capable of.  I have the proper horizontal and vertical frequencies in place, and I tried using the modeline function to add appropriate substitutes, but the option doesn't seem to add to my resolution options via System -> Preferences -> Resolution!  Any help, much appreciated ~_~

---

### Post by Nexxus6 on 2006-11-09
When I install Ubuntu edgy I boot the cd and hit f4 and change my resolution to 1280x1024 that seems to open up higher resolutions. Might help you next time you do a clean install.

---

### Post by Nocturnal on 2006-11-19
When I had problems setting the refresh rate of my viewsonic vp191b i just ran xvidtune and adjusted it so that i had 75 hz in refresh rate and applied. 
somehow 75hz magicly appeared and I can now select 60 hz and 75 hz in settings :)

---

### Post by dorcssa on 2006-12-17
I have a strange problem. I have several options for resolution and refresh rate, but now that I installed the ati driver, I can't change them. If I chose another option than 1280x1024, nothing happens, it goes back to the original resolution. Same for the 75 Hz. I'm ok with these options, but it's a little annoying, that I can't change them. And yes, I can see the options, can click one, but it goes back.

---

### Post by bmaehr on 2007-01-13
Hello!

I was searching for a solution a long time, perhaps someone has an idea.

I have an CoreDuo MiniMac with debian on it. It is connected with a DVI to HDMI cable to a 37" Xoro screen with a resolution of 1920x1080. The screen supports 1080i and 1080p. The video-card is an intel i945gm.

I was able to select a setting of 1920x1080 with 12 Hz at MacOS and thaht works (the mouse pointer is slow but who cares). If I try higher frequencys the screen doesn't recognice the signal. Also 1080i with 60Hz seems to work.

Now i would like to setup linux with xorg to use these settings. I was able to enable 1920x1080 with 915resolution. But if I start xorg it ignores my modeline with 12Hz and chooses 70Hz which is not supported by my TV. 
If I try to lower the HorizSync and VertRefresh settings xorg doesn't start with the message "no screens found".

Anybody an idea?

---

### Post by Domie on 2007-01-18
Nice guide, but it didn't work. I'm still stuck on 60Hz...

---

### Post by Domie on 2007-01-19
Well, I finally found it out myself.

[https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)

Vesa is just not a good driver for me. So I used OpenChrome. How I found out? Thanks to deleting Ubuntu, installing Mandriva which uses the right driver... Now it was just googling...

So I wished I could say thanks to someone, but I can't...

---

### Post by kaka0502 on 2007-02-21
I had this scrolling effect. I was successful troubleshooting it by changing driver from vesa to nv. Thanks for the HOWTO.

---

### Post by vsandz on 2007-04-08
thanks mate. worked perfectly and i'm up to 1280x1024 now. 

I have one small doubt however. I know this might seem lame but my monitor's user reference states that i can run it @60kHz if in digital mode or @75kHz in Analog mode. I've got both connectors and was wondering if anyone could help me with this digital v/s analog thingy cos i've googled it and cant find enuff info out there. cheerio.

---

### Post by RedSquirrel on 2007-04-09
> **heimo said:**
> [B][SIZE=3]
[/SIZE][/B]**[SIZE=3][SIZE=2]Adding custom modeline[/SIZE][/SIZE]**
If you know what your monitor can do, for example 1024x768@75Hz, you can use this page to generate a custom Modeline for you xorg.conf:[LIST]
[*]     [online modeline generator]("http://www.dkfz-heidelberg.de/spec/linux/modeline/")[/LIST]Copy paste the new Modeline to *Monitor section* (for example):

```
 [FONT=monospace]
[/FONT]# 1024x768 @ 75.00 Hz (GTF) hsync: 60.15 kHz; pclk: 81.80 MHz[FONT=monospace]
[/FONT]Modeline [COLOR=Red]"1024x768_75.00"[/COLOR]  81.80  1024 1080 1192 1360  768 769 772 802  -HSync +Vsync[FONT=monospace]
[/FONT]
```Watch that the hsync is in range with the HorizSync on the same section (in this example the range is 31-101 and this modelines hsync is 60.15, so we're safe). Also the VertRefresh and the refresh rate you selected (75Hz in this example) should match - in this example VertRefresh is 60-160 and modeline is 75Hz, so that's all good.

Now you can select the default resolution and colordepth by tweaking the *Screen section*. It should look something like this:

```
Section "Screen"
    Identifier    "Default Screen"
    Device        "NVIDIA Corporation NV34 [GeForce FX 5200]"
    Monitor        "CM752ET"
    DefaultDepth    16
    SubSection "Display":
        Depth        16
        Modes      [COLOR=Red]"1024x768_75.00"[/COLOR] "1024x768"
    EndSubSection
EndSection

```Monitor name here (CM752ET) matches the Identifier on your Monitor Section. Device line here matches the identifier on your Device section - you get the idea? :) It ties together some settings for your screen - the graphics card and your monitor. You may have more Subsections here, but only one is needed.

Change the DefaultDepth to what you would want it to be, 16 (65536 colors) or 24 (16M colors). Change the Modes line to match the resolutions you want to use - Depth must match DefaultDepth (here it's 16).



Great guide. :)

I would suggest that you make sure the _Modeline_ and the _Modes_ line match (as I indicated above) in your example just to make it clear that that has to be the case in order for the Modeline to be used. If they don't match, then it won't work.

---

### Post by heimo on 2007-04-10
Thanks! Done. I've been quite active on these forums, trying to help with various resolution/refresh rate problems and this guide has helped myself a lot - no need to remember all the links, cryptic settings etc.

Back in... I think it was 1996, I was trying to get my X working and ESR's howto was really helpful. First it was really confusing, but I soon fell in love with the kind of minute control you actually get of your hardware with GNU/Linux+X.
[http://tldp.org/HOWTO/XFree86-Video-Timings-HOWTO/index.html](http://tldp.org/HOWTO/XFree86-Video-Timings-HOWTO/index.html)
([COLOR=Red]historic howto, not maintained, useful for learning, not for configuring Xorg)

[COLOR=black]I think it was ESR's, but it must have been older version by Chin Fang.[/COLOR]
[COLOR=black] [http://tldp.org/HOWTO/XFree86-Video-Timings-HOWTO/credits.html](http://tldp.org/HOWTO/XFree86-Video-Timings-HOWTO/credits.html)[/COLOR]

[/COLOR]

---

### Post by agnul on 2007-05-04
Not sure if this is related at all but...

I have a DELL dimension 3100 (intel integrated graphics board, i910 i think) and a DELL 1905fp 19" LCD. 

X believes the optimal resolution is 1280x1024@75Hz (both in my previous 6.06 and in the freshly installed 7.04), while the monitor reports the optimal resolution as 1280x1024@60Hz. The image is OK, but the most annoying thing is that each time i boot into linux i must fiddle with the monitor controls to re-center the image. I have the same problem (off-center image) when running in text mode. 

Any suggestion for fixing this?
TIA.

---

### Post by zedfrugnug on 2007-05-07
I tried adding a modeline, to get the right refresh rate, as suggested, but now my screen looks even worse:( 
System>settings>screen resolution still tells me I'm still at 55Hz, should be 60Hz..
Using nvidia FX5200 with nividia driver and 1680x1050 resolution.
I've set the horizontal and vertical frequency using "sudo dpkg-reconfigure xsever-xorg" 

Section "Monitor"
	Identifier	"Generieke beeldscherm"
	Option		"DPMS"
	HorizSync	30-83
	VertRefresh	56-75
 # V-freq: 56.00 Hz  // h-freq: 60.85 KHz
 	Modeline "1680x1050" 135.32  1680 1752 1920 2224  1050 1050 1052 1086 
EndSection

I've been playing with ubuntu since last year, reinstalling it over and over again, whenever I screwed something up and didn't know how else to get it right again:lolflag: 
For some reason the screen did look perfectly sharp sometimes, but afther reinstalling again with the same settings it didn't:confused:

---

### Post by zedfrugnug on 2007-05-14
Bump

Does anyone know if this (impossebility to select correct refresh rate and unsharp screen) might be a problem with the nvidia-drivers or a bug in Ubuntu?

I'd like to know , because If it's a bug I'd like to file a bug-report.

---

### Post by Gen2ly on 2007-05-26
Nice tutorial.  Just in case you update this still,  modeline can also be discovered with:
```

gtf x y refresh
```

---

### Post by kc2005 on 2007-05-27
GREAT guide!!! My eyes thank you for your time.

---

### Post by en3rgy on 2007-05-30
Thus far I am not having any luck. I have a Dell E1505 laptop with an nVidia Go7300. I am trying to get to 1680x1050 @ 60hz but cant seem to break the 1024x768 barrier. I've been searching these forums as well as Google for a couple of hours now and have found some excellent advice but sadly none of it seems to be working for me. Can someone assist me please? Thank you in advance:D

---

### Post by zedfrugnug on 2007-05-31
Were you able to select 1680*1050 resolution during configuring; 
sudo dpkg-reconfigure xserver-xorg?

What does "sudo gedit /etc/X11/xorg.conf" tell you, in section " screen"?
Once you've configured xorg it should list the resolutions you've selected.

---

### Post by en3rgy on 2007-05-31
> **zedfrugnug said:**
> Were you able to select 1680*1050 resolution during configuring; 
sudo dpkg-reconfigure xserver-xorg?

What does "sudo gedit /etc/X11/xorg.conf" tell you, in section " screen"?
Once you've configured xorg it should list the resolutions you've selected.

Hi Zed,
Yes, 1680x1050 was available in configuration and I hit the space bar to make sure it was selected.

This is my Xorg file...
```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
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
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us "
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
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
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
	Identifier	"go7300 "
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-90
	VertRefresh	50-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"go7300 "
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1680x1050"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1680x1050"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

---

### Post by en3rgy on 2007-05-31
I also want to add that I am currently @ 1280x800 @? refresh rate according to Nvidia settings.

---

### Post by en3rgy on 2007-05-31
Anyone?

---

### Post by zedfrugnug on 2007-06-01
Very strange. Maybe it's a bug??
Laptopsupport is getting more attention, so maybe things will work better for widescreens when Gutsy arrives.

Where did you find " nvidia settings"?
And what about preferences > screenresolution?

---

### Post by frodon on 2007-06-01
en3rgy, try to add the modelline of the wanted resolution if nothing else works.

---

### Post by en3rgy on 2007-06-01
> **zedfrugnug said:**
> Very strange. Maybe it's a bug??
Laptopsupport is getting more attention, so maybe things will work better for widescreens when Gutsy arrives.

Where did you find " nvidia settings"?
And what about preferences > screenresolution?

Hi again Zed,

The Nvidia settings I found are located under APPLICATIONS>SYSTEM TOOLS>SYSINFO>NVIDIA.

As far as preferences goes, this is a joke. It says 1280x800 but then tells me I'm @ 50hz refresh rate. 

I've posted this problem of mine in other threads too to see if I could get some help with this and thus far this problem seems to be stumping everyone.

The E1505 Dell laptop has the upgraded screen and came with XP (which I am duel booting with Ubuntu). In XP my max (and only) screen size is 1680x1050 @60hz and it really looks wonderful.

I have installed Ubuntu on two other PC's I have and so far all of them work really well except for the video. Then again, they're all Nvidia boxes so I am wondering if Nvidia actually is not very good to begin with and Ubuntu forces this imperfection to come out? 

Either way, I am almost demoralized at this point and am not sure what to do with this video/Nvidia problem.

---

### Post by en3rgy on 2007-06-01
> **frodon said:**
> en3rgy, try to add the modelline of the wanted resolution if nothing else works.

Hi Frodon,

This is an excellent suggestion but I thought this sort of thing went out with 6.10... yes? Perhaps I should try it with Feisty anyway as this seems the only logical alternative. 

Thanks,

en3rgy

---

### Post by rapollon on 2007-06-02
I've been using various distos of debian for the last five years, but this one has me stumped.  
I have a 19" monitor, I want a 1280x1024 screen size.  dpkg allowed me to get a giant screen area outside of view and that's with vesa.  I get the size I'm little for it doesn't fit my screen.  Monitor specs are: 1280x1024@75hz ; v:60.0 h:64.0 or v:75.03 h:80.0

I'm stuck in 1024x768

The microsoft users in my house are annoying me, one hiccup after five years worth of fixing their adawares and virus and windows boo boo's...  
I want silence again...  Thanks!!!

here's my conf:


Section "Device"
	Identifier	"S3 Inc. 86C270-294 Savage/IX-MV"
	Driver		"savage"
	BusID		"PCI:1:1:0"
EndSection

Section "Monitor"
	Identifier	"synaps"
	Option		"DPMS"
Modeline "1280x1024@75" 156.43 1280 1312 1904 1936 1024 1043 1056 1076
	HorizSync	80.8
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"S3 Inc. 86C270-294 Savage/IX-MV"
	Monitor		"synaps"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024_75"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024_75"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024_75"
	EndSubSection
EndSection

---

### Post by SkyScrap on 2007-06-03
Hi,

as all I am having problems with my resolution. My hardware is an ASUS M2NPV-VM mainboard with NVIDIA GeForce 6150 onbaord and an LG Flatron L2000C Screen. 

I would like to run the screen on 1600x1200, and am using the "nv" driver currently.

* In the xorg log, the driver reports a maximum panel size of 1280x1024, which is wrong, the panel supports 1600x1200. How can I change/override that? I already have the option "DCC" "False" in my drivers section, but it does not seem to have the wanted effect.

* When I try to use the restricted driver for nvidia, the dialog goes grey for some time, but nothing changes (as far as I can tell). Where does it tries to get the driver from? I'm not connected to the internet, you think that might be the problem?

Thanks for any help.
(Actually, it's really tiring that setting screen resolutions is THIS hard!!!)

---

### Post by SkyScrap on 2007-06-07
> **SkyScrap said:**
> as all I am having problems with my resolution. My hardware is an ASUS M2NPV-VM mainboard with NVIDIA GeForce 6150 onbaord and an LG Flatron L2000C Screen. 

I would like to run the screen on 1600x1200, and am using the "nv" driver currently.

There seem to be some bugs in the nv driver, which are preventing usage of 1600x1200. Best guess is to use the nvidia driver instead.

Some handy links
[LIST]
[*][http://wiki.x.org/wiki/nv]("http://wiki.x.org/wiki/nv")
[*]Bug: [Unable to obtain the right resolution for DVI panel]("https://bugs.freedesktop.org/show_bug.cgi?id=3654")
[*]Bug: [nouveau can't use a Dell 2001FP in 1600x1200 mode]("https://bugs.freedesktop.org/show_bug.cgi?id=10673")
[/LIST]

---

### Post by zedfrugnug on 2007-06-14
> **en3rgy said:**
> Hi again Zed,

The Nvidia settings I found are located under APPLICATIONS>SYSTEM TOOLS>SYSINFO>NVIDIA.

As far as preferences goes, this is a joke. It says 1280x800 but then tells me I'm @ 50hz refresh rate. 

I've posted this problem of mine in other threads too to see if I could get some help with this and thus far this problem seems to be stumping everyone.

The E1505 Dell laptop has the upgraded screen and came with XP (which I am duel booting with Ubuntu). In XP my max (and only) screen size is 1680x1050 @60hz and it really looks wonderful.

I have installed Ubuntu on two other PC's I have and so far all of them work really well except for the video. Then again, they're all Nvidia boxes so I am wondering if Nvidia actually is not very good to begin with and Ubuntu forces this imperfection to come out? 

Either way, I am almost demoralized at this point and am not sure what to do with this video/Nvidia problem.

Nvidia is supporting linux better than ATI at the moment. Only Intel is better, but they only do integrated graphics (this might change though) 
So not too much choice there...

Just hope things will be better with Gutsy..

---

### Post by en3rgy on 2007-06-26
I am going to delete Ubuntu in a few minutes and install Suse 10.2. Maybe this will be better for me.

---

### Post by fifa255 on 2007-07-04
I just installed ubuntu (dual boot. oh boy that took a while to get right).  I have the GeForce 7800gs using the nvidia driver installed using envy script.  I have an IBM p260 monitor that support upto 1920x1440 resolution and with horizontal freq: 30-120 and vertical refresh: 50-160.  I have edited the xorg.conf file and added a modeline to get 1600x1200 at 65hz.  However I don't see that option when I go to System-> Preference -> screen resolution.  Here is my xorg.conf file Is there something I'm doing wrong or need to add.  Please help.

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Wed Jun 13 18:39:30 PDT 2007

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
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
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/share/fonts/X11/cyrillic"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Monitor"
	Identifier   "IBM Monitor"
	VendorName   "IBM"
	ModelName    "P260"
	HorizSync    30.0 - 121.0
	VertRefresh  50.0 - 160.0
	Option      "DPMS"
	# 1600x1200 @ 65.00 Hz (GTF) hsync: 80.99 kHz; pclk: 176.23 MHz
  	Modeline "1600x1200_65.00"  176.23  1600 1712 1888 2176  1200 1201 1204 1246  -HSync +Vsync
	# 1600x1200 @ 70.00 Hz (GTF) hsync: 87.43 kHz; pclk: 190.25 MHz
  	Modeline "1600x1200_70.00"  190.25  1600 1712 1888 2176  1200 1201 1204 1249  -HSync +Vsync


EndSection


Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "IBM Monitor"
    DefaultDepth    16
    SubSection     "Display"
        Depth       1
        Modes      "1600x1200_65.00" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1600x1200_65.00" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1600x1200_65.00" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1600x1200_65.00" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1600x1200_65.00" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes 	    "1600x1200_65.00" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

---

### Post by andrek on 2007-07-06
Have a look at my xorg.conf file :
```

(...)
Section "Monitor"
	Identifier	"AX3818UTC B"
	Option		"DPMS"
	HorizSync	31-65
	VertRefresh	56-80
 # V-freq: 79.00 Hz  // h-freq: 63.69 KHz
 	Modeline "1024x768" 87.64  1024 1072 1184 1376   768  768  770  806 
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV17 [GeForce4 MX 440]"
	Monitor		"AX3818UTC B"
	DefaultDepth	24
	SubSection "Display"
	Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection
(...)

```

I want to get real 79Hz Vertical Freq / 64KHz Horizontal Freq. What's wrong with my conf file?

---

### Post by mryilauer on 2007-07-08
Thanks, guys. I just wanted to summarize something that worked for me to help anyone else who has to do exactly what I did in exactly the same situation. 

All I wanted to do was to increase the refresh rate from 60 to 75 since I can see the flicker and it drives me nuts. The advice here was very helpful, but parts were obscure or too general, as usual. I tried the xinit -- :2 trick, but ubuntu rejected that with some kind of error message at the console. Thank goodness for the recommendation to use ctrl-alt-F7 to get back to my existing X session. Also, the ctrl-alt-backspace to restart X was very helpful.

Again, all I wanted to do was to increase the refresh rate, nothing else. As to the suggestion that I make sure that my monitor and video card both support the higher resolution, well, gee guys, I'm using an old P3 with an onboard video card that Dell tells me nothing about, and a donated monitor, but before I installed ubuntu, I'm pretty sure I had it at the higher refresh rate running Windows 98 or whatever. 

So, what I did, exactly, was to follow the advice to backup the conf file as shown below, then added the desired refresh rate after the resolution I intend to use. It didn't work when I just added _75, by the way, I had to keep looking and found another suggestion to use _75.00, and that worked.

sudo cp /etc/X11/xorg.conf  /etc/X11/xorg.conf_backup
sudo gedit /etc/X11/xorg.conf

Here's the way my conf file looked at first:
Section "Screen"
    Identifier    "Default Screen"
    Device        "ATI Technologies Inc Rage 128 PF/PRO AGP 4x TMDS"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection "Display"
        Depth        1
        Modes        "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
    EndSubSection
    SubSection "Display"
        Depth        4
        Modes        "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
    EndSubSection
    SubSection "Display"
        Depth        8
        Modes        "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
    EndSubSection
    SubSection "Display"
        Depth        15
        Modes        "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
    EndSubSection
    SubSection "Display"
        Depth        16
        Modes        "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
    EndSubSection
    SubSection "Display"
        Depth        24
        Modes        "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
    EndSubSection
EndSection

I changed it to this: 

Section "Screen"
    Identifier    "Default Screen"
    Device        "ATI Technologies Inc Rage 128 PF/PRO AGP 4x TMDS"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection "Display"
        Depth        1
        Modes        "1600x1200" "1280x1024_75.00" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
    EndSubSection
    SubSection "Display"
        Depth        4
        Modes        "1600x1200" "1280x1024_75.00" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
    EndSubSection
    SubSection "Display"
        Depth        8
        Modes        "1600x1200" "1280x1024_75.00" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
    EndSubSection
    SubSection "Display"
        Depth        15
        Modes        "1600x1200" "1280x1024_75.00" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
    EndSubSection
    SubSection "Display"
        Depth        16
        Modes        "1600x1200" "1280x1024_75.00" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
    EndSubSection
    SubSection "Display"
        Depth        24
        Modes        "1600x1200" "1280x1024_75.00" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
    EndSubSection
EndSection

---

### Post by mryilauer on 2007-07-08
geez, I left the mustard out of the recipe! here's another change I had to make before it worked:

before:
Section "Monitor"
    Identifier    "Generic Monitor"
    Option        "DPMS"
    HorizSync    28-80
    VertRefresh    43-60
EndSection

after:
Section "Monitor"
    Identifier    "Generic Monitor"
    Option        "DPMS"
    HorizSync    28-80
    VertRefresh    43-75
EndSection

---

### Post by pabsco on 2007-09-18
I am trying to load ubuntu 7.04 And install fails because Monitor shows
 only a "Frequency out of Range" error so I see nothing of what is 
happening therefore install stops.

The error says it is trying to load 70.14 & 86.16 
My monitor works in windows at 60.02 & 75.03

Can any one help please

---

### Post by agds on 2007-09-23
Thanks for a very comprehensive HOWTO.  The part about adding a modeline was exactly what I needed.  Now my GeForce4 and my SyncMaster are speaking the same language, as it were.

---

### Post by Asger on 2007-09-28
Thakns for a great howto.

If possible please add this hint regarding configureing the Nvidia driver:

Go to
APPLICATIONS>SYSTEM TOOLS>SYSINFO>NVIDIA
or if this menu option is not present type in a terminal:
sudo nvidia-settings

This opens a Nvidia driver configuartion window where all screen resolutions are avaliable, so just choose the right one, apply, save to X configuration file and quit.

This info comes from: [http://ubuntuforums.org/showthread.php?t=492195&highlight=no+output+from+xresprobe]("http://ubuntuforums.org/showthread.php?t=492195&highlight=no+output+from+xresprobe")

---

### Post by fifafrazer on 2007-10-28
>  *heimo wrote:*
```
Section "Screen"
    Identifier    "Default Screen"
    Device        "NVIDIA Corporation NV34 [GeForce FX 5200]"
    Monitor        "CM752ET"
    DefaultDepth    16
    SubSection "Display":
        Depth        16
        Modes      "1024x768_75.00"
    EndSubSection
EndSection
```

Please remove the ":" after the Subsection "Display", otherwise the xserver will fail to initialize. I had to read the logs to find this error, which caused me some trouble.

---

### Post by heimo on 2007-10-29
> **fifafrazer said:**
> Please remove the ":" after the Subsection "Display", otherwise the xserver will fail to initialize. I had to read the logs to find this error, which caused me some trouble.

Thank you very much fifafrazer, fixed it.

---

### Post by pabsco on 2007-11-08
> **pabsco said:**
> I am trying to load ubuntu 7.04 And install fails because Monitor shows
 only a "Frequency out of Range" error so I see nothing of what is 
happening therefore install stops.

The error says it is trying to load 70.14 & 86.16 
My monitor works in windows at 60.02 & 75.03

Can any one help please


I poster the above Quote in September and it looks like I have had not one single reply.
Disappointing to say the least.

I cannot even get my 'ubuntu' beyond loading a few files. Maybe someone can help. I hope so!

I'll tell my story.

Having run out of room on the HD used for XP Pro  I purchased a bigger drive. 400Gig ! 
OK that fixed my XP Problem. 

But spare 40Gig HD and an empty removable draw, tempted me to put my toe into the Linux pool.

I down loaded the latest version of Ubuntu ( 7.4 I think ) and burnt the CD as instructed.
I Set-up a boot sequence so that when the ubuntu drive was in the draw ... ubuntu would load and when the draw was empty XP loads.

So far a piece of Cake!  Disconnected the XP drive so I did not risk messing it up and tried to install ubuntu on the 40 Gig drive. 

But, I could not install Ununtu because I was getting an error Message.  
"Refresh Rate out of range."
Apparently ubuntu uses Hf 70 Hv   Vf 87 Hz    ...a rate higher that my Monitor.

While XP is loaded I can change the refresh Rate to what Ubuntu requires.
But all apparently that is only a software fix and does not 'stick' so ubuntu is still seeing an unsatisfactory Refresh Rate      I am guessing it sees  a Hf of 60HZ.

I was told by one local " expert" that if got someone to install Ubuntu onto my 40 Gig disk from another Computer where the error did not come up I could then I re-installed ubuntu again from my own computer and Ubuntu would recognise my Monitor rate.

Sounds easy, ubuntu looked to, my inexperienced eye, to be working well on my friend's Computer but it does not work on my Computer. It goes to the log-in and accepts my ID and Password, loads a few Drivers ( I think that what they are ) that shows me that Refresh Rate Error again.

I guess, I could just go out and purchase a new  Monitor. But the one I have is hp72  of 2002 vintage, Manufactured in China. It is in perfect working order and I really don't want to blow some of my budget replacing it.

I have read most of the posts in this topic but understand very little about the technical stuff posted.

Any way! ! Can one access the place where those scripts are and change them 
when the Monitor  is not talking to Ubuntu and I don't know what I am doing  any away.

Yes, I can keep a computer functioning well with XP and seldom need help from a technician. But with ubunutu I am a lost. I am still a very  new newbie.

I would appreciate come help. 

Thanks  Guys.

Gil Pahlow

---

### Post by satbunny on 2007-11-12
I have used this thread before to successfully tune the 2 PCs I have using a single monitor using a kvm.

Even with the same modeline the two graphic cards produce differently located images, so I used xvidtune to slightly move them so they both are aligned on my monitor.

I have just moved to Gutsy and have turned on the restricted driver for nvidia (as before in Feisty) but have discovered that xvidtune no longer allows for adjustment in real time: "Sorry you have requested a modeline that is not possible or supported by your hardware configuration".. is the error when I try to apply or test a minor adjustment left or right.

Anyone know why xvidtune doesn't work anymore and/or an alternative real time to subtly jog my modeline to the left or right?

---

### Post by panrubius on 2007-11-26
Thank you Thank you Thank you Thank you Thank you  Thank you! 

This has totally saved me.

P

---

### Post by polytropos on 2008-02-08
A note from a somewhat frustrated newbie: 

I've been fiddling with this for hours but still can't get rid of that flickery effect, which, I take it, has something to do with the refresh rate.  I've been manually editing because my monitor is an AG Neovo F-417, which is not a model one can edit in "Screens and Graphics Preferences".   I've tried several different modelines (which I've gotten from <http://xtiming.sourceforge.net/cgi-bin/xtiming.pl>), but none gets rid of the flicker.

Here are some specs on my monitor:

1280-1024
H: 24-80 kHz
V: 49-75 Hz
Max clock: 135 MHz

Any advice?

---

### Post by kidznco on 2008-02-15
Thank you. You saved me from certain death. I nearly had to reinstall AGAIN.:)

---

### Post by junki on 2008-02-15
I also have this problems before thank you for the informations.

---

### Post by IceSunrise on 2008-03-12
Hello all!

I read this useful HOWTO but can't correct my problem... :(
Maybe someone can help me! The problem is, I only get a frequency refresh
rate of 60Hz and can't set it to 75Hz.
I now, that my monitor (Samsung SyncMaster 710N) can work with this
refresh rate. And with vesa driver it's work!
But with intel it doesn't...
I'm using video card: VGA compatible controller: Intel Corporation 82865G
Integrated Graphics Controller (rev 02)
 
My Xorg.0.log and xorg.conf here:

***Xorg.0.log***
```

X Window System Version 1.3.0 
Release Date: 19 April 2007 
X Protocol Version 11, Revision 0, Release 1.3 
Build Operating System: UNKNOWN 
Current Operating System: Linux cosmos 2.6.23-gentoo-r8 #4 SMP Wed Mar 12 11:28:54 MSK 2008 i686 
Build Date: 12 March 2008 
   Before reporting problems, check http://wiki.x.org 
   to make sure that you have the latest version. 
Module Loader present 
Markers: (--) probed, (**) from config file, (==) default setting, 
   (++) from command line, (!!) notice, (II) informational, 
   (WW) warning, (EE) error, (NI) not implemented, (??) unknown. 
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Mar 12 15:12:55 2008 
(==) Using config file: "/etc/X11/xorg.conf" 
(==) ServerLayout "Dimas Layout" 
(**) |-->Screen "Screen" (0) 
(**) |   |-->Monitor "SyncMaster_710N" 
(**) |   |-->Device "intel" 
(**) |-->Input Device "Mouse" 
(**) |-->Input Device "Keyboard" 
(WW) The directory "/usr/share/fonts/TTF/" does not exist. 
   Entry deleted from font path. 
(WW) The directory "/usr/share/fonts/OTF" does not exist. 
   Entry deleted from font path. 
(WW) `fonts.dir' not found (or not valid) in "/usr/share/fonts/terminus". 
   Entry deleted from font path. 
   (Run 'mkfontdir' on "/usr/share/fonts/terminus"). 
(**) FontPath set to: 
   /usr/share/fonts/misc/, 
   /usr/share/fonts/Type1/, 
   /usr/share/fonts/100dpi/, 
   /usr/share/fonts/75dpi/, 
   /usr/share/fonts/dejavu 
(**) RgbPath set to "/usr/share/X11/rgb" 
(**) ModulePath set to "/usr/lib/xorg/modules" 
(**) Option "AIGLX" "true" 
(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory) 
(II) No APM support in BIOS or kernel 
(II) Loader magic: 0x81d9520 
(II) Module ABI versions: 
   X.Org ANSI C Emulation: 0.3 
   X.Org Video Driver: 1.2 
   X.Org XInput driver : 0.7 
   X.Org Server Extension : 0.3 
   X.Org Font Renderer : 0.5 
(II) Loader running on linux 
(II) LoadModule: "pcidata" 
(II) Loading /usr/lib/xorg/modules//libpcidata.so 
(II) Module pcidata: vendor="X.Org Foundation" 
   compiled for 1.3.0, module version = 1.0.0 
   ABI class: X.Org Video Driver, version 1.2 
(--) using VT number 7 
  
(II) PCI: PCI scan (all values are in hex) 
(II) PCI: 00:00:0: chip 8086,2570 card 1043,80a5 rev 02 class 06,00,00 hdr 00 
(II) PCI: 00:02:0: chip 8086,2572 card 1043,80a5 rev 02 class 03,00,00 hdr 00 
(II) PCI: 00:1d:0: chip 8086,24d2 card 1043,80a6 rev 02 class 0c,03,00 hdr 80 
(II) PCI: 00:1d:1: chip 8086,24d4 card 1043,80a6 rev 02 class 0c,03,00 hdr 00 
(II) PCI: 00:1d:2: chip 8086,24d7 card 1043,80a6 rev 02 class 0c,03,00 hdr 00 
(II) PCI: 00:1d:3: chip 8086,24de card 1043,80a6 rev 02 class 0c,03,00 hdr 00 
(II) PCI: 00:1d:7: chip 8086,24dd card 1043,80a6 rev 02 class 0c,03,20 hdr 00 
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev c2 class 06,04,00 hdr 01 
(II) PCI: 00:1f:0: chip 8086,24d0 card 0000,0000 rev 02 class 06,01,00 hdr 80 
(II) PCI: 00:1f:1: chip 8086,24db card 1043,80a6 rev 02 class 01,01,8a hdr 00 
(II) PCI: 00:1f:2: chip 8086,24d1 card 1043,80a6 rev 02 class 01,01,8f hdr 00 
(II) PCI: 00:1f:3: chip 8086,24d3 card 1043,80a6 rev 02 class 0c,05,00 hdr 00 
(II) PCI: 01:08:0: chip 8086,1050 card 1043,80f8 rev 02 class 02,00,00 hdr 00 
(II) PCI: 01:0b:0: chip 1102,0002 card 1102,8026 rev 07 class 04,01,00 hdr 80 
(II) PCI: 01:0b:1: chip 1102,7002 card 1102,0020 rev 07 class 09,80,00 hdr 80 
(II) PCI: End of PCI scan 
(II) Intel Bridge workaround enabled 
(II) Host-to-PCI bridge: 
(II) Bus 0: bridge is at (0:0:0), (0,0,1), BCTRL: 0x0008 (VGA_EN is set) 
(II) Bus 0 I/O range: 
   [0] -1   0   0x00000000 - 0x0000ffff (0x10000) IX[B] 
(II) Bus 0 non-prefetchable memory range: 
   [0] -1   0   0x00000000 - 0xffffffff (0x0) MX[B] 
(II) Bus 0 prefetchable memory range: 
   [0] -1   0   0x00000000 - 0xffffffff (0x0) MX[B] 
(II) Subtractive PCI-to-PCI bridge: 
(II) Bus 1: bridge is at (0:30:0), (0,1,1), BCTRL: 0x0002 (VGA_EN is cleared) 
(II) Bus 1 I/O range: 
   [0] -1   0   0x0000d000 - 0x0000dfff (0x1000) IX[B] 
(II) Bus 1 non-prefetchable memory range: 
   [0] -1   0   0xfe500000 - 0xfe5fffff (0x100000) MX[B] 
(II) PCI-to-ISA bridge: 
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set) 
(--) PCI:*(0:2:0) Intel Corporation 82865G Integrated Graphics Controller rev 2, Mem @ 0xf0000000/27, 0xfe780000/19, I/O @ 0xefe0/3 
(II) Addressable bus resource ranges are 
   [0] -1   0   0x00000000 - 0xffffffff (0x0) MX[B] 
   [1] -1   0   0x00000000 - 0x0000ffff (0x10000) IX[B] 
(II) OS-reported resource ranges: 
   [0] -1   0   0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B) 
   [1] -1   0   0x000f0000 - 0x000fffff (0x10000) MX[B] 
   [2] -1   0   0x000c0000 - 0x000effff (0x30000) MX[B] 
   [3] -1   0   0x00000000 - 0x0009ffff (0xa0000) MX[B] 
   [4] -1   0   0x0000ffff - 0x0000ffff (0x1) IX[B] 
   [5] -1   0   0x00000000 - 0x000000ff (0x100) IX[B] 
(II) PCI Memory resource overlap reduced 0xfe800000 from 0xfebfffff to 0xfe7fffff 
(II) Active PCI resource ranges: 
   [0] -1   0   0xfe5ff000 - 0xfe5fffff (0x1000) MX[B] 
   [1] -1   0   0x50000000 - 0x500003ff (0x400) MX[B] 
   [2] -1   0   0xfe77bc00 - 0xfe77bfff (0x400) MX[B] 
   [3] -1   0   0xfe800000 - 0xfe7fffff (0x0) MX[B]O 
   [4] -1   0   0xfe780000 - 0xfe7fffff (0x80000) MX[B](B) 
   [5] -1   0   0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B) 
   [6] -1   0   0x0000dfe0 - 0x0000dfe7 (0x8) IX[B] 
   [7] -1   0   0x0000df80 - 0x0000df9f (0x20) IX[B] 
   [8] -1   0   0x0000df00 - 0x0000df3f (0x40) IX[B] 
   [9] -1   0   0x00000400 - 0x0000041f (0x20) IX[B] 
   [10] -1   0   0x0000eed0 - 0x0000eedf (0x10) IX[B] 
   [11] -1   0   0x0000efa0 - 0x0000efa3 (0x4) IX[B] 
   [12] -1   0   0x0000ef68 - 0x0000ef6f (0x8) IX[B] 
   [13] -1   0   0x0000efa4 - 0x0000efa7 (0x4) IX[B] 
   [14] -1   0   0x0000efa8 - 0x0000efaf (0x8) IX[B] 
   [15] -1   0   0x0000fc00 - 0x0000fc0f (0x10) IX[B] 
   [16] -1   0   0x000001f0 - 0x000001f0 (0x1) IX[B] 
   [17] -1   0   0x000001f0 - 0x000001f7 (0x8) IX[B] 
   [18] -1   0   0x000001f0 - 0x000001f0 (0x1) IX[B] 
   [19] -1   0   0x000001f0 - 0x000001f7 (0x8) IX[B] 
   [20] -1   0   0x0000ef80 - 0x0000ef9f (0x20) IX[B] 
   [21] -1   0   0x0000ef40 - 0x0000ef5f (0x20) IX[B] 
   [22] -1   0   0x0000ef20 - 0x0000ef3f (0x20) IX[B] 
   [23] -1   0   0x0000ef00 - 0x0000ef1f (0x20) IX[B] 
   [24] -1   0   0x0000efe0 - 0x0000efe7 (0x8) IX[B](B) 
(II) Active PCI resource ranges after removing overlaps: 
   [0] -1   0   0xfe5ff000 - 0xfe5fffff (0x1000) MX[B] 
   [1] -1   0   0x50000000 - 0x500003ff (0x400) MX[B] 
   [2] -1   0   0xfe77bc00 - 0xfe77bfff (0x400) MX[B] 
   [3] -1   0   0xfe800000 - 0xfe7fffff (0x0) MX[B]O 
   [4] -1   0   0xfe780000 - 0xfe7fffff (0x80000) MX[B](B) 
   [5] -1   0   0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B) 
   [6] -1   0   0x0000dfe0 - 0x0000dfe7 (0x8) IX[B] 
   [7] -1   0   0x0000df80 - 0x0000df9f (0x20) IX[B] 
   [8] -1   0   0x0000df00 - 0x0000df3f (0x40) IX[B] 
   [9] -1   0   0x00000400 - 0x0000041f (0x20) IX[B] 
   [10] -1   0   0x0000eed0 - 0x0000eedf (0x10) IX[B] 
   [11] -1   0   0x0000efa0 - 0x0000efa3 (0x4) IX[B] 
   [12] -1   0   0x0000ef68 - 0x0000ef6f (0x8) IX[B] 
   [13] -1   0   0x0000efa4 - 0x0000efa7 (0x4) IX[B] 
   [14] -1   0   0x0000efa8 - 0x0000efaf (0x8) IX[B] 
   [15] -1   0   0x0000fc00 - 0x0000fc0f (0x10) IX[B] 
   [16] -1   0   0x000001f0 - 0x000001f0 (0x1) IX[B] 
   [17] -1   0   0x000001f0 - 0x000001f7 (0x8) IX[B] 
   [18] -1   0   0x000001f0 - 0x000001f0 (0x1) IX[B] 
   [19] -1   0   0x000001f0 - 0x000001f7 (0x8) IX[B] 
   [20] -1   0   0x0000ef80 - 0x0000ef9f (0x20) IX[B] 
   [21] -1   0   0x0000ef40 - 0x0000ef5f (0x20) IX[B] 
   [22] -1   0   0x0000ef20 - 0x0000ef3f (0x20) IX[B] 
   [23] -1   0   0x0000ef00 - 0x0000ef1f (0x20) IX[B] 
   [24] -1   0   0x0000efe0 - 0x0000efe7 (0x8) IX[B](B) 
(II) OS-reported resource ranges after removing overlaps with PCI: 
   [0] -1   0   0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B) 
   [1] -1   0   0x000f0000 - 0x000fffff (0x10000) MX[B] 
   [2] -1   0   0x000c0000 - 0x000effff (0x30000) MX[B] 
   [3] -1   0   0x00000000 - 0x0009ffff (0xa0000) MX[B] 
   [4] -1   0   0x0000ffff - 0x0000ffff (0x1) IX[B] 
   [5] -1   0   0x00000000 - 0x000000ff (0x100) IX[B] 
(II) All system resource ranges: 
   [0] -1   0   0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B) 
   [1] -1   0   0x000f0000 - 0x000fffff (0x10000) MX[B] 
   [2] -1   0   0x000c0000 - 0x000effff (0x30000) MX[B] 
   [3] -1   0   0x00000000 - 0x0009ffff (0xa0000) MX[B] 
   [4] -1   0   0xfe5ff000 - 0xfe5fffff (0x1000) MX[B] 
   [5] -1   0   0x50000000 - 0x500003ff (0x400) MX[B] 
   [6] -1   0   0xfe77bc00 - 0xfe77bfff (0x400) MX[B] 
   [7] -1   0   0xfe800000 - 0xfe7fffff (0x0) MX[B]O 
   [8] -1   0   0xfe780000 - 0xfe7fffff (0x80000) MX[B](B) 
   [9] -1   0   0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B) 
   [10] -1   0   0x0000ffff - 0x0000ffff (0x1) IX[B] 
   [11] -1   0   0x00000000 - 0x000000ff (0x100) IX[B] 
   [12] -1   0   0x0000dfe0 - 0x0000dfe7 (0x8) IX[B] 
   [13] -1   0   0x0000df80 - 0x0000df9f (0x20) IX[B] 
   [14] -1   0   0x0000df00 - 0x0000df3f (0x40) IX[B] 
   [15] -1   0   0x00000400 - 0x0000041f (0x20) IX[B] 
   [16] -1   0   0x0000eed0 - 0x0000eedf (0x10) IX[B] 
   [17] -1   0   0x0000efa0 - 0x0000efa3 (0x4) IX[B] 
   [18] -1   0   0x0000ef68 - 0x0000ef6f (0x8) IX[B] 
   [19] -1   0   0x0000efa4 - 0x0000efa7 (0x4) IX[B] 
   [20] -1   0   0x0000efa8 - 0x0000efaf (0x8) IX[B] 
   [21] -1   0   0x0000fc00 - 0x0000fc0f (0x10) IX[B] 
   [22] -1   0   0x000001f0 - 0x000001f0 (0x1) IX[B] 
   [23] -1   0   0x000001f0 - 0x000001f7 (0x8) IX[B] 
   [24] -1   0   0x000001f0 - 0x000001f0 (0x1) IX[B] 
   [25] -1   0   0x000001f0 - 0x000001f7 (0x8) IX[B] 
   [26] -1   0   0x0000ef80 - 0x0000ef9f (0x20) IX[B] 
   [27] -1   0   0x0000ef40 - 0x0000ef5f (0x20) IX[B] 
   [28] -1   0   0x0000ef20 - 0x0000ef3f (0x20) IX[B] 
   [29] -1   0   0x0000ef00 - 0x0000ef1f (0x20) IX[B] 
   [30] -1   0   0x0000efe0 - 0x0000efe7 (0x8) IX[B](B) 
(II) LoadModule: "glx" 
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so 
(II) Module glx: vendor="X.Org Foundation" 
   compiled for 1.3.0, module version = 1.0.0 
   ABI class: X.Org Server Extension, version 0.3 
(**) AIGLX enabled 
(II) Loading extension GLX 
(II) LoadModule: "extmod" 
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so 
(II) Module extmod: vendor="X.Org Foundation" 
   compiled for 1.3.0, module version = 1.0.0 
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
(II) LoadModule: "extmod" 
(II) Reloading /usr/lib/xorg/modules/extensions//libextmod.so 
(II) Loading extension SHAPE 
(II) Loading extension MIT-SUNDRY-NONSTANDARD 
(II) Loading extension BIG-REQUESTS 
(II) Loading extension SYNC 
(II) Loading extension MIT-SCREEN-SAVER 
(II) Loading extension XC-MISC 
(II) Loading extension XFree86-VidModeExtension 
(II) Loading extension XFree86-Misc 
(II) Loading extension DPMS 
(II) Loading extension TOG-CUP 
(II) Loading extension Extended-Visual-Information 
(II) Loading extension XVideo 
(II) Loading extension XVideo-MotionCompensation 
(II) Loading extension X-Resource 
(II) LoadModule: "record" 
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so 
(II) Module record: vendor="X.Org Foundation" 
   compiled for 1.3.0, module version = 1.13.0 
   Module class: X.Org Server Extension 
   ABI class: X.Org Server Extension, version 0.3 
(II) Loading extension RECORD 
(II) LoadModule: "dbe" 
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so 
(II) Module dbe: vendor="X.Org Foundation" 
   compiled for 1.3.0, module version = 1.0.0 
   Module class: X.Org Server Extension 
   ABI class: X.Org Server Extension, version 0.3 
(II) Loading extension DOUBLE-BUFFER 
(II) LoadModule: "xtrap" 
(II) Loading /usr/lib/xorg/modules/extensions//libxtrap.so 
(II) Module xtrap: vendor="X.Org Foundation" 
   compiled for 1.3.0, module version = 1.0.0 
   Module class: X.Org Server Extension 
   ABI class: X.Org Server Extension, version 0.3 
(II) Loading extension DEC-XTRAP 
(II) LoadModule: "dri" 
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so 
(II) Module dri: vendor="X.Org Foundation" 
   compiled for 1.3.0, module version = 1.0.0 
   ABI class: X.Org Server Extension, version 0.3 
(II) Loading extension XFree86-DRI 
(II) LoadModule: "freetype" 
(II) Loading /usr/lib/xorg/modules/fonts//libfreetype.so 
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project" 
   compiled for 1.3.0, module version = 2.1.0 
   Module class: X.Org Font Renderer 
   ABI class: X.Org Font Renderer, version 0.5 
(II) Loading font FreeType 
(II) LoadModule: "type1" 
(II) Loading /usr/lib/xorg/modules/fonts//libtype1.so 
(II) Module type1: vendor="X.Org Foundation" 
   compiled for 1.3.0, module version = 1.0.2 
   Module class: X.Org Font Renderer 
   ABI class: X.Org Font Renderer, version 0.5 
(II) Loading font Type1 
(II) LoadModule: "intel" 
(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so 
(II) Module intel: vendor="X.Org Foundation" 
   compiled for 1.3.0, module version = 2.1.1 
   Module class: X.Org Video Driver 
   ABI class: X.Org Video Driver, version 1.2 
(II) LoadModule: "mouse" 
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so 
(II) Module mouse: vendor="X.Org Foundation" 
   compiled for 1.3.0, module version = 1.2.3 
   Module class: X.Org XInput Driver 
   ABI class: X.Org XInput driver, version 0.7 
(II) LoadModule: "kbd" 
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so 
(II) Module kbd: vendor="X.Org Foundation" 
   compiled for 1.3.0, module version = 1.1.0 
   Module class: X.Org XInput Driver 
   ABI class: X.Org XInput driver, version 0.7 
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810, 
   i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G, 
   E7221 (i915), 915GM, 945G, 945GM, 945GME, 965G, 965G, 965Q, 946GZ, 
   965GM, 965GME/GLE, G33, Q35, Q33 
(II) Primary Device is: PCI 00:02:0 
(--) Chipset 865G found 
(II) resource ranges after xf86ClaimFixedResources() call: 
   [0] -1   0   0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B) 
   [1] -1   0   0x000f0000 - 0x000fffff (0x10000) MX[B] 
   [2] -1   0   0x000c0000 - 0x000effff (0x30000) MX[B] 
   [3] -1   0   0x00000000 - 0x0009ffff (0xa0000) MX[B] 
   [4] -1   0   0xfe5ff000 - 0xfe5fffff (0x1000) MX[B] 
   [5] -1   0   0x50000000 - 0x500003ff (0x400) MX[B] 
   [6] -1   0   0xfe77bc00 - 0xfe77bfff (0x400) MX[B] 
   [7] -1   0   0xfe800000 - 0xfe7fffff (0x0) MX[B]O 
   [8] -1   0   0xfe780000 - 0xfe7fffff (0x80000) MX[B](B) 
   [9] -1   0   0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B) 
   [10] -1   0   0x0000ffff - 0x0000ffff (0x1) IX[B] 
   [11] -1   0   0x00000000 - 0x000000ff (0x100) IX[B] 
   [12] -1   0   0x0000dfe0 - 0x0000dfe7 (0x8) IX[B] 
   [13] -1   0   0x0000df80 - 0x0000df9f (0x20) IX[B] 
   [14] -1   0   0x0000df00 - 0x0000df3f (0x40) IX[B] 
   [15] -1   0   0x00000400 - 0x0000041f (0x20) IX[B] 
   [16] -1   0   0x0000eed0 - 0x0000eedf (0x10) IX[B] 
   [17] -1   0   0x0000efa0 - 0x0000efa3 (0x4) IX[B] 
   [18] -1   0   0x0000ef68 - 0x0000ef6f (0x8) IX[B] 
   [19] -1   0   0x0000efa4 - 0x0000efa7 (0x4) IX[B] 
   [20] -1   0   0x0000efa8 - 0x0000efaf (0x8) IX[B] 
   [21] -1   0   0x0000fc00 - 0x0000fc0f (0x10) IX[B] 
   [22] -1   0   0x000001f0 - 0x000001f0 (0x1) IX[B] 
   [23] -1   0   0x000001f0 - 0x000001f7 (0x8) IX[B] 
   [24] -1   0   0x000001f0 - 0x000001f0 (0x1) IX[B] 
   [25] -1   0   0x000001f0 - 0x000001f7 (0x8) IX[B] 
   [26] -1   0   0x0000ef80 - 0x0000ef9f (0x20) IX[B] 
   [27] -1   0   0x0000ef40 - 0x0000ef5f (0x20) IX[B] 
   [28] -1   0   0x0000ef20 - 0x0000ef3f (0x20) IX[B] 
   [29] -1   0   0x0000ef00 - 0x0000ef1f (0x20) IX[B] 
   [30] -1   0   0x0000efe0 - 0x0000efe7 (0x8) IX[B](B) 
(II) resource ranges after probing: 
   [0] -1   0   0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B) 
   [1] -1   0   0x000f0000 - 0x000fffff (0x10000) MX[B] 
   [2] -1   0   0x000c0000 - 0x000effff (0x30000) MX[B] 
   [3] -1   0   0x00000000 - 0x0009ffff (0xa0000) MX[B] 
   [4] -1   0   0xfe5ff000 - 0xfe5fffff (0x1000) MX[B] 
   [5] -1   0   0x50000000 - 0x500003ff (0x400) MX[B] 
   [6] -1   0   0xfe77bc00 - 0xfe77bfff (0x400) MX[B] 
   [7] -1   0   0xfe800000 - 0xfe7fffff (0x0) MX[B]O 
   [8] -1   0   0xfe780000 - 0xfe7fffff (0x80000) MX[B](B) 
   [9] -1   0   0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B) 
   [10] 0   0   0x000a0000 - 0x000affff (0x10000) MS[B] 
   [11] 0   0   0x000b0000 - 0x000b7fff (0x8000) MS[B] 
   [12] 0   0   0x000b8000 - 0x000bffff (0x8000) MS[B] 
   [13] -1   0   0x0000ffff - 0x0000ffff (0x1) IX[B] 
   [14] -1   0   0x00000000 - 0x000000ff (0x100) IX[B] 
   [15] -1   0   0x0000dfe0 - 0x0000dfe7 (0x8) IX[B] 
   [16] -1   0   0x0000df80 - 0x0000df9f (0x20) IX[B] 
   [17] -1   0   0x0000df00 - 0x0000df3f (0x40) IX[B] 
   [18] -1   0   0x00000400 - 0x0000041f (0x20) IX[B] 
   [19] -1   0   0x0000eed0 - 0x0000eedf (0x10) IX[B] 
   [20] -1   0   0x0000efa0 - 0x0000efa3 (0x4) IX[B] 
   [21] -1   0   0x0000ef68 - 0x0000ef6f (0x8) IX[B] 
   [22] -1   0   0x0000efa4 - 0x0000efa7 (0x4) IX[B] 
   [23] -1   0   0x0000efa8 - 0x0000efaf (0x8) IX[B] 
   [24] -1   0   0x0000fc00 - 0x0000fc0f (0x10) IX[B] 
   [25] -1   0   0x000001f0 - 0x000001f0 (0x1) IX[B] 
   [26] -1   0   0x000001f0 - 0x000001f7 (0x8) IX[B] 
   [27] -1   0   0x000001f0 - 0x000001f0 (0x1) IX[B] 
   [28] -1   0   0x000001f0 - 0x000001f7 (0x8) IX[B] 
   [29] -1   0   0x0000ef80 - 0x0000ef9f (0x20) IX[B] 
   [30] -1   0   0x0000ef40 - 0x0000ef5f (0x20) IX[B] 
   [31] -1   0   0x0000ef20 - 0x0000ef3f (0x20) IX[B] 
   [32] -1   0   0x0000ef00 - 0x0000ef1f (0x20) IX[B] 
   [33] -1   0   0x0000efe0 - 0x0000efe7 (0x8) IX[B](B) 
   [34] 0   0   0x000003b0 - 0x000003bb (0xc) IS[B] 
   [35] 0   0   0x000003c0 - 0x000003df (0x20) IS[B] 
(II) Setting vga for screen 0. 
(II) Loading sub module "int10" 
(II) LoadModule: "int10" 
(II) Loading /usr/lib/xorg/modules//libint10.so 
(II) Module int10: vendor="X.Org Foundation" 
   compiled for 1.3.0, module version = 1.0.0 
   ABI class: X.Org Video Driver, version 1.2 
(II) Loading sub module "vbe" 
(II) LoadModule: "vbe" 
(II) Loading /usr/lib/xorg/modules//libvbe.so 
(II) Module vbe: vendor="X.Org Foundation" 
   compiled for 1.3.0, module version = 1.1.0 
   ABI class: X.Org Video Driver, version 1.2 
(II) Loading sub module "vgahw" 
(II) LoadModule: "vgahw" 
(II) Loading /usr/lib/xorg/modules//libvgahw.so 
(II) Module vgahw: vendor="X.Org Foundation" 
   compiled for 1.3.0, module version = 0.1.0 
   ABI class: X.Org Video Driver, version 1.2 
(**) intel(0): Depth 16, (--) framebuffer bpp 16 
(==) intel(0): RGB weight 565 
(==) intel(0): Default visual is TrueColor 
(**) intel(0): Option "DRI" "True" 
(II) intel(0): Integrated Graphics Chipset: Intel(R) 865G 
(--) intel(0): Chipset: "865G" 
(--) intel(0): Linear framebuffer at 0xF0000000 
(--) intel(0): IO registers at addr 0xFE780000 
(II) intel(0): 1 display pipe available. 
(==) intel(0): Using XAA for acceleration 
(--) intel(0): Will try to allocate texture pool for old Mesa 3D driver. 
(II) intel(0): Will try to reserve 32768 kiB of AGP aperture space 
   for the DRM memory manager. 
(II) Loading sub module "ddc" 
(II) LoadModule: "ddc"(II) Module already built-in 
(II) Loading sub module "i2c" 
(II) LoadModule: "i2c"(II) Module already built-in 
(II) intel(0): Output VGA using monitor section SyncMaster_710N 
(II) intel(0): I2C bus "CRTDDC_A" initialized. 
(II) intel(0): I2C bus "DVODDC_D" initialized. 
(II) Loading sub module "sil164" 
(II) LoadModule: "sil164" 
(II) Loading /usr/lib/xorg/modules/drivers//sil164.so 
(II) Module sil164: vendor="X.Org Foundation" 
   compiled for 1.3.0, module version = 1.0.0 
   ABI class: X.Org Video Driver, version 1.2 
(II) intel(0): I2C bus "DVOI2C_E" initialized. 
(EE) intel(0): detecting sil164 
(EE) intel(0): Unable to read from DVOI2C_E Slave 112. 
(II) Loading sub module "ch7xxx" 
(II) LoadModule: "ch7xxx" 
(II) Loading /usr/lib/xorg/modules/drivers//ch7xxx.so 
(II) Module ch7xxx: vendor="X.Org Foundation" 
   compiled for 1.3.0, module version = 1.0.0 
   ABI class: X.Org Video Driver, version 1.2 
(II) intel(0): I2C bus "DVOI2C_E" removed. 
(II) intel(0): I2C bus "DVOI2C_E" initialized. 
(EE) intel(0): Unable to read from DVOI2C_E Slave 236. 
(II) Loading sub module "ivch" 
(II) LoadModule: "ivch" 
(II) Loading /usr/lib/xorg/modules/drivers//ivch.so 
(II) Module ivch: vendor="X.Org Foundation" 
   compiled for 1.3.0, module version = 1.0.0 
   ABI class: X.Org Video Driver, version 1.2 
(II) intel(0): I2C bus "DVOI2C_E" removed. 
(II) intel(0): I2C bus "DVOI2C_B" initialized. 
(EE) intel(0): ivch: Unable to read register 0x00 from DVOI2C_B:04. 
(II) Loading sub module "tfp410" 
(II) LoadModule: "tfp410" 
(II) Loading /usr/lib/xorg/modules/drivers//tfp410.so 
(II) Module tfp410: vendor="X.Org Foundation" 
   compiled for 1.3.0, module version = 1.0.0 
   ABI class: X.Org Video Driver, version 1.2 
(II) intel(0): I2C bus "DVOI2C_B" removed. 
(II) intel(0): I2C bus "DVOI2C_E" initialized. 
(II) intel(0): detecting tfp410 
(EE) intel(0): Unable to read from DVOI2C_E Slave 112. 
(EE) intel(0): tfp410 not detected got VID FFFFFFFF: from DVOI2C_E Slave 112. 
(II) intel(0): I2C bus "DVOI2C_E" removed. 
(II) intel(0): I2C bus "DVODDC_D" removed. 
(II) intel(0): Output VGA connected 
(II) intel(0): I2C device "CRTDDC_A:ddc2" registered at address 0xA0. 
(II) intel(0): I2C device "CRTDDC_A:ddc2" removed. 
(II) intel(0): EDID for output VGA 
(II) intel(0): Manufacturer: SAM  Model: 11e  Serial#: 1296707895 
(II) intel(0): Year: 2005  Week: 43 
(II) intel(0): EDID Version: 1.3 
(II) intel(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V 
(II) intel(0): Sync:  Separate  Composite 
(II) intel(0): Max H-Image Size [cm]: horiz.: 34  vert.: 27 
(II) intel(0): Gamma: 2.20 
(II) intel(0): DPMS capabilities: Off; RGB/Color Display 
(II) intel(0): First detailed timing is preferred mode 
(II) intel(0): redX: 0.650 redY: 0.330   greenX: 0.330 greenY: 0.600 
(II) intel(0): blueX: 0.150 blueY: 0.080   whiteX: 0.313 whiteY: 0.329 
(II) intel(0): Supported VESA Video Modes: 
(II) intel(0): 720x400@70Hz 
(II) intel(0): 640x480@60Hz 
(II) intel(0): 640x480@67Hz 
(II) intel(0): 640x480@72Hz 
(II) intel(0): 640x480@75Hz 
(II) intel(0): 800x600@56Hz 
(II) intel(0): 800x600@60Hz 
(II) intel(0): 800x600@72Hz 
(II) intel(0): 800x600@75Hz 
(II) intel(0): 832x624@75Hz 
(II) intel(0): 1024x768@60Hz 
(II) intel(0): 1024x768@70Hz 
(II) intel(0): 1024x768@75Hz 
(II) intel(0): 1280x1024@75Hz 
(II) intel(0): 1152x870@75Hz 
(II) intel(0): Manufacturer's mask: 0 
(II) intel(0): Supported Future Video Modes: 
(II) intel(0): #0: hsize: 1280  vsize 1024  refresh: 60  vid: 32897 
(II) intel(0): #1: hsize: 1152  vsize 864  refresh: 75  vid: 20337 
(II) intel(0): Supported additional Video Mode: 
(II) intel(0): clock: 108.0 MHz   Image Size:  338 x 270 mm 
(II) intel(0): h_active: 1280  h_sync: 1328  h_sync_end 1440 h_blank_end 1688 h_border: 0 
(II) intel(0): v_active: 1024  v_sync: 1025  v_sync_end 1028 v_blanking: 1066 v_border: 0 
(II) intel(0): Ranges: V min: 56  V max: 75 Hz, H min: 30  H max: 81 kHz, PixClock max 140 MHz 
(II) intel(0): Monitor name: SyncMaster 
(II) intel(0): Serial No: HMDYA60235 
(II) intel(0): EDID (in hex): 
(II) intel(0):    00ffffffffffff004c2d1e0137314a4d 
(II) intel(0):    2b0f01036c221b782aaaa5a654549926 
(II) intel(0):    145054bfef808180714f010101010101 
(II) intel(0):    010101010101302a009851002a403070 
(II) intel(0):    1300520e1100001e000000fd00384b1e 
(II) intel(0):    510e000a202020202020000000fc0053 
(II) intel(0):    796e634d61737465720a2020000000ff 
(II) intel(0):    00484d44594136303233350a20200016 
(II) intel(0): Using hsync ranges from config file 
(II) intel(0): Using vrefresh ranges from config file 
(II) intel(0): Printing DDC gathered Modelines: 
(II) intel(0): Modeline "800x600"   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync 
(II) intel(0): Modeline "800x600"   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync 
(II) intel(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync 
(II) intel(0): Modeline "640x480"   31.50  640 664 704 832  480 489 491 520 -hsync -vsync 
(II) intel(0): Modeline "640x480"   30.24  640 704 768 864  480 483 486 525 -hsync -vsync 
(II) intel(0): Modeline "640x480"   25.20  640 656 752 800  480 490 492 525 -hsync -vsync 
(II) intel(0): Modeline "720x400"   28.32  720 738 846 900  400 412 414 449 -hsync +vsync 
(II) intel(0): Modeline "1280x1024"  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync 
(II) intel(0): Modeline "1024x768"   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync 
(II) intel(0): Modeline "1024x768"   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync 
(II) intel(0): Modeline "1024x768"   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync 
(II) intel(0): Modeline "832x624"   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync 
(II) intel(0): Modeline "800x600"   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync 
(II) intel(0): Modeline "800x600"   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync 
(II) intel(0): Modeline "1152x864"  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync 
(II) intel(0): Modeline "1280x1024"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync 
(II) intel(0): Modeline "1152x864"  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync 
(II) intel(0): Modeline "1280x1024"  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync 
(II) intel(0): EDID vendor "SAM", prod id 286 
(II) intel(0): Not using mode "1280x1024" (vrefresh out of range) 
(II) intel(0): Not using mode "1024x768" (vrefresh out of range) 
(II) intel(0): Not using default mode "640x350" (bad mode clock/interlace/doublescan) 
(II) intel(0): Not using default mode "640x400" (bad mode clock/interlace/doublescan) 
(II) intel(0): Not using default mode "720x400" (bad mode clock/interlace/doublescan) 
(II) intel(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan) 
(II) intel(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan) 
(II) intel(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan) 
(II) intel(0): Not using default mode "640x480" (bad mode clock/interlace/doublescan) 
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan) 
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan) 
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan) 
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan) 
(II) intel(0): Not using default mode "800x600" (bad mode clock/interlace/doublescan) 
(II) intel(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan) 
(II) intel(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan) 
(II) intel(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan) 
(II) intel(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan) 
(II) intel(0): Not using default mode "1152x864" (bad mode clock/interlace/doublescan) 
(II) intel(0): Not using default mode "1280x960" (bad mode clock/interlace/doublescan) 
(II) intel(0): Not using default mode "1280x960" (bad mode clock/interlace/doublescan) 
(II) intel(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan) 
(II) intel(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan) 
(II) intel(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan) 
(II) intel(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan) 
(II) intel(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan) 
(II) intel(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan) 
(II) intel(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan) 
(II) intel(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan) 
(II) intel(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan) 
(II) intel(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan) 
(II) intel(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan) 
(II) intel(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan) 
(II) intel(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan) 
(II) intel(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan) 
(II) intel(0): Not using default mode "832x624" (bad mode clock/interlace/doublescan) 
(II) intel(0): Not using default mode "1152x768" (bad mode clock/interlace/doublescan) 
(II) intel(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan) 
(II) intel(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan) 
(II) intel(0): Not using default mode "1600x1024" (bad mode clock/interlace/doublescan) 
(II) intel(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan) 
(II) intel(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan) 
(II) intel(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan) 
(II) intel(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan) 
(II) intel(0): Printing probed modes for output VGA 
(II) intel(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz) 
(II) intel(0): Modeline "1280x1024"x59.9  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync (63.7 kHz) 
(II) intel(0): Modeline "1280x1024_75.0"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz) 
(II) intel(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz) 
(II) intel(0): Modeline "1152x864"x74.8  104.00  1152 1224 1344 1536  864 867 871 905 -hsync +vsync (67.7 kHz) 
(II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz) 
(II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz) 
(II) intel(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz) 
(II) intel(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz) 
(II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz) 
(II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz) 
(II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz) 
(II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz) 
(II) intel(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz) 
(II) intel(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz) 
(II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz) 
(II) intel(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz) 
(II) intel(0): Output VGA connected 
(II) intel(0): Output VGA using initial mode 1280x1024 
(II) intel(0): detected 128 kB GTT. 
(II) intel(0): detected 32636 kB stolen memory. 
(==) intel(0): video overlay key set to 0x83e 
(==) intel(0): Will not try to enable page flipping 
(==) intel(0): Triple buffering disabled 
(==) intel(0): Using gamma correction (1.0, 1.0, 1.0) 
(**) intel(0): Display dimensions: (340, 270) mm 
(**) intel(0): DPI set to (95, 120) 
(II) Loading sub module "fb" 
(II) LoadModule: "fb" 
(II) Loading /usr/lib/xorg/modules//libfb.so 
(II) Module fb: vendor="X.Org Foundation" 
   compiled for 1.3.0, module version = 1.0.0 
   ABI class: X.Org ANSI C Emulation, version 0.3 
(II) Loading sub module "xaa" 
(II) LoadModule: "xaa" 
(II) Loading /usr/lib/xorg/modules//libxaa.so 
(II) Module xaa: vendor="X.Org Foundation" 
   compiled for 1.3.0, module version = 1.2.0 
   ABI class: X.Org Video Driver, version 1.2 
(II) Loading sub module "ramdac" 
(II) LoadModule: "ramdac"(II) Module already built-in 
(II) intel(0): Comparing regs from server start up to After PreInit 
(II) Loading sub module "dri" 
(II) LoadModule: "dri" 
(II) Reloading /usr/lib/xorg/modules/extensions//libdri.so 
(II) do I need RAC?  No, I don't. 
(II) resource ranges after preInit: 
   [0] 0   0   0xfe780000 - 0xfe7fffff (0x80000) MS[B] 
   [1] 0   0   0xf0000000 - 0xf7ffffff (0x8000000) MS[B] 
   [2] -1   0   0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B) 
   [3] -1   0   0x000f0000 - 0x000fffff (0x10000) MX[B] 
   [4] -1   0   0x000c0000 - 0x000effff (0x30000) MX[B] 
   [5] -1   0   0x00000000 - 0x0009ffff (0xa0000) MX[B] 
   [6] -1   0   0xfe5ff000 - 0xfe5fffff (0x1000) MX[B] 
   [7] -1   0   0x50000000 - 0x500003ff (0x400) MX[B] 
   [8] -1   0   0xfe77bc00 - 0xfe77bfff (0x400) MX[B] 
   [9] -1   0   0xfe800000 - 0xfe7fffff (0x0) MX[B]O 
   [10] -1   0   0xfe780000 - 0xfe7fffff (0x80000) MX[B](B) 
   [11] -1   0   0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B) 
   [12] 0   0   0x000a0000 - 0x000affff (0x10000) MS[B](OprD) 
   [13] 0   0   0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD) 
   [14] 0   0   0x000b8000 - 0x000bffff (0x8000) MS[B](OprD) 
   [15] 0   0   0x0000efe0 - 0x0000efe7 (0x8) IS[B] 
   [16] -1   0   0x0000ffff - 0x0000ffff (0x1) IX[B] 
   [17] -1   0   0x00000000 - 0x000000ff (0x100) IX[B] 
   [18] -1   0   0x0000dfe0 - 0x0000dfe7 (0x8) IX[B] 
   [19] -1   0   0x0000df80 - 0x0000df9f (0x20) IX[B] 
   [20] -1   0   0x0000df00 - 0x0000df3f (0x40) IX[B] 
   [21] -1   0   0x00000400 - 0x0000041f (0x20) IX[B] 
   [22] -1   0   0x0000eed0 - 0x0000eedf (0x10) IX[B] 
   [23] -1   0   0x0000efa0 - 0x0000efa3 (0x4) IX[B] 
   [24] -1   0   0x0000ef68 - 0x0000ef6f (0x8) IX[B] 
   [25] -1   0   0x0000efa4 - 0x0000efa7 (0x4) IX[B] 
   [26] -1   0   0x0000efa8 - 0x0000efaf (0x8) IX[B] 
   [27] -1   0   0x0000fc00 - 0x0000fc0f (0x10) IX[B] 
   [28] -1   0   0x000001f0 - 0x000001f0 (0x1) IX[B] 
   [29] -1   0   0x000001f0 - 0x000001f7 (0x8) IX[B] 
   [30] -1   0   0x000001f0 - 0x000001f0 (0x1) IX[B] 
   [31] -1   0   0x000001f0 - 0x000001f7 (0x8) IX[B] 
   [32] -1   0   0x0000ef80 - 0x0000ef9f (0x20) IX[B] 
   [33] -1   0   0x0000ef40 - 0x0000ef5f (0x20) IX[B] 
   [34] -1   0   0x0000ef20 - 0x0000ef3f (0x20) IX[B] 
   [35] -1   0   0x0000ef00 - 0x0000ef1f (0x20) IX[B] 
   [36] -1   0   0x0000efe0 - 0x0000efe7 (0x8) IX[B](B) 
   [37] 0   0   0x000003b0 - 0x000003bb (0xc) IS[B](OprU) 
   [38] 0   0   0x000003c0 - 0x000003df (0x20) IS[B](OprU) 
(II) intel(0): Kernel reported 295424 total, 1 used 
(II) intel(0): I830CheckAvailableMemory: 1181692 kB available 
(==) intel(0): VideoRam: 131072 KB 
(II) intel(0): Attempting memory allocation with tiled buffers and 
          large DRI memory manager reservation: 
(II) intel(0): Allocating 5880 scanlines for pixmap cache 
(II) intel(0): Success. 
(II) intel(0): Increasing the scanline pitch to allow tiling mode (1280 -> 2048). 
(II) intel(0): Memory allocation layout: 
(II) intel(0): 0x00000000-0x0001ffff: ring buffer (128 kB) 
(II) intel(0): 0x00020000-0x00024fff: HW cursors (20 kB) 
(II) intel(0): 0x00025000-0x0002cfff: logical 3D context (32 kB) 
(II) intel(0): 0x00030000-0x01c27fff: front buffer (28640 kB) 
(II) intel(0): 0x01c28000-0x01c37fff: xaa scratch (64 kB) 
(II) intel(0): 0x01fdf000:            end of stolen memory 
(II) intel(0): 0x01fdf000-0x01fdffff: overlay registers (4 kB, 0x        3507a000 physical) 
(II) intel(0): 0x02000000-0x027fffff: back buffer (5120 kB) 
(II) intel(0): 0x02800000-0x02ffffff: depth buffer (5120 kB) 
(II) intel(0): 0x03000000-0x04ffffff: DRI memory manager (32768 kB) 
(II) intel(0): 0x05000000-0x06ffffff: textures (32768 kB) 
(II) intel(0): 0x08000000:            end of aperture 
(II) intel(0): front buffer is not tiled 
(II) intel(0): back buffer is tiled 
(II) intel(0): depth buffer is tiled 
drmOpenDevice: node name is /dev/dri/card0 
drmOpenDevice: open result is -1, (No such device or address) 
drmOpenDevice: open result is -1, (No such device or address) 
drmOpenDevice: Open failed 
drmOpenDevice: node name is /dev/dri/card0 
drmOpenDevice: open result is -1, (No such device or address) 
drmOpenDevice: open result is -1, (No such device or address) 
drmOpenDevice: Open failed 
[drm] failed to load kernel module "i915" 
(II) intel(0): [drm] drmOpen failed 
(EE) intel(0): [dri] DRIScreenInit failed. Disabling DRI. 
(II) intel(0): Page Flipping disabled 
(==) intel(0): Write-combining range (0xf0000000,0x8000000) 
(II) intel(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000 
(II) intel(0): Using XFree86 Acceleration Architecture (XAA) 
   Screen to screen bit blits 
   Solid filled rectangles 
   8x8 mono pattern filled rectangles 
   Indirect CPU to Screen color expansion 
   Solid Horizontal and Vertical Lines 
   Offscreen Pixmaps 
   Setting up tile and stipple cache: 
      32 128x128 slots 
      32 256x256 slots 
      16 512x512 slots 
(==) intel(0): Backing store disabled 
(==) intel(0): Silken mouse enabled 
(II) intel(0): Initializing HW Cursor 
(II) intel(0): xf86BindGARTMemory: bind key 0 at 0x01fdf000 (pgoffset 8159) 
(II) intel(0): Output configuration: 
(II) intel(0):   Pipe A is on 
(II) intel(0):   Display plane A is now enabled and connected to pipe A. 
(II) intel(0):   Output VGA is connected to pipe A 
(**) Option "dpms" 
(**) intel(0): DPMS enabled 
(II) intel(0): Set up overlay video 
(II) intel(0): direct rendering: Failed 
(II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message. 
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
(EE) AIGLX: Screen 0 is not DRI capable 
(II) Loading local sub module "GLcore" 
(II) LoadModule: "GLcore" 
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so 
(II) Module GLcore: vendor="X.Org Foundation" 
   compiled for 1.3.0, module version = 1.0.0 
   ABI class: X.Org Server Extension, version 0.3 
(II) GLX: Initialized MESA-PROXY GL provider for screen 0 
(II) intel(0): Setting screen physical size to 338 x 270 
(**) Option "Protocol" "auto" 
(**) Mouse: Device: "/dev/input/mice" 
(**) Mouse: Protocol: "auto" 
(**) Option "CorePointer" 
(**) Mouse: Core Pointer 
(**) Option "Device" "/dev/input/mice" 
(==) Mouse: Emulate3Buttons, Emulate3Timeout: 50 
(**) Option "ZAxisMapping" "4 5 6 7" 
(**) Mouse: ZAxisMapping: buttons 4, 5, 6 and 7 
(**) Mouse: Buttons: 11 
(**) Mouse: Sensitivity: 1 
(**) Option "CoreKeyboard" 
(**) Keyboard: Core Keyboard 
(**) Option "Protocol" "standard" 
(**) Keyboard: Protocol: standard 
(**) Option "AutoRepeat" "500 30" 
(**) Option "XkbRules" "xorg" 
(**) Keyboard: XkbRules: "xorg" 
(**) Option "XkbModel" "pc104" 
(**) Keyboard: XkbModel: "pc104" 
(**) Option "XkbLayout" "us,ru (winkeys)" 
(**) Keyboard: XkbLayout: "us,ru (winkeys)" 
(**) Option "XkbOptions" "grp:alt_shift_toggle" 
(**) Keyboard: XkbOptions: "grp:alt_shift_toggle" 
(**) Option "CustomKeycodes" "off" 
(**) Keyboard: CustomKeycodes disabled 
(II) XINPUT: Adding extended input device "Keyboard" (type: KEYBOARD) 
(II) XINPUT: Adding extended input device "Mouse" (type: MOUSE) 
(--) Mouse: PnP-detected protocol: "ExplorerPS/2" 
(II) Mouse: ps2EnableDataReporting: succeeded

```

***xorg.conf***
```

Section "ServerLayout"
	Identifier     "Dimas Layout"
	Screen      0  "Screen" 0 0
	InputDevice    "Mouse" "CorePointer"
	InputDevice    "Keyboard" "CoreKeyboard"
	Option "AIGLX" "true"
EndSection
 
Section "Files"
	RgbPath      "/usr/share/X11/rgb"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/misc/"
	FontPath     "/usr/share/fonts/TTF/"
	FontPath     "/usr/share/fonts/OTF"
	FontPath     "/usr/share/fonts/Type1/"
	FontPath     "/usr/share/fonts/100dpi/"
	FontPath     "/usr/share/fonts/75dpi/"
	FontPath     "/usr/share/fonts/terminus"
	FontPath     "/usr/share/fonts/dejavu"
EndSection
 
Section "Module"
	Load  "glx"
	Load  "extmod"
   SubSection  "extmod"
     Option    "omit xfree86-dga"   # don't initialise the DGA extension
   EndSubSection
	Load  "record"
	Load  "dbe"
	Load  "GLcore"
	Load  "xtrap"
	Load  "dri"
	Load  "freetype"
	Load  "type1"
EndSection
 
Section "InputDevice"
  Identifier  "Keyboard"
  Driver      "kbd"
  Option "AutoRepeat" "500 30"
  Option "XkbRules"	"xorg"
  Option "XkbModel"	"pc104"
  Option "XkbLayout"	"us,ru (winkeys)"
  Option "XkbOptions" "grp:alt_shift_toggle"
EndSection
 
Section "InputDevice"
	Identifier  "Mouse"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection
 
Section "Monitor"
	#DisplaySize	  340   270	# mm
	Identifier   "SyncMaster_710N"
	VendorName   "SAM"
	ModelName    "SyncMaster"
  ### Comment all HorizSync and VertRefresh values to use DDC:
	HorizSync    30.0 - 81.0
	VertRefresh  56.0 - 75.0
	Option	    "DPMS"
	ModeLine     "1280x1024_75.0" 108.0 1280 1328 1440 1688 1024 1025 1028
1066 +hsync +vsync
EndSection
 
Section "Device"
	  Identifier  "VESA Framebuffer"
		Driver      "vesa"
EndSection
 
Section "Device"
         ### Available Driver options are:-
         ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
         ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
         ### [arg]: arg optional
         #Option     "NoAccel"            	# [<bool>]
         #Option     "SWcursor"           	# [<bool>]
         #Option     "ColorKey"           	# <i>
         #Option     "CacheLines"         	# <i>
         #Option     "Dac6Bit"            	# [<bool>]
         Option     "DRI" "True"               	# [<bool>]
         #Option     "NoDDC"             	# [<bool>]
         #Option     "ShowCache"          	# [<bool>]
         #Option     "XvMCSurfaces"       	# <i>
         #Option     "PageFlip"           	# [<bool>]
	Identifier  "intel"
	Driver      "intel"
	#Driver      "i810"
	VendorName  "Intel Corporation"
	BoardName   "82865G Integrated Graphics Controller"
	BusID       "PCI:0:2:0"
EndSection
 
Section "DRI"
	Mode 0666
EndSection
 
Section "Screen"
  Identifier "Screen"
  Device     "intel"
  #Device     "VESA Framebuffer"
  Monitor    "SyncMaster_710N"
  DefaultDepth 16
  Subsection "Display"
	Depth       16
	Modes       "1280x1024_75.0"
	ViewPort    0 0
  EndSubsection
EndSection

```

Thanks... :)

---

### Post by agds on 2008-03-12
I've personally experienced the problem of being stuck at one refresh rate with my own SyncMaster monitor.  Which tool did you use to determine the modeline? gtf.c worked well for me, but I'm using an NVIDIA card.

I don't know if xorg.conf is case-sensitive, but you might want to try Modeline instead of ModeLine.

---

### Post by IceSunrise on 2008-03-12
All what you need to do that change upper limits of HorizSync and VertRefresh. You need to set it some higher than in monitor specifications and of course write correct modeline:
```

Modeline "1280x1024_75.0" 135.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync

```

---

### Post by v_mallikarjun on 2008-05-01
This might help you for ubuntu hardy users using Nvidia cards and not able to increase there resolution from 800x600.
  type  "displayconfig-gtk" in terminal and modify the settings

---

### Post by bred on 2008-05-02
[COLOR="Blue"]it worked for me, my compiz is working for the 1'st time, so a BIG thanks ![/COLOR]

---

### Post by mtbdrew on 2008-05-20
Nice information in one location.

Thank you.

---

### Post by stumegan on 2008-05-30
If this helps. I had the same issue with an install on an old GX110 with an onboard Intel 810 chip. I read all the posts here., and found that all I needed to do was add the Vert and Horiz settings in the monitor section. I found these just by plugging in the monitor type/modle number in a google search. I did not need toadd modes, or other values elsewhere. Just the vert and horiz values were all i needed.
Thanks to all before me who posted help on this. I am new to ubuntu, but really excited that it seems to work well and is a great combination of windows/unix 

:guitar:

---

### Post by haplo9 on 2008-07-06
Heimo writes

"Howto: change resolution/refresh rate in Xorg
If you can't change your display resolution or refresh rate (no desired option available) these instructions may help.

Backup your configuration file

Code:
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup


How to reconfigure Xorg
Notice that auto detection of devices works best if Xorg is not running. Therefore it's recommended to stop X before reconfiguring this will put you to text only mode / command line:

Code:
sudo /etc/init.d/gdm stop (or kdm for KDE)




I do this in terminal and the backup works fine. However when enter 
sudo /etc/init.d/gdm stop everything goes blank and i have to reboot.
How do i follow Heimo's instruction if my screen is blank. 
I believe I am badly misunderstanding what to do.
help!8-[8-[8-[8-[

charels 8-[

---

### Post by Mirmil on 2008-07-27
Hi there! I am using Hardy and I have strange problem with my refreshing rate: I cannot set it higher than 60 (range is 56-60) but ACTUALLY it seems to be higher (at 56 it would flicker much more than it does now).

My xorx.conf:

> Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Philips 107S11"
	VendorName   "PHILIPS"
	HorizSync    30-88
	VertRefresh  50-160
 # V-freq: 85.00 Hz  // h-freq: 68.79 KHz
#Modeline "1024x768" 97.41  1024 1072 1192 1416   768  768  771  809 



EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Philips 107S11"
	Device		"Configured Video Device"
	Defaultdepth	24
 	SubSection "Display"
        	Depth        24
       		 Modes      "1024x768_85.00"
    EndSubSection

EndSection


but in the log I've found this:

> II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce 7600 GS (G73) at PCI:7:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 262144 kBytes
(--) NVIDIA(0): VideoBIOS: 05.73.22.19.00
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 7600 GS at PCI:7:0:0:
(--) NVIDIA(0):     PHILIPS 107S (CRT-0)
(--) NVIDIA(0): PHILIPS 107S (CRT-0): 400.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
**(WW) NVIDIA(0): No valid modes for "1024x768_85.00"; removing.**
(WW) NVIDIA(0): 
(WW) NVIDIA(0): Unable to validate any modes; falling back to the default mode
(WW) NVIDIA(0):     "nvidia-auto-select".
(WW) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
(--) NVIDIA(0): DPI set to (104, 113); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp

EDIT: It seems that I managed to bypass this problem a bit using [ENVY](http://www.albertomilone.com/envyngfaq.html#A) script, but official screen resolution still says "56 Hz refresh rate"

---

### Post by yamatteo on 2008-08-29
Hi, I have some problem with Ubuntu 7.04 upgrade. I'm not sure this concern refresh rate so I'm going to tell what happend.
7.04 works good and complete the upgrade without reporting any problem. The next reboot, when it's time to load login windows, screen go mad.
It seems like evry single line of pixels choose her own horizontal position, even it at the exact height. So it is not possible to recognize nothing but colors...

Does this concern with xorg?

(I tried to install Hardy directly, but same result)

---

### Post by jarrettgold11 on 2008-09-05
Ever Want free stuff but you cant afford it? Then join prize rebel now! In order for you to get a game like GTA 4 or a free Wii or even a PS3 all you have to do is fill out surveys and get points easy as that. No more getting up and having to buy stuff. Get it right in the privacy of your home and for FREE!!! Join now at         


            [http://www.prizerebel.com/index.php?r=507390](http://www.prizerebel.com/index.php?r=507390)   
              
                          Thats Right 

            [http://www.prizerebel.com/index.php?r=507390](http://www.prizerebel.com/index.php?r=507390)

---

### Post by trunks14 on 2008-09-25
Yupi!, this helped me get my desired 1440x900 resolution on this monitor, it looked really awkward on good old 1024x768 ^_^

---

### Post by eekfonky on 2008-10-27
Having issues here too with both Hardy and now Intrepid
Here is my xorg as it stands, when I restart it goes into low graphics mode due to parsing error??
```
Section "Monitor"
	Identifier	"Monitor0"
	VendorName	"Acer"
	Model Name	"AL1716"
	HorizSync       31.0 - 81.0
    	VertRefresh     56.0 - 75.0
	Modeline "1280x1024" 151.83  1280 1360 1544 1888  1024 1024 1027 1072 +hsync +vsync
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Monitor0"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection
```

---

### Post by gg4u on 2008-10-31
I guys, just installed it for the first time.

I cannot see properly, screen resolution is different (it is a dell with not a 800x600 or alike monitor.. )

Is there any GUI to change the screen resolution?

I tryed via the command line:
sudo /etc/x11 ...

but it reply: no such file or directory.

Likely I have another computer to surgf in internet...

Please help!

---

### Post by bobby.blanc on 2008-11-04
Hello, I got caught out with the Ibex unsupported driver release bug and as a result was stuck in 'low graphics mode'. Just when I thought things couldn't get worse I tried changing the screen resolution which totally messed up my display - I can't see anything to put it back.

The login screen is still visable and when I log in as another user it is ok, so I think there is a user specific resolution setting for my other user that I need to reset, but I can't find it.

Any help appreciated.

---

### Post by kindofabuzz on 2008-11-22
> **gg4u said:**
> I guys, just installed it for the first time.

I cannot see properly, screen resolution is different (it is a dell with not a 800x600 or alike monitor.. )

Is there any GUI to change the screen resolution?

I tryed via the command line:
sudo /etc/x11 ...

but it reply: no such file or directory.

Likely I have another computer to surgf in internet...

Please help!

It's /etc/X11 not /etc/x11

---

### Post by eekfonky on 2008-11-23
did you try this:
```
sudo gedit /etc/X11/xorg.conf
```

---

### Post by chaeron on 2009-01-14
I've got a bunch of Koala's, all running latest updated Intrepid release of Ubuntu.

They are all sharing a monitor, keyboard, mouse using a KVM switch, and I typically use VNC to access the machines rather than the physical kvm devices.

The latest X11 release has a problem when you boot without a monitor attached, ie. it's switched to a different box through the KVM. It generates an error dialog and gives you the option of booting into low rez mode.  

Has anyone figured out a way to boot a machine without an attached monitor and have X use hardcoded settings for the monitor under Intrepid?

I've tried custom xorg.conf files, but nothing works and none of the Ubuntu Forums have come up with a resolution to this.

Free set of wildlife posters to anyone that has resolved this and can steer me in the right direction!

Thanks!

---

### Post by kimharding on 2009-04-25
I am having trouble changing the screen resolution under Jaunty Jackalope on my laptop, it uses a Trident Video Accelerator Cyberblade XP Ai1 card. I have tried ```
sudo nano /etc/X11/xorg.conf
``` but can get it to stick. ](*,)](*,)](*,)

I had everything working under Intrepid Ibex but that all got wiped out by the update. Anyone got any ideas??

---

### Post by SirAry on 2009-05-10
I am having trouble with my 42'' TFT TV on hdmi.
On vga I have image, all good, but monitor detected as unknown so max res. is 1360x768. No big problem, is ok as screen for X but movies and other sucks. So I need HDMI output ... All worked in Ibex so no hardware problems ... After  I set resolution 1360x768 - monitor is detected as HEC 49" - and I switch to HDMI the screen si trying to show image, and after 0.5 sec falls in black for 0.5 sec and so on ...
I need to set a generic panel -1920x768 with all refresh rates ...
How is posible to be so hard in Ubuntu to select a monitor, a resolution and a refresh rate ? I am searching for days now ...
I had seen that xrandr still works but settings are not saved, xorg.conf is changed ...
My hw is Asus p5q-em (intel g45) so intel video onboard ...
Hmmm ... 
please help

---

### Post by kiarfuzzy on 2009-05-19
This kind of things makes people run from linux ....
To do a simple thing like changing refresh rate you have to spend like 10 min , if you know a little bit about linux ... In windows with just a few clicks your done ... I keep installing and uninstalling ubuntu because of this kind of problems.. at almost every little thing you normaly do it in windows , in linux you have to read like 10 pages of documentation an 7 of them you read for nothing .....
When this kind of problems will disapear from linux there will be a lot of people who will swich to linux ...

But, the problems are not because of linux , they are because of the software manufacters..

Sorry for my bad english ...

---

### Post by Captain_Falafel on 2009-07-20
I've got a problem and I get lost in the posts.

after I plugged in ```
 /var/log/Xorg.0.log
```, I get some errors and warnings listed here:

```
(EE) Failed to initialize GLX extension (Compatibile NVIDIA X driver not found)
(WW) VESA(0): Unable to estimate virtual size
(WW) VESA(0): No valid modes left. Trying less strict filter...
(WW) VESA(0): The directory "/usr/share/fonts/X11/cyrillic" does not exist
```

I use an NVIDIA GeForce 8200 card and the refresh rate is at 0 hz with no other option..

---

### Post by James_nac on 2009-08-02
I'm a newbie, but "sudo /etc/init.d/gdm stop" does not give me any mode, just a blinking cursor and I have no choice but to reboot.

---

### Post by James_nac on 2009-08-16
I still can't figure out what to do about my resolution being wrong.  Again, it should be 1600x1200 as it is in Windows.  The highest option I'm given is 1400x1050 and the highest that works reasonably ok is 1280x1024.

The first time I tried I gave up and restored Windows.  It looks like I'll be doing the same this time.  I really wanted to get away from Windows and maybe even learn how to develop for Linux and contribute.  I can't believe it is this difficult to resolve a simple video mode issue.  I've been writing software code for 25+ years and can't figure this out?  How will Linux ever be accepted by the masses?  If someone could give me a clue and save me from the Microsoft tyranny, please please do.

Sorry for the rant, very frustrated.

---

### Post by gmsbeak22 on 2009-09-10
tried the first post and it worked like a charm.:smile:

---

### Post by gmsbeak22 on 2009-09-22
> **gmsbeak22 said:**
> tried the first post and it worked like a charm.:smile:

It worked like a charm the first time, however it seldom works.  I enter the codes in terminal, but the screen goes blank with a blinking cursor???

Can anyone help?](*,)

---

### Post by missmoondog on 2009-09-29
seeing as how this thread has been going on for years, at least since i tried the 6.04 version of xubuntu, i have one computer that i just can't get right.

when entering sudo gedit /etc/X11/xorg.conf, i don't have squat in there. nothing to change. i believe this computer has a SiS 650/651/740/661FX/741/760 series graphics card. i have ALL screen sizes available, but it won't stick at 1024x768. it always wants to go back to 1280x1024. what do i have to do?

here it is:
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
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

---

### Post by missmoondog on 2009-10-13
wow! no help on this?
this isn't a read only thread. :(

---

### Post by samisomy on 2009-10-17
> **kiarfuzzy said:**
> This kind of things makes people run from linux ....
To do a simple thing like changing refresh rate you have to spend like 10 min , if you know a little bit about linux ... In windows with just a few clicks your done ... I keep installing and uninstalling ubuntu because of this kind of problems.. at almost every little thing you normaly do it in windows , in linux you have to read like 10 pages of documentation an 7 of them you read for nothing .....
When this kind of problems will disapear from linux there will be a lot of people who will swich to linux ...

But, the problems are not because of linux , they are because of the software manufacters..

Sorry for my bad english ...

[SIZE=5][COLOR=Green]
you are absolutely right,
add my voice to you !!!![/COLOR][/SIZE]

---

### Post by kimharding on 2009-10-30
The solution I ended up with is

Open a terminal, the easiest way is to use Alt+F2, then paste in the command:

      ```
gksudo gedit /etc/X11/xorg.conf 

```
  This takes you into a text editor with root permissions (so take care), then paste in the following code:

 ```
Section "Device"
  Identifier "Trident Microsystems CyberBlade XPAi1"
  Driver "trident"
   BusID "PCI:1:0:0"
EndSection

 Section "Monitor"
  Identifier "Configured Monitor"
  Option "DPMS" "true"
  HorizSync 30.0-60.0
  VertRefresh 50.0-70.0
EndSection

 Section "Screen"
  Identifier "Default Screen"
  Monitor "Configured Monitor"
  Device "Configured Video Device"
  DefaultDepth 24
  SubSection "Display"
  Depth 24
  Modes "1024x768" "800x600"
EndSubSection

 EndSection   
```

Don't know if that is any help to anyone.

Just started to try out Karmic Koala and am having the same problems all over again... ](*,)](*,)](*,)

At this rate I might as well just get Window 7 and save all the hassle.:(

---

### Post by missmoondog on 2009-10-30
Hey Kim,
I believe that looks familiar to how I had xorg set up last time I was using Xubuntu (6.04). All I want is the 1024x768 option.

On the right computer at the moment, but been testing Vista out on it. Always hated Vista, but have to learn some of it.

Thanks.
Will give it a try.

---

### Post by LanceyD on 2009-11-02
I am having a similar problem, but being a newbie i am totally confused at what to do after reading the OP and 16 pages of comments.  I just want my screen to work at 85Hz like it used to.

Ubuntu 9.04 
GeForce 7900 GTO
Belinea 19" CRT

Is there a reliable solution to this yet?  
Thanks.

---

### Post by rmp73 on 2009-11-02
Gosh, this seems to be a common problem for people.

As a noob to Ubuntu and Linux I'm only posting after having spent several hours trying to exhaust every suggestion I can find on these threads.

My story: I've a Sony Vaio VGN-FZ11Z with a nVidia GeForce 8400M GT chipset inside.  I recently decided to make the move to Ubuntu 9.10.  I have downloaded the NVidia hardware drivers via 'System/Admin/Hardware drivers' and I'm running version 185.

The default laptop screen is running fine at 1280x800.

I recently bought an LG W2243S LCD Monitor, which it is claimed has a preferred mode of 1920x1080 pixels.

I simply CANNOT get the external LCD to display at anything other than 1024x768 pixels.  I'm wondering if it's a restriction on the VGA output of the Sony Vaio (as I know only 2 channel audio is enabled over the HDMI port on this laptop, rather than full 5.1 etc.)

I've attached the xorg.conf content below, as well as entries (warnings) from the /var/log/Xorg.0.log file.  Can someone help please?  I've tried making changes to xorg.conf in text mode having disabled the GRUB as suggested on page 1, which is a great tip BTW.

I used 'cvt 1920 1080 60' to generate a modeline. 

xorg.conf >>>>
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@palmer)  Sun Feb  1 20:21:04 UTC 2009


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 1024 0
    Screen      1  "Screen1" LeftOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Nvidia Default Flat Panel"
    HorizSync       29.0 - 49.0
    VertRefresh     0.0 - 61.0
    Option         "DPMS"
EndSection

Section "Monitor"

    # HorizSync source: xconfig, VertRefresh source: xconfig
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "CRT-0"
    HorizSync       28.0 - 55.0
    VertRefresh     43.0 - 72.0
    ModeLine       "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8400M GT"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8400M GT"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "DFP: 1280x800_60 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"

# Removed Option "metamodes" "CRT: nvidia-auto-select +0+0"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "TwinView" "0"
    Option         "metamodes" "1920x1080 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


/var/log/Xorg.0.log >>>>
X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux ryan-vaio 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-14-generic root=UUID=d2f09b89-c028-4ce3-8286-624692b03a04 ro quiet splash
Build Date: 26 October 2009  05:15:02PM
xorg-server 2:1.6.4-2ubuntu4 (buildd@) 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Nov  2 19:23:32 2009
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
(**) |-->Screen "Screen1" (1)
(**) |   |-->Monitor "Monitor1"
(**) |   |-->Device "Device1"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
(**) Option "Xinerama" "0"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
(==) ModulePath set to "/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(II) Loader magic: 0x3bc0
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.4
	X.Org Video Driver: 5.0
	X.Org XInput driver : 4.0
	X.Org Server Extension : 2.0
(II) Loader running on linux
(--) using VT number 9

(--) PCI:*(0:1:0:0) 10de:0426:104d:9005 nVidia Corporation G86 [GeForce 8400M GT] rev 161, Mem @ 0xce000000/16777216, 0xd0000000/268435456, 0xcc000000/33554432, I/O @ 0x00002000/128
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) "extmod" will be loaded. This was enabled by default and also specified in the config file.
(II) "dbe" will be loaded. This was enabled by default and also specified in the config file.
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.
(II) "record" will be loaded by default.
(II) "dri" will be loaded by default.
(II) "dri2" will be loaded by default.
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "type1"
(WW) Warning, couldn't open module type1
(II) UnloadModule: "type1"
(EE) Failed to load module "type1" (module does not exist, 0)
(II) LoadModule: "freetype"
(WW) Warning, couldn't open module freetype
(II) UnloadModule: "freetype"
(EE) Failed to load module "freetype" (module does not exist, 0)
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
(II) NVIDIA GLX Module  185.18.36  Fri Aug 14 17:50:12 PDT 2009
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.1.0
	ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Video Driver
(II) NVIDIA dlloader X Driver  185.18.36  Fri Aug 14 17:24:40 PDT 2009
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01@00:00:0
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "wfb"
(II) LoadModule: "wfb"
(II) Loading /usr/lib/xorg/modules//libwfb.so
(II) Module wfb: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.4
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Module "ramdac" already built-in
(II) resource ranges after probing:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "TwinView" "0"
(**) NVIDIA(0): Option "MetaModes" "DFP: 1280x800_60 +0+0"
(**) NVIDIA(0): Option "TwinViewXineramaInfoOrder" "DFP-0"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
(II) NVIDIA(0): NVIDIA GPU GeForce 8400M GT (G86M) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 524288 kBytes
(--) NVIDIA(0): VideoBIOS: 60.86.3b.00.15
(II) NVIDIA(0): Detected PCI Express Link width: 16X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce 8400M GT at PCI:1:0:0:
(--) NVIDIA(0):     CRT-0
(--) NVIDIA(0):     Nvidia Default Flat Panel (DFP-0)
(--) NVIDIA(0): CRT-0: 400.0 MHz maximum pixel clock
(--) NVIDIA(0): Nvidia Default Flat Panel (DFP-0): 330.0 MHz maximum pixel
(--) NVIDIA(0):     clock
(--) NVIDIA(0): Nvidia Default Flat Panel (DFP-0): Internal Dual Link LVDS
(II) NVIDIA(0): Display Device found referenced in MetaMode: DFP-0
(II) NVIDIA(0): Assigned Display Device: DFP-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "DFP:1280x800_60+0+0"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 800
(--) NVIDIA(0): DPI set to (101, 101); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.
(**) NVIDIA(1): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(1): RGB weight 888
(==) NVIDIA(1): Default visual is TrueColor
(==) NVIDIA(1): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(1): Option "TwinView" "0"
(**) NVIDIA(1): Option "MetaModes" "1920x1080 +0+0"
(**) NVIDIA(1): Option "TwinViewXineramaInfoOrder" "CRT-0"
(**) NVIDIA(1): Enabling RENDER acceleration
(II) NVIDIA(1): NVIDIA GPU GeForce 8400M GT (G86M) at PCI:1:0:0 (GPU-0)
(--) NVIDIA(1): Memory: 524288 kBytes
(--) NVIDIA(1): VideoBIOS: 60.86.3b.00.15
(II) NVIDIA(1): Detected PCI Express Link width: 16X
(--) NVIDIA(1): Interlaced video modes are supported on this GPU
(--) NVIDIA(1): Connected display device(s) on GeForce 8400M GT at PCI:1:0:0:
(--) NVIDIA(1):     CRT-0
(--) NVIDIA(1):     Nvidia Default Flat Panel (DFP-0)
(--) NVIDIA(1): CRT-0: 400.0 MHz maximum pixel clock
(--) NVIDIA(1): Nvidia Default Flat Panel (DFP-0): 330.0 MHz maximum pixel
(--) NVIDIA(1):     clock
(--) NVIDIA(1): Nvidia Default Flat Panel (DFP-0): Internal Dual Link LVDS
(II) NVIDIA(1): Assigned Display Device: CRT-0
(WW) NVIDIA(1): No valid modes for "1920x1080+0+0"; removing.
(WW) NVIDIA(1): 
(WW) NVIDIA(1): Unable to validate any modes; falling back to the default mode
(WW) NVIDIA(1):     "nvidia-auto-select".
(WW) NVIDIA(1): 
(II) NVIDIA(1): Validated modes:
(II) NVIDIA(1):     "nvidia-auto-select"
(II) NVIDIA(1): Virtual screen size determined to be 1024 x 768
(WW) NVIDIA(1): Unable to get display device CRT-0's EDID; cannot compute DPI
(WW) NVIDIA(1):     from CRT-0's EDID.
(==) NVIDIA(1): DPI set to (75, 75); computed from built-in default
(==) NVIDIA(1): Enabling 32-bit ARGB GLX visuals.
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  Yes, I do.
(II) resource ranges after preInit:
	[0] -1	0	0xffffffff - 0xffffffff (0x1) MX[B]
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x00000000 (0x1) IX[B]
(II) NVIDIA(0): Initialized GPU GART.
(II) NVIDIA(0): Setting mode "DFP:1280x800_60+0+0"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(==) NVIDIA(0): Disabling shared memory pixmaps
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(II) Loading extension XINERAMA
(==) RandR enabled
(II) NVIDIA(1): Initialized GPU GART.
(II) NVIDIA(1): Setting mode "nvidia-auto-select"
(II) NVIDIA(1): NVIDIA 3D Acceleration Architecture Initialized
(==) NVIDIA(1): Disabling shared memory pixmaps
(II) NVIDIA(1): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(1): Backing store disabled
(==) NVIDIA(1): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(1): DPMS enabled
(==) RandR enabled
(II) Entity 0 shares no resources
(II) Entity 1 shares no resources
(II) Initializing built-in extension Generic Event Extension
(II) Initializing built-in extension SHAPE
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension BIG-REQUESTS
(II) Initializing built-in extension SYNC
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-MISC
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing extension GLX
(II) config/hal: Adding input device AT Translated Set 2 keyboard
(II) LoadModule: "evdev"
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so
(II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 2.2.5
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(**) AT Translated Set 2 keyboard: always reports core events
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"
(II) AT Translated Set 2 keyboard: Found keys
(II) AT Translated Set 2 keyboard: Configuring as keyboard
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "gb"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "gb"
(II) config/hal: Adding input device Sony Vaio Keys
(**) Sony Vaio Keys: always reports core events
(**) Sony Vaio Keys: Device: "/dev/input/event5"
(II) Sony Vaio Keys: Found keys
(II) Sony Vaio Keys: Configuring as keyboard
(II) XINPUT: Adding extended input device "Sony Vaio Keys" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "gb"
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/hal: Adding input device AlpsPS/2 ALPS GlidePoint
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.1.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(II) Synaptics touchpad driver version 1.1.2
(**) Option "Device" "/dev/input/event8"
(II) AlpsPS/2 ALPS GlidePoint: x-axis range 0 - 1023
(II) AlpsPS/2 ALPS GlidePoint: y-axis range 0 - 767
(II) AlpsPS/2 ALPS GlidePoint: pressure range 0 - 127
(II) AlpsPS/2 ALPS GlidePoint: finger width range 0 - 0
(II) AlpsPS/2 ALPS GlidePoint: buttons: left right middle
(--) AlpsPS/2 ALPS GlidePoint: touchpad found
(**) AlpsPS/2 ALPS GlidePoint: always reports core events
(II) XINPUT: Adding extended input device "AlpsPS/2 ALPS GlidePoint" (type: TOUCHPAD)
(**) AlpsPS/2 ALPS GlidePoint: (accel) keeping acceleration scheme 1
(**) AlpsPS/2 ALPS GlidePoint: (accel) filter chain progression: 2.00
(**) AlpsPS/2 ALPS GlidePoint: (accel) filter stage 0: 20.00 ms
(**) AlpsPS/2 ALPS GlidePoint: (accel) set acceleration profile 0
(--) AlpsPS/2 ALPS GlidePoint: touchpad found
(II) config/hal: Adding input device PS/2 Mouse
(**) PS/2 Mouse: always reports core events
(**) PS/2 Mouse: Device: "/dev/input/event7"
(II) PS/2 Mouse: Found 3 mouse buttons
(II) PS/2 Mouse: Found x and y relative axes
(II) PS/2 Mouse: Configuring as mouse
(**) PS/2 Mouse: YAxisMapping: buttons 4 and 5
(**) PS/2 Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "PS/2 Mouse" (type: MOUSE)
(**) PS/2 Mouse: (accel) keeping acceleration scheme 1
(**) PS/2 Mouse: (accel) filter chain progression: 2.00
(**) PS/2 Mouse: (accel) filter stage 0: 20.00 ms
(**) PS/2 Mouse: (accel) set acceleration profile 0
(II) PS/2 Mouse: initialized for relative axes.
(II) config/hal: Adding input device Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)
(**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): always reports core events
(**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Device: "/dev/input/event4"
(II) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Found 3 mouse buttons
(II) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Found x and y relative axes
(II) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Found scroll wheel(s)
(II) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): Configuring as mouse
(**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): YAxisMapping: buttons 4 and 5
(**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)" (type: MOUSE)
(**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): (accel) keeping acceleration scheme 1
(**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): (accel) filter chain progression: 2.00
(**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): (accel) filter stage 0: 20.00 ms
(**) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): (accel) set acceleration profile 0
(II) Microsoft Microsoft 3-Button Mouse with IntelliEye(TM): initialized for relative axes.

Thanks for helping.

---

### Post by missmoondog on 2009-11-07
just upgraded to karmic and now my xorg file looks like this:

Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
	Option	"AddARGBGLXVisuals"	"True"
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection


used the hardware driver finder to get this far, but can only get a refresh rate up to 52. i do have a 1024x768 desktop, at least. gosh, this is getting old!

---

### Post by running.rabbit on 2009-11-09
I've got an ATI graphics card and a Ubuntu Karmic system. At first I had the same problem (couldn't change refresh rate). What I did to solve that problem was simply modifying the /etc/X11/xorg.conf a bit:

```
Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor" 
    Identifier    "Configured Monitor" 
    HorizSync    30-85 
    VertRefresh    50-120 
EndSection 

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    SubSection "Display" 
        Depth    24 
        Modes    "1024x768"         
    EndSubSection 
EndSection
```

It didn't work until I removed the Driver of the Device section (Driver vesa)..
Now with this xorg.conf it works pretty well!

---

### Post by izak on 2009-11-19
While I managed to get my setup working after using this HOWTO, it was far from easy. I think we should support making these configuration changes easier, by promoting an idea in ubuntu brainstorm. 

I found [this idea]("http://brainstorm.ubuntu.com/idea/22091/") which seems to fit the description. If you think that this is an area of Ubuntu that needs improving please let your vote count!

---

### Post by realzippy on 2009-11-19
Thats an ancient HowTo.In Karmic there is no xorg.conf file anymore.
Also new nvidia driver is out (190.42),which solves many problems (e.g. wrong EDID readings),nvidia mobile chips bugs solved.
For nvidia users I highly recommend to install this driver before starting to edit modelines somewhere....

---

### Post by izak on 2009-11-19
> In Karmic there is no xorg.conf file anymore. Also new nvidia driver is out...
Yes, I noticed both of these facts. These in fact made it more difficult to migrate form 8.04, since I was left wondering whether I could still use my old (working) xorg.conf, or whether I could still use xorg.conf at all to change these settings.

After reading forum posts I gathered that you can add a new xorg.conf. Simply copying my old one did not work, since the driver had changed and the "virtual" mode I had used with the previous driver did not work with the new one. Even the new nvidia driver **did** give wrong/no EDID readings so I **had to** manually specify a modeline to get it to work.

Like I said in my comments in [the brainstorm idea]("http://brainstorm.ubuntu.com/idea/22091/"), when autodetection works, obviously that is the ideal and then there is no need for this. But when it fails (and, judging by the activity of this thread, it still does fail often enough to warrant attention) an easier GUI configuration method would help tremendously.

---

### Post by missmoondog on 2009-11-21
> **izak said:**
> Yes, I noticed both of these facts. These in fact made it more difficult to migrate form 8.04, since I was left wondering whether I could still use my old (working) xorg.conf, or whether I could still use xorg.conf at all to change these settings.

After reading forum posts I gathered that you can add a new xorg.conf. Simply copying my old one did not work, since the driver had changed and the "virtual" mode I had used with the previous driver did not work with the new one. Even the new nvidia driver **did** give wrong/no EDID readings so I **had to** manually specify a modeline to get it to work.

Like I said in my comments in [the brainstorm idea]("http://brainstorm.ubuntu.com/idea/22091/"), when autodetection works, obviously that is the ideal and then there is no need for this. But when it fails (and, judging by the activity of this thread, it still does fail often enough to warrant attention) an easier GUI configuration method would help tremendously.


boy, do you have that right!!

unfortunately, i don't have a clue as to what kind or model number the monitor is that's attached to this thing. there is absolutely nothing written, printed, stamped, etched, etc., on this thing!

running the hardware driver app finds nothing, for me. have a real old, onboard, gforce2, some kind of crap video card.

---

### Post by algonco on 2009-11-27
Hi all.
I'm using karmic withm ati x550. Only works 800x600 in my lg studioworks 552v (crt) monitor.
This is my xorg.org.
any idea?
Thanks a lot.
```
Section "ServerLayout"
        Identifier     "X.org Configured"
        Screen      0  "Screen0" 0 0
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
        Load  "extmod"
        Load  "dri2"
        Load  "dri"
        Load  "record"
        Load  "glx"
        Load  "dbe"
EndSection

Section "InputDevice"
        Identifier  "Keyboard0"
        Driver      "kbd"
EndSection
Section "InputDevice"
        Identifier  "Keyboard0"
        Driver      "kbd"
EndSection

Section "InputDevice"
        Identifier  "Mouse0"
        Driver      "mouse"
        Option      "Protocol" "auto"
        Option      "Device" "/dev/input/mice"
        Option      "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
        #DisplaySize      280   210     # mm
        Identifier   "Monitor0"
        VendorName   "GSM"
        ModelName    "52V"
        HorizSync    30.0 - 54.0
        VertRefresh  50.0 - 120.0
        Option      "DPMS"
EndSection
Section "Device"
       Identifier  "Card0"
        Driver      "radeon"
        VendorName  "ATI Technologies Inc"
        BoardName   "Radeon X550/X700 Series (RV410)"
        BusID       "PCI:4:0:0"
EndSection

Section "Screen"
        Identifier "Screen0"
        Device     "Card0"
        Monitor    "Monitor0"
        SubSection "Display"
        #       Viewport   0 0
                Depth     24
                Modes      "1024x768_60.00"
        EndSubSection
EndSection

```

---

### Post by izak on 2009-11-30
Follow the instructions in the first post regarding adding a custom modeline. It worked for me. Try using cvs (command line tool) to generate the modeline you require.

And, this is important, when things aren't working, check in the log file and look for errors and warnings. The instructions are in the first post. 

If this feels to difficult for you, please vote for [my solution]("http://brainstorm.ubuntu.com/idea/22091/") on brainstorm so the dev's can make it easier.

---

### Post by haradeep on 2009-12-12
This helped me to set my resolution, but I faced another problem.

I have to set my resolution every time when I reboot.


Problem solved by changing display options.

---

### Post by timmyhiggy on 2010-05-12
Hi

I just did a fresh install of 10.04 on an old-ish laptop that previously had a semi-working ubuntu 9.10 (wireless wasnt working, neither was headphone port amonst some other minor issues)

The default resolution is huge (1600X1200) so i cant see much of the screen when the actual screen itself is 1024X800 I can't seem to be able to change the display to something useful. 

I have no xorg.conf in /etc/X11/

If I use the GUI to change res then it looks like this:
[[IMG]http://img15.imageshack.us/img15/9576/imgp0464f.th.jpg[/IMG]](http://img15.imageshack.us/i/imgp0464f.jpg/)

Uploaded with [ImageShack.us](http://imageshack.us)

I have scoured google's suggestions, this forums suggestions etc please help!

---

### Post by Carlitoes on 2010-07-12
None of this helps me atall! i have a horrible 800x600 screen and thats all it will me have the resolution at!!!
i have tried the edit of xorg but its empty to start with. I am using a fujitsu siemens v5535 esprimo mobile.

---

### Post by scarflash on 2010-07-16
Hey I accidentaly changed the x11.config file in etc and now when i start the computer, it recognizes a problem in the graphics. I added a couple lines to the x11 files that were something along the liens "beginsection" blah blah "endsection" The blah blah included a bunch of resolutions that i wanted my computer to display like "1280*1024" Right now when i turn on the computer i get pass the flashing ubuntu white logo but after that i get several graphic options that lead to nothing but a blank screen if I click one of them. I'm running ubuntu 9.04. Thanks

---

### Post by Carlitoes on 2010-07-19
I simply Copied and pasted this to get a good resolution.
> Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
    HorizSync       30-50
        VertRefresh     50-120

EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
             SubSection      "Display"
                Viewport        0 0
                Depth           24
                Modes           "1024x768"
             EndSubSection
EndSection

---

### Post by scarflash on 2010-07-19
> **Carlitoes said:**
> I simply Copied and pasted this to get a good resolution.

Any ideas how to do this in the startup screen? My computer no longer turns on beyond the boot screen, it just goes blank. I'm guessing theres problems with the reolution file i edited.

---

### Post by Carlitoes on 2010-07-19
Well I am kind of new to Linux etc, But Have u tried low graphics mode? I am on windows at the moment so i can't check to see if there is the option to boot into low graphics mode although i am sure there is, I am currently not @ Home.

---

### Post by scarflash on 2010-07-19
> **Carlitoes said:**
> Well I am kind of new to Linux etc, But Have u tried low graphics mode? I am on windows at the moment so i can't check to see if there is the option to boot into low graphics mode although i am sure there is, I am currently not @ Home.

Yep I don't have my ubuntu computer with me either. I'm pretty sure there might be a low-graphics mode though, i'll check it out when I get home.

---

### Post by jastonas on 2010-09-24
Are these instructions updated? I want to try this with my projector to support 120hz...

---

### Post by wheels666 on 2010-10-18
beginners guide???

omg isn't there a way of just selecting the desired 16:9 resolution like on windows?

---

### Post by janpol on 2010-11-02
> **wheels666 said:**
> beginners guide???

omg isn't there a way of just selecting the desired 16:9 resolution like on windows?
Yes there is: System -> Preferences -> Monitors

---

### Post by TG12 on 2011-01-11
I have just posted a little guide for those of you having problems like I have and how to solve it

[http://ubuntuforums.org/showthread.php?t=1664919](http://ubuntuforums.org/showthread.php?t=1664919)

---

### Post by I_Am_Einstein on 2011-01-30
YES!!!!!!!!!!!!!!!!!

I HAVE SPENT LIKE 4 HOURS TRYING TO DO THIS!!!!

Here is what I did (after installing Guest Additions):

1) Terminal:
```
sudo gedit /etc/X11/xorg.conf
```

2) Found the line with:
```
SubSection "Display"
        Depth        32
```

3) Simply added this line below the Depth line:
```
        Modes      "1366x768_60.00"
```

4) Then rebooted.

Automatically is was fixed!!! It was so simple!!! =D =D =D

NOTES: 
a) My screen max resolution is 1366 x 768. 
Change that to your desired resolution

b) My screen max refresh rate is 60Hz. 
Change that to your refresh rate.

THANK YOU OP FOR GIVING THE IDEA!!!

---

### Post by COKEDUDE on 2011-03-07
Very nice guide.

---

### Post by geek.de.nz on 2011-03-10
Hi, After a long time without using Linux as my main OS, I decided to switch back to Ubuntu, because of its user friendliness...

Anyway, it would be great if someone could help me with this weird problem I am having:

When I login to X with my 2 monitor setup, and a Radeon HD 5450 video card, my second screen (the one with the "Applications, Places, System" panels) looks all funny except for the panels. When I then change the refresh rate of my monitor to 60Hz and back to 75Hz all is fine and gets displayed properly. I'm thinking here there must be a bug in the proprietary driver, so I thought, maybe an easy solution would be to write a little bash script, which changes the screen resolution to 60Hz for a few seconds and then back to 75Hz, only I haven't found a command to do that. It's really annoying that I have to change the refresh rate on every boot manually, so please help if you know the answer to this question. All I need is a one-liner to change the refresh rate. And btw, changing it to 60Hz permanently has the same problem.

I was pretty impressed how Ubuntu auto-detected everything. But this bug is really annoying, so please help.

Thanks for reading in any case.

---

### Post by matt_symes on 2011-03-10
Hi

> All I need is a one-liner to change the refresh rate.

No idea if this will work for you but investigate this ....

```
xrandr --rate 60
xrandr --rate 75
```

Please post back results.

Kind regards

---

### Post by geek.de.nz on 2011-03-11
Hi, Thank you so much for replying so quickly!

However, when I execute (with output):
```
$ xrandr --rate 75
$ xrandr 
Screen 0: minimum 320 x 200, current 2560 x 1024, maximum 2560 x 1024
DFP1 disconnected (normal left inverted right x axis y axis)
DFP2 disconnected (normal left inverted right x axis y axis)
CRT1 connected 1280x1024+1280+0 (normal left inverted right x axis y axis) 376mm x 301mm
   1280x1024      60.0 +   75.0* 
   1280x960       75.0     60.0  
   1280x768       75.0     60.0  
   1280x720       75.0     60.0  
   1024x768       75.0     70.1     60.0  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     67.0     59.9  
CRT2 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 376mm x 301mm
   1280x1024      60.0 +   75.0* 
   1280x960       75.0     60.0  
   1280x768       75.0     60.0  
   1280x720       75.0     60.0  
   1024x768       75.0     70.1     60.0  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     67.0     59.9  


```
it makes my left screen turn off. It's almost what I wanted, but I would need it to leave my left screen on. Any ideas?

Thanks for your help so far!

---

### Post by geek.de.nz on 2011-03-26
Just a follow-up:

If someone has the same problem, switching the monitors around physically seems to have fixed this issue at the root. Maybe something to consider testing for the next Ubuntu release...

EDIT: Sorry, this is wrong information, the monitor still does this. Maybe the monitor has an issue though, because it also makes a weird high-pitch noise.

---

### Post by matt_symes on 2011-03-28
Hi

> **geek.de.nz said:**
> Just a follow-up:

If someone has the same problem, switching the monitors around physically seems to have fixed this issue at the root. Maybe something to consider testing for the next Ubuntu release...

EDIT: Sorry, this is wrong information, the monitor still does this. Maybe the monitor has an issue though, because it also makes a weird high-pitch noise.

Sorry. I managed to lose your post. Maybe it is a monitor issue. Unfortunately i only have one monitor so i am not able to test.

Kind regards

---

### Post by geek.de.nz on 2011-03-28
> **matt_symes said:**
> Hi



Sorry. I managed to lose your post. Maybe it is a monitor issue. Unfortunately i only have one monitor so i am not able to test.

Kind regards

Thanks for your reply and sorry, I had just dumped my question in here...

Yes, it was regarding a monitor issue. I have a 2 monitor setup and every time I boot into Ubuntu, one of them has display issues. It basically draws everything onto the monitor and windows for example look like they stay open when closed. It's as if it does not "undraw" things, if you know what I mean.

So, to work around the problem, I thought I could use something like xrandr to change the refresh rate for a second and then change it back. However, when I use that, one of my monitors just switches off, so I have to manually go to preferences->monitors to change the refresh rate back and forth.

Thanks for any ideas.

---

### Post by matt_symes on 2011-03-28
Hi

> **geek.de.nz said:**
> Thanks for your reply and sorry, I had just dumped my question in here...

Yes, it was regarding a monitor issue. I have a 2 monitor setup and every time I boot into Ubuntu, one of them has display issues. It basically draws everything onto the monitor and windows for example look like they stay open when closed. It's as if it does not "undraw" things, if you know what I mean.

So, to work around the problem, I thought I could use something like xrandr to change the refresh rate for a second and then change it back. However, when I use that, one of my monitors just switches off, so I have to manually go to preferences->monitors to change the refresh rate back and forth.

Thanks for any ideas.

You could try to reset the refresh rate on each monitor.

```
xrandr --output CRT1 --rate 75
xrandr --output CRT2 --rate 75
```

Is it switching the monitor off ? The monitor can definitely handle that refresh rate?

What does this do ? Change CRT1 if it is incorrect.

```
xrandr --output CRT1 --auto
```

As i said, i only have one monitor so i can do no more than offer suggestions :(

Kind regards

---

### Post by geek.de.nz on 2011-03-30
> **matt_symes said:**
> Hi



You could try to reset the refresh rate on each monitor.

```
xrandr --output CRT1 --rate 75
xrandr --output CRT2 --rate 75
```Is it switching the monitor off ? The monitor can definitely handle that refresh rate?

What does this do ? Change CRT1 if it is incorrect.

```
xrandr --output CRT1 --auto
```As i said, i only have one monitor so i can do no more than offer suggestions :(

Kind regards

Thanks a lot! That worked! I just did the following:

```

echo "#!/bin/sh
xrandr --output CRT2 --auto" > ~/refresh_fix.sh

```Went to System->Preferences->Startup Applications, clicked Add, typed a name and browsed for ~/refresh_fix.sh and restarted happily ever after.

---

