---
title: "Is it possible to play embedded quicktime on firefox 3 B5?"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by opendevlite on 2008-05-18
i've tried a lot of things lately but to no avail, is it possible to play embedded quicktime on firefox 3 Beta 5?

I'm referring to trailers in [http://www.apple.com/trailers/](http://www.apple.com/trailers/)

How did you do it?

---

### Post by opendevlite on 2008-05-18
bump

---

### Post by hyper_ch on 2008-05-18
it is not very much appreciated to bump a thread after only 3h...

---

### Post by philinux on 2008-05-18
Plays fine here with Totem external player embedded and standalone. Standalone totem does keep stopping to buffer though. The HD trailers trigger the standalone version.

Type 

about: plugins 
minus the space in the Firefox address bar and post the output

---

### Post by opendevlite on 2008-05-18
> **philinux said:**
> Plays fine here with Totem external player embedded and standalone. Standalone totem does keep stopping to buffer though. The HD trailers trigger the standalone version.

Type 

about: plugins 
minus the space in the Firefox address bar and post the output

Installed plugins
Find more information about browser plugins at mozilla.org.
Help for installing plugins is available from plugindoc.mozdev.org.
Default Plugin

    File name: libnullplugin.so
    The default plugin handles plugin data for mimetypes and extensions that are not specified and facilitates downloading of new plugins.

MIME Type 	Description 	Suffixes 	Enabled
* 	All types 	.* 	No
Demo Print Plugin for unix/linux

    File name: libunixprintplugin.so
    The demo print plugin for unix.

MIME Type 	Description 	Suffixes 	Enabled
application/x-print-unix-nsplugin 	Demo Print Plugin for Unix/Linux 	.pnt 	Yes
Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 9.0 r124

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes
iTunes Application Detector

    File name: librhythmbox-itms-detection-plugin.so
    This plug-in detects the presence of iTunes when opening iTunes Store URLs in a web page with Firefox.

MIME Type 	Description 	Suffixes 	Enabled
application/itunes-plugin 			Yes

---

### Post by philinux on 2008-05-18
Open synaptic package manager and install 

totem-mozilla

---

### Post by opendevlite on 2008-05-18
> **philinux said:**
> Open synaptic package manager and install 

totem-mozilla

Ubuntu 8.04 installs that by default, it doesn't work, I already tried that

---

### Post by TitanTiger on 2008-05-18
I'm having the same problem and tried the "apt-get install totem-mozilla" as well.  It just tells me it already has the latest version.

---

### Post by michaelzap on 2008-05-18
These trailers play fine for me with FF3b5. How about posting your about:plugins output as requested above? The key may be in there.

---

### Post by opendevlite on 2008-05-18
> **michaelzap said:**
> These trailers play fine for me with FF3b5. How about posting your about:plugins output as requested above? The key may be in there.

i already did, read post #5

---

### Post by okey666 on 2008-05-18
Plays for me, I use the mplayer Firefox plug-in with xine.

---

### Post by TitanTiger on 2008-05-18
Installed plugins
Find more information about browser plugins at mozilla.org.
Help for installing plugins is available from plugindoc.mozdev.org.


Shockwave Flash
    File name: npwrapper.libflashplayer.so
    Shockwave Flash 9.0 r124

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes
Default Plugin

    File name: libnullplugin.so
    The default plugin handles plugin data for mimetypes and extensions that are not specified and facilitates downloading of new plugins.

MIME Type 	Description 	Suffixes 	Enabled
* 	All types 	.* 	No
Demo Print Plugin for unix/linux

    File name: libunixprintplugin.so
    The demo print plugin for unix.

MIME Type 	Description 	Suffixes 	Enabled
application/x-print-unix-nsplugin 	Demo Print Plugin for Unix/Linux 	.pnt 	Yes
iTunes Application Detector

    File name: librhythmbox-itms-detection-plugin.so
    This plug-in detects the presence of iTunes when opening iTunes Store URLs in a web page with Firefox.

MIME Type 	Description 	Suffixes 	Enabled
application/itunes-plugin 			Yes
Totem Web Browser Plugin 2.22.1

    File name: libtotem-basic-plugin.so
    The Totem 2.22.1 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
application/x-ogg 	- 	ogg 	Yes
application/ogg 	Ogg multimedia 	ogg 	Yes
audio/ogg 	Ogg Audio 	oga 	Yes
audio/x-ogg 	Ogg Audio 	ogg 	Yes
video/ogg 	Ogg Video 	ogv 	Yes
video/x-ogg 	Ogg Video 	ogg 	Yes
application/annodex 	- 	anx 	Yes
audio/annodex 	- 	axa 	Yes
video/annodex 	- 	axv 	Yes
video/mpeg 	MPEG video 	mpg, mpeg, mpe 	Yes
audio/wav 	WAV audio 	wav 	Yes
audio/x-wav 	WAV audio 	wav 	Yes
audio/mpeg 	MP3 audio 	mp3 	Yes
application/x-nsv-vp3-mp3 	NullSoft video 	nsv 	Yes
video/flv 	Flash video 	flv 	Yes
Helix DNA Plugin: RealPlayer G2 Plug-In Compatible (compatible; Totem)

    File name: libtotem-complex-plugin.so
    The Totem 2.22.1 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
audio/x-pn-realaudio-plugin 	RealAudio document 	rpm 	Yes
VLC Multimedia Plugin (compatible Totem 2.22.1)

    File name: libtotem-cone-plugin.so
    The Totem 2.22.1 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
application/x-vlc-plugin 	unknown 		Yes
application/vlc 	unknown 		Yes
video/x-google-vlc-plugin 	unknown 		Yes
Windows Media Player Plug-in 10 (compatible; Totem)

    File name: libtotem-gmp-plugin.so
    The Totem 2.22.1 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
application/x-mplayer2 	AVI video 	avi, wma, wmv 	Yes
video/x-ms-asf-plugin 	ASF video 	asf, wmv 	Yes
video/x-msvideo 	AVI video 	asf, wmv 	Yes
video/x-ms-asf 	ASF video 	asf 	Yes
video/x-ms-wmv 	Windows Media video 	wmv 	Yes
video/x-wmv 	Windows Media video 	wmv 	Yes
video/x-ms-wvx 	Microsoft ASX playlist 	wmv 	Yes
video/x-ms-wm 	ASF video 	wmv 	Yes
application/x-ms-wms 	Windows Media video 	wms 	Yes
application/asx 	Microsoft ASX playlist 	asx 	Yes
audio/x-ms-wma 	Windows Media audio 	wma 	Yes
DivX® Web Player

    File name: libtotem-mully-plugin.so
    DivX Web Player version 1.4.0.233

MIME Type 	Description 	Suffixes 	Enabled
video/divx 	AVI video 	divx 	Yes
QuickTime Plug-in 7.2.0

    File name: libtotem-narrowspace-plugin.so
    The Totem 2.22.1 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
video/quicktime 	QuickTime video 	mov 	Yes
video/mp4 	MPEG-4 video 	mp4 	Yes
image/x-macpaint 	MacPaint Bitmap image 	pntg 	Yes
image/x-quicktime 	QuickTime image 	pict, pict1, pict2 	Yes
video/x-m4v 	MPEG-4 video 	m4v 	Yes

---

### Post by michaelzap on 2008-05-18
> **opendevlite said:**
> i already did, read post #5

Sorry! Somehow I missed that. I also have the following QT plugin installed:

QuickTime Plug-in 7.2.0

    File name: libtotem-narrowspace-plugin.so
    The Totem 2.22.1 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
video/quicktime 	QuickTime video 	mov 	Yes
video/mp4 	MPEG-4 video 	mp4 	Yes
image/x-macpaint 	MacPaint Bitmap image 	pntg 	Yes
image/x-quicktime 	QuickTime image 	pict, pict1, pict2 	Yes
video/x-m4v 	MPEG-4 video 	m4v 	Yes

---

### Post by opendevlite on 2008-05-18
> **okey666 said:**
> Plays for me, I use the mplayer Firefox plug-in with xine.

how did you do it?

---

### Post by philinux on 2008-05-18
The OP's plugins are missing all the lib-totem plugins.

Close all instances of firefox.
Go into your home folder, ctrl h to show hidden files. Open .mozilla then firefox then your ????????.default folder. Delete xpti.dat this will be rebuilt when you start FF.

---

### Post by opendevlite on 2008-05-18
> **philinux said:**
> The OP's plugins are missing all the lib-totem plugins.

Close all instances of firefox.
Go into your home folder, ctrl h to show hidden files. Open .mozilla then firefox then your ????????.default folder. Delete xpti.dat this will be rebuilt when you start FF.

still doesn't work

---

### Post by opendevlite on 2008-05-19
up

---

### Post by philinux on 2008-05-19
Can you post your list of FF plugins again?

---

### Post by THAiSi on 2008-05-19
```

Find more information about browser plug-ins at mozilla.org.
Help for installing plug-ins is available from plugindoc.mozdev.org.
Shockwave Flash
    File name: libflashplayer.so
    Shockwave Flash 9.0 r115

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes


```

everything worked great in gutsy, in hardy it's broken for me as well..

tried mplayer (plugin loaded, no image) tried vlc or something and all kinds of totem stuff.. nothing works.

I'm really fed up with hardy.

---

### Post by philinux on 2008-05-19
You need to type

```
about:plugins
```

no spaces, in the address bar of firefox then press enter. If this is what you did then we'll start again.

---

### Post by THAiSi on 2008-05-20
that's what i did

---

### Post by huczek on 2008-05-23
try the simplest way

in synaptic uninstall:
totem plugin for mozilla, vlc plugin for mozilla etc.
also in synaptic install mplayer-plugin for mozilla

in firefox preferences set up for quicktime metalink and video "use quicktime plug-in 6.0/7..."

...but i still have problem with [http://www.apple.com/getamac/ads/](http://www.apple.com/getamac/ads/)

Trailers work just fine.

---

### Post by frank002 on 2008-05-23
I was having the same problem as you with Gutsy. There was no way to play Quicktime trailers. With Hardy, I have had no problems playing any video. I suggest you go to Synaptic and make sure you have the following gstreamer plug ins:
     all the fluendo 
     the ffmpeg
     the pitfdll
     plug ins bad from the bad set and multiverse
     plug-ins-base 0.10.18-3
     plug-ins-good
     plug-ins-ugly 0.10.7-3 and 0.10.7-1
     pulseaudio
     0.10-tools
     0.10X
 I have these installed and have had no problems. Good Luck

---

### Post by THAiSi on 2008-05-27
I have all those packages installed but I still get the message from FF that there is no plugin to play the trailer

---

### Post by timcredible on 2008-06-08
here's what i found:

- apple.com/trailers play with totem plugin correctly, but not vlc or mplayer

- can't play the hd videos with any plugin

- can't play xm online radio with totem, but mplayer works well, vlc so-so

- totem and vlc plugin mess up some sites, can't even get to their videos

- i really, really hope that firefox 3 comes out soon and fixes all these issues.

- if you want to try these things, just uninstall one plugin, apply, then install another plugin, and restart firefox.  synaptic keeps the files cached locally, so it only takes a minute to switch between the plugins.

---

### Post by sudipta_cht on 2008-07-23
I found a fix... so in my firefox 3 it was downloading everything and then then said "Download Complete" for the .mov files with the mplayer-plugin written out. All I needed to do then was to right click and select "Play". :)

---

