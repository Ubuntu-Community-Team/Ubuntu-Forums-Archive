---
title: "How to play .mov file?"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by L Campbell on 2008-11-03
I have Hardy 8.04 on a PC and thought I had installed all the codecs (or whatever) to open any kind of files but when I try to open this:-

[http://www.dbfletcher.com/files/dbfletcher_capstan_ilona.mov](http://www.dbfletcher.com/files/dbfletcher_capstan_ilona.mov)

I get this message, "the player does not have the capabilities to play back this content".

I clicked on 'check for updates' but didn't see a suggestion as to what I should update to.

If you could give me a suggestion here, I would appreciate it.

TIA.

---

### Post by tuxxy on 2008-11-03
works fine here have you got w32codecs installed? sldo ubuntu-restricted-extras comes with plenty of codecs

---

### Post by eder.apt-get on 2008-11-03
Which browser is yours? Firefox? Maybe you should install a quicktime package in Synaptic, or gsteremer codecs and the w32codecs.

---

### Post by L Campbell on 2008-11-03
> **tuxxy said:**
> works fine here have you got w32codecs installed? sldo ubuntu-restricted-extras comes with plenty of codecs

Thanks for your interest.

I checked in Synaptic and I do have 'w32codecs' installed.

My browser is FF 3.0.3, just in case that is helpful.

Kind regards.

---

### Post by tuxxy on 2008-11-03
You could try installing mplayer as it comes with plenty of codecs

```
sudo apt-get install mplayer
```

---

### Post by dark_harmonics on 2008-11-03
Yes mplayer is much better IMO for use with firefox and often times opens files that totem does not. Replace totem with mplayer in firefox with:

Remove Totem Component
```
sudo apt-get remove totem-mozilla 
```

Add Mplayer Component
```
sudo apt-get install mozilla-mplayer
```

---

### Post by philinux on 2008-11-03
> **L Campbell said:**
> Thanks for your interest.

I checked in Synaptic and I do have 'w32codecs' installed.

My browser is FF 3.0.3, just in case that is helpful.

Kind regards.

This mov plays fine here on a clean install with restricted extras installed. 
Post the contents of 
```
about:plugins
```Put that in the firefox address bar.
It's totem that plays these so nothing fancy needed.
```
QuickTime Plug-in 7.2.0

 File name:  /usr/lib/totem/gstreamer/libtotem-narrowspace-plugin.so The [Totem]("http://www.gnome.org/projects/totem/") 2.24.2 plugin handles video and audio streams.   MIME Type Description Suffixes Enabled    video/quicktime QuickTime video mov Yes   video/mp4 MPEG-4 video mp4 Yes   image/x-macpaint MacPaint Bitmap image pntg Yes   image/x-quicktime Macintosh Quickdraw/PICT drawing pict, pict1, pict2 Yes   video/x-m4v MPEG-4 video m4v Yes
```

---

### Post by L Campbell on 2008-11-03
> **tuxxy said:**
> You could try installing mplayer as it comes with plenty of codecs

```
sudo apt-get install mplayer
```

Thanks for the suggestion but it hasn't changed anything.  Still getting the same error message.

Kind regards.

---

### Post by L Campbell on 2008-11-03
> **philinux said:**
> This mov plays fine here on a clean install with restricted extras installed. 
Post the contents of 
```
about:plugins
```Put that in the firefox address bar.
It's totem that plays these so nothing fancy needed.
```
QuickTime Plug-in 7.2.0

 File name:  /usr/lib/totem/gstreamer/libtotem-narrowspace-plugin.so The [Totem]("http://www.gnome.org/projects/totem/") 2.24.2 plugin handles video and audio streams.   MIME Type Description Suffixes Enabled    video/quicktime QuickTime video mov Yes   video/mp4 MPEG-4 video mp4 Yes   image/x-macpaint MacPaint Bitmap image pntg Yes   image/x-quicktime Macintosh Quickdraw/PICT drawing pict, pict1, pict2 Yes   video/x-m4v MPEG-4 video m4v Yes
```

Thanks.

Shockwave Flash

    File name: libflashplayer.so
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
Java(TM) Plug-in 1.6.0_07-b06

    File name: libjavaplugin_oji.so
    Java(TM) Plug-in 1.6.0_07

MIME Type 	Description 	Suffixes 	Enabled
application/x-java-vm 	Java 		Yes
application/x-java-applet 	Java 		Yes
application/x-java-applet;version=1.1 	Java 		Yes
application/x-java-applet;version=1.1.1 	Java 		Yes
application/x-java-applet;version=1.1.2 	Java 		Yes
application/x-java-applet;version=1.1.3 	Java 		Yes
application/x-java-applet;version=1.2 	Java 		Yes
application/x-java-applet;version=1.2.1 	Java 		Yes
application/x-java-applet;version=1.2.2 	Java 		Yes
application/x-java-applet;version=1.3 	Java 		Yes
application/x-java-applet;version=1.3.1 	Java 		Yes
application/x-java-applet;version=1.4 	Java 		Yes
application/x-java-applet;version=1.4.1 	Java 		Yes
application/x-java-applet;version=1.4.2 	Java 		Yes
application/x-java-applet;version=1.5 	Java 		Yes
application/x-java-applet;version=1.6 	Java 		Yes
application/x-java-applet;jpi-version=1.6.0_07 	Java 		Yes
application/x-java-bean 	Java 		Yes
application/x-java-bean;version=1.1 	Java 		Yes
application/x-java-bean;version=1.1.1 	Java 		Yes
application/x-java-bean;version=1.1.2 	Java 		Yes
application/x-java-bean;version=1.1.3 	Java 		Yes
application/x-java-bean;version=1.2 	Java 		Yes
application/x-java-bean;version=1.2.1 	Java 		Yes
application/x-java-bean;version=1.2.2 	Java 		Yes
application/x-java-bean;version=1.3 	Java 		Yes
application/x-java-bean;version=1.3.1 	Java 		Yes
application/x-java-bean;version=1.4 	Java 		Yes
application/x-java-bean;version=1.4.1 	Java 		Yes
application/x-java-bean;version=1.4.2 	Java 		Yes
application/x-java-bean;version=1.5 	Java 		Yes
application/x-java-bean;version=1.6 	Java 		Yes
application/x-java-bean;jpi-version=1.6.0_07 	Java 		Yes
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
DivXÂ® Web Player

    File name: libtotem-mully-plugin.so
    DivX Web Player version 1.4.0.233

MIME Type 	Description 	Suffixes 	Enabled
video/divx 	AVI video 	divx 	Yes

---

### Post by gandaran on 2008-11-03
the url works fine with totem and gstreamer plugins, no need for mplayer,
just look in synaptic for the gstreamer plugins you are missing and can still install.

---

### Post by L Campbell on 2008-11-03
> **gandaran said:**
> the url works fine with totem and gstreamer plugins, no need for mplayer,
just look in synaptic for the gstreamer plugins you are missing and can still install.

Thanks for your interest.

It appears, in Synaptic, that there are about 30 gstreamer items and I have about 14 of them installed.

Is there a specific item that I need, or should I just install all of them?

---

### Post by gandaran on 2008-11-03
first, install only gstreamer0.10 plugins, just don't install the documentation and the debugger ones, install the rest, ffmpeg ugly,good and bad and multiverse, the w32codecs are useless to totem unless you have the gstreamer pitfdll installed

---

### Post by L Campbell on 2008-11-03
> **gandaran said:**
> first, install only gstreamer0.10 plugins, just don't install the documentation and the debugger ones, install the rest, ffmpeg ugly,good and bad and multiverse, the w32codecs are useless to totem unless you have the gstreamer pitfdll installed

OK, I think I followed your instructions properly but I'm still getting the same error message.

Is there any list of codes I can show you that might indicate whether I have  something missing?

Kind regards.

---

### Post by philinux on 2008-11-03
sudo apt-get install ubuntu-restricted-extras

or use synaptic.

---

### Post by L Campbell on 2008-11-03
> **philinux said:**
> sudo apt-get install ubuntu-restricted-extras

or use synaptic.

Thanks again but it looks like I already have everything.

qwer@qwer-desktop:~$ sudo apt-get install ubuntu-restricted-extras
[sudo] password for qwer: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-restricted-extras is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
qwer@qwer-desktop:~$ 

Kind regards.

---

### Post by philinux on 2008-11-03
From your first post right click the link and choose "save link as".
Try and then play it from the downloaded file.
This is a workaround for now.
I raised this bug which i just remembered. I think that intrepid is the fix. Cant be 100% sure.
[https://bugs.launchpad.net/ubuntu/+source/totem/+bug/227701](https://bugs.launchpad.net/ubuntu/+source/totem/+bug/227701)

---

### Post by gandaran on 2008-11-03
I don't get it, aren't you trying to play this url in firefox totem plugin?  [http://www.dbfletcher.com/files/dbfletcher_capstan_ilona.mov](http://www.dbfletcher.com/files/dbfletcher_capstan_ilona.mov)
whats real player have to do with it?
linux real player only plays real audio and video

---

### Post by L Campbell on 2008-11-03
> **philinux said:**
> From your first post right click the link and choose "save link as".
Try and then play it from the downloaded file.
This is a workaround for now.
I raised this bug which i just remembered. I think that intrepid is the fix. Cant be 100% sure.
[https://bugs.launchpad.net/ubuntu/+source/totem/+bug/227701](https://bugs.launchpad.net/ubuntu/+source/totem/+bug/227701)

YIKES!!  That worked perfectly, thanks.

I saved it into 'Documents' and it opened without a problem from there.

Why would whatever opened it from there in Documents, not open it from the link?  One of those great mysteries, huh?    :-)

Kind regards.

---

### Post by philinux on 2008-11-03
Mystery indeed. Maybe it's something in Intrepid that fixes this bug. Kernel or whatever, or the totem plugin or a combination of both.

---

### Post by L Campbell on 2008-11-03
> **gandaran said:**
> I don't get it, aren't you trying to play this url in firefox totem plugin?  [http://www.dbfletcher.com/files/dbfletcher_capstan_ilona.mov](http://www.dbfletcher.com/files/dbfletcher_capstan_ilona.mov)
whats real player have to do with it?
linux real player only plays real audio and video

Sorry, I'm kind of a dunce and don't know how to answer your question intelligently.  :-)

I thought I had all the codecs needed to run everything but I don't question which program opened what, because most of that still goes over my head at this point.

Kind regards.

---

### Post by L Campbell on 2008-11-03
> **philinux said:**
> Mystery indeed. Maybe it's something in Intrepid that fixes this bug. Kernel or whatever, or the totem plugin or a combination of both.

Well, the bottom line is that you have given me a simple fix and I really appreciate it.

Kind regards.

---

### Post by kansasnoob on 2008-11-03
Following up a bit here. 

First of all, did you remove totem-mozilla and install mozilla-mplayer as instructed in post #6? Only as a matter of personal preference I'd stick with totem-mozilla, and if you do make sure you also have totem-gstreamer installed.

As far as realplayer, if you installed it from synaptic, I'd also remove it the same way.

Oops, never mind.

---

