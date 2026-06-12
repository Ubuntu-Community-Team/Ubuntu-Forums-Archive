---
title: "Mplayer plugin for FF"
date: 2008-09-10
forum: New to Ubuntu
---

### Post by cartisdm on 2008-09-10
How can I test to see if my Mplayer plugin is working?  I've been trying to play a radio stream but I can't get it to play.  The sight suggested to install the Mplayer plugin for FF, which I did.  Still no luck.  The site seems to load all the way, the little ad plays just fine, then no music.

[This is the site I'm trying to play]("http://dc101.com/cc-common/ondemand/player.html?world=st")

If you can play it, is there anyway you can find out what plugin you're using to get it working?

---

### Post by Bakon Jarser on 2008-09-10
I'm using mplayer and it doesn't work.

---

### Post by Presto123 on 2008-09-10
Go into "Add/Remove" and search for "MPlayer". Get the "Mplayer Plugin" listed and restart Firefox. Should work that way...an ad from there just blasted through my house at almost 2am.

---

### Post by Presto123 on 2008-09-10
Well...see what happens, looks like even the plugin doesn't work. I have a feeling that their support is a bit off.

---

### Post by cartisdm on 2008-09-10
> **Presto123 said:**
> Go into "Add/Remove" and search for "MPlayer". Get the "Mplayer Plugin" listed and restart Firefox. Should work that way...an ad from there just blasted through my house at almost 2am.

That's how I installed the Mplayer plugin in the first place was through Add/Remove.  I feel like I have most of the basic plugins already for FF, is there anything else that might cause the site not to play?  I tried another online stream (basically set up through the same player as this one) and I couldn't get it work either

---

### Post by t0p on 2008-09-10
You can try to listen to a stream at [this site]("http://www.live365.com/index.live").

**EDIT:** Ah, I see you already have streams you want to play.

---

### Post by Vivaldi Gloria on 2008-09-10
> **cartisdm said:**
> The site seems to load all the way, the little ad plays just fine, then no music.

[This is the site I'm trying to play]("http://dc101.com/cc-common/ondemand/player.html?world=st")


I cannot try that site because it gives me

> Due to licensing restrictions, we are not able to allow access to the content you are requesting from outside the United States. We are sorry we can no longer provide access to Canada. If you currently reside in the United States, please select one of the options below to process your request. Please allow up to 60 hours to process your request.

But try this:

First enable medibuntu repos from

[http://www.medibuntu.org/](http://www.medibuntu.org/)

Follow the howto there to add medibuntu to your repo list. If you have ubuntu 8.04 hardy heron then these are the commands:

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

Now install mozilla-mplayer using the commands

```
sudo apt-get remove --purge totem-mozilla
sudo apt-get install mplayer mozilla-mplayer
```

I also followed pulseaudio fixes here: [http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

This setup played everything I tried. You can also try right clicking a mozilla-mplayer window and changing its settings.

---

### Post by cartisdm on 2008-09-10
Tried all those commands.  I needed to do them anyway since this is basically a fresh install, but still no luck.  I noticed that when reading the Help page that firefox users need to install the IE Tab plugin.  That isn't available for linux users, think that could be a problem?  There's gotta be somewhere out there (on ubuntu) that can play this stream:(

---

### Post by philinux on 2008-09-10
Can you play these streams.
[http://www.bbc.co.uk/radio/](http://www.bbc.co.uk/radio/)

If you can it's the site in question, if not it's the plugins.

---

### Post by sloggerkhan on 2008-09-10
At the station you first linked it keeps playing an ad for eastern motors.

---

### Post by cartisdm on 2008-09-10
> **philinux said:**
> Can you play these streams.
[http://www.bbc.co.uk/radio/](http://www.bbc.co.uk/radio/)

Yeah I can play those streams

> At the station you first linked it keeps playing an ad for eastern motors.

I know, it's annoying trust me.  They've had that ad for years.  Music starts after the ad plays a few times.  I normally just boot into windows and play the stream with IE or Chrome (which they need to make for linux!)

---

### Post by wolfen69 on 2008-09-10
so there's no conflicts, completely remove totem-mozilla that comes with ubuntu by default before install another plugin.

---

### Post by kansasnoob on 2008-09-10
It works for me but I don't use mplayer at all. My list of plugins (from typing about:PLUGINS into the URL box:

> Installed plugins
Find more information about browser plugins at mozilla.org.
Help for installing plugins is available from plugindoc.mozdev.org.
Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 10.0.0 d569

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes
Adobe Reader 8.0

    File name: nppdf.so
    The Adobe Reader plugin is used to enable viewing of PDF and FDF files from within the browser.

MIME Type 	Description 	Suffixes 	Enabled
application/pdf 	Portable Document Format 	pdf 	Yes
application/vnd.fdf 	Acrobat Forms Data Format 	fdf 	Yes
application/vnd.adobe.xfdf 	XML Version of Acrobat Forms Data Format 	xfdf 	Yes
application/vnd.adobe.xdp+xml 	Acrobat XML Data Package 	xdp 	Yes
application/vnd.adobe.xfd+xml 	Adobe FormFlow99 Data File 	xfd 	Yes
VLC Multimedia Plugin

    File name: libvlcplugin.so
    Version 0.8.6e Janus, copyright 1996-2007 The VideoLAN Team
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
GCJ Web Browser Plugin (using IcedTea) 1.0

    File name: gcjwebplugin.so
    The GCJ Web Browser Plugin (using IcedTea) executes Java applets.

MIME Type 	Description 	Suffixes 	Enabled
application/x-java-vm 	IcedTea 	class,jar 	Yes
application/x-java-applet 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.1 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.1.1 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.1.2 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.1.3 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.2 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.2.1 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.2.2 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.3 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.3.1 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.4 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.4.1 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.4.2 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.5 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.6 	IcedTea 	class,jar 	Yes
application/x-java-applet;jpi-version=1.6.0_00 	IcedTea 	class,jar 	Yes
application/x-java-bean 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.1 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.1.1 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.1.2 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.1.3 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.2 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.2.1 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.2.2 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.3 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.3.1 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.4 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.4.1 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.4.2 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.5 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.6 	IcedTea 	class,jar 	Yes
application/x-java-bean;jpi-version=1.6.0_00 	IcedTea 	class,jar 	Yes


What I have installed from synaptic:

mozilla-plugin-vlc
vlc
ALL vlc plugins BUT NOT vlc-plugin-alsa (I used the pulse audio fix)

totem
totem-common
totem-gstreamer
totem-plugins

ALL gstreamer

ALL sun-java6 EXCEPT -doc and -source

Regarding the aforementioned "pulse audio" fix:

>  Re: Fire fox is relly messed upp
I've had excellent luck solving Firefox crashes following this guide:

[http://ubuntuforums.org/showpost.php...&postcount=472](http://ubuntuforums.org/showpost.php...&postcount=472)

NOTE: there are specific sections for 64bit and i386!

When you're done just type into the URL box,

Quote:
about:PLUGINS
PLUGINS can be all lower case but I don't want to post

If it shows anything older than Shockwave Flash 10.0.0 d569 you can remove any older versions by:

Code:

sudo apt-get remove --purge flashplugin-nonfree

and:

Code:

cd ~/.mozilla
rm flashplayer.xpt libflashplayer.so

And then get the latest release candidate here:

[http://launchpadlibrarian.net/167664...Eppa2_i386.deb](http://launchpadlibrarian.net/167664...Eppa2_i386.deb)

It's a deb file so it's easy as falling off a log to install.

---

### Post by kansasnoob on 2008-09-10
Hmmmm, I see my link to the Flash 10 RC is broken, I'll look and see what's going on there. 

Just read post #6 in this thread regarding the pulse audio/flash fix:

[http://ubuntuforums.org/showthread.php?t=913400](http://ubuntuforums.org/showthread.php?t=913400)

---

### Post by cartisdm on 2008-09-10
I dunno guys, I tried installing those plugins that kansasnoob mentioned.  Still no luck.  I think I'm about to give up on this.  I just have having to boot into windows just to hear my favorite station.

---

### Post by kansasnoob on 2008-09-10
Maybe you need to remove some mplayer stuff, I'm not sure!

Before giving up I'd at least try:

```
sudo apt-get update
```

```
sudo apt-get upgrade
```

```
sudo apt-get -f install
```

And going to synaptic and seeing what mplayer stuff is installed. I've had nothing but heartache from mplayer!

---

