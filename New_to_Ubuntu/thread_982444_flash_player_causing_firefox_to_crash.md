---
title: "flash player causing firefox to crash"
date: 2008-11-14
forum: New to Ubuntu
---

### Post by Matt26 on 2008-11-14
i have recently installed the latest version of flashplugin-nonfree from the repositories on ubuntu 8.10, and now Firefox (latest version) crashes without warning- it just closes unexpectedly.  is there a way to fix this?

---

### Post by MasterSander on 2008-11-14
Is it with every flash file you play or? I'd try reinstalling

---

### Post by Matt26 on 2008-11-14
> **MasterSander said:**
> Is it with every flash file you play or? I'd try reinstalling

no flash files being played (i assume you mean interactively like a video).  the site that i was on when firefox last crashed had a flash navigation menu, and i wasn't even at the computer when the browser crashed.

---

### Post by caro on 2008-11-14
I had the same problem on 8.04.  After I removed libflashsupport the problem went away.  Haven't had a problem with 8.10.

---

### Post by redbob on 2008-11-14
After installed Intrepid, flashplugin-nonfree didn't work for anymore. I simply download flash 10 from [www.adobe.com](www.adobe.com) site and install it from console. By this way there's no error.

---

### Post by Matt26 on 2008-11-14
> **caro said:**
> I had the same problem on 8.04.  After I removed libflashsupport the problem went away.  Haven't had a problem with 8.10.

i just checked and i don't have libflashsupport installed.

---

### Post by Matt26 on 2008-11-14
> **redbob said:**
> After installed Intrepid, flashplugin-nonfree didn't work for anymore. I simply download flash 10 from [www.adobe.com](www.adobe.com) site and install it from console. By this way there's no error.

which version of the flash player did you choose to download from the adobe site (deb, tar.gz etc)?

---

### Post by Meshach on 2008-11-14
Here is the flash player and it works perfectly.

Select the tar.gz one from here (which is the one I used):

[LINK]("http://get.adobe.com/flashplayer/?promoid=BUIGP")



Best Regards,
Meshach

---

### Post by XxX_VLAD_XxX on 2008-11-15
> **redbob said:**
> After installed Intrepid, flashplugin-nonfree didn't work for anymore. I simply download flash 10 from [www.adobe.com](www.adobe.com) site and install it from console. By this way there's no error.

I have another problem maybe you can help me, I already download the .deb package and install it, but firefox keep asking me the plug in, I open Youtube and keeps asking me for a download of the flash player.

I think I have to install it with the fire fox extension browser but I can't find it...

---

### Post by Meshach on 2008-11-15
Go here: [https://addons.mozilla.org/en-US/firefox/browse/type:7]("https://addons.mozilla.org/en-US/firefox/browse/type:7")

And the second one down is adobe flash player.


Have fun.
Meshach

---

### Post by InfectedWithDrew on 2008-11-15
> **Meshach said:**
> Here is the flash player and it works perfectly.

Select the tar.gz one from here (which is the one I used):

[LINK]("http://get.adobe.com/flashplayer/?promoid=BUIGP")



Best Regards,
Meshach

This would work, but I'd use the .deb, since it's a simple as double-clicking it to install.  Synaptic takes care of it.

---

### Post by Matt26 on 2008-11-15
> **InfectedWithDrew said:**
> This would work, but I'd use the .deb, since it's a simple as double-clicking it to install.  Synaptic takes care of it.

i would suggest installing this version of the flash player from the repositories as there is an updated version there- as soon as i installed the .deb from adobe's website, updated manager notified me of an update to the flash player.

---

### Post by InfectedWithDrew on 2008-11-15
> **Matt26 said:**
> i would suggest installing this version of the flash player from the repositories as there is an updated version there- as soon as i installed the .deb from adobe's website, updated manager notified me of an update to the flash player.

You must have received that message in error.  There would not be an updated version of Flash on a third-party site and not on Adobe's site.  That would be like tigerdirect selling Windows 7 copies right now.

---

### Post by XxX_VLAD_XxX on 2008-11-15
Ok Adobe Flash player doesn't work on my firefox, it keeps asking me for the plugin. I have Ubuntu 8.04 and this is what I've done

download and install the .deb package
download via apt the restricted-extensions

I have installed the plugin but is as if Firefox can't find it

---

### Post by gandaran on 2008-11-15
> **XxX_VLAD_XxX said:**
> Ok Adobe Flash player doesn't work on my firefox, it keeps asking me for the plugin. I have Ubuntu 8.04 and this is what I've done

download and install the .deb package
download via apt the restricted-extensions

I have installed the plugin but is as if Firefox can't find it
can you post the output of
locate libflash (type in terminal)
and
```
about:plugins (type in firefox url bar)
```

did you install another version of firefox?

---

### Post by XxX_VLAD_XxX on 2008-11-15
Ok
```
locate libflash 
```

the output is

```
/usr/lib/openoffice/program/libflash680li.so

```

I have Fifeox 3 Beta 5 the one that comes with Ubuntu 8.04 I have installed some others plugins 'cause when I go to Tools-> extensions -> plugins     I have a long list but no Flash Player

that second line, how I should write it? I'm confused

```
 about:plugins firefox3 
```

---

### Post by gandaran on 2008-11-15
> **XxX_VLAD_XxX said:**
> Ok
```
locate libflash 
```

the output is

```
/usr/lib/openoffice/program/libflash680li.so

```

I have Fifeox 3 Beta 5 the one that comes with Ubuntu 8.04 I have installed some others plugins 'cause when I go to Tools-> extensions -> plugins     I have a long list but no Flash Player

that second line, how I should write it? I'm confused

```
 about:plugins firefox3 
```
just type the code in firefox url bar this code, post the full output
```
about:plugins
```

---

### Post by gandaran on 2008-11-15
still running firefox 3 beta? haven't you installed the updates? you should have firefox 3.0.3

---

### Post by XxX_VLAD_XxX on 2008-11-15
OK this is the output (I was writing that in the terminal! ah newbies)

    Nombre de archivo: libflashplayer.so
    Shockwave Flash 9.0 r124

Tipo MIME 	Descripción 	Sufijos 	Habilitado
application/x-shockwave-flash 	Shockwave Flash 	swf 	Si
application/futuresplash 	FutureSplash Player 	spl 	Si


It's in spanish 'cause I'm in South America, but I believe they are installed it 'Si' means 'yes'

Maybe you can write a link to download the latest firefox version or
the code like

sudo apt-get install "firefox 3.0  or something"

---

### Post by XxX_VLAD_XxX on 2008-11-15
The FULL  output is like this: 

Shockwave Flash

    Nombre de archivo: libflashplayer.so
    Shockwave Flash 9.0 r124

Tipo MIME 	Descripción 	Sufijos 	Habilitado
application/x-shockwave-flash 	Shockwave Flash 	swf 	Si
application/futuresplash 	FutureSplash Player 	spl 	Si
Java(TM) Plug-in 1.6.0_07-b06

    Nombre de archivo: libjavaplugin_oji.so
    Java(TM) Plug-in 1.6.0_07

Tipo MIME 	Descripción 	Sufijos 	Habilitado
application/x-java-vm 	Java 		Si
application/x-java-applet 	Java 		Si
application/x-java-applet;version=1.1 	Java 		Si
application/x-java-applet;version=1.1.1 	Java 		Si
application/x-java-applet;version=1.1.2 	Java 		Si
application/x-java-applet;version=1.1.3 	Java 		Si
application/x-java-applet;version=1.2 	Java 		Si
application/x-java-applet;version=1.2.1 	Java 		Si
application/x-java-applet;version=1.2.2 	Java 		Si
application/x-java-applet;version=1.3 	Java 		Si
application/x-java-applet;version=1.3.1 	Java 		Si
application/x-java-applet;version=1.4 	Java 		Si
application/x-java-applet;version=1.4.1 	Java 		Si
application/x-java-applet;version=1.4.2 	Java 		Si
application/x-java-applet;version=1.5 	Java 		Si
application/x-java-applet;version=1.6 	Java 		Si
application/x-java-applet;jpi-version=1.6.0_07 	Java 		Si
application/x-java-bean 	Java 		Si
application/x-java-bean;version=1.1 	Java 		Si
application/x-java-bean;version=1.1.1 	Java 		Si
application/x-java-bean;version=1.1.2 	Java 		Si
application/x-java-bean;version=1.1.3 	Java 		Si
application/x-java-bean;version=1.2 	Java 		Si
application/x-java-bean;version=1.2.1 	Java 		Si
application/x-java-bean;version=1.2.2 	Java 		Si
application/x-java-bean;version=1.3 	Java 		Si
application/x-java-bean;version=1.3.1 	Java 		Si
application/x-java-bean;version=1.4 	Java 		Si
application/x-java-bean;version=1.4.1 	Java 		Si
application/x-java-bean;version=1.4.2 	Java 		Si
application/x-java-bean;version=1.5 	Java 		Si
application/x-java-bean;version=1.6 	Java 		Si
application/x-java-bean;jpi-version=1.6.0_07 	Java 		Si
iTunes Application Detector

    Nombre de archivo: librhythmbox-itms-detection-plugin.so
    This plug-in detects the presence of iTunes when opening iTunes Store URLs in a web page with Firefox.

Tipo MIME 	Descripción 	Sufijos 	Habilitado
application/itunes-plugin 			Si
Default Plugin

    Nombre de archivo: libnullplugin.so
    The default plugin handles plugin data for mimetypes and extensions that are not specified and facilitates downloading of new plugins.

Tipo MIME 	Descripción 	Sufijos 	Habilitado
* 	All types 	.* 	No
Demo Print Plugin for unix/linux

    Nombre de archivo: libunixprintplugin.so
    The demo print plugin for unix.

Tipo MIME 	Descripción 	Sufijos 	Habilitado
application/x-print-unix-nsplugin 	Demo Print Plugin for Unix/Linux 	.pnt 	Si
Totem Web Browser Plugin 2.22.1

    Nombre de archivo: libtotem-basic-plugin.so
    The Totem 2.22.1 plugin handles video and audio streams.

Tipo MIME 	Descripción 	Sufijos 	Habilitado
application/x-ogg 	- 	ogg 	Si
application/ogg 	multimedia Ogg 	ogg 	Si
audio/ogg 	audio Ogg 	oga 	Si
audio/x-ogg 	audio Ogg 	ogg 	Si
video/ogg 	vídeo Ogg 	ogv 	Si
video/x-ogg 	vídeo Ogg 	ogg 	Si
application/annodex 	- 	anx 	Si
audio/annodex 	- 	axa 	Si
video/annodex 	- 	axv 	Si
video/mpeg 	vídeo MPEG 	mpg, mpeg, mpe 	Si
audio/wav 	audio WAV 	wav 	Si
audio/x-wav 	audio WAV 	wav 	Si
audio/mpeg 	audio MP3 	mp3 	Si
application/x-nsv-vp3-mp3 	NullSoft video 	nsv 	Si
video/flv 	vídeo Flash 	flv 	Si
Helix DNA Plugin: RealPlayer G2 Plug-In Compatible (compatible; Totem)

    Nombre de archivo: libtotem-complex-plugin.so
    The Totem 2.22.1 plugin handles video and audio streams.

Tipo MIME 	Descripción 	Sufijos 	Habilitado
audio/x-pn-realaudio-plugin 	documento RealAudio 	rpm 	Si
VLC Multimedia Plugin (compatible Totem 2.22.1)

    Nombre de archivo: libtotem-cone-plugin.so
    The Totem 2.22.1 plugin handles video and audio streams.

Tipo MIME 	Descripción 	Sufijos 	Habilitado
application/x-vlc-plugin 	desconocido 		Si
application/vlc 	desconocido 		Si
video/x-google-vlc-plugin 	desconocido 		Si
Windows Media Player Plug-in 10 (compatible; Totem)

    Nombre de archivo: libtotem-gmp-plugin.so
    The Totem 2.22.1 plugin handles video and audio streams.

Tipo MIME 	Descripción 	Sufijos 	Habilitado
application/x-mplayer2 	vídeo AVI 	avi, wma, wmv 	Si
video/x-ms-asf-plugin 	vídeo ASF 	asf, wmv 	Si
video/x-msvideo 	vídeo AVI 	asf, wmv 	Si
video/x-ms-asf 	vídeo ASF 	asf 	Si
video/x-ms-wmv 	Windows Media video 	wmv 	Si
video/x-wmv 	Windows Media video 	wmv 	Si
video/x-ms-wvx 	Microsoft ASX playlist 	wmv 	Si
video/x-ms-wm 	vídeo ASF 	wmv 	Si
application/x-ms-wms 	Windows Media video 	wms 	Si
application/asx 	Microsoft ASX playlist 	asx 	Si
audio/x-ms-wma 	Windows Media audio 	wma 	Si
DivX® Web Player

    Nombre de archivo: libtotem-mully-plugin.so
    DivX Web Player version 1.4.0.233

Tipo MIME 	Descripción 	Sufijos 	Habilitado
video/divx 	vídeo AVI 	divx 	Si
QuickTime Plug-in 7.2.0

    Nombre de archivo: libtotem-narrowspace-plugin.so
    The Totem 2.22.1 plugin handles video and audio streams.

Tipo MIME 	Descripción 	Sufijos 	Habilitado
video/quicktime 	QuickTime video 	mov 	Si
video/mp4 	vídeo MPEG-4 	mp4 	Si
image/x-macpaint 	imagen en mapa de bits de MacPaint 	pntg 	Si
image/x-quicktime 	QuickTime image 	pict, pict1, pict2 	Si
video/x-m4v 	vídeo MPEG-4 	m4v 	Si

---

### Post by gandaran on 2008-11-15
so you have adobe flash 9 installed and it shows in firefox, doesn't it work?
do you have any addon like flashblock or addblock installed?
when you go to firefox»tools»addons»plugins do you see a shockwave flash 9 plugin? is it enabled?

---

### Post by XxX_VLAD_XxX on 2008-11-15
I can see it in add ons, it is enable, I do have installed Flash video Resources Downloader, but I installed it long after the Sockwave Flash.

How can I upgrade it

---

### Post by gandaran on 2008-11-15
> **XxX_VLAD_XxX said:**
> I can see it in add ons, it is enable, I do have installed Flash video Resources Downloader, but I installed it long after the Sockwave Flash.

How can I upgrade it
upgrade flash? open synaptic package manager, scroll down to flashplugin-nonfree, mark for complete removal and click the apply button
next go adobe site [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/) download the flash 10 .deb package for ubuntu 8.04.
to install double click the package and hit the install button.

try disabling the Flash video Resources Downloader plugin just to check if it's the addon causing the problem

for updating firefox, enable the update channels in system » administration » software sources » update tab, tic the security and recommended channels (first two lines)

---

