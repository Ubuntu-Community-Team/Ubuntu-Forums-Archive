---
title: "Flash problems"
date: 2008-09-23
forum: New to Ubuntu
---

### Post by MikesGuitar on 2008-09-23
For so reason even though I installed the Flash that came with Ubunutu I still can't watch any videos (youtube) It says I may have Java disabled ( I dont) or that I might need the latest version of adobe flash (im pretty sure that i do) Any suggestions?

---

### Post by Joeb454 on 2008-09-23
Try installing [ubuntu-restricted-extras]("apt://ubuntu-restricted-extras") That should install flash, java, some common Microsoft fonts, amongst other commonly used media codecs etc.

---

### Post by drtre on 2008-09-23
Once i had the same problem. But after updating the installed flash via update manager the problem automatically got solved. I suggest update your flash. However its just a suggestion. There is a alternative choice for flash in Ubuntu but I just don't remember the name and I suggest you not use it cuz it really sucks. Thought this might help u.

---

### Post by HittingSmoke on 2008-09-23
> **Joeb454 said:**
> Try installing [ubuntu-restricted-extras]("apt://ubuntu-restricted-extras") That should install flash, java, some common Microsoft fonts, amongst other commonly used media codecs etc.

I just switched from Kubuntu to Ubuntu with a fresh install and after knowing a bit more than my first try around just installed the ubuntu-restricted-extras package instead of trying everything individually. The install went fine but Flash, MP3, and DVD support didn't work still. The only thing noticeable that it changed was Java installed.

I still had to install Flash, MP3 and DVD support myself so you might try just installing the Flash package separately

---

### Post by MikesGuitar on 2008-09-23
How do I update it? When I get the message on youtube i tried to click on the link and download the latest version of Flash but I had no idea how to install or use it or where to go from there. If this is what you mean let me know how i can do it

---

### Post by drtre on 2008-09-23
> **MikesGuitar said:**
> How do I update it? When I get the message on youtube i tried to click on the link and download the latest version of Flash but I had no idea how to install or use it or where to go from there. If this is what you mean let me know how i can do it

u have to do this using the update manager of the ubuntu. Update manager frequently checks for the newest packages. Check it, it should contain an update for flash. Btw u better wait for the better responses. There might be better way. It's just a way I used and worked out for me.

---

### Post by MikesGuitar on 2008-09-23
Will do, it says my stuff it all up to date anyway...

---

### Post by kansasnoob on 2008-09-23
Start by typing about:PLUGINS in the URL box. That'll show a script like this:

> Installed plugins
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
    Shockwave Flash 10.0.0 d525

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes
VLC Multimedia Plugin

    File name: libvlcplugin.so
    Version 0.8.6h Janus, copyright 1996-2007 The VideoLAN Team
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


Oh, and tell me if this is Hardy Heron (8.04).

---

