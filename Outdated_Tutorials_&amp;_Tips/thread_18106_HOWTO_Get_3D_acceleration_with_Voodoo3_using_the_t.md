---
title: "HOWTO: Get 3D acceleration with Voodoo3 using the tdfx driver"
date: 2005-03-04
forum: Outdated Tutorials &amp; Tips
---

### Post by mr_ed on 2005-03-04
Edit /etc/X11/XF86Config-4 or /etc/X11/xorg.conf depending on which you have with your favourite text editor.

In section "Screen"
Change the DefaultDepth value to 16
And for the display:
Code:
```

        SubSection "Display"
                Depth           16
                Modes           "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection

```

The LARGEST value for Modes must be 1024x768, and the DefaultDepth must be 16, otherwise no 3D.  This is a hardware limitation on the card.

I tried setting the resolution higher, and then using the Screen Resolution program to lower to 1024x768 to no effect.

You should probably also install libglide3 from the Ubuntu main repository

---

### Post by budda on 2005-05-01
worked for me :-)
i googled and first installed xlibmesa3. it did not work at that moment but gave no error message e.g. in the /var/log/XFree86.log file.

to find out if opengl works:

> glxinfo | grep direct
you should see: direct rendering: Yes

and to see it in action: start glxgears and make the window big. you will see the difference :-)

and to do something useful (well, funny): install chromium!

---

### Post by kamstrup on 2005-09-14
I have been trying to get 3d acceleration on a really old box of mine. It has a Voodoo Banshee graphics card so I figured I'd give this thread a go...

I stripped out my 24 bit color depth, and made 16 default. I also set ```
Option "UseFBDev" "False"
``` in my Device section in xorg.conf (I can't remember where I picked that up... ). I also installed libglide3. But alas.
```
mikkel@smallpox:~$ glxinfo | grep direct
libGL warning: 3D driver returned no fbconfigs.
libGL error: InitDriver failed
libGL error: reverting to (slow) indirect rendering
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect
```

Any help would be greatly appreciated. My processor could use the spare clock cycles (266MHz)!

EDIT: glxgears also gives the libGL warnings/errors and shows < 1 fps...

---

### Post by kamstrup on 2005-09-14
Ok poking around on the net I find this useful document:
[http://dri.sourceforge.net/doc/DRIuserguide.html](http://dri.sourceforge.net/doc/DRIuserguide.html)

It states that Voodoo Banshee is indeed supported by DRI. Working my way through it I discover that I don't have bus mastering enabled (what ever that is...). When I follow the instructions in the doc to enable it, nothing happens. Ie. bus mastering does not get turned on.

Some more relevant output...
```
lsmikkel@smallpox:~$ lsmod | grep tdfx
tdfx                    3840  1 
drm                    58004  2 tdfx
```

```
mikkel@smallpox:~$ xdpyinfo | grep DRI
    XFree86-DRI
mikkel@smallpox:~$ xdpyinfo | grep GL
    GLX
    SGI-GLX
```

Device section of /etc/X11/xorg.conf
```
Section "Device"
        Identifier      "3Dfx Interactive, Inc. Voodoo Banshee"
        Driver          "tdfx"
        Option          "UseFBDev"      "False"
        BusID           "PCI:0:5:0"
EndSection
```

```
mikkel@smallpox:~$ lspci | grep Banshee
0000:00:05.0 VGA compatible controller: 3Dfx Interactive, Inc. Voodoo Banshee (rev 03)
```

---

### Post by StinkyPete on 2005-11-18
I install libglide3 I get 3D accelaration but a "Illegal instruction" when running glxgears. Any suggestions?

---

### Post by kamstrup on 2005-11-20
What more have you done? Please be a bit more specific. Do you have busmastering enabled as explained [here](http://dri.sourceforge.net/doc/DRIuserguide.html)?

---

### Post by maclark on 2006-01-28
I'm using a Voodoo3 3000 and am getting the same error "Illegal instruction" when I try to run any glx apps (e.g. glxinfo or glxgears).

I verified bus mastering was enabled, changed xorg.conf as suggested above, and installed libglide3.  I didn't see any errors in Xorg.0.log and it appears DRM loaded.  I also ran xdpyinfo and found the extensions GLX, SGI-GLX, and XFree86-DRI as suggested in the DRI users guide.  

Not sure what's wrong.

Please help!

Regards,
Mike

---

### Post by Mizery De Aria on 2006-04-26
I just recently installed Ubuntu on one of my computers.  I had Gentoo Linux installed on it prior, but because it is a slower computer, I spent most of the time compiling and it wasn't being used for anything else, really, hence the switch.  I did successfully manage to enable direct rendering, 1024x768 16-bit resolution when running Gentoo Linux, however I am having difficulty configuring everything with Ubuntu.  I did not determine if bus mastering was enabled when I had everything configured running Gentoo, but I am having difficulty configuring it using Ubuntu.  It seems bus mastering is disabled for my 3Dfx Voodoo 3 card and enabling per instructions does nothing.  My bios for the system doesn't seem to show any reference to enable/disable or even display its status.  Currently glxinfo shows direct rendering as enabled, but I get invalid instruction error when running glxinfo.  I'm stuck at this point.  Any suggestions/ideas?

---

### Post by cbrinegar on 2007-05-16
Okay, so I installed the glide/mesa stuff and made sure tdfx gets loaded by adding it to /etc/modules (after doing an sudo modprobe tdfx), and yes DRI is enabled and 3-D glxgears runs as 700+ fps.  The system does have to be configured so that you start X at 1024x768 to get hardware acceleration.

That really sucks, because I use my system at 1600x1200, and DRI/2-D hardware acceleration (even windowed 3-D) worked great under my ancient Mandrake installation with XFree 4.0 thru 4.2.  The hardware is capable of acceleration at these higher resolutions, and I don't appreciate someone "fixing" or "changing" it to do otherwise...

Maybe it is time to download the DRI source code and see if someone limited the features there or if it is in xorg...

---

### Post by cbrinegar on 2007-05-18
Okay, so I am now using my Voodoo3 3000 AGP video card (16 MB of memory) at 1600x1200 with DRI (hardware acceleration) as I wanted.  I found that some Ubuntu developers decided to try to protect us from not having enough memory to use fancy textures at this resolution and limited the DRI to lower resolutions.  I wanted the DRI at this resolution, because the 2-D acceleration makes my old system much more responsive (PII 400 MHz --- don't laugh).  

I'm sure a lot of people don't care, and the people who changed it probably don't want to revert the Ubuntu code.  But the power of open source has allowed me to choose what I want for my machine, so that is great.  I do think that there must be a more elegant solution to still allow DRI at high resolutions for this card, and I will submit a patch if I come up with something good.

--------------------

Here is a summary of how I enabled DRI at 1600x1200 under Ubuntu 7.04.

The basic problem comes from a change made to the tdfx_dri.c file:
[http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-driver-tdfx/](http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-driver-tdfx/)

(Note: look in /var/logs/Xorg.0.log to see the error report that disables
DRI.  This text is also in the Ubuntu code.)

The development tools were not all installed, so I used the Add Programs
option to add Glade and got most of the development tools (like autoconf).
I searched for the original code and found the Debian sources and a lot of
other things too.  It was a bit overwhelming, and the Debian version did
not compile yet.

I found the Sources.gz file for 7.04 and determined the name of the package
that had the tdfx driver in it.

Then I found a post on the Ubuntu forums that gave me information about
how to get source code:
[http://ubuntuforums.org/showthread.php?t=14756](http://ubuntuforums.org/showthread.php?t=14756)

sudo apt-get build-dep xserver-xorg-video-tdfx
sudo apt-get source xserver-xorg-video-tdfx

Then I had all the dependencies and code.  The diff file showed the change
that I did not want, so I went into the original Debian code and did the standard
./configure, make, sudo make install.

The files were installed into here though:
/usr/local/lib/xorg/modules/drivers/
  tdfx_drv.la
  tdfx_drv.so

They needed to be elsewhere, so I put them there:
  cd /usr/local/lib/xorg/modules/drivers/
  sudo cp *.* /usr/lib/xorg/modules/drivers/

X did not like that, so it restarted but with the new tdfx driver.

DRI is now enabled at the higher resolutions as I desired.

---

### Post by Newmark on 2007-07-01
Hi 
You posted:
>Then I had all the dependencies and code. The diff file showed the change
>that I did not want, so I went into the _original Debian code_ and did the standard
.>/configure, make, sudo make install.

What code?
What line?
Where did you get it?

 Sorry if I did not see it, but I'm a bit of a newbie to all this, so...

Thx in advance

---

### Post by cbrinegar on 2007-07-05
It is a bit confusing.  The downloaded ubuntu package has the change in a diff file.  Here is a copy of the patch so you can see the code I'm talking about.  I recompiled the code without this patch being applied.


See: 01_tdfx_disable_dri_on_16mb_with_highres.diff

----------------------------------------------
Index: xserver-xorg-video-tdfx/src/tdfx_dri.c
===================================================================
--- xserver-xorg-video-tdfx.orig/src/tdfx_dri.c	2006-04-04 12:06:58.000000000 +0000
+++ xserver-xorg-video-tdfx/src/tdfx_dri.c	2006-08-16 00:23:47.000000000 +0000
@@ -297,6 +297,22 @@
     return FALSE;
   }
 
+  /* Disable DRI if using a 16Mb card with virtual resolution higher than
+   * 1024x768 because DRI does not have enough memory available for textures
+   * at higher resolutions, and will not operate correctly.
+   */
+  xf86DrvMsg(pScreen->myNum, X_INFO, "[dri] VideoRAM = %d, VirtualXres = %d, VirtualYres= %d,\n",
+             pScrn->videoRam, pScrn->virtualX, pScrn->virtualY);
+
+  if ( (pTDFX->ChipType == PCI_CHIP_VOODOO3) || (pTDFX->ChipType == PCI_CHIP_BANSHEE) ) {
+    if (pScrn->videoRam <= 16384 && ((pScrn->virtualX * pScrn->virtualY) > (1024 * 768 )) ) {
+      xf86DrvMsg(pScreen->myNum, X_WARNING,
+        "[dri] To use DRI, with a 16Mb Voodoo 3 or Banshee card, you must\n"
+        "\tinvoke the server using a maximum resolution of 1024x768 or lower.\n");
+      return FALSE;
+    }
+  }
+  
     /* Check that the GLX, DRI, and DRM modules have been loaded by testing
        for canonical symbols in each module. */
     if (!xf86LoaderCheckSymbol("GlxSetVisualConfigs")) return FALSE;

---

### Post by introspectif on 2007-08-31
Thank you so much for the great guide! I got this working on my PC, thanks to you.

I'd just like to confirm: you applied no patch at all, or you patched but omitted that specific segment of the .diff file?

---

### Post by gonssal on 2007-11-10
Hi.

I recently installed Ubuntu in an old PC with a Voodoo3. Everything is OK, the xorg logfile shows the line "(II) TDFX(0): Direct rendering enabled", but when I run glxinfo it says it's not enabled. I've set the DefaultDepth to 16 and max resolution to 1024x768.

Googling arround, i found that your card needs to have bus mastering enabled in orther for the DRI driver to work, but doing a "setpci -s 01:05.0 4.w", it returns 0003, which means it's not enabled. I tried doing a "setpci -s 01:05.0 4.w=0007" to force the bus mastering on, but it returns "pcilib: Cannot open /sys/bus/pci/devices/0000:01:05.0/config" and the 0003 value is not changed.

I really don't know if the bus mastering thingy is really the problem, as far as it is an AGP card. Btw, I'd like to know if there's any other option to set the bus mastering on through linux (my BIOS does not show the option) or if you know what's the problem here.

Thank you.

---

### Post by SystemeD on 2007-11-13
Hi all,
I installed mesa and liglide3 and now I've exactly the same problem as gonssal on the same hardware.

Any help? Thank you!

---

### Post by ivzm on 2008-01-12
i have the same problem as well but i run a nvidia 6200
my xorg.conf consists of:

Section "Files"
	Fontpath	"/usr/share/fonts/X11/misc"
	Fontpath	"/usr/share/fonts/X11/cyrillic"
	Fontpath	"/usr/share/fonts/X11/100dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/75dpi/:unscaled"
	Fontpath	"/usr/share/fonts/X11/Type1"
	Fontpath	"/usr/share/fonts/X11/100dpi"
	Fontpath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	Fontpath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load		"i2c"
	Load		"bitmap"
	Load		"ddc"
	Load		"extmod"
	Load		"freetype"
	Load		"glx"
	Load		"int10"
	Load		"vbe"
EndSection

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
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
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
	Identifier	"nVidia Corporation NV44A [GeForce 6200]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Acer AC713"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV44A [GeForce 6200]"
	Monitor		"Acer AC713"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	4
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	8
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	15
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	16
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
	SubSection "Display"
		Depth	24
		Modes		"1024x768"	"800x600"	"640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"cursor"	"SendCoreEvents"
	Inputdevice	"eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by lupin492 on 2008-01-26
[QUOTE=cbrinegar;2681105]Okay, so I am now using my Voodoo3 3000 AGP video card (16 MB of memory) at 1600x1200 with DRI (hardware acceleration) as I wanted.  I found that some Ubuntu developers decided to try to protect us from not having enough memory to use fancy textures at this resolution and limited the DRI to lower resolutions.  I wanted the DRI at this resolution, because the 2-D acceleration makes my old system much more responsive (PII 400 MHz --- don't laugh).  

I'd like to THANK to cbrinegar, first of all.
This procedure WORKS.
I also use an AMD @ 750MHZ with a Voodoo 3 3000 video card with 16Megs of video memory (it seems we are still many ! :) )

**To start with, be aware that what cbrinegar describes here is not 'magic'.  We are 'squeezing' the video card's resources so, due to the lack of enough video memory, you will notice things like flickering when rendering 3D at fullscreen. ** For example, if you run the OpenGL screensaver that come with Ubuntu, in fullscreen mode, you will notice this flickering in most of them, and a heavy one in the most complex of them.
So, what is done here is just to be able to use 2D acceleration whenever it is useful, and to have ocasional 3D acceleration, preferably not at fullscreen if exceeding 1024x768 pix. 

I just will try to explain further a couple of the steps for nOObs like me to have it easier.
-Begin cbrinegar's procedure.  At the point where he/she says to **'add Glade**', I did this: used Synaptic to look for 'glade-3'.  Right clicking on it, I installed just the packages listed under 'recommended for installation', which in my case implied only the installation of 'autoconf' and 'automake 1.4'.  I didn't install 'glade-3' itself.
-Jump to the point where he/she types:** 'sudo apt-get...'**.  Once I completed those two operations, I found a directory called 'xserver-xorg-video-tdfx-1.3.0' under my home directory.  Inside it there is a subdir called 'debian'.  Again inside it, there is a subdir called 'patches', where there is a file called '01_tdfx_disable_dri_on_16mb_with_highres.diff'.   Open this file for edition.  I started gedit from a console: 'sudo gedit' to have root permissions, cause this directories and files where placed with root ownership.
-Look for a sentence near the middle of the file where it says: **'1024 * 768'**.   I replaced it with: '1600 * 1200'.   If you want it, you can add an explanatory comment of what you did here for if you happen to return to read this file in the future.
- Then, I typed** './configure', 'make' and 'make install'** (while having 'xserver-xorg-video-tdfx-1.3.0' as 'CWD').  The only note is that I had to do all of them with 'sudo' cause all the files had root ownership, at least in my case.
-Follow the rest of cbrinegar's procedure up to the end.

-NOTE: I am using video with 1440x900 pix at 16bpp (didn't tried at 24bpp, but I bet it's not worthy.
Furthermore, it is assumed you already have  'glide3' installed.  If not, you didn't have 3D acceleration anyway, so follow other tutorials in this forum to get the card working with OpenGL first.

Hope this to be useful for you!   Thanks community ! :popcorn:

---

### Post by OCEAN11 on 2008-05-15
Hello, I'm totally new to Ubuntu, just finished installing Ubuntu 8.04 LTS on a older computer and wanted to force myself into Ubuntu and stray away from the evil empire, lol, this being my first post, I have a Voodoo 5 5500 AGP video card installed, and the install went smooth as pie, but I'm stuck at 800 x 600 resolution, maybe that's an ok resolution, but could go higher, but I'm also stuck as to how to update to  this tdfx driver and I'm also trying to install Unreal Tournament ( The origional retail CD ) and I'm way fresh to Ubuntu, need a little help if someone would not mind helping a newbie like myself.
Thanks for any help anyone would to give.
Glad to be here.

Chad

---

### Post by G20-Budo on 2008-07-04
I just installed ubuntu 8.04 on an old IBM intellistation ZPRO. (866 Intel Pentium III Xeon processor) with 500mb's of ram, and a 3d Wildcat 4110 video card. The video card would only work in 640x480.. After searching all over the internet, and only finding posts from people saying they could not get any kind of drivers for the wildcat 4110, I replaced the wildcat card with an old 3dfx voodoo 3 3000.  The system will now work in 800x600, but that's the best I can get. 

I tried doing some of the fixes mentioned earlier in this thread, but they were on earlier versions of ubuntu.  

I'm setting this system up for my 13 year old son.. for web browsing, listening to music and watching videos.. as well as IM and for him to do his homework.  Ubuntu is running well on it..with all the current patches.. 

I'd just like to see if I can take better advantage of the video card.

Thanks in advance for any help anyone can provide.

---

