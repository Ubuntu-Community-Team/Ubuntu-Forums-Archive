---
title: "HOWTO: TV-out for legacy ATI cards using GATOS"
date: 2006-07-14
forum: Outdated Tutorials &amp; Tips
---

### Post by stungeye on 2006-07-14
[SIZE="3"]**Purpose:**[/SIZE]

Enable simple TV-out functionality for legacy ATI Radeon cards with Rage Theater 100 (RT 100) or Embedded Rage Theater (ERT).


[SIZE="3"]**Scope:**[/SIZE]

The driver used has successfully enabled TV-out for the following cards ([other legacy cards](" http://gatos.sourceforge.net/supported_cards.php ") may also work):

* Radeon 7200 / European model
* Radeon 9000
* Radeon 9100
* Radeon 9200SE
* Radeon 7000
* Radeon QD
* Radeon Mobility M7

I used a PowerColor Radeon 7000 based card with Ubuntu 6.06 Dapper Drake to produce this tutorial.


[SIZE="3"]**Means:**[/SIZE]

We will compile and install a [GATOS](" http://gatos.sourceforge.net/") patched ATI driver for [X.org](" http://xorg.freedesktop.org/wiki/ "), the X Window System used by Ubuntu.


[SIZE="3"]**Skill Level:**[/SIZE]

To complete this tutorial you should be comfortable using the command line.


[SIZE="3"]**Conventions Used:**[/SIZE]

Commands meant to be run from Terminal or Konsole will be shown inside of boxes labeled "Code". When the command is preceded by "sudo" you may be required to enter your administrator password.

_This HOWTO also contains some sections marked "STUB" where I request help in fleshing out the solution._


[SIZE="3"]**Prep Work:**[/SIZE]

First, install some basic compilation tools, as well as various required X libraries.

```

sudo apt-get install build-essential
sudo apt-get install xserver-xorg-dev
sudo apt-get install x11proto-xinerama-dev
sudo apt-get install x11proto-xf86misc-dev
sudo apt-get install x11proto-gl-dev
sudo apt-get install mesa-common-dev

```


[SIZE="3"]**Fetch Driver and Patch:**[/SIZE]

You may want to create a directory in which to store the temporary files we'll be using.

```

cd ~
mkdir atidrivers
cd atidrivers

```

You can now download driver and the patch.

```

wget http://xorg.freedesktop.org/releases/individual/driver/xf86-video-ati-6.5.8.0.tar.bz2
wget http://megahurts.dk/rune/stuff/xorg7-6.5.8.0-tv_output.patch.gz

```

The latest patches can be found [here](" http://megahurts.dk/rune/tv_output.html ").


[SIZE="3"]**Decompress the Driver Source and Apply the Patch:**[/SIZE]

```

tar xjvf xf86-video-ati-6.5.8.0.tar.bz2
gunzip -c xorg7-6.5.8.0-tv_output.patch.gz | patch -p1 -d xf86-video-ati-6.5.8.0

```


[SIZE="3"]**Configure and Compile the Driver:**[/SIZE]

```

cd xf86-video-ati-6.5.8.0
export XORG_PREFIX="/usr"
export XORGCONFIG="--prefix=$XORGPREFIX --sysconfdir=/etc --localstatedir=/var"
./configure $XORG_CONFIG --with-xorg-module-dir=/usr/lib/xorg/modules
make

```

[SIZE="3"]**Back-up Current X.org Driver**[/SIZE]

*STUB: The user should probably backup their current X.org driver. How is this done?*


[SIZE="3"]**Install the new Driver:**[/SIZE]

```

sudo make install

```

If you reboot, X.Org will now use the new video drivers. However, TV-out will only be enabled when your screen resolution is set to 800x600.

For some reason, when I rebooted I was unable to change my resolution using the Screen Resolution tool found under the System->Preferences menu. Also, my ATI card defaults to PAL output, but my TV requires NTSC. Further tweaking was therefore required.

[SIZE="3"]
**Tweaking the X.Org Configurations**[/SIZE]

The X.Org configurations are stored in /etc/X11/xorg.conf which can be edited with your favourite text-editor. We'll backup the file, and edit with gedit.

```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old
sudo gedit /etc/X11/xorg.conf

```

The relevant sections of my xorg.conf:

```

Section "Device"
    Identifier  	"ATI Technologies, Inc. Radeon RV100 QY [Radeon 7000/VE]"
    Driver      	"ati"
    BusID		"PCI:1:0:0"
    **Option		"TVOutput" "NTSC"**
EndSection

```

TVOutput can be set to one of the follow: NTSC, NTSC-J, PAL, PAL-CN, PAL-M, PAL-N, PAL-60

```

Section "Monitor"
    Identifier		"SyncMaster"
    [B]HorizSync		30 - 50
    VertRefresh		60 - 60[/B]
    Option		"DPMS"
EndSection

```

I set the Horizontal and Vertical refresh rates to match that of a CRT TV. This probably wasn't necessary, but since I don't have an actual monitor attached to this computer it doesn't hurt.

```

Section "Screen"
    Identifier    "Default Screen"
    Device        "ATI Technologies, Inc. Radeon RV100 QY [Radeon 7000/VE]"
    Monitor        "SyncMaster"
[B]    DefaultDepth    24
    SubSection "Display"
        Depth        24
        Modes        "800x600"
    EndSubSection[/B]
EndSection

```

Again, since I don't have a monitor attached to this computer I'm restricting the output to 800x600. That way, TV-Out will always be enabled. Note the 'Depth' must match the 'DefaultDepth'.


[SIZE="3"]**End Notes**[/SIZE]

After a reboot (or an Xorg restart) your TV-Out should be enabled.

On my first try the TV output was only in black/white. A new S-Video to Composition cable solved this problem.

If you have both a monitor and TV-Out you may run into overlay issues. For example, when playing a DVD, the video may only show on your monitor, with a black box showing on the TV-Out.

This is solved by adding the following to the "Device" section of xorg.conf, setting the TV-Out as the primary monitor:

```

Option "MonitorLayout"        "STV, CRT"

```

On the patch site, the following "MonitorLayout" option is suggested, but this didn't work for me:

```

Option "MonitorLayout"        "AUTO, NONE"

```

**Suggestions for improvements to this HOWTO are welcome.**

---

### Post by m085 on 2006-07-20
I followed all of these instructions. Thank you so very much for posting this up! Unfortuately I'm too noob to get it working well. When I start up my computer the loading screen and the shut down screen are both displayed on my television, but it's the wrong refresh rate so it's very unclear. When I'm actually using Ubuntu the desktop isn't cloned and I don't know how to switch it over. Any suggestions?

---

### Post by Turtle.net on 2006-07-22
When I compile the driver with the instruction make I have an error ... and I do not understand why. Any idea ?
```
~/atidrivers/xf86-video-ati-6.5.8.0$ make
make  all-recursive
make[1]: entrant dans le répertoire « /home/cassini/atidrivers/xf86-video-ati-6.5.8.0 »
Making all in src
make[2]: entrant dans le répertoire « /home/cassini/atidrivers/xf86-video-ati-6.5.8.0/src »
if /bin/sh ../libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I..    -DXFree86Server -DIN_MODULE -DXFree86Module -DXFree86LOADER -I/usr/include/xorg   -I/usr/include/drm -I/usr/include/X11/dri   -g -O2 -MT ati.lo -MD -MP -MF ".deps/ati.Tpo" \
          -c -o ati.lo `test -f 'ati.c' || echo './'`ati.c; \
        then mv -f ".deps/ati.Tpo" ".deps/ati.Plo"; \
        else rm -f ".deps/ati.Tpo"; exit 1; \
        fi
mkdir .libs
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -DXFree86Server -DIN_MODULE -DXFree86Module -DXFree86LOADER -I/usr/include/xorg -I/usr/include/drm -I/usr/include/X11/dri -g -O2 -MT ati.lo -MD -MP -MF .deps/ati.Tpo -c ati.c  -fPIC -DPIC -o .libs/ati.o
if /bin/sh ../libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I..    -DXFree86Server -DIN_MODULE -DXFree86Module -DXFree86LOADER -I/usr/include/xorg   -I/usr/include/drm -I/usr/include/X11/dri   -g -O2 -MT atiadapter.lo -MD -MP -MF ".deps/atiadapter.Tpo" \
          -c -o atiadapter.lo `test -f 'atiadapter.c' || echo './'`atiadapter.c; \
        then mv -f ".deps/atiadapter.Tpo" ".deps/atiadapter.Plo"; \
        else rm -f ".deps/atiadapter.Tpo"; exit 1; \
        fi
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -DXFree86Server -DIN_MODULE -DXFree86Module -DXFree86LOADER -I/usr/include/xorg -I/usr/include/drm -I/usr/include/X11/dri -g -O2 -MT atiadapter.lo -MD -MP -MF .deps/atiadapter.Tpo -c atiadapter.c  -fPIC -DPIC -o .libs/atiadapter.o
if /bin/sh ../libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I..    -DXFree86Server -DIN_MODULE -DXFree86Module -DXFree86LOADER -I/usr/include/xorg   -I/usr/include/drm -I/usr/include/X11/dri   -g -O2 -MT atibus.lo -MD -MP -MF ".deps/atibus.Tpo" \
          -c -o atibus.lo `test -f 'atibus.c' || echo './'`atibus.c; \
        then mv -f ".deps/atibus.Tpo" ".deps/atibus.Plo"; \
        else rm -f ".deps/atibus.Tpo"; exit 1; \
        fi
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -DXFree86Server -DIN_MODULE -DXFree86Module -DXFree86LOADER -I/usr/include/xorg -I/usr/include/drm -I/usr/include/X11/dri -g -O2 -MT atibus.lo -MD -MP -MF .deps/atibus.Tpo -c atibus.c  -fPIC -DPIC -o .libs/atibus.o
In file included from atidripriv.h:40,
                 from atistruct.h:41,
                 from atibus.c:33:
/usr/include/GL/glxint.h:28:19: error: GL/gl.h: No such file or directory
In file included from atidripriv.h:40,
                 from atistruct.h:41,
                 from atibus.c:33:
/usr/include/GL/glxint.h:95: error: syntax error before 'GLboolean'
/usr/include/GL/glxint.h:97: error: syntax error before 'doubleBufferMode'
/usr/include/GL/glxint.h:98: error: syntax error before 'stereoMode'
/usr/include/GL/glxint.h:99: error: syntax error before 'haveAccumBuffer'
/usr/include/GL/glxint.h:100: error: syntax error before 'haveDepthBuffer'
/usr/include/GL/glxint.h:101: error: syntax error before 'haveStencilBuffer'
/usr/include/GL/glxint.h:104: error: syntax error before 'accumRedBits'
/usr/include/GL/glxint.h:105: error: syntax error before 'depthBits'
/usr/include/GL/glxint.h:106: error: syntax error before 'stencilBits'
/usr/include/GL/glxint.h:107: error: syntax error before 'indexBits'
/usr/include/GL/glxint.h:108: error: syntax error before 'redBits'
/usr/include/GL/glxint.h:109: error: syntax error before 'redMask'
/usr/include/GL/glxint.h:111: error: syntax error before 'multiSampleSize'
/usr/include/GL/glxint.h:113: error: syntax error before 'nMultiSampleBuffers'
/usr/include/GL/glxint.h:114: error: syntax error before 'maxAuxBuffers'
/usr/include/GL/glxint.h:117: error: syntax error before 'level'
/usr/include/GL/glxint.h:120: error: syntax error before 'extendedRange'
/usr/include/GL/glxint.h:121: error: syntax error before 'minRed'
/usr/include/GL/glxint.h:122: error: syntax error before 'minGreen'
/usr/include/GL/glxint.h:123: error: syntax error before 'minBlue'
/usr/include/GL/glxint.h:124: error: syntax error before 'minAlpha'
/usr/include/GL/glxint.h:125: error: syntax error before '}' token
make[2]: *** [atibus.lo] Erreur 1
make[2]: quittant le répertoire « /home/cassini/atidrivers/xf86-video-ati-6.5.8.0/src »
make[1]: *** [all-recursive] Erreur 1
make[1]: quittant le répertoire « /home/cassini/atidrivers/xf86-video-ati-6.5.8.0 »
make: *** [all] Erreur 2

```

---

### Post by lokimon on 2006-07-28
wrong forum

---

### Post by lokimon on 2006-07-28
wrong forum

---

### Post by lokimon on 2006-07-28
wrong forum

---

### Post by damagedspline on 2006-07-30
didn't work for me on radeon IGP340M (~radeon 7000):
followed the how-to exactly.
the lcd is working at 640x480 and tv out is not working.

reverted back to original foss ati driver

---

### Post by fragmede on 2006-08-01
Hi,

To backup the xorg driver, I believe something like 

  [PHP]sudo cp /usr/lib/xorg/modules/drivers/ati_drv.so /usr/lib/xorg/modules/drivers/ati_drv.so.bku[/PHP]

could be used? Have I got the right file?

-s

---

### Post by oBuntu on 2006-08-02
I have a Radeon Mobility M7 and when I do it my monitor gets stuck at 640x480 and TV out doesn't work. Any suggestions?

---

### Post by stungeye on 2006-08-08
> **Turtle.net said:**
> When I compile the driver with the instruction make I have an error ... and I do not understand why. Any idea ?
```

/usr/include/GL/glxint.h:28:19: error: GL/gl.h: No such file or directory

```

Looks like you are missing the gl.h header file. Did you apt-get all the libraries in the "prep work" section?

More specifically, to install gl.h:

```
sudo apt-get install mesa-common-dev
```

---

### Post by stungeye on 2006-08-08
> **m085 said:**
> I followed all of these instructions. Thank you so very much for posting this up! Unfortuately I'm too noob to get it working well. When I start up my computer the loading screen and the shut down screen are both displayed on my television, but it's the wrong refresh rate so it's very unclear. When I'm actually using Ubuntu the desktop isn't cloned and I don't know how to switch it over. Any suggestions?

During the loading and shutdown screens your video card is probably displaying in the wrong mode. For example: PAL instead of NTSC.

This is okay, as we set the correct mode in the xorg.conf file, and this will "kick-in" once you log in.

The real problem here is that your Xorg isn't displaying at 800x600, which is required for TV-out to be enabled. Looks like **damagedspline** and **oBuntu** are having this same problem.

Please note that in the my tutorial I set the horizontal sync, vertical refresh, and resolution specifically for a CRT TV.

If you have a monitor attached, you would be better off setting the HorizSync & VertRefresh to those listed in your monitor manual. With those values set correctly you should be able to switch to 800x600 using the Screen Resolution tool found under the System->Preferences menu.

If that doesn't help, you might find this HowTo useful: [How to change resolution/refresh rate in Xorg]("http://www.ubuntuforums.org/showthread.php?t=83973")

---

### Post by mattbatt on 2006-08-17
Thank you for the gudie It worked perfectly and I am using a an ATI Radeon 7200 US version 

Thanks

---

### Post by fvboegeld on 2006-08-18
I got an ATI RADEON 7500 (IBM TP30), followed the instructions in this thread and finally managed to get some activity on the TV but its all messed up, lines.. I can see something is going on but the whole image/screen is distorted.

Any ideas?

Thanks

Btw i'm a total noob in ubuntu/linux

Frederik

---

### Post by mattbatt on 2006-08-20
sounds like the refresh rate is wrong make sure it's 60hz.

---

### Post by GoDamN on 2006-08-22
Well this worked fine until today...

I completed this within the last fortnight and i had my 7500 displaying tv-out nicely.

Today i installed updates to X (very dumb) and tv-out is now kaput... even using the vesa driver :( 

I tried recompiling the patched gatos driver but now get errors... bad errors...

[INDENT]root@mediamobile:~/atidrivers/xf86-video-ati-6.5.8.0# make
make  all-recursive
make[1]: Entering directory `/root/atidrivers/xf86-video-ati-6.5.8.0'
Making all in src
make[2]: Entering directory `/root/atidrivers/xf86-video-ati-6.5.8.0/src'
if /bin/sh ../libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I..    -DXFree86Server -DIN_MODULE -DXFree86Module -DXFree86LOADER -I/usr/include/xorg   -I/usr/include/drm -I/usr/include/X11/dri   -g -O2 -MT radeon_accel.lo -MD -MP -MF ".deps/radeon_accel.Tpo" \
          -c -o radeon_accel.lo `test -f 'radeon_accel.c' || echo './'`radeon_accel.c; \
        then mv -f ".deps/radeon_accel.Tpo" ".deps/radeon_accel.Plo"; \
        else rm -f ".deps/radeon_accel.Tpo"; exit 1; \
        fi
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -DXFree86Server -DIN_MODULE -DXFree86Module -DXFree86LOADER -I/usr/include/xorg -I/usr/include/drm -I/usr/include/X11/dri -g -O2 -MT radeon_accel.lo -MD -MP -MF .deps/radeon_accel.Tpo -c radeon_accel.c  -fPIC -DPIC -o .libs/radeon_accel.o
In file included from radeon_accel.c:78:
radeon.h:738:25: error: theater_out.h: No such file or directory
In file included from radeon_accel.c:78:
radeon.h:750: error: syntax error before 'TVStd'
radeon.h:751: error: syntax error before 'RADEONTheaterOutGetStandard'
radeon.h:751: warning: data definition has no type or storage class
radeon.h:753: error: syntax error before 'TheaterOutAttr'
radeon.h:754: error: syntax error before 'TheaterOutAttr'
radeon.h:755: error: syntax error before 'TheaterOutAttr'
make[2]: *** [radeon_accel.lo] Error 1
make[2]: Leaving directory `/root/atidrivers/xf86-video-ati-6.5.8.0/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/root/atidrivers/xf86-video-ati-6.5.8.0'
make: *** [all] Error 2[/INDENT]

I am still investigating but was wondering if anyone else has found this (or has ideas... I like packages, not compliers...:( )

---

### Post by GoDamN on 2006-08-22
Well... pays to be patient...

re-downloaded everything, retried from scratch and all is well again...

---

### Post by _profox on 2006-09-02
> cd xf86-video-ati-6.5.8.0
export XORG_PREFIX="/usr"
export XORGCONFIG="--prefix=$XORGPREFIX --sysconfdir=/etc --localstatedir=/var"
./configure $XORG_CONFIG --with-xorg-module-dir=/usr/lib/xorg/modules
make
XORG_PREFIX vs XORGPREFIX
XORGCONFIG vs XORG_CONFIG

This looks wrong?

---

### Post by ksyhne on 2006-10-03
Thank you for your guide!!! It worked with my Ati Radeon 7500 (powercolor).

Thanks!

---

### Post by Snifffurt on 2006-10-07
Hello

I'm stuck at the configure Process. I'm using Edgy beta tho.

The error output in the shell is:
```
checking for XORG... configure: error: Package requirements (xorg-server xproto fontsproto  xineramaproto randrproto renderproto videoproto xf86miscproto xextproto) were not met:

No package 'xproto' found
No package 'fontsproto' found
No package 'randrproto' found
No package 'renderproto' found
No package 'videoproto' found
No package 'xextproto' found

```

What might this be?
I've installed all the packages that ought to be installed.
Or doesn't Gatos work with Xorg 7.1?

Thx for any help

Regards

Casper

---

### Post by marx2k on 2006-10-30
> **Snifffurt said:**
> Hello

I'm stuck at the configure Process. I'm using Edgy beta tho.

The error output in the shell is:
```
checking for XORG... configure: error: Package requirements (xorg-server xproto fontsproto  xineramaproto randrproto renderproto videoproto xf86miscproto xextproto) were not met:

No package 'xproto' found
No package 'fontsproto' found
No package 'randrproto' found
No package 'renderproto' found
No package 'videoproto' found
No package 'xextproto' found

```

What might this be?
I've installed all the packages that ought to be installed.
Or doesn't Gatos work with Xorg 7.1?

Thx for any help

Regards

Casper

Same problem here...

checking for XORG... configure: error: Package requirements (xorg-server xproto fontsproto  xineramaproto randrproto renderproto videoproto xf86miscproto xextproto) were not met:

No package 'fontsproto' found
No package 'videoproto' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.


...etc....etc

---

### Post by Pawel on 2006-10-30
Hi!

What about patches for xorg 7.1 //edgy// ?
Is there available ?

Best ragards
Pawel

---

### Post by PooBaa on 2006-11-02
So I got this working on edgy. Below are the changes to the original steps:

I had to download more packages:

sudo apt-get install x11proto-xf86dri-dev libdrm-dev x11proto-xext-dev x11proto-xextproto-dev x11proto-video-dev render-dev x11proto-randr-dev x11proto-fonts-dev x11proto-core-dev

I had to download different version of the driver + patch:
wget [http://megahurts.dk/rune/stuff/xorg7.1-6.6.3-tv_output.patch.gz](http://megahurts.dk/rune/stuff/xorg7.1-6.6.3-tv_output.patch.gz)
wget [http://xorg.freedesktop.org/releases/individual/driver/xf86-video-ati-6.6.3.tar.bz2](http://xorg.freedesktop.org/releases/individual/driver/xf86-video-ati-6.6.3.tar.bz2)

Fix the _ spacing: 
export XORG_PREFIX="/usr"

export XORG_CONFIG="--prefix=$XORG_PREFIX --sysconfdir=/etc --localstatedir=/var"

./configure $XORG_CONFIG --with-xorg-module-dir=$XORG_PREFIX/lib/xorg/modules

make


So the original post is very close. Just needs updating. 

I'm super happy that I have video out now, does anyone know how to make it fill the whole screen, mine seems to the a little to the top, and a little to the right. In the windows world I used the overscan option with the ATI card.

---

### Post by cconcolato on 2006-11-09
Hi, 

I have bought a Sapphire ATI Radeon 9250 PCI 128 MB DDR. I've put in an old PC which had already a video card on the motherboard. I've installed Ubuntu Edgy. The new video is detected and when I connect it to my LCD it works fine. I've followed this forum and recompiled the source code and the patch as indicated in the previous posts. The compilation and installation went well. But I don't get any signal on my TV. atitvout does not detect the TV monitor. I guess it's a problem of configuration. Could someone post a complete xorg.conf, because each time I modify it myself I get errors ... Here is the current one I have:
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
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/75dpi"
        FontPath        "/usr/share/fonts/X11/misc"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "bitmap"
        Load    "dbe"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "record"
        Load    "type1"
        Load    "v4l"
        Load    "vbe"
        Load    "i2c"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "fr"
        Option          "XkbVariant"    "latin9"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "Device"
        Identifier      "Carte video generique"
        Driver          "radeon"
        BusID           "PCI:0:20:0"
        Option          "UseFBDev"              "true"
        Option          "TVOutput"              "PAL"
EndSection

Section "Monitor"
        Identifier      "NEC LCD1760N"
        Option          "DPMS"
        HorizSync       30-70
        VertRefresh     50-160
EndSection

Section "Monitor"
        Identifier      "TV"
        HorizSync       30 - 50
        VertRefresh     60 - 60
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "ScreenTV"
        Device          "Carte video generique"
        Monitor         "TV"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "800x600"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Option          "TVOut"         "on"
        Screen          "ScreenTV" 0 0
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

Section "DRI"
        Mode    0666
EndSection

```

Thanks,

Cyril

---

### Post by La muerte del DIos on 2006-11-09
Hi, i'm stock at the "make" part. ](*,) Heres the output:

```
last@maquina:~/tvati/xf86-video-ati-6.5.8.0$ make
make: *** No targets specified and no makefile found.  Stop.
```
 
Also I've tried PooBaa's method but it gives me an 404 not found error with the files.

Can anyone help me please? I'm using Ubuntu Edgy with a Ati Radeon 9250.

---

### Post by Fittersman on 2006-11-14
im stuck at the make part too

```
cleippi@cleippi-desktop:~/atidrivers/xf86-video-ati-6.5.8.0$ make
make: *** No targets specified and no makefile found.  Stop.

```

i followed your directions exactally and thats where i end up at

---

### Post by La muerte del DIos on 2006-11-17
I think i can't get the MAKE part work because i need some extra files. Here my ./configure output:
```

last@maquina:~/tvati/xf86-video-ati-6.5.8.0$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking for a sed that does not truncate output... /bin/sed
checking for egrep... grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for f77... no
checking for xlf... no
checking for frt... no
checking for pgf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for epcf90... no
checking for f95... no
checking for fort... no
checking for xlf95... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for gfortran... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... cat: /etc/ld.so.conf.d/*.conf: No such file or directory
GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... cat: /etc/ld.so.conf.d/*.conf: No such file or directory
GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking if XINERAMA is defined... yes
checking if RANDR is defined... yes
checking if RENDER is defined... yes
checking if XV is defined... yes
checking if XF86MISC is defined... yes
checking if DPMSExtension is defined... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for XORG... configure: error: Package requirements (xorg-server xproto fontsproto  xineramaproto randrproto renderproto videoproto xf86miscproto xextproto) were not met:

No package 'fontsproto' found
No package 'videoproto' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables XORG_CFLAGS
and XORG_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```

So can somebody tell me where can i get the fontsproto and videoproto files?

---

### Post by bill_mcgonigle on 2006-11-20
> checking for XORG... configure: error: Package requirements (xorg-server xproto fontsproto  xineramaproto randrproto renderproto videoproto xf86miscproto xextproto) were not met:

I got the same error message trying to compile on fc6 (same hardware/software/problem) - I needed to install the xorg sdk package and then the compile and install went fine.  Ubuntu must have a similar package (my ubuntu machine is offline while I tackle this project...).

No luck with the TV-Out yet (9100 IGP hardware, Pundit-R, future MythTV box).

---

### Post by josesanders on 2006-11-20
I had the same error for missing packages, and fixed it with (as above):

> sudo apt-get install x11proto-xf86dri-dev libdrm-dev x11proto-xext-dev x11proto-video-dev render-dev x11proto-randr-dev x11proto-fonts-dev x11proto-core-dev

This command is the same as above, but it couldn't find the following:
> x11proto-xextproto-dev

The make begins without errors until:

> radeon_exa.c: In function 'RADEONGetOffsetPitch':
radeon_exa.c:160: error: 'ExaDriverRec' has no member named 'card'
radeon_exa.c:163: error: 'ExaDriverRec' has no member named 'card'
In file included from radeon_exa.c:334:
radeon_exa_funcs.c: In function 'RADEONDrawInitMMIO':
radeon_exa_funcs.c:350: error: 'ExaDriverRec' has no member named 'accel'
radeon_exa_funcs.c:350: error: 'ExaAccelInfoRec' undeclared (first use in this function)
radeon_exa_funcs.c:350: error: (Each undeclared identifier is reported only once
radeon_exa_funcs.c:350: error: for each function it appears in.)
radeon_exa_funcs.c:352: error: 'ExaDriverRec' has no member named 'accel'
radeon_exa_funcs.c:353: error: 'ExaDriverRec' has no member named 'accel'
radeon_exa_funcs.c:354: error: 'ExaDriverRec' has no member named 'accel'
radeon_exa_funcs.c:356: error: 'ExaDriverRec' has no member named 'accel'
radeon_exa_funcs.c:357: error: 'ExaDriverRec' has no member named 'accel'
radeon_exa_funcs.c:358: error: 'ExaDriverRec' has no member named 'accel'
radeon_exa_funcs.c:360: error: 'ExaDriverRec' has no member named 'accel'
radeon_exa_funcs.c:361: error: 'ExaDriverRec' has no member named 'accel'
radeon_exa_funcs.c:362: error: 'ExaDriverRec' has no member named 'accel'
radeon_exa_funcs.c:369: error: 'ExaDriverRec' has no member named 'card'
radeon_exa_funcs.c:370: error: 'ExaDriverRec' has no member named 'card'
radeon_exa_funcs.c:371: error: 'ExaDriverRec' has no member named 'card'
radeon_exa_funcs.c:373: error: 'ExaDriverRec' has no member named 'card'
radeon_exa_funcs.c:374: error: 'ExaDriverRec' has no member named 'card'
radeon_exa_funcs.c:387: error: 'ExaDriverRec' has no member named 'accel'
radeon_exa_funcs.c:388: error: 'ExaDriverRec' has no member named 'accel'
radeon_exa_funcs.c:390: error: 'ExaDriverRec' has no member named 'accel'
radeon_exa_funcs.c:391: error: 'ExaDriverRec' has no member named 'accel'
radeon_exa_funcs.c:395: error: 'ExaDriverRec' has no member named 'accel'
radeon_exa_funcs.c:396: error: 'ExaDriverRec' has no member named 'accel'
radeon_exa_funcs.c:398: error: 'ExaDriverRec' has no member named 'accel'
radeon_exa_funcs.c:399: error: 'ExaDriverRec' has no member named 'accel'
In file included from radeon_exa.c:357:
radeon_exa_funcs.c: In function 'RADEONDrawInitCP':
radeon_exa_funcs.c:350: error: 'ExaDriverRec' has no member named 'accel'
radeon_exa_funcs.c:350: error: 'ExaAccelInfoRec' undeclared (first use in this function)
radeon_exa_funcs.c:352: error: 'ExaDriverRec' has no member named 'accel'
radeon_exa_funcs.c:353: error: 'ExaDriverRec' has no member named 'accel'
radeon_exa_funcs.c:354: error: 'ExaDriverRec' has no member named 'accel'
radeon_exa_funcs.c:356: error: 'ExaDriverRec' has no member named 'accel'
radeon_exa_funcs.c:357: error: 'ExaDriverRec' has no member named 'accel'
radeon_exa_funcs.c:358: error: 'ExaDriverRec' has no member named 'accel'
radeon_exa_funcs.c:360: error: 'ExaDriverRec' has no member named 'accel'
radeon_exa_funcs.c:361: error: 'ExaDriverRec' has no member named 'accel'
radeon_exa_funcs.c:362: error: 'ExaDriverRec' has no member named 'accel'
radeon_exa_funcs.c:369: error: 'ExaDriverRec' has no member named 'card'
radeon_exa_funcs.c:370: error: 'ExaDriverRec' has no member named 'card'
radeon_exa_funcs.c:371: error: 'ExaDriverRec' has no member named 'card'
radeon_exa_funcs.c:373: error: 'ExaDriverRec' has no member named 'card'
radeon_exa_funcs.c:374: error: 'ExaDriverRec' has no member named 'card'
radeon_exa_funcs.c:387: error: 'ExaDriverRec' has no member named 'accel'
radeon_exa_funcs.c:388: error: 'ExaDriverRec' has no member named 'accel'
radeon_exa_funcs.c:390: error: 'ExaDriverRec' has no member named 'accel'
radeon_exa_funcs.c:391: error: 'ExaDriverRec' has no member named 'accel'
radeon_exa_funcs.c:395: error: 'ExaDriverRec' has no member named 'accel'
radeon_exa_funcs.c:396: error: 'ExaDriverRec' has no member named 'accel'
radeon_exa_funcs.c:398: error: 'ExaDriverRec' has no member named 'accel'
radeon_exa_funcs.c:399: error: 'ExaDriverRec' has no member named 'accel'
radeon_exa.c: In function 'RADEONSetupMemEXA':
radeon_exa.c:382: error: 'ExaDriverRec' has no member named 'card'
radeon_exa.c:383: error: 'ExaDriverRec' has no member named 'card'
radeon_exa.c:384: error: 'ExaDriverRec' has no member named 'card'
radeon_exa.c:387: error: 'ExaDriverRec' has no member named 'card'
radeon_exa.c:415: error: 'ExaDriverRec' has no member named 'card'
radeon_exa.c:417: error: 'ExaDriverRec' has no member named 'card'
radeon_exa.c:420: error: 'ExaDriverRec' has no member named 'card'
radeon_exa.c:431: error: 'ExaDriverRec' has no member named 'card'
radeon_exa.c:432: error: 'ExaDriverRec' has no member named 'card'
radeon_exa.c:435: error: 'ExaDriverRec' has no member named 'card'
radeon_exa.c:441: error: 'ExaDriverRec' has no member named 'card'
radeon_exa.c:442: error: 'ExaDriverRec' has no member named 'card'
radeon_exa.c:449: error: 'ExaDriverRec' has no member named 'card'
radeon_exa.c:450: error: 'ExaDriverRec' has no member named 'card'
radeon_exa.c:463: error: 'ExaDriverRec' has no member named 'card'
radeon_exa.c:463: error: 'ExaDriverRec' has no member named 'card'
radeon_exa.c:464: error: 'ExaDriverRec' has no member named 'card'
make[2]: *** [radeon_exa.lo] Error 1
make[2]: Leaving directory `/home/dvr/atidrivers/xf86-video-ati-6.5.8.0/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/dvr/atidrivers/xf86-video-ati-6.5.8.0'
make: *** [all] Error 2


---

### Post by yoav_steinberg on 2006-12-02
I solved this by commenting out all references to the accel and card fields in the src/radeon_exa.c and src/radeon_exa_funcs.c files. Seems like all the stuff in "card" and "accel" was moved up to the root of the exa struct. For example, i changed this line:
info->exa.card.flags = EXA_OFFSCREEN_PIXMAPS;
to:
info->exa.flags = EXA_OFFSCREEN_PIXMAPS;
.. sorry didn't have time to make a nice patch.

---

### Post by Fittersman on 2006-12-08
hey for that last post, could you provide more specific directions please?

i went in and could not find what you were talking about, just incase ill post the radeon_exa.c file here for you

```
/*
 * Copyright 2005 Eric Anholt
 * Copyright 2005 Benjamin Herrenschmidt
 * All Rights Reserved.
 *
 * Permission is hereby granted, free of charge, to any person obtaining a
 * copy of this software and associated documentation files (the "Software"),
 * to deal in the Software without restriction, including without limitation
 * the rights to use, copy, modify, merge, publish, distribute, sublicense,
 * and/or sell copies of the Software, and to permit persons to whom the
 * Software is furnished to do so, subject to the following conditions:
 *
 * The above copyright notice and this permission notice (including the next
 * paragraph) shall be included in all copies or substantial portions of the
 * Software.
 *
 * THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
 * IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
 * FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.  IN NO EVENT SHALL
 * THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
 * LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
 * OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
 * SOFTWARE.
 *
 * Authors:
 *    Eric Anholt <anholt@FreeBSD.org>
 *    Zack Rusin <zrusin@trolltech.com>
 *    Benjamin Herrenschmidt <benh@kernel.crashing.org>
 *
 */

#ifdef HAVE_CONFIG_H
#include "config.h"
#endif

#include "radeon.h"
#include "radeon_reg.h"
#ifdef XF86DRI
#include "radeon_dri.h"
#endif
#include "radeon_macros.h"
#include "radeon_probe.h"
#include "radeon_version.h"
#ifdef XF86DRI
#include "radeon_sarea.h"
#endif

#include "xf86.h"


/***********************************************************************/
#define RINFO_FROM_SCREEN(pScr) ScrnInfoPtr pScrn =  xf86Screens[pScr->myNum]; \
    RADEONInfoPtr info   = RADEONPTR(pScrn)

#define RADEON_TRACE_FALL 0
#define RADEON_TRACE_DRAW 0

#if RADEON_TRACE_FALL
#define RADEON_FALLBACK(x)     		\
do {					\
	ErrorF("%s: ", __FUNCTION__);	\
	ErrorF x;			\
	return FALSE;			\
} while (0)
#else
#define RADEON_FALLBACK(x) return FALSE
#endif

#if RADEON_TRACE_DRAW
#define TRACE do { ErrorF("TRACE: %s\n", __FUNCTION__); } while(0)
#else
#define TRACE
#endif

static struct {
    int rop;
    int pattern;
} RADEON_ROP[] = {
    { RADEON_ROP3_ZERO, RADEON_ROP3_ZERO }, /* GXclear        */
    { RADEON_ROP3_DSa,  RADEON_ROP3_DPa  }, /* Gxand          */
    { RADEON_ROP3_SDna, RADEON_ROP3_PDna }, /* GXandReverse   */
    { RADEON_ROP3_S,    RADEON_ROP3_P    }, /* GXcopy         */
    { RADEON_ROP3_DSna, RADEON_ROP3_DPna }, /* GXandInverted  */
    { RADEON_ROP3_D,    RADEON_ROP3_D    }, /* GXnoop         */
    { RADEON_ROP3_DSx,  RADEON_ROP3_DPx  }, /* GXxor          */
    { RADEON_ROP3_DSo,  RADEON_ROP3_DPo  }, /* GXor           */
    { RADEON_ROP3_DSon, RADEON_ROP3_DPon }, /* GXnor          */
    { RADEON_ROP3_DSxn, RADEON_ROP3_PDxn }, /* GXequiv        */
    { RADEON_ROP3_Dn,   RADEON_ROP3_Dn   }, /* GXinvert       */
    { RADEON_ROP3_SDno, RADEON_ROP3_PDno }, /* GXorReverse    */
    { RADEON_ROP3_Sn,   RADEON_ROP3_Pn   }, /* GXcopyInverted */
    { RADEON_ROP3_DSno, RADEON_ROP3_DPno }, /* GXorInverted   */
    { RADEON_ROP3_DSan, RADEON_ROP3_DPan }, /* GXnand         */
    { RADEON_ROP3_ONE,  RADEON_ROP3_ONE  }  /* GXset          */
};

/* Compute log base 2 of val. */
static __inline__ int
RADEONLog2(int val)
{
	int bits;

	for (bits = 0; val != 0; val >>= 1, ++bits)
		;
	return bits - 1;
}

static __inline__ CARD32 F_TO_DW(float val)
{
    union {
	float f;
	CARD32 l;
    } tmp;
    tmp.f = val;
    return tmp.l;
}

/* Assumes that depth 15 and 16 can be used as depth 16, which is okay since we
 * require src and dest datatypes to be equal.
 */
static Bool RADEONGetDatatypeBpp(int bpp, CARD32 *type)
{
	switch (bpp) {
	case 8:
		*type = ATI_DATATYPE_CI8;
		return TRUE;
	case 16:
		*type = ATI_DATATYPE_RGB565;
		return TRUE;
	case 24:
		*type = ATI_DATATYPE_CI8;
		return TRUE;
	case 32:
		*type = ATI_DATATYPE_ARGB8888;
		return TRUE;
	default:
		RADEON_FALLBACK(("Unsupported bpp: %d\n", bpp));
		return FALSE;
	}
}

static Bool RADEONPixmapIsColortiled(PixmapPtr pPix)
{
    RINFO_FROM_SCREEN(pPix->drawable.pScreen);

    /* This doesn't account for the back buffer, which we may want to wrap in
     * a pixmap at some point for the purposes of DRI buffer moves.
     */
    if (info->tilingEnabled && exaGetPixmapOffset(pPix) == 0)
	return TRUE;
    else
	return FALSE;
}

static Bool RADEONGetOffsetPitch(PixmapPtr pPix, int bpp, CARD32 *pitch_offset,
				 unsigned int offset, unsigned int pitch)
{
	RINFO_FROM_SCREEN(pPix->drawable.pScreen);

	if (pitch % info->exa->pixmapPitchAlign != 0)
		RADEON_FALLBACK(("Bad pitch 0x%08x\n", pitch));

	if (offset % info->exa->pixmapOffsetAlign != 0)
		RADEON_FALLBACK(("Bad offset 0x%08x\n", offset));

	pitch = pitch >> 6;
	*pitch_offset = (pitch << 22) | (offset >> 10);

	/* If it's the front buffer, we've got to note that it's tiled? */
	if (RADEONPixmapIsColortiled(pPix))
		*pitch_offset |= RADEON_DST_TILE_MACRO;
	return TRUE;
}

static Bool RADEONGetPixmapOffsetPitch(PixmapPtr pPix, CARD32 *pitch_offset)
{
	RINFO_FROM_SCREEN(pPix->drawable.pScreen);
	CARD32 pitch, offset;
	int bpp;

	bpp = pPix->drawable.bitsPerPixel;
	if (bpp == 24)
		bpp = 8;

	offset = exaGetPixmapOffset(pPix) + info->fbLocation;
	pitch = exaGetPixmapPitch(pPix);

	return RADEONGetOffsetPitch(pPix, bpp, pitch_offset, offset, pitch);
}

#if X_BYTE_ORDER == X_BIG_ENDIAN

static unsigned long swapper_surfaces[3];

static Bool RADEONPrepareAccess(PixmapPtr pPix, int index)
{
    RINFO_FROM_SCREEN(pPix->drawable.pScreen);
    unsigned char *RADEONMMIO = info->MMIO;
    CARD32 offset = exaGetPixmapOffset(pPix);
    int bpp, soff;
    CARD32 size, flags;

    /* Front buffer is always set with proper swappers */
    if (offset == 0)
        return TRUE;

    /* If same bpp as front buffer, just do nothing as the main
     * swappers will apply
     */
    bpp = pPix->drawable.bitsPerPixel;
    if (bpp == pScrn->bitsPerPixel)
        return TRUE;

    /* We need to setup a separate swapper, let's request a
     * surface. We need to align the size first
     */
    size = exaGetPixmapSize(pPix);
    size = (size + RADEON_BUFFER_ALIGN) & ~(RADEON_BUFFER_ALIGN);

    /* Set surface to tiling disabled with appropriate swapper */
    switch (bpp) {
    case 16:
        flags = RADEON_SURF_AP0_SWP_16BPP | RADEON_SURF_AP1_SWP_16BPP;
	break;
    case 32:
        flags = RADEON_SURF_AP0_SWP_32BPP | RADEON_SURF_AP1_SWP_32BPP;
	break;
    default:
        flags = 0;
    }
#if defined(XF86DRI)
    if (info->directRenderingEnabled && info->allowColorTiling) {
	drmRadeonSurfaceAlloc drmsurfalloc;
	int rc;

        drmsurfalloc.address = offset;
        drmsurfalloc.size = size;
	drmsurfalloc.flags = flags | 1; /* bogus pitch to please DRM */

        rc = drmCommandWrite(info->drmFD, DRM_RADEON_SURF_ALLOC,
			     &drmsurfalloc, sizeof(drmsurfalloc));
	if (rc < 0) {
	    xf86DrvMsg(pScrn->scrnIndex, X_ERROR,
		       "drm: could not allocate surface for access"
		       " swapper, err: %d!\n", rc);
	    return FALSE;
	}
	swapper_surfaces[index] = offset;

	return TRUE;
    }
#endif
    soff = (index + 1) * 0x10;
    OUTREG(RADEON_SURFACE0_INFO + soff, flags);
    OUTREG(RADEON_SURFACE0_LOWER_BOUND + soff, offset);
    OUTREG(RADEON_SURFACE0_UPPER_BOUND + soff, offset + size - 1);
    swapper_surfaces[index] = offset;
    return TRUE;
}

static void RADEONFinishAccess(PixmapPtr pPix, int index)
{
    RINFO_FROM_SCREEN(pPix->drawable.pScreen);
    unsigned char *RADEONMMIO = info->MMIO;
    CARD32 offset = exaGetPixmapOffset(pPix);
    int soff;

    /* Front buffer is always set with proper swappers */
    if (offset == 0)
        return;

    if (swapper_surfaces[index] == 0)
        return;
#if defined(XF86DRI)
    if (info->directRenderingEnabled && info->allowColorTiling) {
	drmRadeonSurfaceFree drmsurffree;

	drmsurffree.address = offset;
	drmCommandWrite(info->drmFD, DRM_RADEON_SURF_FREE,
			&drmsurffree, sizeof(drmsurffree));
	swapper_surfaces[index] = 0;
	return;
    }
#endif
    soff = (index + 1) * 0x10;
    OUTREG(RADEON_SURFACE0_INFO + soff, 0);
    OUTREG(RADEON_SURFACE0_LOWER_BOUND + soff, 0);
    OUTREG(RADEON_SURFACE0_UPPER_BOUND + soff, 0);
    swapper_surfaces[index] = 0;
}

#endif /* X_BYTE_ORDER == X_BIG_ENDIAN */

#define RADEON_SWITCH_TO_2D()						\
do {									\
	CARD32 wait_until = 0;			\
	BEGIN_ACCEL(1);							\
	switch (info->engineMode) {					\
	case EXA_ENGINEMODE_UNKNOWN:					\
	    wait_until |= RADEON_WAIT_HOST_IDLECLEAN | RADEON_WAIT_2D_IDLECLEAN;	\
	case EXA_ENGINEMODE_3D:						\
	    wait_until |= RADEON_WAIT_3D_IDLECLEAN;			\
	case EXA_ENGINEMODE_2D:						\
	    break;							\
	}								\
	OUT_ACCEL_REG(RADEON_WAIT_UNTIL, wait_until);			\
	FINISH_ACCEL();							\
        info->engineMode = EXA_ENGINEMODE_2D;                           \
} while (0);

#define RADEON_SWITCH_TO_3D()						\
do {									\
	CARD32 wait_until = 0;			\
	BEGIN_ACCEL(1);							\
	switch (info->engineMode) {					\
	case EXA_ENGINEMODE_UNKNOWN:					\
	    wait_until |= RADEON_WAIT_HOST_IDLECLEAN | RADEON_WAIT_3D_IDLECLEAN;	\
	case EXA_ENGINEMODE_2D:						\
	    wait_until |= RADEON_WAIT_2D_IDLECLEAN;			\
	case EXA_ENGINEMODE_3D:						\
	    break;							\
	}								\
	OUT_ACCEL_REG(RADEON_WAIT_UNTIL, wait_until);			\
	FINISH_ACCEL();							\
        info->engineMode = EXA_ENGINEMODE_3D;                           \
} while (0);

#define ENTER_DRAW(x) TRACE
#define LEAVE_DRAW(x) TRACE
/***********************************************************************/

#define ACCEL_MMIO
#define ACCEL_PREAMBLE()	unsigned char *RADEONMMIO = info->MMIO
#define BEGIN_ACCEL(n)		RADEONWaitForFifo(pScrn, (n))
#define OUT_ACCEL_REG(reg, val)	OUTREG(reg, val)
#define OUT_ACCEL_REG_F(reg, val) OUTREG(reg, F_TO_DW(val))
#define FINISH_ACCEL()

#ifdef RENDER
#include "radeon_exa_render.c"
#endif
#include "radeon_exa_funcs.c"

#undef ACCEL_MMIO
#undef ACCEL_PREAMBLE
#undef BEGIN_ACCEL
#undef OUT_ACCEL_REG
#undef FINISH_ACCEL

#ifdef XF86DRI

#define ACCEL_CP
#define ACCEL_PREAMBLE()						\
    RING_LOCALS;							\
    RADEONCP_REFRESH(pScrn, info)
#define BEGIN_ACCEL(n)		BEGIN_RING(2*(n))
#define OUT_ACCEL_REG(reg, val)	OUT_RING_REG(reg, val)
#define FINISH_ACCEL()		ADVANCE_RING()

#define OUT_RING_F(x) OUT_RING(F_TO_DW(x))

#ifdef RENDER
#include "radeon_exa_render.c"
#endif
#include "radeon_exa_funcs.c"

#endif /* XF86DRI */

/*
 * Once screen->off_screen_base is set, this function
 * allocates the remaining memory appropriately
 */
Bool RADEONSetupMemEXA (ScreenPtr pScreen)
{
    ScrnInfoPtr pScrn = xf86Screens[pScreen->myNum];
    RADEONInfoPtr info = RADEONPTR(pScrn);
    int cpp = info->CurrentLayout.pixel_bytes;
    int screen_size;
    int byteStride = pScrn->displayWidth * cpp;

    if (info->exa != NULL) {
	xf86DrvMsg(pScreen->myNum, X_ERROR, "Memory map already initialized\n");
	return FALSE;
    }
    info->exa = exaDriverAlloc();
    if (info->exa == NULL)
	return FALSE;

    /* Need to adjust screen size for 16 line tiles, and then make it align to.
     * the buffer alignment requirement.
     */
    if (info->allowColorTiling)
	screen_size = RADEON_ALIGN(pScrn->virtualY, 16) * byteStride;
    else
	screen_size = pScrn->virtualY * byteStride;

    info->exa->memoryBase = info->FB + pScrn->fbOffset;
    info->exa->memorySize = info->FbMapSize - info->FbSecureSize;
    info->exa->offScreenBase = screen_size;

    xf86DrvMsg(pScrn->scrnIndex, X_INFO, "Allocating from a screen of %ld kb\n",
	       info->exa->memorySize / 1024);

    xf86DrvMsg(pScrn->scrnIndex, X_INFO,
	       "Will use %d kb for front buffer at offset 0x%08x\n",
	       screen_size / 1024, 0);

    /* Reserve static area for hardware cursor */
    if (!xf86ReturnOptValBool(info->Options, OPTION_SW_CURSOR, FALSE)) {
	int cursor_size = 64 * 4 * 64;

	info->cursor_offset = info->exa->offScreenBase;

	xf86DrvMsg(pScrn->scrnIndex, X_INFO,
		   "Will use %d kb for hardware cursor at offset 0x%08x\n",
		   cursor_size / 1024, (unsigned int)info->cursor_offset);

	info->exa->offScreenBase += cursor_size;
    }

#if defined(XF86DRI)
    if (info->directRenderingEnabled) {
	int depthCpp = (info->depthBits - 8) / 4, l, next, depth_size;

	info->frontOffset = 0;
	info->frontPitch = pScrn->displayWidth;

	RADEONDRIAllocatePCIGARTTable(pScreen);
	
	if (info->cardType==CARD_PCIE)
	  xf86DrvMsg(pScrn->scrnIndex, X_INFO,
		     "Will use %d kb for PCI GART at offset 0x%08x\n",
		     RADEON_PCIGART_TABLE_SIZE / 1024,
		     (int)info->pciGartOffset);

	/* Reserve a static area for the back buffer the same size as the
	 * visible screen.  XXX: This would be better initialized in ati_dri.c
	 * when GLX is set up, but the offscreen memory manager's allocations
	 * don't last through VT switches, while the kernel's understanding of
	 * offscreen locations does.
	 */
	info->backPitch = pScrn->displayWidth;
	next = RADEON_ALIGN(info->exa->offScreenBase, RADEON_BUFFER_ALIGN);
	if (!info->noBackBuffer &&
	    next + screen_size <= info->exa->memorySize)
	{
	    info->backOffset = next;
	    info->exa->offScreenBase = next + screen_size;
	    xf86DrvMsg(pScrn->scrnIndex, X_INFO,
		       "Will use %d kb for back buffer at offset 0x%08x\n",
		       screen_size / 1024, info->backOffset);
	}

	/* Reserve the static depth buffer, and adjust pitch and height to
	 * handle tiling.
	 */
	info->depthPitch = RADEON_ALIGN(pScrn->displayWidth, 32);
	depth_size = RADEON_ALIGN(pScrn->virtualY, 16) * info->depthPitch * depthCpp;
	next = RADEON_ALIGN(info->exa->offScreenBase, RADEON_BUFFER_ALIGN);
	if (next + depth_size <= info->exa->memorySize)
	{
	    info->depthOffset = next;
	    info->exa->offScreenBase = next + depth_size;
	    xf86DrvMsg(pScrn->scrnIndex, X_INFO,
		       "Will use %d kb for depth buffer at offset 0x%08x\n",
		       depth_size / 1024, info->depthOffset);
	}
	
	info->textureSize *= (info->exa->memorySize -
			      info->exa->offScreenBase) / 100;

	l = RADEONLog2(info->textureSize / RADEON_NR_TEX_REGIONS);
	if (l < RADEON_LOG_TEX_GRANULARITY)
	    l = RADEON_LOG_TEX_GRANULARITY;
	info->textureSize = (info->textureSize >> l) << l;
	if (info->textureSize >= 512 * 1024) {
	    info->textureOffset = info->exa->offScreenBase;
	    info->exa->offScreenBase += info->textureSize;
	    xf86DrvMsg(pScrn->scrnIndex, X_INFO,
		       "Will use %d kb for textures at offset 0x%08x\n",
		       info->textureSize / 1024, info->textureOffset);
	} else {
	    /* Minimum texture size is for 2 256x256x32bpp textures */
	    info->textureSize = 0;
	}
    }
#endif /* XF86DRI */
	
    xf86DrvMsg(pScrn->scrnIndex, X_INFO,
	       "Will use %ld kb for X Server offscreen at offset 0x%08lx\n",
	       (info->exa->memorySize - info->exa->offScreenBase) /
	       1024, info->exa->offScreenBase);

    return TRUE;
}

```

and here is the radeon_exa_funcs.c

```
/*
 * Copyright 2005 Eric Anholt
 * Copyright 2005 Benjamin Herrenschmidt
 * Copyright 2006 Tungsten Graphics, Inc.
 * All Rights Reserved.
 *
 * Permission is hereby granted, free of charge, to any person obtaining a
 * copy of this software and associated documentation files (the "Software"),
 * to deal in the Software without restriction, including without limitation
 * the rights to use, copy, modify, merge, publish, distribute, sublicense,
 * and/or sell copies of the Software, and to permit persons to whom the
 * Software is furnished to do so, subject to the following conditions:
 *
 * The above copyright notice and this permission notice (including the next
 * paragraph) shall be included in all copies or substantial portions of the
 * Software.
 *
 * THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
 * IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
 * FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.  IN NO EVENT SHALL
 * THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
 * LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
 * OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
 * SOFTWARE.
 *
 * Authors:
 *    Eric Anholt <anholt@FreeBSD.org>
 *    Zack Rusin <zrusin@trolltech.com>
 *    Benjamin Herrenschmidt <benh@kernel.crashing.org>
 *    Michel Dänzer <michel@tungstengraphics.com>
 *
 */

#if defined(ACCEL_MMIO) && defined(ACCEL_CP)
#error Cannot define both MMIO and CP acceleration!
#endif

#if !defined(UNIXCPP) || defined(ANSICPP)
#define FUNC_NAME_CAT(prefix,suffix) prefix##suffix
#else
#define FUNC_NAME_CAT(prefix,suffix) prefix/**/suffix
#endif

#ifdef ACCEL_MMIO
#define FUNC_NAME(prefix) FUNC_NAME_CAT(prefix,MMIO)
#else
#ifdef ACCEL_CP
#define FUNC_NAME(prefix) FUNC_NAME_CAT(prefix,CP)
#else
#error No accel type defined!
#endif
#endif

#include <errno.h>
#include <string.h>

#include "radeon.h"
#include "atidri.h"

#include "exa.h"

static void
FUNC_NAME(RADEONSync)(ScreenPtr pScreen, int marker)
{
    TRACE;

    FUNC_NAME(RADEONWaitForIdle)(xf86Screens[pScreen->myNum]);

    RADEONPTR(xf86Screens[pScreen->myNum])->engineMode = EXA_ENGINEMODE_UNKNOWN;
}

static Bool
FUNC_NAME(RADEONPrepareSolid)(PixmapPtr pPix, int alu, Pixel pm, Pixel fg)
{
    RINFO_FROM_SCREEN(pPix->drawable.pScreen);
    CARD32 datatype, dst_pitch_offset;
    ACCEL_PREAMBLE();

    TRACE;

    if (pPix->drawable.bitsPerPixel == 24)
	RADEON_FALLBACK(("24bpp unsupported\n"));
    if (!RADEONGetDatatypeBpp(pPix->drawable.bitsPerPixel, &datatype))
	RADEON_FALLBACK(("RADEONGetDatatypeBpp failed\n"));
    if (!RADEONGetPixmapOffsetPitch(pPix, &dst_pitch_offset))
	RADEON_FALLBACK(("RADEONGetPixmapOffsetPitch failed\n"));

    RADEON_SWITCH_TO_2D();

    BEGIN_ACCEL(5);
    OUT_ACCEL_REG(RADEON_DP_GUI_MASTER_CNTL,
	    RADEON_GMC_DST_PITCH_OFFSET_CNTL |
	    RADEON_GMC_BRUSH_SOLID_COLOR |
	    (datatype << 8) |
	    RADEON_GMC_SRC_DATATYPE_COLOR |
	    RADEON_ROP[alu].pattern |
	    RADEON_GMC_CLR_CMP_CNTL_DIS);
    OUT_ACCEL_REG(RADEON_DP_BRUSH_FRGD_CLR, fg);
    OUT_ACCEL_REG(RADEON_DP_WRITE_MASK, pm);
    OUT_ACCEL_REG(RADEON_DP_CNTL,
	(RADEON_DST_X_LEFT_TO_RIGHT | RADEON_DST_Y_TOP_TO_BOTTOM));
    OUT_ACCEL_REG(RADEON_DST_PITCH_OFFSET, dst_pitch_offset);
    FINISH_ACCEL();

    return TRUE;
}


static void
FUNC_NAME(RADEONSolid)(PixmapPtr pPix, int x1, int y1, int x2, int y2)
{

    RINFO_FROM_SCREEN(pPix->drawable.pScreen);
    ACCEL_PREAMBLE();

    TRACE;

    BEGIN_ACCEL(2);
    OUT_ACCEL_REG(RADEON_DST_Y_X, (y1 << 16) | x1);
    OUT_ACCEL_REG(RADEON_DST_HEIGHT_WIDTH, ((y2 - y1) << 16) | (x2 - x1));
    FINISH_ACCEL();
}

static void
FUNC_NAME(RADEONDoneSolid)(PixmapPtr pPix)
{
    TRACE;
}

static Bool
FUNC_NAME(RADEONPrepareCopy)(PixmapPtr pSrc,   PixmapPtr pDst,
			     int xdir, int ydir,
			     int rop,
			     Pixel planemask)
{
    RINFO_FROM_SCREEN(pDst->drawable.pScreen);
    CARD32 datatype, src_pitch_offset, dst_pitch_offset;
    ACCEL_PREAMBLE();

    TRACE;

    info->xdir = xdir;
    info->ydir = ydir;

    if (pDst->drawable.bitsPerPixel == 24)
	RADEON_FALLBACK(("24bpp unsupported"));
    if (!RADEONGetDatatypeBpp(pDst->drawable.bitsPerPixel, &datatype))
	RADEON_FALLBACK(("RADEONGetDatatypeBpp failed\n"));
    if (!RADEONGetPixmapOffsetPitch(pSrc, &src_pitch_offset))
	RADEON_FALLBACK(("RADEONGetPixmapOffsetPitch source failed\n"));
    if (!RADEONGetPixmapOffsetPitch(pDst, &dst_pitch_offset))
	RADEON_FALLBACK(("RADEONGetPixmapOffsetPitch dest failed\n"));

    RADEON_SWITCH_TO_2D();

    BEGIN_ACCEL(5);
    OUT_ACCEL_REG(RADEON_DP_GUI_MASTER_CNTL,
	RADEON_GMC_DST_PITCH_OFFSET_CNTL |
	RADEON_GMC_SRC_PITCH_OFFSET_CNTL |
	RADEON_GMC_BRUSH_NONE |
	(datatype << 8) |
	RADEON_GMC_SRC_DATATYPE_COLOR |
	RADEON_ROP[rop].rop |
	RADEON_DP_SRC_SOURCE_MEMORY |
	RADEON_GMC_CLR_CMP_CNTL_DIS);
    OUT_ACCEL_REG(RADEON_DP_WRITE_MASK, planemask);
    OUT_ACCEL_REG(RADEON_DP_CNTL,
	((xdir >= 0 ? RADEON_DST_X_LEFT_TO_RIGHT : 0) |
	 (ydir >= 0 ? RADEON_DST_Y_TOP_TO_BOTTOM : 0)));
    OUT_ACCEL_REG(RADEON_DST_PITCH_OFFSET, dst_pitch_offset);
    OUT_ACCEL_REG(RADEON_SRC_PITCH_OFFSET, src_pitch_offset);
    FINISH_ACCEL();

    return TRUE;
}

static void
FUNC_NAME(RADEONCopy)(PixmapPtr pDst,
		      int srcX, int srcY,
		      int dstX, int dstY,
		      int w, int h)
{

    RINFO_FROM_SCREEN(pDst->drawable.pScreen);
    ACCEL_PREAMBLE();

    TRACE;

    if (info->xdir < 0) {
	srcX += w - 1;
	dstX += w - 1;
    }
    if (info->ydir < 0) {
	srcY += h - 1;
	dstY += h - 1;
    }

    BEGIN_ACCEL(3);

    OUT_ACCEL_REG(RADEON_SRC_Y_X,	   (srcY << 16) | srcX);
    OUT_ACCEL_REG(RADEON_DST_Y_X,	   (dstY << 16) | dstX);
    OUT_ACCEL_REG(RADEON_DST_HEIGHT_WIDTH, (h  << 16) | w);

    FINISH_ACCEL();
}

static void
FUNC_NAME(RADEONDoneCopy)(PixmapPtr pDst)
{
    TRACE;
}

static Bool
FUNC_NAME(RADEONUploadToScreen)(PixmapPtr pDst, int x, int y, int w, int h,
				char *src, int src_pitch)
{
#if X_BYTE_ORDER == X_BIG_ENDIAN || defined(ACCEL_CP)
    RINFO_FROM_SCREEN(pDst->drawable.pScreen);
#endif
    CARD8	   *dst	     = pDst->devPrivate.ptr;
    unsigned int   dst_pitch = exaGetPixmapPitch(pDst);
    unsigned int   bpp	     = pDst->drawable.bitsPerPixel;
#ifdef ACCEL_CP
    unsigned int   hpass;
    CARD32	   buf_pitch, dst_pitch_off;
#endif
#if X_BYTE_ORDER == X_BIG_ENDIAN 
    unsigned char *RADEONMMIO = info->MMIO;
    unsigned int swapper = info->ModeReg.surface_cntl &
	    ~(RADEON_NONSURF_AP0_SWP_32BPP | RADEON_NONSURF_AP1_SWP_32BPP |
	      RADEON_NONSURF_AP0_SWP_16BPP | RADEON_NONSURF_AP1_SWP_16BPP);
#endif

    TRACE;

    if (bpp < 8)
	return FALSE;

#ifdef ACCEL_CP
    if (info->directRenderingEnabled &&
	RADEONGetPixmapOffsetPitch(pDst, &dst_pitch_off)) {
	CARD8 *buf;
	int cpp = bpp / 8;
	ACCEL_PREAMBLE();

	RADEON_SWITCH_TO_2D();
	while ((buf = RADEONHostDataBlit(pScrn,
					 cpp, w, dst_pitch_off, &buf_pitch,
					 x, &y, (unsigned int*)&h, &hpass)) != 0) {
	    RADEONHostDataBlitCopyPass(pScrn, cpp, buf, (CARD8 *)src,
				       hpass, buf_pitch, src_pitch);
	    src += hpass * src_pitch;
	}

	exaMarkSync(pDst->drawable.pScreen);
	return TRUE;
  }
#endif

    /* Do we need that sync here ? probably not .... */
    exaWaitSync(pDst->drawable.pScreen);

#if X_BYTE_ORDER == X_BIG_ENDIAN
    switch(bpp) {
    case 15:
    case 16:
	swapper |= RADEON_NONSURF_AP0_SWP_16BPP
		|  RADEON_NONSURF_AP1_SWP_16BPP;
	break;
    case 24:
    case 32:
	swapper |= RADEON_NONSURF_AP0_SWP_32BPP
		|  RADEON_NONSURF_AP1_SWP_32BPP;
	break;
    }
    OUTREG(RADEON_SURFACE_CNTL, swapper);
#endif
    w *= bpp / 8;
    dst += (x * bpp / 8) + (y * dst_pitch);

    while (h--) {
	memcpy(dst, src, w);
	src += src_pitch;
	dst += dst_pitch;
    }

#if X_BYTE_ORDER == X_BIG_ENDIAN
    /* restore byte swapping */
    OUTREG(RADEON_SURFACE_CNTL, info->ModeReg.surface_cntl);
#endif

    return TRUE;
}

#ifdef ACCEL_CP
/* Emit blit with arbitrary source and destination offsets and pitches */
static void
RADEONBlitChunk(ScrnInfoPtr pScrn, CARD32 datatype, CARD32 src_pitch_offset,
		CARD32 dst_pitch_offset, int srcX, int srcY, int dstX, int dstY,
		int w, int h)
{
    RADEONInfoPtr info = RADEONPTR(pScrn);
    ACCEL_PREAMBLE();

    BEGIN_ACCEL(6);
    OUT_ACCEL_REG(RADEON_DP_GUI_MASTER_CNTL,
		  RADEON_GMC_DST_PITCH_OFFSET_CNTL |
		  RADEON_GMC_SRC_PITCH_OFFSET_CNTL |
		  RADEON_GMC_BRUSH_NONE |
		  (datatype << 8) |
		  RADEON_GMC_SRC_DATATYPE_COLOR |
		  RADEON_ROP3_S |
		  RADEON_DP_SRC_SOURCE_MEMORY |
		  RADEON_GMC_CLR_CMP_CNTL_DIS |
		  RADEON_GMC_WR_MSK_DIS);
    OUT_ACCEL_REG(RADEON_SRC_PITCH_OFFSET, src_pitch_offset);
    OUT_ACCEL_REG(RADEON_DST_PITCH_OFFSET, dst_pitch_offset);
    OUT_ACCEL_REG(RADEON_SRC_Y_X, (srcY << 16) | srcX);
    OUT_ACCEL_REG(RADEON_DST_Y_X, (dstY << 16) | dstX);
    OUT_ACCEL_REG(RADEON_DST_HEIGHT_WIDTH, (h << 16) | w);
    FINISH_ACCEL();
}
#endif

static Bool
FUNC_NAME(RADEONDownloadFromScreen)(PixmapPtr pSrc, int x, int y, int w, int h,
				    char *dst, int dst_pitch)
{
#if defined(ACCEL_CP) || X_BYTE_ORDER == X_BIG_ENDIAN
    RINFO_FROM_SCREEN(pSrc->drawable.pScreen);
#endif
#if X_BYTE_ORDER == X_BIG_ENDIAN
    unsigned char *RADEONMMIO = info->MMIO;
    unsigned int swapper = info->ModeReg.surface_cntl &
	    ~(RADEON_NONSURF_AP0_SWP_32BPP | RADEON_NONSURF_AP1_SWP_32BPP |
	      RADEON_NONSURF_AP0_SWP_16BPP | RADEON_NONSURF_AP1_SWP_16BPP);
#endif
    CARD8	  *src	     = pSrc->devPrivate.ptr;
    int		   src_pitch = exaGetPixmapPitch(pSrc);
    int		   bpp	     = pSrc->drawable.bitsPerPixel;
#ifdef ACCEL_CP
    CARD32 datatype, src_pitch_offset, scratch_pitch = (w * bpp/8 + 63) & ~63, scratch_off = 0;
    drmBufPtr scratch;
#endif

    TRACE;

#ifdef ACCEL_CP
    /*
     * Try to accelerate download. Use an indirect buffer as scratch space,
     * blitting the bits to one half while copying them out of the other one and
     * then swapping the halves.
     */
    if (info->accelDFS && bpp != 24 && RADEONGetDatatypeBpp(bpp, &datatype) &&
	RADEONGetPixmapOffsetPitch(pSrc, &src_pitch_offset) &&
	(scratch = RADEONCPGetBuffer(pScrn)))
    {
	int swap = RADEON_HOST_DATA_SWAP_NONE, wpass = w * bpp / 8;
	int hpass = min(h, scratch->total/2 / scratch_pitch);
	CARD32 scratch_pitch_offset = scratch_pitch << 16
				    | (info->gartLocation + info->bufStart
				       + scratch->idx * scratch->total) >> 10;
	drmRadeonIndirect indirect;
	ACCEL_PREAMBLE();

	RADEON_SWITCH_TO_2D();

	/* Kick the first blit as early as possible */
	RADEONBlitChunk(pScrn, datatype, src_pitch_offset, scratch_pitch_offset,
			x, y, 0, 0, w, hpass);
	FLUSH_RING();

#if X_BYTE_ORDER == X_BIG_ENDIAN
	switch (bpp) {
	case 16:
	  swap = RADEON_HOST_DATA_SWAP_16BIT;
	  break;
	case 32:
	  swap = RADEON_HOST_DATA_SWAP_32BIT;
	  break;
	}
#endif

	while (h) {
	    int oldhpass = hpass, i = 0;

	    src = (CARD8*)scratch->address + scratch_off;

	    y += oldhpass;
	    h -= oldhpass;
	    hpass = min(h, scratch->total/2 / scratch_pitch);

	    /* Prepare next blit if anything's left */
	    if (hpass) {
		scratch_off = scratch->total/2 - scratch_off;
		RADEONBlitChunk(pScrn, datatype, src_pitch_offset, scratch_pitch_offset + (scratch_off >> 10),
				x, y, 0, 0, w, hpass);
	    }

	    /*
	     * Wait for previous blit to complete.
	     *
	     * XXX: Doing here essentially the same things this ioctl does in
	     * the DRM results in corruption with 'small' transfers, apparently
	     * because the data doesn't actually land in system RAM before the
	     * memcpy. I suspect the ioctl helps mostly due to its latency; what
	     * we'd really need is a way to reliably wait for the host interface
	     * to be done with pushing the data to the host.
	     */
	    while ((drmCommandNone(info->drmFD, DRM_RADEON_CP_IDLE) == -EBUSY)
		   && (i++ < RADEON_TIMEOUT))
		;

	    /* Kick next blit */
	    if (hpass)
		FLUSH_RING();

	    /* Copy out data from previous blit */
	    if (wpass == scratch_pitch && wpass == dst_pitch) {
		RADEONCopySwap((CARD8*)dst, src, wpass * oldhpass, swap);
		dst += dst_pitch * oldhpass;
	    } else while (oldhpass--) {
		RADEONCopySwap((CARD8*)dst, src, wpass, swap);
		src += scratch_pitch;
		dst += dst_pitch;
	    }
	}

	indirect.idx = scratch->idx;
	indirect.start = indirect.end = 0;
	indirect.discard = 1;

	drmCommandWriteRead(info->drmFD, DRM_RADEON_INDIRECT,
			    &indirect, sizeof(drmRadeonIndirect));

	return TRUE;
    }
#endif

    /* Can't accelerate download */
    exaWaitSync(pSrc->drawable.pScreen);

#if X_BYTE_ORDER == X_BIG_ENDIAN
    switch(bpp) {
    case 15:
    case 16:
	swapper |= RADEON_NONSURF_AP0_SWP_16BPP
		|  RADEON_NONSURF_AP1_SWP_16BPP;
	break;
    case 24:
    case 32:
	swapper |= RADEON_NONSURF_AP0_SWP_32BPP
		|  RADEON_NONSURF_AP1_SWP_32BPP;
	break;
    }
    OUTREG(RADEON_SURFACE_CNTL, swapper);
#endif

    src += (x * bpp / 8) + (y * src_pitch);
    w *= bpp / 8;

    while (h--) {
	memcpy(dst, src, w);
	src += src_pitch;
	dst += dst_pitch;
    }

#if X_BYTE_ORDER == X_BIG_ENDIAN
    /* restore byte swapping */
    OUTREG(RADEON_SURFACE_CNTL, info->ModeReg.surface_cntl);
#endif

    return TRUE;
}

Bool FUNC_NAME(RADEONDrawInit)(ScreenPtr pScreen)
{
    RINFO_FROM_SCREEN(pScreen);

    if (info->exa == NULL) {
	xf86DrvMsg(pScreen->myNum, X_ERROR, "Memory map not set up\n");
	return FALSE;
    }

    info->exa->exa_major = 2;
    info->exa->exa_minor = 0;

    info->exa->PrepareSolid = FUNC_NAME(RADEONPrepareSolid);
    info->exa->Solid = FUNC_NAME(RADEONSolid);
    info->exa->DoneSolid = FUNC_NAME(RADEONDoneSolid);

    info->exa->PrepareCopy = FUNC_NAME(RADEONPrepareCopy);
    info->exa->Copy = FUNC_NAME(RADEONCopy);
    info->exa->DoneCopy = FUNC_NAME(RADEONDoneCopy);

    info->exa->WaitMarker = FUNC_NAME(RADEONSync);
    info->exa->UploadToScreen = FUNC_NAME(RADEONUploadToScreen);
    info->exa->DownloadFromScreen = FUNC_NAME(RADEONDownloadFromScreen);

#if X_BYTE_ORDER == X_BIG_ENDIAN
    info->exa->PrepareAccess = RADEONPrepareAccess;
    info->exa->FinishAccess = RADEONFinishAccess;
#endif /* X_BYTE_ORDER == X_BIG_ENDIAN */

    info->exa->flags = EXA_OFFSCREEN_PIXMAPS;
    info->exa->pixmapOffsetAlign = RADEON_BUFFER_ALIGN + 1;
    info->exa->pixmapPitchAlign = 64;

    info->exa->maxX = 2047;
    info->exa->maxY = 2047;

#ifdef RENDER
    if (info->RenderAccel) {
	if (info->ChipFamily >= CHIP_FAMILY_R300) {
	    xf86DrvMsg(pScrn->scrnIndex, X_INFO, "Render acceleration "
			       "unsupported on R300 type cards and newer.\n");
	} else if ((info->ChipFamily == CHIP_FAMILY_RV250) || 
		   (info->ChipFamily == CHIP_FAMILY_RV280) || 
		   (info->ChipFamily == CHIP_FAMILY_RS300) || 
		   (info->ChipFamily == CHIP_FAMILY_R200)) {
		xf86DrvMsg(pScrn->scrnIndex, X_INFO, "Render acceleration "
			       "enabled for R200 type cards.\n");
		info->exa->CheckComposite = R200CheckComposite;
		info->exa->PrepareComposite =
		    FUNC_NAME(R200PrepareComposite);
		info->exa->Composite = FUNC_NAME(RadeonComposite);
		info->exa->DoneComposite = RadeonDoneComposite;
	} else {
		xf86DrvMsg(pScrn->scrnIndex, X_INFO, "Render acceleration "
			       "enabled for R100 type cards.\n");
		info->exa->CheckComposite = R100CheckComposite;
		info->exa->PrepareComposite =
		    FUNC_NAME(R100PrepareComposite);
		info->exa->Composite = FUNC_NAME(RadeonComposite);
		info->exa->DoneComposite = RadeonDoneComposite;
	}
    }
#endif

    RADEONEngineInit(pScrn);

    if (!exaDriverInit(pScreen, info->exa)) {
	xfree(info->exa);
	return FALSE;
    }
    exaMarkSync(pScreen);

    return TRUE;
}

#undef FUNC_NAME

```


im not sure if i got these files from the right place but they were the only src/(filename) i could find using the locate command. i am running edgy

---

### Post by dmjones500 on 2006-12-11
> hey for that last post, could you provide more specific directions please?

I had the same problem.  I made a few changes to my source code, and it now compiles ok.  But then I realised I already had xserver-xorg-video-ati installed, which conflicts with this package.

Anyway, I've attached a patch file that should do the trick. Uncompress the archive, navigate to the src/ directory, and run the following command:

```
patch -p1 -i myfix.patch
```

Note: having decided not to install this package, I'm not sure my changes result in a working driver set up.  I just got it compiling...

---

### Post by mirr0r on 2006-12-13
[QUOTE=dmjones500;1873440

Note: having decided not to install this package, I'm not sure my changes result in a working driver set up.  I just got it compiling...[/QUOTE]

this is my output
```
patch unexpectedly ends in middle of line
patch: **** Only garbage was found in the patch input.

```

And I m not able to open your patch by text editor..

Thanks,

MiRr0r

---

### Post by dmjones500 on 2006-12-13
Strange, something seems to have corrupted the file.  I untarred the copy I uploaded and it was garbage for me too...

I've uploaded it with a .txt extension now.

---

### Post by yoav_steinberg on 2006-12-14
Obviously you're not looking at the correct radeon_exa.c and radeon_exa_accel.c. If you were, then you should see a card and accel fields which caused the compilation error to begin with.

Please follow the instructions in my previous post and apply them to you're
xf86-video-ati-6.5.8.0/src/radeon_exa.c and xf86-video-ati-6.5.8.0/src/radeon_exa_funcs.c.

If you followed the instructions for installing this driver (as described in the beginning of this forum) you should have these files after untaring xf86-video-ati-6.5.8.0.tar.bz2 and applying xorg7-6.5.8.0-tv_output.patch.gz.

---

### Post by RedRedKrovy on 2006-12-30
Does anyone know if this works with an ATI Rage Mobility 128?  I have a PowerBook "Pismo" I am trying to get the tv out to work on.  I'm not having any luck.  I followed the HowTo to the T.  I don't know wether it's not working because I'm using a powerpc arch or because I'm screwing something up.  Everthing installed ok with no errors, the only thing I noticed is that when I went into the config.log I found a line that said

configure:20511: checking whether to include TV Out support
configure:20513: result: no

Any help would be great.

---

### Post by Naranek on 2007-01-06
I just updated to Edgy and tried patching according to PooBaa's instructions. Everything seems to go well, but my computer hangs completely when starting xorg. I can't find any errors on xorg.0.log or messages log. Any ideas what to try next? Is there any chance I should be using different files from the ones in the guide? My card is Radeon 7200 VIVO

---

### Post by WilliamAnderson on 2007-01-16
Hi all,

First I want to say what fantastic instructions you gave. Thank you for creating this post and providing this information. I had no trouble following them and successfuly downloaded, patched, compiled, installed, and configured TV out following these instructions. I encountered no errors or warnings as I did this. However, it did not work. After chasing down a faulty TV in plug on one TV, I get nothing on the TV screen after X starts.

Contrary to the list of supported cards at the Gatos site, the patch supplied does not touch the r128 driver source files. It does not enable TV out for these cards. If your card is not a Radeon, it will not work. However, the TV Out on my Rage 128 pro card does work until the frame buffer is enabled (Ubuntu splash screen) and/or until the X server starts. 

When I find a way to enable TV out I will come back and post how I was able to make it work.

William

---

### Post by CyberCod on 2007-01-19
First off, I appreciate the hard work that has gone into this guide... but at its current state i find it nearly unusable.

Would anyone mind posting a revised and complete set of instructions?  Trying to find my way through all this muck is more likely to break my system than fix it.

I did try, and got to "make"  and it was missing packages.  Tried to install the suggested packages from a few posts ago and all but two were installed and those two were unavailable.

So.

Someone.

Please.

Re-write this.


(soon?)

---

### Post by dlg on 2007-01-21
> **CyberCod said:**
> 
So.

Someone.

Please.

Re-write this.


(soon?)



Right.  For edgy, it's just a little bit of the original post, and a little bit of  [PooBaa's post](http://ubuntuforums.org/showpost.php?p=1703492&postcount=22).  Once you've got the driver installed, the original howto is all you need.

[SIZE="4"]install driver[/SIZE]
[LIST=1]
[*]**install packages**
[HTML]
sudo apt-get install build-essential libdrm-dev mesa-common-dev \
render-dev x11proto-core-dev x11proto-fonts-dev x11proto-gl-dev \
x11proto-randr-dev x11proto-video-dev x11proto-xext-dev \
x11proto-xf86dri-dev x11proto-xf86misc-dev x11proto-xinerama-dev \
xserver-xorg-dev pkg-config[/HTML]

[*]**get the driver**
[HTML]
mkdir ~/ati
cd ~/ati
wget http://megahurts.dk/rune/stuff/xorg7.1-6.6.3-tv_output.patch.gz
wget http://xorg.freedesktop.org/releases/individual/driver/xf86-video-ati-6.6.3.tar.bz2[/HTML]

[*]**patch the driver**
[HTML]
tar xjvf xf86-video-ati-6.6.3.tar.bz2
gunzip -c xorg7.1-6.6.3-tv_output.patch.gz | patch -p1 -d xf86-video-ati-6.6.3[/HTML]

[*]**configure, build and install the driver**
[HTML]
cd xf86-video-ati-6.6.3
export XORG_PREFIX="/usr"
export XORG_CONFIG="--prefix=$XORG_PREFIX --sysconfdir=/etc --localstatedir=/var"
./configure $XORG_CONFIG --with-xorg-module-dir=$XORG_PREFIX/lib/xorg/modules
make
sudo make install[/HTML]
[/LIST]


[SIZE="4"]tweak xorg.conf[/SIZE]
add the bits in bold

```

Section "Device" 
    Identifier "ATI Technologies, Inc. Radeon RV100 QY [Radeon 7000/VE]" 
    **Driver "ati" **
    BusID "PCI:1:0:0" 
    **Option "TVOutput" "NTSC"**
EndSection
```

```

Section "Monitor"
    Identifier "SyncMaster"
    [b]HorizSync 30 - 50
    VertRefresh 60 - 60[/b]
    Option "DPMS"
EndSection
```

```

Section "Screen"
    Identifier "Default Screen"
    Device "ATI Technologies, Inc. Radeon RV100 QY [Radeon 7000/VE]" 
    Monitor "SyncMaster" 
    [b]DefaultDepth 24 
    SubSection "Display" 
        Depth 24 
        Modes "800x600" 
    EndSubSection [/b]
EndSection
```


if you want explanations about why you do any of this, read the original howto.  it really is quite good.



**update, 13 august 2007, for 7.04 support**
[LIST=1]
[*]add "pkg-config" to the long list of packages to install
[*]make sure the Driver is "ati" and not "vesa" in xorg.conf.  i've bolded it to make sure you don't miss it.
[/LIST]


everything else seems to be okay.

---

### Post by dlg on 2007-01-21
and now, I have a question.

This works very well, with one notable problem: the picture on the tv is shifted up and to the right about an inch.

Anybody know how to fix this?  I'd like to be able to see the top and right edges of the display.

---

### Post by CyberCod on 2007-01-21
Man, I just wanna say...

YOU ARE PHREAKING BEAUTIFUL!

It's working, now after two days of trying to get different things to work, its working fine.  No cursor artifacts, no gamma, no nada.  All is well.  

I am experiencing the offset picture like the above post mentions, but I can live with that.  If you can give a tip to fix that, even better.  But just so you know, YOU HAVE MADE MY DAY.

---

### Post by CyberCod on 2007-02-02
dlg, I have posted your revised HOW-TO as a wiki article.  It can be found at 
[http://wiki.cchtml.com/index.php/Tvout#Configuration]("http://wiki.cchtml.com/index.php/Tvout#Configuration")

Perhaps if you find time, you may go and check it out and make sure I made no mistakes in my posting.

Thanx again.

---

### Post by jkwarras on 2007-02-11
> **RedRedKrovy said:**
> Does anyone know if this works with an ATI Rage Mobility 128?  I have a PowerBook "Pismo" I am trying to get the tv out to work on.  I'm not having any luck.  I followed the HowTo to the T.  I don't know wether it's not working because I'm using a powerpc arch or because I'm screwing something up.  Everthing installed ok with no errors, the only thing I noticed is that when I went into the config.log I found a line that said

configure:20511: checking whether to include TV Out support
configure:20513: result: no

Any help would be great.

I have the same problem. The patch install anyway but when I use the Option TVoutput in the xorg the PC hangs and I have to hard reboot. If I disable this option the radeon driver works fine.

The tv theatre module is loaded, I've looked in the Xorg.0.log file, but there's a problem since the file doesn't end as usual, it seems that something is preventing the driver to load when TVoutput option.

I have a X700 ATI radeon (medion PC). I've used the instructions posted by dlg.

Any ideas?

---

### Post by Marktrix on 2007-02-15
:D Yes, first time i saw my screen on the TV Monitor!

But i have two Problems.

First I am using CRT + TV and the CRT is on 800X600 with 60 Hz how to fix?

Second when i am starting a movie for example with the VLC Player the TV
turns into real deep green, the CRT shut down and i can do nothing more.

Any Suggestions?

Greetings Marktrix

---

### Post by CyberCod on 2007-02-15
Don't quote me on this, but i think that 800x600 60hz is what it has to be in order for the TVout to function.  As far as the deep green screen, I dunno.  Perhaps something to do with your overlay settings?  but thats just a guess.

---

### Post by yu_raider on 2007-02-18
Hi! Is this driver used for TV-out only, or it can enable 3D acceleration?

---

### Post by 00Kell on 2007-03-23
Hi,

I am trying to enable the TV out on an ATI Rage 128 under kubuntu 6.06.1 and Xorg.  As anyone actually managed to get this to work?  I have seen a lot of people on the internet ask but no-one seems to have found an answer yet.  The TV-out has worked with XFree86 so I had hoped that the GATOS fix from this thread would solve my problems but it hasn't.

I have reached the point where I want to pull my hair out! ](*,) 

**The problem:**
TV out (PAL) on an ATI Rage 128 does not work under kubuntu 6.06.1 and Xorg.  TV-out does work during the bios boot sequence but stops as soon as ubuntu starts to load.

**What I have done:**

[LIST=1]

[*]Tried ever resolution setting and display frequency available to me under system settings -> display (KDE desktop).
[*]Tried every possible xorg.conf combination that I could find and think of.
[*]Followed the GATOS installation instructions in this thread.  Then repeated the above.
[/LIST]

Things that I have learned:

**800x600**

All I should need to do is set my display resolution to 800x600 and the TV out on my card should fire up and display my desktop on my TV.

Many people on the net have used modelines to set display conditions for PAL or NTSC and they have set appropriate display frequencies.  I have tried this (didn't work) but I am not trying to drive the TV from the VGA out of my graphics card using a VGA to scart adapter.  I am just trying to get the TV out function of my card to work using composite or s-video...

**GATOS**

I had the same installation problem for GATOS as other people had on page two of this thread e.g.:

No package 'xproto' found
No package 'fontsproto' found
No package 'randrproto' found

At first I tried compiling and installing pkg-config but then discovered that it was already installed and just had to type:

export PKG_CONFIG_PATH="/usr/lib/pkgconfig"

**What am I missing?**

Is there something that I am missing?  Something that I really should have done but haven't?  It seems like this should be a very simple problem to solve - especially now that I have GATOS installed.

Any questions and comments will be gratefully received.

Thanks

---

### Post by YAFU on 2007-03-27
Hello. Can somebody please post the complete working xorg.conf file?. Thanks.

---

### Post by 00Kell on 2007-03-27
I would if I thought that I had one that worked!  Sorry. :(

---

### Post by thor4ooo on 2007-04-01
Any luck 00Kell? I just encountered this same problem, same card. Very strange. The weird thing is, I tried to install kubuntu with the TV as the monitor. I see the bios load and then the kubuntu splash screen appears. After a few seconds the signal disappears. The same type of thing hapens with ubuntu and OpenSuse. Do we just have crappy cards?

Cheers,
Thorarin Bjarnason

---

### Post by 00Kell on 2007-04-02
Unfortunately not.

I've been too busy lately to follow this up in other forums but do plan to.  If you learn the secret then please let me know!  I've been thinking that it isn't worth me wasting any more time on and that I should buy a cheap Nvidia card on ebay.  Still, I don't really have the money to spend right now... :(

---

### Post by thor4ooo on 2007-04-03
Thanks for the reply 00Kell,

I have given up on the ATI card <and I have 2 of them :( >. Numerous forums have indicated that older ATI cards have poor drivers <from a TV standpoint> and there is no intension on improving them. I'm looking for an nvida card as well.

Cheers,
Thorarin Bjarnason

---

### Post by sebos69 on 2007-04-09
Hi, and big thanks for the tip. I am running feisty fawn, so the drivers versions for gatos do not match with this how-to however, this one : 

[http://wiki.cchtml.com/index.php/Tvout](http://wiki.cchtml.com/index.php/Tvout)

uses the latest radeon drivers to compile a tv-out capable driver. It works fine here.

Moreover, I had some issues (like others did in previous threads) with black borders around the screen, but there is actually a small and convenient utility provided in the patched driver :  you need to compile the tvo_set utility (see README.tvout in the SRC folder, section 5) which helps a lot solving overscan issues etc...

(for the record, I have a Radeon 9200 SE)

---

### Post by Yossarian on 2007-04-20
I am using Feisty and trying to setup TV out on a radeon 7200 (r100).  I'm gonna give the guide from the last post a shot.

---

### Post by jkwarras on 2007-04-22
I'm running Feisty. I've followed the last guide posted here, but when I get into a 800x600 resolution the monitor gets out of range, and display a 'non supported mode' message. Trying to force a particular range in xorg.conf (60 or 50Hz) doesn't work either. If I disable EDID info, it brings a corrupted display on the monitor, but still TVoutput (PAL) remains blank. I've tried both with DVI and VGA plug. TV is attached via S-Video.

I've checked the Xorg.0.log and it seems that theather out is working via TVoutput PAL option.

Any idea?

---

### Post by Yossarian on 2007-04-22
This is a follow-up to my last post.

My TV is setup as a second monitor.  It works except for a few problems:

- New windows usually open on the TV.  I don't want this, as I will not always have the TV on.  I'm guessing there's some sort of GNOME setting to fix this
- If I fullscreen VLC it opens the fullsceen on the monitor, even if VLC was running on the TV.  Totem doesn't do this, so I'm guessing I'll have to play with VLCs settings somehow
- The screen resolution utility from the top menu shows an error saying "The X Server does not support the XRandR extension.  Runtime resolution changes to the display size are not available."  I don't really care, but I imagine the fix is just to renable whatever XRandR is in my config file.

I'll post a followup if I manage to fix any of the problems.  Here's my xorg.conf if anyone wants an example of TV out or multi-monitor (or both).  The files comments are sparse, and I was a little lame with the naming ("Screen 1", "Screen 2", etc).  To use the below config file you must have patched the 'ati' driver as per the guide in this thread.  Otherwise the TVout option will do nothing.

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
	Load	"i2c"
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
	Option		"XkbLayout"	"us"
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
	Identifier	"Intel Corporation 82810E DC-133 CGC [Chipset Graphics Controller]"
	Driver		"i810"
	BusID		"PCI:0:1:0"
EndSection

Section "Device"
	Identifier	"Radeon 7200"
	Driver		"ati"
	BusID		"PCI:1:8:0"
	Option "TVOutput" "NTSC"    #<---------Important line here
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Monitor" 
   	 Identifier "Television" 
    	HorizSync 30 - 50           #<---------Important line here
    	VertRefresh 60 - 60         #<---------Important line here
    	Option "DPMS" 
EndSection

# Main screen: Intel video card with a CRT monitor
Section "Screen"
	Identifier	"Screen 1"
	Device		"Intel Corporation 82810E DC-133 CGC [Chipset Graphics Controller]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

# Auxilary screen with a radeon 7200 video card and a television
Section "Screen" 
    Identifier "Screen 2" 
    Device "Radeon 7200" 
    Monitor "Television" 
    DefaultDepth 24             #<---------Important line here
    SubSection "Display"        #<---------Important line here
         Depth 24               #<---------Important line here
         Modes "800x600"        #<---------Important line here
    EndSubSection               #<---------Important line here
 EndSection

# Serverlayout uses both screens
Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Screen 1"
	Screen		"Screen 2" RightOf "Screen 1"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	Option          "Xinerama"      "on"
	Option "Clone" "off"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

---

### Post by dread45153 on 2007-04-22
Thank you to all of you who have been working on this.  I have a Rage 128 PRO All-In-Wonder.  I installed GATOS, and could only get an occasional blur on the screen.  I know that the card and wiring is correct because the BIOS boot up screen is displayed on the TV.  I followed the steps on this forum, including the updated version for Edgy, but is still does not work.  I installed AtiTVOut, and it says that the TV is connected and working, but I can't get anything to display on it.  

I tried to install the ATI drivers that are explained on [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide) .  After I installed this, X would not load, but the text based loggin screen was displayed on both the TV and my CRT.  Any advice?


Thanks

---

### Post by Yossarian on 2007-04-25
> Originally posted by **dread45153**
Thank you to all of you who have been working on this. I have a Rage 128 PRO All-In-Wonder. I installed GATOS, and could only get an occasional blur on the screen. I know that the card and wiring is correct because the BIOS boot up screen is displayed on the TV. I followed the steps on this forum, including the updated version for Edgy, but is still does not work. I installed AtiTVOut, and it says that the TV is connected and working, but I can't get anything to display on it. 

I tried to install the ATI drivers that are explained on [http://wiki.cchtml.com/index.php/Ubu...allation_Guide](http://wiki.cchtml.com/index.php/Ubu...allation_Guide) . After I installed this, X would not load, but the text based loggin screen was displayed on both the TV and my CRT. Any advice?


Thanks

It seems like your driver is patched correctly, but your X config is broken.  

I would backup your old X config```
 sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.BACKUP
``` to a file called xorg.conf.BACKUP, and then run ```
sudo dpkg-reconfigure xserver-xorg
``` to reset your X config to something that works.  If your monitor works correctly after this, but your TV does not, manually edit xorg.conf again and switch it to use the driver you patched.

---

### Post by jkwarras on 2007-05-10
> **jkwarras said:**
> I'm running Feisty. I've followed the last guide posted here, but when I get into a 800x600 resolution the monitor gets out of range, and display a 'non supported mode' message. Trying to force a particular range in xorg.conf (60 or 50Hz) doesn't work either. If I disable EDID info, it brings a corrupted display on the monitor, but still TVoutput (PAL) remains blank. I've tried both with DVI and VGA plug. TV is attached via S-Video.

I've checked the Xorg.0.log and it seems that theather out is working via TVoutput PAL option.

Any idea?

I see in the [gatos]("http://gatos.sourceforge.net/theater_out.php") site that

> Theater_out only works on cards having a 27 MHz reference frequency. All the radeon cards I had a chance to examine have this frequency, so this limitation should not be an issue.

That's exactly what I get on my LCD monitor "non supported mode" for a range of "H: 24.9 Hz // V: 22.1 Hz", which makes me think that the monitor is trying to display a 27 MHz range and for some reason it doesn't support it. Any ideas how to solve this? I mean, avoid the monitor to get out of range. Other modes like 640x480 works.

Thanks.

---

### Post by fergal on 2007-05-30
I found that the simplest way to get my tv-out working again with 7.04 was to switch to the vesa X-driver. I only tried this after trying a few other options, including getting the GATOS patch to apply and compile with xorg 7.2.0! I blogged the details at [http://wargle.blogspot.com/2007/05/solution-to-ati-9100-igp-tv-out-with.html]("http://wargle.blogspot.com/2007/05/solution-to-ati-9100-igp-tv-out-with.html"). It even gave me a significant improvement in CPU usage when playing video (xv mode was busted for me on the old ATI drivers).

Hope this helps someone.

---

### Post by Pawel on 2007-06-01
Hi!

What about patches for xorg 7.2 //fiesty// form gatos ?

Is there available ? where we cand find them ?

PooBa - where did you find pathes for xorg 7.1 ? On official site i can't find link for those pathes.

Best ragards
Pawel

---

### Post by sebos69 on 2007-06-01
> **Pawel said:**
> Hi!

What about patches for xorg 7.2 //fiesty// form gatos ?

Is there available ? where we cand find them ?

PooBa - where did you find pathes for xorg 7.1 ? On official site i can't find link for those pathes.

Best ragards
Pawel

already mentionned:

[http://wiki.cchtml.com/index.php/Tvout](http://wiki.cchtml.com/index.php/Tvout)

---

### Post by se2131 on 2007-06-02
**EDIT**: After looking back through the thread some more, I realized I should've looked at [http://wiki.cchtml.com/index.php/Tvout](http://wiki.cchtml.com/index.php/Tvout) more closely, I completely forgot that the versions of the patch and driver should match up (stupid me).  Anyway, now I'm not getting the Option TVOutput error, but I haven't been able to try it out yet.  I'll update tomorrow

I followed the HOW-TO (except I used **xf86-video-ati-6.6.192** and **xorg7-6.5.8.0-tv_output**), and everything seemed to work from this side, no error messages or anything.  However, I don't see any activity at all on my TV screen.  It may be because I don't know how to actually activate the TV-OUT function, I've tried atitvout and that didn't seem to work (e.g. "sudo atitvout ntsc" or "sudo atitvout lct").  I've also tried having the TV connected before starting or restarting X.  What do I need to do in order to actually activate the TV-OUT functionallity?  I have a Toshiba A75, w/ an ATI Radeon 9100 IGP card.

Also, I see this line in my Xorg.0.log file: (I can put the entire output if it'll help)

```

(WW) RADEON(0): Option "TVOutput" is not used

```

Here's my xorg.conf file

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
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
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
	Option		"HorizEdgeScroll"	"1"
	Option		"MaxSpeed"		"0.6"
	Option		"AccelFactor"		"0.04"
EndSection

#Section "InputDevice"
#	Driver		"wacom"
#	Identifier	"stylus"
#	Option		"Device"	"/dev/input/wacom"
#	Option		"Type"		"stylus"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
#EndSection

#Section "InputDevice"
#	Driver		"wacom"
#	Identifier	"eraser"
#	Option		"Device"	"/dev/input/wacom"
#	Option		"Type"		"eraser"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
#EndSection

#Section "InputDevice"
#	Driver		"wacom"
#	Identifier	"cursor"
#	Option		"Device"	"/dev/input/wacom"
#	Option		"Type"		"cursor"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
#EndSection

Section "Device"
	Identifier	"ATI RADEON 9100"
	Driver		"ati"
	BusID		"PCI:1:5:0"
	Option		"TVOutput"	"NTSC"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Monitor"
	Identifier	"Television"
	HorizSync 	30 - 50
	VertRefresh	60 - 60
	Option 		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI RADEON 9100"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800" "1280x768" "1200x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800" "1280x768" "1200x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800" "1280x768" "1200x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800" "1280x768" "1200x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800" "1280x768" "1200x800" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800" "1280x768" "1200x800" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier	"Television Screen"
	Device 		"ATI RADEON 9100"
	Monitor		"Television"
	DefaultDepth	24
	SubSection	"Display"
		Depth	24
		Modes	"800x600"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	Screen		"Television Screen" RightOf "Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection


```

---

### Post by se2131 on 2007-06-02
So I tried it and I still don't see any activity at all on the TV.  Any ideas as to what I should do? (see previous post)

---

### Post by Pawel on 2007-06-04
> **sebos69 said:**
> already mentionned:

[http://wiki.cchtml.com/index.php/Tvout](http://wiki.cchtml.com/index.php/Tvout)
Hello!

Yes, but what about xorg 7.2 and ubuntu 7.04 ? Is there any other official gatos projct site where we can find some information  e.g. about new patch release. 

=================

Note: I noticed that patches for xorg 7.1  (Ubuntu 6.10) should works on xorg 7.2 (Ubuntu 7.04). ati-drivers are the same in xorg repsitory :)
Best regards
Pawel

---

### Post by se2131 on 2007-06-05
So does anybody have any ideas on what I'm doing wrong?  I've installed the 6.6.3 driver and patch w/ no error messages.  My xorg.conf is given a couple of posts above.

This is **literally** the only thing that is keeping me from uninstalling windows from my computer (dual-boot right now).  Thanks in advance for any ideas you may have.

---

### Post by jkwarras on 2007-06-05
> **se2131 said:**
> So does anybody have any ideas on what I'm doing wrong?  I've installed the 6.6.3 driver and patch w/ no error messages.  My xorg.conf is given a couple of posts above.

Try using the monitor layout option as mentioned here:
[http://megahurts.dk/rune/tv_output.html](http://megahurts.dk/rune/tv_output.html)

---

### Post by se2131 on 2007-06-05
Thanks for the response jkwarras.  I added the line

```
 Option "MonitorLayout" "AUTO, NONE" 
```

to my Device section, restarted and still no activity unfortunately.  I then saw that there may be problems w/ LCD screens, so I followed the instructions on that same page for that, namely adding the following lines to xorg.conf and commenting out the appropriate lines:

```

"Device" section:
	Option     "IgnoreEDID" "true"

"Monitor" section:
        HorizSync    30.0 - 40.0
        VertRefresh  60

```

And still nothing unfortunately

---

### Post by jkwarras on 2007-06-07
> **se2131 said:**
> 
to my Device section, restarted and still no activity unfortunately.  I then saw that there may be problems w/ LCD screens, so I followed the instructions on that same page for that, namely adding the following lines to xorg.conf and commenting out the appropriate lines:


You could try to plug the LCD via standard VGA. But I have also done this and when I switch to 800x600 to get tv-out the monitor gets out of range. See if this work for you.

---

### Post by erik.teichmann on 2007-06-13
Ugh. I am so frustrated by this. I would never have upgraded to Fiesty if I had known about the dead fglrx. I have a Thinkpad R51 with the M9000 and I use it exclusively hooked up to the TV. Therefore, this is a big issue for me. I really don't want to have to reinstall edgy from the CD. 
Here's what I've got so far. I'm running Fiesty. I've managed to download the driver and patch as described at [http://wiki.cchtml.com/index.php/Tvout](http://wiki.cchtml.com/index.php/Tvout)
After much mucking about, I got ./configure working. Now I'm getting this error on make
```

gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/xorg -I/usr/include/drm -I/usr/include/X11/dri -g -O2 -MT r128_accel.lo -MD -MP -MF .deps/r128_accel.Tpo -c r128_accel.c  -fPIC -DPIC -o .libs/r128_accel.o
r128_accel.c: In function 'R128CCEWaitForIdle':
r128_accel.c:247: error: 'errno' undeclared (first use in this function)
r128_accel.c:247: error: (Each undeclared identifier is reported only once
r128_accel.c:247: error: for each function it appears in.)
r128_accel.c:247: error: 'EBUSY' undeclared (first use in this function)
r128_accel.c: In function 'R128CCEStop':
r128_accel.c:286: error: 'errno' undeclared (first use in this function)
r128_accel.c:286: error: 'EBUSY' undeclared (first use in this function)
r128_accel.c: In function 'R128CCEGetBuffer':
r128_accel.c:1573: error: 'EAGAIN' undeclared (first use in this function)
make[2]: *** [r128_accel.lo] Error 1
make[2]: Leaving directory `/home/erik/downloads/gatos/xf86-video-ati-6.5.8.0/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/erik/downloads/gatos/xf86-video-ati-6.5.8.0'
make: *** [all] Error 2

```
Anybody have any ideas? I'd really like to have this working, we don't have cable!

---

### Post by erik.teichmann on 2007-06-14
Dealbreaker. I think I'll have to go back to edgy tonight.

---

### Post by sebos69 on 2007-06-14
> **erik.teichmann said:**
> Ugh. I am so frustrated by this. I would never have upgraded to Fiesty if I had known about the dead fglrx. I have a Thinkpad R51 with the M9000 and I use it exclusively hooked up to the TV. Therefore, this is a big issue for me. I really don't want to have to reinstall edgy from the CD. 
Here's what I've got so far. I'm running Fiesty. I've managed to download the driver and patch as described at [http://wiki.cchtml.com/index.php/Tvout](http://wiki.cchtml.com/index.php/Tvout)
After much mucking about, I got ./configure working. Now I'm getting this error on make
```

gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/xorg -I/usr/include/drm -I/usr/include/X11/dri -g -O2 -MT r128_accel.lo -MD -MP -MF .deps/r128_accel.Tpo -c r128_accel.c  -fPIC -DPIC -o .libs/r128_accel.o
r128_accel.c: In function 'R128CCEWaitForIdle':
r128_accel.c:247: error: 'errno' undeclared (first use in this function)
r128_accel.c:247: error: (Each undeclared identifier is reported only once
r128_accel.c:247: error: for each function it appears in.)
r128_accel.c:247: error: 'EBUSY' undeclared (first use in this function)
r128_accel.c: In function 'R128CCEStop':
r128_accel.c:286: error: 'errno' undeclared (first use in this function)
r128_accel.c:286: error: 'EBUSY' undeclared (first use in this function)
r128_accel.c: In function 'R128CCEGetBuffer':
r128_accel.c:1573: error: 'EAGAIN' undeclared (first use in this function)
make[2]: *** [r128_accel.lo] Error 1
make[2]: Leaving directory `/home/erik/downloads/gatos/xf86-video-ati-6.5.8.0/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/erik/downloads/gatos/xf86-video-ati-6.5.8.0'
make: *** [all] Error 2

```
Anybody have any ideas? I'd really like to have this working, we don't have cable!

I guess you did not exactly follow the howto as it suggests to compile the 6.6.3. version of the driver, and not the 6.5.8....

good luck

---

### Post by bigblop on 2007-06-25
I have followed the updated guide at this link:

[http://wiki.cchtml.com/index.php/Tvout](http://wiki.cchtml.com/index.php/Tvout)

When I connect the tvout to my tv I just get a lot of flickering, but I can see that the background changes when the desktop appears. This is my xorg.conf:

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
	Option		"XkbLayout"	"dk"
	Option		"XkbOptions"	"lv3:ralt_switch"
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
	Identifier	"Generic Video Card"
	Driver		"ati"
	BusID		"PCI:1:0:0"
    	Option "TVOutput" "PAL" #add
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	#HorizSync	28-33
	#VertRefresh	43-72
	HorizSync 30 - 50 #add
    	VertRefresh 60 - 60 #add
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		#Depth		1
        	Depth 24 		#add
		#Modes		"1400x1050" "1024x768" "800x600" "640x480"
		Modes		"800x600"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1400x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1400x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1400x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1400x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1400x1050" "1024x768" "800x600" "640x480"
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

any ideas?

---

### Post by sebos69 on 2007-06-25
> **bigblop said:**
> I have followed the updated guide at this link:

[http://wiki.cchtml.com/index.php/Tvout](http://wiki.cchtml.com/index.php/Tvout)

When I connect the tvout to my tv I just get a lot of flickering, but I can see that the background changes when the desktop appears. This is my xorg.conf:

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
	Option		"XkbLayout"	"dk"
	Option		"XkbOptions"	"lv3:ralt_switch"
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
	Identifier	"Generic Video Card"
	Driver		"ati"
	BusID		"PCI:1:0:0"
    	Option "TVOutput" "PAL" #add
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	#HorizSync	28-33
	#VertRefresh	43-72
	HorizSync 30 - 50 #add
    	VertRefresh 60 - 60 #add
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		#Depth		1
        	Depth 24 		#add
		#Modes		"1400x1050" "1024x768" "800x600" "640x480"
		Modes		"800x600"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1400x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1400x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1400x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1400x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1400x1050" "1024x768" "800x600" "640x480"
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

any ideas?

Maybe you should remove those three lines:
	
        SubSection "Display"
		Depth		24
		Modes		"1400x1050" "1024x768" "800x600" "640x480"
	EndSubSection

because they may override the modifications you made :
	#Depth		1
        	Depth 24 		#add
		#Modes		"1400x1050" "1024x768" "800x600" "640x480"
		Modes		"800x600"

---

### Post by bigblop on 2007-06-25
I have tried to outcomment all the below lines, but the screen still flickers.

```

SubSection "Display"
		Depth		4
		Modes		"1400x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1400x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1400x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1400x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1400x1050" "1024x768" "800x600" "640x480"
	EndSubSection

```

??

---

### Post by sebos69 on 2007-06-25
> **bigblop said:**
> I have tried to outcomment all the below lines, but the screen still flickers.

```

SubSection "Display"
		Depth		4
		Modes		"1400x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1400x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1400x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1400x1050" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1400x1050" "1024x768" "800x600" "640x480"
	EndSubSection

```

??
Have you tried to tweak the "MonitorLayout" option (see first post of the thread, section "End Notes" ?

Otherwise, I don't have other clues..

---

### Post by sebos69 on 2007-06-25
You can also try in the "device" section to add:

Option     "IgnoreEDID" "true"

---

### Post by hito1 on 2007-07-10
I'm using the gatos package from synaptic + the xorg options described in the first post, my TV shows the boot process fine until the GDM login screen, when it becomes all distorted, like a blocked cable chanel or something like that.

Could it be something with the HorizSync and VertRefresh options?

---

### Post by Ryoushi19 on 2007-07-30
Ew.  All this did was make my resolution max out at 800x600.  The TV doesn't even work.

---

### Post by vintagevalves on 2007-08-06
I'm stuck where it seems most of the other recent posters are.  I've tried several of the 'latest' GATOS TV out drivers.  They work find with just the laptop LCD, but when I add the TV output section to my xorg.conf the TV display is completely garbled, and the laptop LCD display is garbled into vertical columns, but still readable.   Hopefully now that the code has been relicensed under MIT, development will continue.   
I was able to get atitvout functioning properly, however VESA video performance is so poor that you can't even play a youtube video.   Kind of defeats the purpose.  =(

---

### Post by Whoopie on 2007-08-06
Hi,

Alex Deucher added TV-Out support to the xrandr-1.2 version of the OSS radeon.
This means hotplug support via xrandr 1.2 and TV-Out!! That's great.

Keep in mind that this driver needs xorg 1.3 which is only available at Gutsy.

Here the link:
[http://gitweb.freedesktop.org/?p=xorg/driver/xf86-video-ati.git;a=shortlog;h=randr-1.2](http://gitweb.freedesktop.org/?p=xorg/driver/xf86-video-ati.git;a=shortlog;h=randr-1.2)

Best regards,
Whoopie

---

### Post by mstephens on 2007-08-08
Hi just joined here.

After much frustration last week I managed to get TV out working on Ubuntu 7.04 with a Radeon 7500 card.

You need to do **exactly** what it says in the wiki - absolutely no thinking required, just paste the instructions onto your command line and let it get on with it. The only variation I made was I don't have wget (or its hiding somewhere) so I just downloaded the files with Firefox.

The mods to xorg.conf are very important - my advice is to get rid of any other resolutions so that the  card has no option but to go to 800 x 600.
See my posts at

[http://www.linuxquestions.org/questions/showthread.php?t=569272]("http://www.linuxquestions.org/questions/showthread.php?t=569272")

for more info.

I will post my xorg.conf if anyone really wants it.

Only problem I have at the moment is that the TV display is truncated at the RHS by about 2 characters worth of dots but it sits centrally on a 16:9 LCD TV set to 4:3 mode. On the CRT  monitor the image is displaced to the left so that the LHS is just visible but I can see all of the RHS unlike on the TV (and also have a black band to the right of the image). The monitor image is also squashed to almost 16:9 with black bands top and bottom.

Any thoughts ?

Edited to add

Just got a new VGA cable so I can now use LCD TV (which has VGA input) as a" normal"  monitor. Output is now central (sort of) and a whole lot "crisper" than the Svideo output to the same screen (sort of HD if you like) . Still quite a lot of the screen unused  as the 4:3 image doesn't fill the screen vertically

Some more interesting quirks:

tvo_set will stretch the picture horizontally but trying to change the position to get the RHS completed has no effect no matter what you put in. The TV  I am testing on is multistandard (PAL/NTSC) with a VGA input and an Svideo so I am feeding both VGA and Svideo inputs at the moment. tvo_set does not affect the VGA image at all, unless I switch the mode from NTSC to PAL at which point the TV decides that the VGA setting is out of range and won't display anything at all ( but the image on the Svideo input increases in height and still has the RHS cut off)

---

### Post by kansei on 2007-08-10
Followed the guide here: [http://wiki.cchtml.com/index.php/Tvout](http://wiki.cchtml.com/index.php/Tvout)

on an old Dell D600 running feisty with a Radeon 9000. It definitely looks like it wants to output some no good resolution to the tv, though the laptop LCD is restricted to 800x600 now. I'll have to try booting the laptop with the s-video cable already attached to see if that changes something.

---

### Post by dlg on 2007-08-13
> **mstephens said:**
> 
You need to do **exactly** what it says in the wiki - absolutely no thinking required, just paste the instructions onto your command line and let it get on with it. The only variation I made was I don't have wget (or its hiding somewhere) so I just downloaded the files with Firefox.

The mods to xorg.conf are very important - my advice is to get rid of any other resolutions so that the  card has no option but to go to 800 x 600.


Almost exactly everything.  I needed to apt-get install pkg-config.

but that was the only change.  And the bit about modifying xorg.conf being important?  he's right.  that's important.

---

### Post by stafio on 2007-08-26
> This works very well, with one notable problem: the picture on the tv is shifted up and to the right about an inch.

Anybody know how to fix this? I'd like to be able to see the top and right edges of the display.

You need to use the tvo_set  to fix this: [http://wiki.cchtml.com/index.php/Tvout#Utilities]("http://wiki.cchtml.com/index.php/Tvout#Utilities").

I created a simple script to adjust it for me.
```
gedit adjustTVOut
```
```
#!/bin/bash
#
# Small script to adjust TV out position since ATI sucks on Linux

tvo_set set hpos -5
tvo_set set vpos +4
``````

chmod +x adjustTVOut
sudo cp adjustTVOut /usr/bin
```

Play around with the hpos and vpos values to see what works for you. I then set it up so that the script runs automatically on startup.

---

### Post by dlg on 2007-08-26
> **stafio said:**
> I then set it up so that the script runs automatically on startup.

This works great, thanks!

It seems to be a per-session value, though.  Where do you put the shell script so it runs at startup?

---

### Post by stafio on 2007-08-26
If you're using Gnome, I believe you should be able to add it to the Startup Programs within Gnome. Select System > Preferences > Sessions. You should get the sessions dialog open with the Startup Programs tab. Click New, give it a name, and add the path to the script in the Command field. 

That should do the trick.

---

### Post by mstephens on 2007-08-29
Any ideas as to how to get back the missing bit of the RHS of my picture ?

On a VGA connection the whole screen is displayed but using the SVideo connection, the far right part is missing - so you can't see the close button on a maximised window. 

I have tried tvo_set but although I can shift the image to a central position the RHS is still truncated no matter what I do (even if I reduce hsize).  I have reflashed the card BIOS with a couple of different versions ( to try and sort an unrelated issue) and this doesn't make any difference.

---

### Post by sebos69 on 2007-09-06
> **mstephens said:**
> Any ideas as to how to get back the missing bit of the RHS of my picture ?

On a VGA connection the whole screen is displayed but using the SVideo connection, the far right part is missing - so you can't see the close button on a maximised window. 

I have tried tvo_set but although I can shift the image to a central position the RHS is still truncated no matter what I do (even if I reduce hsize).  I have reflashed the card BIOS with a couple of different versions ( to try and sort an unrelated issue) and this doesn't make any difference.

I also had this problem. So I hacked the theater_out.c file in the driver source. I use PAL output, so I had to tweak some values present starting from line number 816. It was pure try-and-error way, but I finally made it. I join my modified theater_out.c for those interested...

---

### Post by dlg on 2007-09-25
> **dlg said:**
> This works great, thanks!

It seems to be a per-session value, though.  Where do you put the shell script so it runs at startup?

Since I'm not using gnome (i'm using ... openbox?  whatever the "Combined Backend Frontend" howto gives you) for my wm, stafio's instructions didn't work.  What you can do, though is add it to the beginning of /etc/gdm/PreSession/Default, just after the #!/bin/sh line

---

### Post by pistaa on 2007-10-03
Hi,

I've been struggling with Feisty 7.04 for few days now, trying to get tv-out to work with my Compaq Evo N600c. The video adapter is ATI Radeon Mobility M6 LY, and I can already get a picture to tv, but it's not quit at its best :)

I've attached my xorg.conf to this, (I've noticed that Option "MonitorLayout" "STV, CRT" seems to be quite important to get any signal out), and for reference here's a screencap of the image that is sent to TV. 

I've tried to change the refresh-rate with no help, and I'm quite new with linux, so I might be missing something simple also. 

Thanks!

---

### Post by mi_sanders on 2007-10-10
> **pistaa said:**
> Hi,

I've been struggling with Feisty 7.04 for few days now, trying to get tv-out to work with my Compaq Evo N600c. The video adapter is ATI Radeon Mobility M6 LY, and I can already get a picture to tv, but it's not quit at its best :)

I've attached my xorg.conf to this, (I've noticed that Option "MonitorLayout" "STV, CRT" seems to be quite important to get any signal out), and for reference here's a screencap of the image that is sent to TV. 

I've tried to change the refresh-rate with no help, and I'm quite new with linux, so I might be missing something simple also. 

Thanks!


Hi,

Did you figure out your problem, I have the same problem, I get something on TV, I guess yours look a bit better, but mine, there are like lines going crazy, you really can not tell what is on, I tried everthing, I just can't change whats on the screen.

Any suggestions?

Thanks,
Mike

---

### Post by dlg on 2007-10-10
> **mi_sanders said:**
> Hi,

Did you figure out your problem, I have the same problem, I get something on TV, I guess yours look a bit better, but mine, there are like lines going crazy, you really can not tell what is on, I tried everthing, I just can't change whats on the screen.

Any suggestions?

Thanks,
Mike

Does it work correctly with just tv-out?  I'm pretty sure this won't work dual-display.

Is the graphics chipset even supported by GATOS?

---

### Post by mi_sanders on 2007-10-11
> **dlg said:**
> Does it work correctly with just tv-out?  I'm pretty sure this won't work dual-display.

Is the graphics chipset even supported by GATOS?

Thanks for your suggestion.

When I change my MonitorLayout to:

        Option          "MonitorLayout" "NONE, CRT"

The TV works perfectly.  I am using a T40 laptop, is there away to get both screen up?  Has anyone done it on a T40, or any laptop I guess?

Btw, I am using this for Mythtv frontend, is there anything about OverLays I should do, I was reading about it, and it was confusing, but they suggest to change it to second monitor and all.

Thanks,
Mike

---

### Post by wildchild on 2007-10-28
Hi

I have a Radeon 8500 QL (AGP) which gives TV-out with the gatos drivers. But whenever I try to play a video or use mythtv, my tv displays a completely green picture. I read in some earlier post in this thread about problem with overlay, but how to fix that? 

I use tv-out with a composite cable with kubuntu (Gutsy Gibbon installed from DVD). Please help!!

TIA

Forgot to mention that using Alex's git-driver for ati does only give a garbled screen.

---

### Post by joemalik on 2007-11-19
Hi!

I just wanted to say that everything works fine here. After months of struggling with different methods to enable TV-OUT (atitvout does crap ;).

I have a ATI Radeon 7200 (European Model) and i'm using Ubuntu 7.10 Gutsy Gibbon, an NEC MultiSync LCD 1760NX (analog) Monitor and S-Video Connection to the TV.

I followed the instructions for Edgy and its all good.
The only beauty problem is that when i go to 800x600 resolution my monitor screen shifts about 2 inches to the lower right corner. I have the same problem on Windows too. Maybe somebody knows how to fix that on Ubuntu.

Thanks for the great HOW-TO.

EDIT: Sorry, not everything is fine. I forgot :) I receive a no signal Message from my monitor on the "splash"? screen (there where i type my usr name and pwd) i have to log in "blind". But then everything works fine.
Here is my xorg.conf
>  # xorg.conf (xorg X Window System server configuration file)
# 
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
# 
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
# sudo dpkg-reconfigure -phigh xserver-xorg
# 
# File edited by xorg-edit v07.08.11 at Sat Nov 10 09:58:25 2007

Section "Module"
	Load "glx"
	Load "GLcore"
	Load "v4l"
EndSection

Section "InputDevice"
	Identifier "Generic Keyboard"
	Driver "kbd"
	Option "CoreKeyboard"
	Option "XkbRules" "xorg"
	Option "XkbModel" "pc105"
	Option "XkbLayout" "de"
	Option "XkbVariant" "nodeadkeys"
EndSection

Section "InputDevice"
	Identifier "Configured Mouse"
	Driver "mouse"
	Option "CorePointer"
	Option "Device" "/dev/input/mice"
	Option "Protocol" "ImPS/2"
	Option "ZAxisMapping" "4 5"
EndSection

Section "Device"
	# Boardname "ATI Radeon 7200"
	Identifier "ATI Technologies, Inc. Radeon R100 (7200)"
	Driver "ati"
	BusID "PCI:1:0:0"
	Option	"TVOutput" "PAL"
EndSection

Section "Monitor"
	# Vendorname "NEC"
	# Modelname "NEC MultiSync LCD1760NX (Analog)"
	Identifier "MultiSync"
	HorizSync 31 - 83
	VertRefresh 56 - 75
 	DisplaySize 344 272
	Gamma 1.0
	Modeline "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
	#[...a lot of Modelines..]
	Modeline "1792x1344@60" 204.8 1792 1920 2120 2448 1344 1345 1348 1394 -hsync +vsync
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device "ATI Technologies, Inc. Radeon R100 (7200)"
	Monitor "MultiSync"
	DefaultDepth 24
	SubSection "Display"
		Depth 24
		Modes "800x600@60"  "1280x1024@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier "Default Layout"
	Screen "Default Screen"
	InputDevice "Generic Keyboard"
	InputDevice "Configured Mouse"
EndSection


---

### Post by joemalik on 2007-11-28
Nobody? Is this Thread just too old? Plz help me with my GDM.

---

### Post by gigahz on 2008-01-06
Hi I run Gutsy 2.6.20-16-generic with a Rage Mobility P/M AGP 2x (rev 64) [1002:4c4d] , X Window System Version 7.2.0 , downloaded the suggested xf86-video-ati-6.5.8.0.tar.bz2 and get to compile, but after a while it stops with:

[...]
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/xorg -I/usr/include/drm -I/usr/include/X11/dri -g -O2 -MT r128_accel.lo -MD -MP -MF .deps/r128_accel.Tpo -c r128_accel.c  -fPIC -DPIC -o .libs/r128_accel.o
r128_accel.c: In function 'R128CCEWaitForIdle':
r128_accel.c:247: error: 'errno' undeclared (first use in this function)
r128_accel.c:247: error: (Each undeclared identifier is reported only once
r128_accel.c:247: error: for each function it appears in.)
r128_accel.c:247: error: 'EBUSY' undeclared (first use in this function)
r128_accel.c: In function 'R128CCEStop':
r128_accel.c:286: error: 'errno' undeclared (first use in this function)
r128_accel.c:286: error: 'EBUSY' undeclared (first use in this function)
r128_accel.c: In function 'R128CCEGetBuffer':
r128_accel.c:1573: error: 'EAGAIN' undeclared (first use in this function)
make[2]: *** [r128_accel.lo] Error 1
make[2]: Leaving directory `/home/arno/atidrivers/xf86-video-ati-6.5.8.0/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/arno/atidrivers/xf86-video-ati-6.5.8.0'
make: *** [all] Error 2

any suggestions?
best
Arno

---

### Post by sebos69 on 2008-01-08
you should try this howto: [http://wiki.cchtml.com/index.php/Tvout](http://wiki.cchtml.com/index.php/Tvout)

this way you will have a more recent driver (6.6.3)

---

### Post by angels on 2008-01-14
Hi, I'm running Gutsy 7.10 with the ATI graphic card Radeon X300, with the S-video connection to the TV.  I followed the instructions mentioned above and everything work out nicely. I saw the picture on the TV, but it is not very clear (maybe because of the refresh rates... I still have to find out). What's bothers me more is that the picture on the TV is black and white. I read on the start of the thread that this is because of the S-video cabel...but throughout the thread I figured out that some of them are using S-video cabel, but no one had reported that the picture is b&w. 

Does anyone experienced that? Do someone of you have an idea how to solve this?
I'd be really happy for your advice

Cheers, Angels

---

### Post by gigahz on 2008-01-15
Hi Thanks, now the driver compiles. However, I get the message "option TVout not used" or something as a (WW) in Xorg.log... Suggestions?

---

### Post by dfoxpro on 2008-01-25
Hi

I'm tried to install GATOS in my pc, but i had a "problem" when i try to make, because i'm a newby i don't understand this lines...:

```
make: *** No se especificó ningún objetivo y no se encontró ningún makefile.  Alto.
```
this mean something like this...:
```
	
Make: *** There is no specified purpose and not found any makefile. Stop
```

Can you help me?
i think because i try to install in a Ubuntu 7.10

(Perdonen mi ingles tan malo...)

---

### Post by sebos69 on 2008-01-28
> **dfoxpro said:**
> Hi

I'm tried to install GATOS in my pc, but i had a "problem" when i try to make, because i'm a newby i don't understand this lines...:

```
make: *** No se especificó ningún objetivo y no se encontró ningún makefile.  Alto.
```
this mean something like this...:
```
	
Make: *** There is no specified purpose and not found any makefile. Stop
```

Can you help me?
i think because i try to install in a Ubuntu 7.10

(Perdonen mi ingles tan malo...)

Did you type all the commands shown in the first post? Such as:

```

cd xf86-video-ati-6.5.8.0
export XORG_PREFIX="/usr"
export XORGCONFIG="--prefix=$XORGPREFIX --sysconfdir=/etc --localstatedir=/var"
./configure $XORG_CONFIG --with-xorg-module-dir=/usr/lib/xorg/modules
make

```

---

### Post by icon_mefisto on 2008-02-16
I want to try this patched ati driver, but it makes me nervous.

Just wondering how I would revert back to the standard ati driver, if this patched driver doesn't work for me.

Is it as simple as reinstalling the ati driver from repos? Or do I have to do something to remove the patched one first?

---

### Post by djhash on 2008-07-07
Ola.. so I did everything in the cchtml wiki.. and i think its half working..

  When I switch to 800x600 the LCD screen gets all squiggly and the tv shows gray-scale squiggly.. below is my xorg.conf

  when I change the -hsync -vsync to either +,- or -,+ or +,+ I get the squiggly stuff and the same is shown on the s-video... when I keep them both -,- the LCD screen shows perfectly, but nothing on the S-video connection..

  So I guess the problem is with either the vertical/horizontal sync or maybe both. Also, it might be possible i'm getting the image as greyscale and no colors. And I hope there is a fix for that. Thanks...

```

# xorg.conf (xorg X Window System server configuration file)
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

Section "Files"
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
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
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
	Identifier	"ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]"
	Boardname	"ati"
	Busid		"PCI:1:0:0"
	Driver		"ati"
	Screen	0
	Option		"TVOutput" "NTSC"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1024x768"
	Horizsync	31.5-48.0
	Vertrefresh	56.0 - 65.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync -vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync -vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Modes		"1024x768@60"	"800x600@60"	"800x600@56"	"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection
Section "device" #   
	Identifier	"device1"
	Boardname	"ati"
	Busid		"PCI:1:0:0"
	Driver		"ati"
	Screen	1
	Option		"MergedFB"	"off"
	Option		"TVOutput" "NTSC"
EndSection
Section "screen" #   
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
	SubSection "Display"
		Depth	24
		Modes		"800x600@60"
	EndSubSection
EndSection
Section "monitor" #   
	Identifier	"monitor1"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync +hsync
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection

```

---

### Post by osxdude on 2008-07-08
Here is my xorg.conf, as I have the same card as you (as you told me in the IRC):

```

# xorg.conf (xorg X Window System server configuration file)
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

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbVariant"	"intl"
	Option		"XkbOptions"	"lv3:ralt_switch"
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
	Option		"HorizEdgeScroll"	"0"
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
	Identifier	"Internal"
	Driver		"radeon"
	BusID		"PCI:1:0:0"
	Option		"AGPMode" "4"
	Option		"AGPFastWrite" "true"
	Option		"RenderAccel" "on"
	Option		"MonitorLayout" "LVDS, NONE"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1024x768"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

```

---

### Post by Borisdieklinge85 on 2009-02-24
Hi, 
I installed Ubuntu 6.06 on a Duron 650 with a Radeon 7200.
I have successfully made the steps in the howto.
When I boot with only the TV at Cinch-TV-Out connected, the Boot sequence is shown on the TV, but when the X server starts, I see the Ubuntu background flickering for half a second and then the screen turns sometimes green, sometimes brown :)

My Xorg.conf is exactly the one in the how-to, but I tried

monitorlayout  "TV"

monitorlayout  "TV, CRT"

monitorlayout  "AUTO"

and

#monitorlayout  "TV"

thx for help!

---

### Post by wavemaking on 2009-10-25
Could anybody tell me what the status of this is in Karmic? Various news messages on the net indicate that this capability should now be inbuilt in the xorg radeon driver. And when I use xrandr, I can just you the commands without any errors popping up, but still the TV shows nothing.

lspci say that I have a:

```
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 If [Radeon 9000] (rev 01)
```

---

### Post by toagathonen on 2010-01-19
> **WilliamAnderson said:**
> Hi all,
 
First I want to say what fantastic instructions you gave. Thank you for creating this post and providing this information. I had no trouble following them and successfuly downloaded, patched, compiled, installed, and configured TV out following these instructions. I encountered no errors or warnings as I did this. However, it did not work. After chasing down a faulty TV in plug on one TV, I get nothing on the TV screen after X starts.
 
Contrary to the list of supported cards at the Gatos site, the patch supplied does not touch the r128 driver source files. It does not enable TV out for these cards. If your card is not a Radeon, it will not work. However, the TV Out on my Rage 128 pro card does work until the frame buffer is enabled (Ubuntu splash screen) and/or until the X server starts. 
 
When I find a way to enable TV out I will come back and post how I was able to make it work.
 
William
Hi William,
 
I know that it you wrote this post a long time ago, but I was wondering if your attempts to enable TV-out for an ATI card that uses the r128 driver ever worked. 
 
I am an absolute newbie with Ubuntu with no Linux or other programming experience whatsoever--my abilities are basically limited to cutting and pasting these code commands without understanding what they are really doing.
 
I have an old Dell Latitude c600 with an ATI Rage Mobility M3 AGP 2x, and Ubuntu 9.10 set up the r128 driver by itself when I installed it.
 
When I followed the How-To I got an error similar to two of those posted here (#19 & #20) during the configuring/compiling (?) stage--in particular, at
 
[FONT=Times New Roman][SIZE=3]./configure $XORG_CONFIG --with-xorg-module-dir=/usr/lib/xorg/modules[/SIZE][/FONT]
 
The "checking" process which followed my input of this command stopped as follows:
 
[FONT=Times New Roman][SIZE=3]checking for DRI... configure: error: Package requirements (libdrm >= 2.0 xf86driproto) were not met:[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]No package 'libdrm' found[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]No package 'xf86driproto' found[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]Consider adjusting the PKG_CONFIG_PATH environment variable if you[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]installed software in a non-standard prefix.[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]Alternatively, you may set the environment variables DRI_CFLAGS[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]and DRI_LIBS to avoid the need to call pkg-config.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]See the pkg-config man page for more details.[/SIZE][/FONT]
 
 
I don't have the slightest idea what this means. But according to what you said in your post, there's no point to it anyway, since the how-to doesn't work for r128. 
 
So did you find another solution? One that someone like myself might be able to implement?
 
Thanks for any help you can give!

---

### Post by pacmanfan on 2010-07-11
**Edit:  Problem resolved.**  Please see the bottom of this post for the fix.

Hello, community. Sorry to bump such an old thread, but I think this is the right place for my issue.  I'm trying to get GATOS running on an Xubuntu Lucid box.  I've successfully completed every step up until the "make" command in this tutorial.  After that, I get the following error:

  [HTML]andrew@xubuntu:~/atidrivers/xf86-video-ati-6.5.8.0$ make
make  all-recursive
make[1]: Entering directory `/home/andrew/atidrivers/xf86-video-ati-6.5.8.0'
Making all in src
make[2]: Entering directory `/home/andrew/atidrivers/xf86-video-ati-6.5.8.0/src'
if /bin/bash ../libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I..    -fvisibility=hidden -I/usr/include/xorg -I/usr/include/pixman-1   -I/usr/include/drm -I/usr/include/X11/dri   -g -O2 -MT atibus.lo -MD -MP -MF ".deps/atibus.Tpo" \
      -c -o atibus.lo `test -f 'atibus.c' || echo './'`atibus.c; \
    then mv -f ".deps/atibus.Tpo" ".deps/atibus.Plo"; \
    else rm -f ".deps/atibus.Tpo"; exit 1; \
    fi
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -fvisibility=hidden -I/usr/include/xorg -I/usr/include/pixman-1 -I/usr/include/drm -I/usr/include/X11/dri -g -O2 -MT atibus.lo -MD -MP -MF .deps/atibus.Tpo -c atibus.c  -fPIC -DPIC -o .libs/atibus.o
In file included from atibus.c:28:
ati.h:32:24: error: xf86_ansic.h: No such file or directory
In file included from atibus.c:33:
atistruct.h:58:27: error: xf86Resources.h: No such file or directory
In file included from atibus.c:33:
atistruct.h:248: error: expected specifier-qualifier-list before 'pciVideoPtr'
atibus.c: In function 'ATIClaimResources':
atibus.c:69: error: 'resPtr' undeclared (first use in this function)
atibus.c:69: error: (Each undeclared identifier is reported only once
atibus.c:69: error: for each function it appears in.)
atibus.c:69: error: expected ';' before 'pResources'
atibus.c:73: error: 'resRange' undeclared (first use in this function)
atibus.c:73: error: expected ';' before 'Resources'
atibus.c:76: error: 'struct _ATIRec' has no member named 'SharedVGA'
atibus.c:86: error: 'struct _ATIRec' has no member named 'SharedVGA'
atibus.c:86: error: 'resVgaSparseShared' undeclared (first use in this function)
atibus.c:86: error: 'resVgaSparseExclusive' undeclared (first use in this function)
atibus.c:87: error: 'struct _ATIRec' has no member named 'SharedVGA'
atibus.c:87: error: 'resVgaShared' undeclared (first use in this function)
atibus.c:87: error: 'resVgaExclusive' undeclared (first use in this function)
atibus.c:88: error: 'struct _ATIRec' has no member named 'iEntity'
atibus.c:92: error: 'struct _ATIRec' has no member named 'SharedVGA'
atibus.c:93: error: 'Resources' undeclared (first use in this function)
atibus.c:93: error: 'ResShrIoSparse' undeclared (first use in this function)
atibus.c:93: error: 'ResBus' undeclared (first use in this function)
atibus.c:95: error: 'ResExcIoSparse' undeclared (first use in this function)
atibus.c:102: error: 'struct _ATIRec' has no member named 'iEntity'
atibus.c:104: error: 'struct _ATIRec' has no member named 'VGAWonderResources'
atibus.c:109: error: 'struct _ATIRec' has no member named 'SharedAccelerator'
atibus.c:115: error: 'struct _ATIRec' has no member named 'SharedAccelerator'
atibus.c:115: error: 'res8514Shared' undeclared (first use in this function)
atibus.c:115: error: 'res8514Exclusive' undeclared (first use in this function)
atibus.c:116: error: 'struct _ATIRec' has no member named 'iEntity'
atibus.c:122: error: 'struct _ATIRec' has no member named 'SharedAccelerator'
atibus.c:129: error: 'struct _ATIRec' has no member named 'iEntity'
atibus.c:145: error: 'pResources' undeclared (first use in this function)
atibus.c:145: error: 'struct _ATIRec' has no member named 'iEntity'
atibus.c:145: error: 'ResExclusive' undeclared (first use in this function)
atibus.c:149: error: 'struct _ATIRec' has no member named 'iEntity'
atibus.c: In function 'ATIClaimBusSlot':
atibus.c:174: error: 'pciVideoPtr' undeclared (first use in this function)
atibus.c:174: error: expected ';' before 'pVideo'
atibus.c:176: error: 'pVideo' undeclared (first use in this function)
atibus.c:177: error: 'struct _ATIRec' has no member named 'iEntity'
atibus.c:179: warning: passing argument 4 of 'xf86ClaimPciSlot' from incompatible pointer type
/usr/include/xorg/xf86.h:97: note: expected 'GDevPtr' but argument is of type 'DriverPtr'
atibus.c:179: error: too many arguments to function 'xf86ClaimPciSlot'
atibus.c:181: error: 'struct _ATIRec' has no member named 'iEntity'
atibus.c:183: error: 'struct _ATIRec' has no member named 'iEntity'
atibus.c:186: error: 'struct _ATIRec' has no member named 'iEntity'
make[2]: *** [atibus.lo] Error 1
make[2]: Leaving directory `/home/andrew/atidrivers/xf86-video-ati-6.5.8.0/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/andrew/atidrivers/xf86-video-ati-6.5.8.0'
make: *** [all] Error 2[/HTML][B]

Fix:  [/B]After all the prerequisites have been installed, enter only:

[HTML]wget http://xorg.freedesktop.org/releases/individual/driver/xf86-video-ati-6.13.1.tar.bz2[/HTML]
in place of the two packages that you would have downloaded in previous versions.

From my experience, this newer package doesn't need to be patched, so you can skip that step.  Good luck!

---

