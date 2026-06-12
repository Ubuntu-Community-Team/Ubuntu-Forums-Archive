---
title: "watching shows full screen"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by ayeshap on 2008-06-20
so i like to watch shows online, especially from surfthechannel.com which uses links from other websites such as youku.com

however, since using ubuntu, i havent been able to watch the shows full screen, and i dont know why. nothing happens when i click the full sceen option but other options such as half screen works.

does it have anything to do with ubuntu?

---

### Post by RomeReactor on 2008-06-20
Hi. Which version of Ubuntu are you running (7.10, 8.04, or a previous one), and for which architecture (32-bit, 64-bit)? Do you have Desktop effects on? If so, and you have Ubuntu 7.10 or 8.04, try disabling the effects and try the videos again.

If you want to keep them on, you can change a setting in compizconfig-settings manager; if you don't have it installed look for it in Synaptic, or to install it from th terminal:
```
sudo aptitude install compizconfig-settings manager
```
After it's installed, go to 'System->Preferences->Advanced Desktop Effects Settings' and in there go to 'General Options' and on the General tab make sure 'Unredirect Fullscreen Windows' is unchecked; press the 'Back' button, then scroll down to the 'Utility' section, press the 'Workarounds' button, and make sure 'Legacy Fullscreen Support' is checked. Then try the videos again.

---

### Post by ayeshap on 2008-06-20
i have 7.10 ubuntu but i dont know which architecture (i actually have no idea what that is). i dont have any desktop effect on because when i tried to change it, a msg came up saying that i cant change the desktop effects.

would that code enable me to get full screen even tho i dont have on any desktop effects?

---

### Post by RomeReactor on 2008-06-20
If you don't use desktop effects,then you don't need compizconfig-settings-manager. I'm not sure if a pop-up blocker would affect the videos since they're in Flash, but if you *do* have a pop-up blocker try disabling it or make sure it's not blocking the site.

Also, in Firefox open a new tab and write in the address bar:
```
about:plugins
```
and post the results.

---

### Post by ayeshap on 2008-06-20
Installed plug-ins
Find more information about browser plug-ins at mozilla.org.
Help for installing plug-ins is available from plugindoc.mozdev.org.
Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 9.0 r48

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes
VLC Multimedia Plugin

    File name: libvlcplugin.so
    Version 0.8.6c Janus, copyright 1996-2007 The VideoLAN Team
    [http://www.videolan.org/](http://www.videolan.org/)

MIME Type 	Description 	Suffixes 	Enabled
audio/mpeg 	MPEG audio 	mp2,mp3,mpga,mpega 	Yes
audio/x-mpeg 	MPEG audio 	mp2,mp3,mpga,mpega 	Yes
video/mpeg 	MPEG video 	mpg,mpeg,mpe 	Yes
video/x-mpeg 	MPEG video 	mpg,mpeg,mpe 	Yes
video/mpeg-system 	MPEG video 	mpg,mpeg,mpe,vob 	Yes
video/x-mpeg-system 	MPEG video 	mpg,mpeg,mpe,vob 	Yes
video/mpeg4 	MPEG-4 video 	mp4,mpg4 	Yes
audio/mpeg4 	MPEG-4 audio 	mp4,mpg4 	Yes
application/mpeg4-iod 	MPEG-4 video 	mp4,mpg4 	Yes
application/mpeg4-muxcodetable 	MPEG-4 video 	mp4,mpg4 	Yes
video/x-msvideo 	AVI video 	avi 	Yes
video/quicktime 	QuickTime video 	mov,qt 	Yes
application/x-ogg 	Ogg stream 	ogg 	Yes
application/ogg 	Ogg stream 	ogg 	Yes
application/x-vlc-plugin 	VLC plugin 	vlc 	Yes
video/x-ms-asf-plugin 	Windows Media Video 	asf,asx 	Yes
video/x-ms-asf 	Windows Media Video 	asf,asx 	Yes
application/x-mplayer2 	Windows Media 		Yes
video/x-ms-wmv 	Windows Media 	wmv 	Yes
application/x-google-vlc-plugin 	Google VLC plugin 		Yes
audio/wav 	WAV audio 	wav 	Yes
audio/x-wav 	WAV audio 	wav 	Yes
audio/3gpp 	3GPP audio 	3gp,3gpp 	Yes
video/3gpp 	3GPP video 	3gp,3gpp 	Yes
audio/3gpp2 	3GPP2 audio 	3g2,3gpp2 	Yes
video/3gpp2 	3GPP2 video 	3g2,3gpp2 	Yes
Totem Web Browser Plugin 2.20.0

    File name: libtotem-basic-plugin.so
    The Totem 2.20.0 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
application/ogg 	Ogg multimedia 	ogg 	Yes
audio/ogg 	Ogg Audio 	ogg 	Yes
audio/x-ogg 	Ogg Audio 	ogg 	Yes
video/ogg 	Ogg Video 	ogg 	Yes
video/x-ogg 	Ogg Video 	ogg 	Yes
video/mpeg 	MPEG video 	mpg, mpeg, mpe 	Yes
audio/wav 	WAV audio 	wav 	Yes
audio/x-wav 	WAV audio 	wav 	Yes
audio/mpeg 	MP3 audio 	mp3 	Yes
application/x-nsv-vp3-mp3 	NSV video 	nsv 	Yes
video/flv 	Flash video 	flv 	Yes
Windows Media Player Plug-in 10 (compatible; Totem)

    File name: libtotem-gmp-plugin.so
    The Totem 2.20.0 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
application/x-mplayer2 	AVI video 	avi, wma, wmv 	Yes
video/x-ms-asf-plugin 	ASF video 	asf, wmv 	Yes
video/x-msvideo 	AVI video 	asf, wmv 	Yes
video/x-ms-asf 	ASF video 	asf 	Yes
video/x-ms-wmv 	WMV video 	wmv 	Yes
video/x-wmv 	WMV video 	wmv 	Yes
video/x-ms-wvx 	Playlist 	wmv 	Yes
video/x-ms-wm 	ASF video 	wmv 	Yes
application/x-ms-wms 	WMV video 	wms 	Yes
application/asx 	Playlist 	asx 	Yes
DivX® Web Player

    File name: libtotem-mully-plugin.so
    The Totem 2.20.0 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
video/divx 	AVI video 	divx 	Yes
QuickTime Plug-in 7.2.0

    File name: libtotem-narrowspace-plugin.so
    The Totem 2.20.0 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
video/quicktime 	QT video 	mov 	Yes
video/mp4 	MPEG-4 video 	mp4 	Yes
image/x-macpaint 	MacPaint Bitmap image 	pntg 	Yes
image/x-quicktime 	Macintosh Quickdraw/PICT drawing 	pict, pict1, pict2 	Yes
video/x-m4v 	MPEG-4 video 	m4v 	Yes

---

### Post by RomeReactor on 2008-06-20
You have an older version of Flash; close Firefox and try this from the terminal:
```
sudo aptitude purge flashplugin-nonfree
```
then:
```
sudo aptitude update && sudo aptitude install flashplugin-nonfree
```

Then open Firefox again and see if the problem persists.

---

### Post by ayeshap on 2008-06-22
that didnt work either...the terminal said that flash was not installed after i entered the second code.

---

### Post by RomeReactor on 2008-06-22
It seems that Gutsy's most recent version of Flash is the one you already had installed; however, you should have had it installed right back with the second command. Make sure you don't have Gnash installed:
```
sudo aptitude purge gnash gnash-common mozilla-plugin-gnash
```
and try to install Flash again:
```
sudo aptitude install flashplugin-nonfree
```
If you get any error messages in the terminal, please post them.

Regarding this:
> **ayeshap said:**
> i have 7.10 ubuntu but i dont know which architecture (i actually have no idea what that is).
Sorry I overlooked that. Architecture refers to having an Intel, AMD or VIA processor (either running in 32 bit mode or 64 bit), or Power PC processor (which not many people do nowadays). So likely you have an Intel or AMD cpu. We need to know if Ubuntu is running in 32 bit or 64 bit (64 bit is faster for certain intensive tasks, but older processors are only 32 bit); you probably have Ubuntu 32 bit, but we need to make sure:
```
uname -m
```
Please post the output. 

You can install a newer version of Flash. If **uname -m** gives you **x86_64**, you have Ubuntu 64 bit and you need [this Flash package]("http://mirrors.xmission.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.124.0ubuntu1~gutsy1_amd64.deb"). If you get i386 or i686, [get this package instead]("http://mirrors.xmission.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.124.0ubuntu1~gutsy1_i386.deb"). Once you download it, close Firefox and double-click on it to install. Afterwards, open Firefox again and see you still have the problem.

---

