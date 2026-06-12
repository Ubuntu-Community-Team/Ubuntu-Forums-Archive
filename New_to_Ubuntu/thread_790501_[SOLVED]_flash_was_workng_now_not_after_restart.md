---
title: "[SOLVED] flash was workng now not after restart"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by hufferd on 2008-05-11
I put this under a new heading for a better response andthought I would also add a bit more info


am starting to become very angry with good old ubuntu maybe its my years of using windows and now when somethings wrong not knowing where to look.

I listen to music [here]("http://www.martiniinthemorning.com/")

Good music btw if you like old Jazz....... I loaded the Flash plug in and all the streaming drivers Firefox said I needed.. And this morning it WAS working... I then had to do a restart (forget why) but anyway did a restart now it wont work all I get isa a grey box in the player I even tried to uninstall and reinstall plugins.. Nota zip-o stil borked.

Not there yet but just something as simple as this Im ready to go back to windows...

Any ideas?


~D 


I am running 8.04 32bit ver. /  And fire fox that came with that I believe its 3 beta?

---

### Post by philinux on 2008-05-11
Ok, now post the output of 

```
about:plugins
```

---

### Post by SunnyRabbiera on 2008-05-11
Alright, well lets get cracking.
I think the main source of your issue is using a 32bit kernel on a 64bit system, the reason is that most of your codecs/ flash/ and other things are mainly intended to work on a 32bit environment only, and even though you have made a way around this maybe using the 64bit version of ubuntu might serve you better.
I am not 100% sure on how to get multimedia to work on the 64bit version of ubuntu but what you ask should not be impossible.

---

### Post by hufferd on 2008-05-11
> **philinux said:**
> Ok, now post the output of 

```
about:plugins
```

And ok totally noob question here 

where exactly will I run "about: plugins" (nospaces of course  I have tried in a few places ?

---

### Post by SunnyRabbiera on 2008-05-11
> **hufferd said:**
> And ok totally noob question here 

where exactly will I run "about: plugins" (nospaces of course  I have tried in a few places ?

you run that one in firefox, in firefox just type it into the address bar.

---

### Post by crjackson on 2008-05-11
> **hufferd said:**
> I put this under a new heading for a better response andthought I would also add a bit more info


am starting to become very angry with good old ubuntu maybe its my years of using windows and now when somethings wrong not knowing where to look.

I listen to music [here]("http://www.martiniinthemorning.com/")

Good music btw if you like old Jazz....... I loaded the Flash plug in and all the streaming drivers Firefox said I needed.. And this morning it WAS working... I then had to do a restart (forget why) but anyway did a restart now it wont work all I get isa a grey box in the player I even tried to uninstall and reinstall plugins.. Nota zip-o stil borked.


Not there yet but just something as simple as this Im ready to go back to windows...

Any ideas?


~D 


I am running 8.04 32bit ver. /  And fire fox that came with that I believe its 3 beta?


Hardy comes with default settings that select swf palyer and icedtea java.  The first thing I would do is go to your pakage manager and remove every last vestige of flash support and java support.

Log off and log back in...

Then go back to synaptic package manager and install flashplugin-nonfree, sun java 6 (all of it), AND follow-up with ubuntu-restricted extras for that extra shot of goodness...

Log off (I know, it's not supposed to be needed, but it's the only way to find out if the settings will work after a reboot) and then login again.

Hopefully you will now have working flash/java.  I'm listening to YOUR favorite JAZZ station right now as we talk.

Let us know what happened...

BTW... Look at my specs...  Not that much different than yours...  I'm running 32-bit and 64-bit on this machine.

---

### Post by hufferd on 2008-05-11
> Installed plugins
Find more information about browser plugins at mozilla.org.
Help for installing plugins is available from plugindoc.mozdev.org.
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



**This was the output from about: plugins**

---

### Post by philinux on 2008-05-11
Well that looks similar to mine. Previous poster suggested complete removal and reinstll of flash and java.

Before you do that close firefox open a terminal, Applications>Accessories>terminal and type

firefox -safe-mode

choose continue in safe mode when dialog box appears, dont tick any boxes. See if your site will run flash.

---

### Post by hufferd on 2008-05-11
> **crjackson said:**
> Hardy comes with default settings that select swf palyer and icedtea java.  The first thing I would do is go to your pakage manager and remove every last vestige of flash support and java support.

Log off and log back in...

Then go back to synaptic package manager and install flashplugin-nonfree, sun java 6 (all of it), AND follow-up with ubuntu-restricted extras for that extra shot of goodness...

Log off (I know, it's not supposed to be needed, but it's the only way to find out if the settings will work after a reboot) and then login again.

Hopefully you will now have working flash/java.  I'm listening to YOUR favorite JAZZ station right now as we talk.

Let us know what happened...

BTW... Look at my specs...  Not that much different than yours...  I'm running 32-bit and 64-bit on this machine.

[B]I tried whats stated above before I saw this next post 

Going to try this now[/B]
> Well that looks similar to mine. Previous poster suggested complete removal and reinstll of flash and java.

Before you do that close firefox open a terminal, Applications>Accessories>terminal and type

firefox -safe-mode

choose continue in safe mode when dialog box appears, dont tick any boxes. See if your site will run flash.

---

### Post by hufferd on 2008-05-11
Hmmmm 
tried both of the things prior posted suggested and still nothing ....  
maybe another browser :lolflag:

---

### Post by philinux on 2008-05-11
Shutdown the pc and reboot. This happened to me last week, similar but with java not flash. Rebooting got it going after I reinstalled java.

---

### Post by gandaran on 2008-05-11
hufferd
      if that site means a lot to you I suggest you change the media plugin, I tried it to with the totem plugin and it worked only once, now it doesn't work! this site is just like bbc, sometimes works sometimes not.
try other plugins like vlc or the xine plugin (uninstall first the totem plugin) the xine plugin is the best plugin for online streaming, works everywhere, only problem is it doesn't have a control bar.
you can also uninstall totem gstreamer and install totem xine, this way you will still be using the totem plugin but with the xine engine.

---

### Post by hufferd on 2008-05-11
Hey you guys thank you very much for all your help I did another unistall of all plugins then a reinstall and its working who knows  :confused: 

I'm not sure if its the site or something on my end 

ButI will try and do as you say gandaran


Thanks for your time ALL!

~D

---

