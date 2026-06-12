---
title: "Still have DVD Problems"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by subaruwrc01 on 2008-06-22
I gave up trying to get Totem to play DVD's, so I installed VLC.  However VLC will not play past the menus.  After clicking on something in the menu, it crashes.

```
VLC media player 0.8.6e Janus
libdvdnav: Using dvdnav version 0.1.10 from http://dvd.sf.net
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdnav: DVD Title: CONQUEROR_OF_SHAMBALLA
libdvdnav: DVD Serial Number: 34f593a9
libdvdnav: DVD Title (Alternative): 
libdvdnav: Unable to find map file '/home/ryan/.dvdnav/CONQUEROR_OF_SHAMBALLA.map'
libdvdnav: DVD disk reports itself with Region mask 0x00fe0000. Regions: 1

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000012f
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000008e8
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x000015d7
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x000f4f4c
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x000f5230
libdvdread: Elapsed time 0
libdvdread: Found 2 VTS's
libdvdread: Elapsed time 0
[00000352] a52 decoder: A/52 channels:2 samplerate:48000 bitrate:256000
libdvdnav: ifoRead_VOBU_ADMAP vtsi failed - CRASHING
vlc: vm.c:214: ifoOpenNewVTSI: Assertion `0' failed.
Aborted
```

Anyone know what's causing this and ways to potentially fix this?

P.S. I'm using 8.04.

---

### Post by phidia on 2008-06-22
Take a look at the thread [here]("http://ubuntuforums.org/showthread.php?t=575729&page=3") and see if the solutions there will work for you. Remember to reboot after installing the codec too.
Hope that's helpful.

---

### Post by subaruwrc01 on 2008-06-22
I already had everything I need installed.  I tried uninstalling, reinstalling, and rebooting, but still no programs will play DVDs.

I'm wondering if it may be a problem with my graphics card.  The graphics on the menu that I do manage to see look terrible.  All my other problems were fixed by odd solutions.

My card is an integrated Intel GMA X3100 GM965.

---

### Post by crjackson on 2008-06-22
Try this...

Go to SYSTEM>ADMINISTRATION>SOFTWARE SOURCES and enable the extra repositories first...

Start from scratch and don't worry if you've already done some of this before.  It will just skip any uneeded items.  This is for 32-bit Hardy...

Go to your menu - Applications>Accessories>Terminal and click!

Next cut and paste the following into the terminal screen.

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
```

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

```
sudo apt-get install libdvdcss2 w32codecs gxine totem-xine xine-ui libdmx1 libxine1 libxine1-ffmpeg libxinerama1 totem libdvdread3
```

---

### Post by phidia on 2008-06-23
> **subaruwrc01 said:**
> I already had everything I need installed.  I tried uninstalling, reinstalling, and rebooting, but still no programs will play DVDs.

I'm wondering if it may be a problem with my graphics card.  The graphics on the menu that I do manage to see look terrible.  All my other problems were fixed by odd solutions.

My card is an integrated Intel GMA X3100 GM965.

What driver is listed in your /etc/X11/xorg.conf?
If it's vesa you need to enable the driver for your card.

I don't know that much about intel graphics cards but there are a few posts at the forums claiming there are problems 
with that card [this post]("http://ubuntuforums.org/showthread.php?t=612617") is from last year but one of the posters there has the same problem as you.

---

