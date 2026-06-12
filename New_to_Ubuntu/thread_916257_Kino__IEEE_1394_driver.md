---
title: "Kino  IEEE 1394 driver"
date: 2008-09-10
forum: New to Ubuntu
---

### Post by roland0702 on 2008-09-10
I'm trying to capture footage onto my computer with the IEEE 1394 or 'firewire' cable from a Sony Digital 8 DCR-TRV 103 NTSC handycam.

I'm only guessing I'm missing this Linux IEEE 1394 thing, the Kino help contents refer to this. I downloaded a libraw1394-2.0.tar.gz file. I know it is a compressed file, but I have no idea how to install it.

:D

---

### Post by lisati on 2008-09-26
Good question: I'm researching this with a Sony DCR-TRV147E PAL Digital-8 camcorder....

---

### Post by bumanie on 2008-09-26
To get kino to work with a firewire supported dv camera, I think you need to install dvgrab > sudo apt-get install dvgrab

---

### Post by lisati on 2008-09-26
Progress report: I've hooked up my camera, installed kino, and it Kino is able to capture from it using Firewire, but only if I start the camera manually.... Now to investigate the dvgrab.....

---

### Post by lisati on 2008-09-26
> **roland0702 said:**
> I'm trying to capture footage onto my computer with the IEEE 1394 or 'firewire' cable from a Sony Digital 8 DCR-TRV 103 NTSC handycam.

I'm only guessing I'm missing this Linux IEEE 1394 thing, the Kino help contents refer to this. I downloaded a libraw1394-2.0.tar.gz file. I know it is a compressed file, but I have no idea how to install it.

:D

> **bumanie said:**
> To get kino to work with a firewire supported dv camera, I think you need to install dvgrab

Please stand by: I installed dvgrab as suggested, Kino expects me to press "Play" on the camera.

If you don't mind controlling the camera manually, it seems from my preliminary research that Kino will happily capture from it without the need for additional drivers. It would be nice, however, if the functionality of the Windows software I've used was there, e.g. fully automatic capture including rewinding the tape.

---

### Post by bumanie on 2008-09-26
I don't think kino provides automatic everything - but it works well overall.

---

### Post by lisati on 2008-09-26
> **bumanie said:**
> I don't think kino provides automatic everything - but it works well overall.

On the rare occasion I'd be using my Firewire cameras with Kino, I could put up with the manual control of the camera, but I'm not sure where the OP downloaded the driver from, Kino seems to be usable on my system without it, even without some of the features I'm accustomed to with other software I've used.

---

### Post by remeeraz on 2008-10-13
> **bumanie said:**
> I don't think kino provides automatic everything - but it works well overall.

Actually Kino does provide camera controls. I've used it in Fedora 9, and Ubuntu 8.04.

I have just set up an Acer Aspire 7520 with Ubuntu 8.04, KinoDV 1.3.2 and firewire capabilities for someone who wanted to do video editing without "Gatesware" and those money grabbing software publishers.

I'm not surprised that many people can't get firewire (ieee1394) to work with Kino in Ubuntu, because the instructions I've found available are in-accurate and incorrect.

You don't need DVGrab, although you could use this instead. Follow from STEPS 9...

It also doesn't matter what version of Ubuntu you are using as (stating the obvious ) they are all LINUX and the core language is the same. But this info is written for users of Gnome.

[COLOR="DarkRed"]**If you want to be able to get firewire to work for total control of DV cams, follow STEPS 9 & 10 in the instructions.**[/COLOR]

STEPS 1 through 8 in this post will tell you how to install the Latest (as of 12 October 2008 ) version of Kino (version 1.3.2) from source code downloaded directly from KinoDV's website.

It looks a lot, but it's not really. :)

1) [COLOR="Red"]Bookmark this page so you can come back to it as we will need to restart X at some point.[/COLOR]

2) Download Kino 1.3.2 from here;
[http://downloads.sourceforge.net/kino/kino-1.3.2.tar.gz](http://downloads.sourceforge.net/kino/kino-1.3.2.tar.gz)
I'm using this version because it's the latest release at this time, and the current version in Ubuntu is "rumoured" to not work.

3) Extract the Kino folder onto your Desktop. (We'll Delete this when it's finished with.)

4) Make sure you have the following Packages installed, you may need to enable the "universe" to install them all, and you can remove them when we've finished if you want;

    * build-essential
    * cvs
    * make
    * autoconf
    * intltool
    * libtool
    * libavformat-dev
    * libiec61883-dev
    * libavc1394-dev
    * libsamplerate0-dev
    * libdv4-dev
    * libquicktime-dev
    * libasound2-dev
    * libglade2-dev
    * libxv-dev
    * ffmpeg
    * ffmpeg2theora
    * sox
    * vorbis-tools

    * nautilus-open-terminal (For ease of access to folders from a GUI,
                              without this, my instructions won't work.)

Might need to enable Multiverse for these packages, but these packages aren't essential to the build.

    * lame
    * mjpegtools
    * qdvdauthor (for advanced DVD Video authoring)


5) Close any programs and save any work and press Ctrl+Alt+Backspace to restart your X Server so that the nautilus-open-terminal plugin is loaded. Then log back in and continue...

6) Right Click on the Kino Folder on your Desktop and Select "Open In Terminal".

7) Enter these commands to start compiling the Kino Source;

```
**./configure --sysconfdir=/etc --enable-quicktime**
```
then
```
**make**
```
then
```
**sudo make install**
```

8 ) Close the Terminal and Delete the Kino Folder from your Desktop, that's done with now.

9) Add your username (the person who will be logged in and doing the Video Capturing) to the group "disk".

To do this, click **System** -> **Administration** -> **Users and Groups**

Click the appropriate username, then click the **Properties** button,
in the new window called "User Properties", click the **Group** tab.

Locate **disk** in the list and put a tick next to it.
Now click ok, and close the "User Manager".

10) Open a terminal and type;

```
**sudo gedit /etc/rc.local**
```
add the following line of text to it and save then close the file.
> [COLOR="Indigo"]**/sbin/modprobe raw1394**[/COLOR]

Now type;

```
**sudo modprobe raw1394**
```
then
```
**sudo chown** "the username concerned" **/dev/raw1394**
```

Now restart your computer and get on with it! heh :popcorn:

---

