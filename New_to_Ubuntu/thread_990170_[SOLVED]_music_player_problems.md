---
title: "[SOLVED] music player problems"
date: 2008-11-22
forum: New to Ubuntu
---

### Post by nynoah on 2008-11-22
Ok this problem seems to effect all my music players at the same time.  For some reason I can not play my music files.  When I open up Amarok it does not work.  With Rythmbox I open it up, it shows the files.  I try to play them but it just acts like the file is not found.  Same with Banshee and Exhail.  But when I go to where the file is in my home folder, I can play the files with VLC just fine.  Any idea what might cause this?

---

### Post by jenkinbr on 2008-11-22
What type of files are you trying to play?  MP3? WMA? Something else?

For mp3, wma, and other proprietary files, you will need the proper gstreamer plugins:
```
sudo apt-get install gstreamer0.10-plugin*
```
That is a quick and easy way to get all the gstreamer plugins.  Input the command into a terminal (menu path:'Applications > Accessories > Terminal) or just press <alt>+<f2> and enter 'gnome-terminal' into the box that pops up.

Hope this helps.

Edit: For AmaroK, you will need the proper libxine plugin.  Can you tell me what version of Ubuntu you have?
Edit2; nevermind - just saw your sig.

---

### Post by nynoah on 2008-11-22
I have all the correct drivers.  Unless something has changed.  I have a pretty good setup.  I have been using all my players now for well over 6 months without a problem.  The Mp3 files play fine on VLC so I don't think drivers are the issue.

I am running 8.04

I also have Kubuntu loaded, and KDE4 encase that gives any clues.  I was running both a lot in the last few days.

---

### Post by laurielegit on 2008-11-22
Its not drivers you need, but codecs. Make sure you have the Ubuntu restricted extras package installed.

---

### Post by nynoah on 2008-11-22
the are installed.  I reinstalled them to make sure.  still did not work.  Basically the files will play when I hover over them.  They will also play in VLC.  But for some reason I can not play them with any of my music players.  I click play and the files act like they are not there.  Skipping from one track to the next never playing anything.

---

### Post by jenkinbr on 2008-11-22
You don't happen to have another application playing audio at the same time, do you?

Try running ```
sudo killall pulse
``` and see if they play now.

Pulse audio was the source of many many problems for me in Hardy.

btw, if the command backfires and does something funky, just reboot your system and all should be back as it was before killall was run.

---

### Post by nynoah on 2008-11-22
> noah@noah-desktop:~$ sudo killall pulse
[sudo] password for noah: 
pulse: no process killed
noah@noah-desktop:~$ 



That is what I get

---

### Post by nynoah on 2008-11-22
is there was to delete my history of scanned files.  Does this have something to do with it?

---

### Post by nynoah on 2008-11-22
Ok what does this mean............... they all work fine in Kubuntu.  But not Ubunutu.  I prefer Gnome of KDE.  I just dable in Kubunut sometimes.  I love the programs but HATE the interface.

---

### Post by CatKiller on 2008-11-22
One thing that might help is going into System -> Preferences -> Sound and changing the playback device to ALSA.

Also, if you try running your music player from the Terminal (Applications -> Accessories -> Terminal) you might get some informative error messages for why it's not playing those files.

In Amarok, you can go to Settings -> Configure Amarok -> Engine to set which method gets used for output. I haven't used the others for quite some time, but I'd imagine there's something similar for those, too.

---

### Post by nynoah on 2008-11-22
ok if I go and open up my sound preferences, everything is on auto detect.  But nothing works.  They all comeback with errors.

---

### Post by CatKiller on 2008-11-22
> **nynoah said:**
> ok if I go and open up my sound preferences, everything is on auto detect.  But nothing works.  They all comeback with errors.

What errors?

---

### Post by nynoah on 2008-11-22
Sorry should have listed that...... stupid me

> audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect stream: Invalid argument

---

### Post by mc4man on 2008-11-22
solely looking at amarok, first do you have libxine1-ffmpeg installed?

If so what happens when you right click on a music file -> open with -> open with amarok.
If amarok's not listed go to 'open with other application'

---

### Post by nynoah on 2008-11-22
This is what I get when I run rhythmbox in terminal.

> /usr/share/themes/Ultimate_Edition_2.0_Red/gtk-2.0/gtkrc:1145: Unable to locate image file in pixmap_path: "Menu-Menubar/menubar-item.png"
/usr/share/themes/Ultimate_Edition_2.0_Red/gtk-2.0/gtkrc:1148: Background image options specified without filename
Rhythmbox: could not connect to socket
Rhythmbox: No such file or directory

(rhythmbox:16946): Rhythmbox-WARNING **: Could not open device /dev/radio0

** (rhythmbox:16946): WARNING **: Invalid borders specified for theme pixmap:
        /usr/share/themes/Ultimate_Edition_2.0_Red/gtk-2.0/Menu-Menubar/menubar.png,
borders don't fit within the image


---

### Post by nynoah on 2008-11-22
Banshee in Terminal

> [Info  11:41:24.737] Running Banshee 1.4.1
/usr/share/themes/Ultimate_Edition_2.0_Red/gtk-2.0/gtkrc:1145: Unable to locate image file in pixmap_path: "Menu-Menubar/menubar-item.png"
/usr/share/themes/Ultimate_Edition_2.0_Red/gtk-2.0/gtkrc:1148: Background image options specified without filename
Mirage - Open DB - URI=file:/home/noah/.cache/banshee-mirage/mirage.db,version=3
Mirage - Database version 2 is up to date
[Info  11:41:33.520] All services are started 7.989078s

** (Banshee:17746): WARNING **: Invalid borders specified for theme pixmap:
        /usr/share/themes/Ultimate_Edition_2.0_Red/gtk-2.0/Menu-Menubar/menubar.png,
borders don't fit within the image
[Info  11:41:36.502] nereid Client Started
[Warn  11:41:36.735] Caught an exception - org.freedesktop.Hal.NoSuchProperty: No property volume.is_mounted on device with id /org/freedesktop/Hal/devices/platform_floppy_0_storage_platform_floppy (in `NDesk.DBus.Proxies')
  at IDeviceProxy.GetPropertyBoolean (System.String ) [0x00000] 
  at Hal.Device.GetPropertyBoolean (System.String key) [0x00000] 
  at Banshee.HalBackend.Volume.get_IsMounted () [0x00000] 
  at Banshee.HalBackend.Volume.CheckVolumeMounted (Banshee.HalBackend.Volume volume) [0x00000] 
  at Banshee.HalBackend.Volume.Resolve (Banshee.HalBackend.BlockDevice parent, Hal.Manager manager, Hal.Device device) [0x00000] 
[Warn  11:41:37.010] Caught an exception - org.freedesktop.Hal.NoSuchProperty: No property volume.is_mounted on device with id /org/freedesktop/Hal/devices/platform_floppy_0_storage_platform_floppy (in `NDesk.DBus.Proxies')
  at IDeviceProxy.GetPropertyBoolean (System.String ) [0x00000] 
  at Hal.Device.GetPropertyBoolean (System.String key) [0x00000] 
  at Banshee.HalBackend.Volume.get_IsMounted () [0x00000] 
  at Banshee.HalBackend.Volume.CheckVolumeMounted (Banshee.HalBackend.Volume volume) [0x00000] 
  at Banshee.HalBackend.Volume.Resolve (Banshee.HalBackend.BlockDevice parent, Hal.Manager manager, Hal.Device device) [0x00000] 
[Warn  11:41:37.236] Caught an exception - org.freedesktop.Hal.NoSuchProperty: No property volume.is_mounted on device with id /org/freedesktop/Hal/devices/platform_floppy_0_storage_platform_floppy (in `NDesk.DBus.Proxies')
  at IDeviceProxy.GetPropertyBoolean (System.String ) [0x00000] 
  at Hal.Device.GetPropertyBoolean (System.String key) [0x00000] 
  at Banshee.HalBackend.Volume.get_IsMounted () [0x00000] 
  at Banshee.HalBackend.Volume.CheckVolumeMounted (Banshee.HalBackend.Volume volume) [0x00000] 
  at Banshee.HalBackend.Volume.Resolve (Banshee.HalBackend.BlockDevice parent, Hal.Manager manager, Hal.Device device) [0x00000] 
[Warn  11:41:37.544] Caught an exception - org.freedesktop.Hal.NoSuchProperty: No property volume.is_mounted on device with id /org/freedesktop/Hal/devices/platform_floppy_0_storage_platform_floppy (in `NDesk.DBus.Proxies')
  at IDeviceProxy.GetPropertyBoolean (System.String ) [0x00000] 
  at Hal.Device.GetPropertyBoolean (System.String key) [0x00000] 
  at Banshee.HalBackend.Volume.get_IsMounted () [0x00000] 
  at Banshee.HalBackend.Volume.CheckVolumeMounted (Banshee.HalBackend.Volume volume) [0x00000] 
  at Banshee.HalBackend.Volume.Resolve (Banshee.HalBackend.BlockDevice parent, Hal.Manager manager, Hal.Device device) [0x00000] 




---

### Post by nynoah on 2008-11-22
Now Amarock will not even open up........... huh

---

### Post by nynoah on 2008-11-22
I also have libxine1-ffmpeg installed already

---

### Post by mc4man on 2008-11-22
Personally i'd slow down, reboot and pick one player at a time and address it's issues. rhythmbox and banshee probably are related.
Myself I only use amarok and sometimes vlc, I have no use for gstreamer apps

---

### Post by nynoah on 2008-11-22
Ok I ran rhythmbox in terminal again and tried to play a file.  I do get an error that does show some idea of what is going on.

> /usr/share/themes/Ultimate_Edition_2.0_Red/gtk-2.0/gtkrc:1145: Unable to locate image file in pixmap_path: "Menu-Menubar/menubar-item.png"
/usr/share/themes/Ultimate_Edition_2.0_Red/gtk-2.0/gtkrc:1148: Background image options specified without filename
Rhythmbox: could not connect to socket
Rhythmbox: No such file or directory

(rhythmbox:21465): Rhythmbox-WARNING **: Could not open device /dev/radio0

** (rhythmbox:21465): WARNING **: Invalid borders specified for theme pixmap:
        /usr/share/themes/Ultimate_Edition_2.0_Red/gtk-2.0/Menu-Menubar/menubar.png,
borders don't fit within the image

(rhythmbox:21465): GStreamer-WARNING **: loop detected in the graph of bin playbin!!

(rhythmbox:21465): GStreamer-WARNING **: loop detected in the graph of bin playbin!!




---

### Post by nynoah on 2008-11-22
Any ideas how to fix my sound?  Do I need to fix Gstreamer or get rid of it and switch to another thing.

---

### Post by nynoah on 2008-11-22
the strange part is that I have audio for everything on the internet and VLC but nothing for the others.  Are some set to Gstreamer and others to Pulse?

---

### Post by mc4man on 2008-11-22
sorry I can't help you with rhythmbox. I don't use it.

What I'll mention is the terminal errors your seeing are related to opening rhythmbox, not from attempting playback.

What do you see if you use rhythmbox-client instead?

I'd try going into preferences -> sound and setting the music one to alsa.

The fact you get sound from the mouse over (totem-audio-preview) indicates your gstreamer plugins are in order. (unless you've installed and set totem-xine as the default totem player, in which case it's totem-xine doing the preview

Edit:
Some apps are set in their own setting like amarok, other like rhythmbox use preferences -> sound

---

### Post by nynoah on 2008-11-22
OK it works.......... I wonder why autodetect does not work?  huh

---

### Post by mc4man on 2008-11-22
> I wonder why autodetect does not work?
I'm not really up on sound issues but I'd think 'autodetect' is using pulse which for a lot of setups in 8.04 needs to be configured to work properly.

In my I can use pulse or alsa so autodetect works though i prefer to specify my audio and video outputs whenever possible. (usuallly from indiv. apps's settings

---

