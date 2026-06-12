---
title: "[SOLVED] Cannot see video on cnn.com"
date: 2008-06-18
forum: New to Ubuntu
---

### Post by jlambeth1 on 2008-06-18
When trying to watch videos on cnn.com I get the message that I need to install the Flash plugin.  I already have the flash non-free plugin installed and have tried re-installing it but I still have no luck.  Any suggestions?

---

### Post by sharks on 2008-06-18
try installing mozilla-mplayer.

---

### Post by sdowney717 on 2008-06-18
type in the browser url
about:plugins  
(about colon plugins )
do you see it ?

---

### Post by jlambeth1 on 2008-06-18
Tried installing mozilla-mplayer through terminal and it says that it is already installed.  This is the output that I get when I type in about:plugins

dobe Reader 8.0

    File name: nppdf.so
    The Adobe Reader plugin is used to enable viewing of PDF and FDF files from within the browser.

MIME Type 	Description 	Suffixes 	Enabled
application/pdf 	Portable Document Format 	pdf 	Yes
application/vnd.fdf 	Acrobat Forms Data Format 	fdf 	Yes
application/vnd.adobe.xfdf 	XML Version of Acrobat Forms Data Format 	xfdf 	Yes
application/vnd.adobe.xdp+xml 	Acrobat XML Data Package 	xdp 	Yes
application/vnd.adobe.xfd+xml 	Adobe FormFlow99 Data File 	xfd 	Yes
Shockwave Flash

    File name: npwrapper.libflashplayer.so
    Shockwave Flash 10.0 b218

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes
iTunes Application Detector

    File name: librhythmbox-itms-detection-plugin.so
    This plug-in detects the presence of iTunes when opening iTunes Store URLs in a web page with Firefox.

MIME Type 	Description 	Suffixes 	Enabled
application/itunes-plugin 			Yes
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
DivX Browser Plug-In

    File name: mplayerplug-in-dvx.so
    mplayerplug-in 3.50

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets

MIME Type 	Description 	Suffixes 	Enabled
video/divx 	DivX Media Format 	divx 	Yes
video/vnd.divx 	DivX Media Format 	divx 	Yes
QuickTime Plug-in 6.0 / 7

    File name: mplayerplug-in-qt.so
    mplayerplug-in 3.50

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets

MIME Type 	Description 	Suffixes 	Enabled
video/quicktime 	Quicktime 	mov 	Yes
video/x-quicktime 	Quicktime 	mov 	Yes
image/x-quicktime 	Quicktime 	mov 	Yes
video/quicktime 	Quicktime 	mp4 	Yes
video/quicktime 	Quicktime - Session Description Protocol 	sdp 	Yes
application/x-quicktimeplayer 	Quicktime 	mov 	Yes
application/smil 	SMIL 	smil 	Yes
RealPlayer 9

    File name: mplayerplug-in-rm.so
    mplayerplug-in 3.50

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets

MIME Type 	Description 	Suffixes 	Enabled
audio/x-pn-realaudio 	RealAudio 	ram,rm 	Yes
application/vnd.rn-realmedia 	RealMedia 	rm 	Yes
application/vnd.rn-realaudio 	RealAudio 	ra,ram 	Yes
video/vnd.rn-realvideo 	RealVideo 	rv 	Yes
audio/x-realaudio 	RealAudio 	ra 	Yes
audio/x-pn-realaudio-plugin 	RealAudio 	rpm 	Yes
application/smil 	SMIL 	smil 	Yes
Windows Media Player Plugin

    File name: mplayerplug-in-wmp.so
    mplayerplug-in 3.50

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets

MIME Type 	Description 	Suffixes 	Enabled
application/asx 	Media Files 	* 	Yes
video/x-ms-asf-plugin 	Media Files 	* 	Yes
video/x-msvideo 	AVI 	avi,* 	Yes
video/msvideo 	AVI 	avi,* 	Yes
application/x-mplayer2 	Media Files 	* 	Yes
application/x-ms-wmv 	Microsoft WMV video 	wmv,* 	Yes
video/x-ms-asf 	Media Files 	asf,asx,* 	Yes
video/x-ms-wm 	Media Files 	wm,* 	Yes
video/x-ms-wmv 	Microsoft WMV video 	wmv,* 	Yes
audio/x-ms-wmv 	Windows Media 	wmv,* 	Yes
video/x-ms-wmp 	Windows Media 	wmp,* 	Yes
application/x-ms-wmp 	Windows Media 	wmp,* 	Yes
video/x-ms-wvx 	Windows Media 	wvx,* 	Yes
audio/x-ms-wax 	Windows Media 	wax,* 	Yes
audio/x-ms-wma 	Windows Media 	wma,* 	Yes
application/x-drm-v2 	Windows Media 	asx,* 	Yes
audio/wav 	Microsoft wave file 	wav,* 	Yes
audio/x-wav 	Microsoft wave file 	wav,* 	Yes
mplayerplug-in 3.50

    File name: mplayerplug-in.so
    mplayerplug-in 3.50

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets

MIME Type 	Description 	Suffixes 	Enabled
video/mpeg 	MPEG 	mpg,mpeg 	Yes
audio/mpeg 	MPEG 	mpg,mpeg 	Yes
video/x-mpeg 	MPEG 	mpg,mpeg 	Yes
video/x-mpeg2 	MPEG2 	mpv2,mp2ve 	Yes
audio/mpeg 	MPEG 	mpg,mpeg 	Yes
audio/x-mpeg 	MPEG 	mpg,mpeg 	Yes
audio/mpeg2 	MPEG audio 	mp2 	Yes
audio/x-mpeg2 	MPEG audio 	mp2 	Yes
video/mp4 	MPEG 4 Video 	mp4 	Yes
video/3gpp 	MPEG 4 Video 	mp4,3gp 	Yes
audio/mpeg3 	MPEG audio 	mp3 	Yes
audio/x-mpeg3 	MPEG audio 	mp3 	Yes
audio/x-mpegurl 	MPEG url 	m3u 	Yes
audio/mp3 	MPEG audio 	mp3 	Yes
application/x-ogg 	Ogg Vorbis Media 	ogg 	Yes
audio/ogg 	Ogg Vorbis Audio 	ogg 	Yes
audio/x-ogg 	Ogg Vorbis Audio 	ogg 	Yes
application/ogg 	Ogg Vorbis / Ogg Theora 	ogg 	Yes
audio/flac 	FLAC Audio 	flac 	Yes
audio/x-flac 	FLAC Audio 	flac 	Yes
video/fli 	FLI animation 	fli,flc 	Yes
video/x-fli 	FLI animation 	fli,flc 	Yes
video/x-flv 	Flash Video 	flv 	Yes
video/vnd.vivo 	VivoActive 	viv,vivo 	Yes
application/x-nsv-vp3-mp3 	Nullsoft Streaming Video 	nsv 	Yes
audio/x-mod 	Soundtracker 	mod 	Yes
audio/basic 	Basic Audio File 	au,snd 	Yes
audio/x-basic 	Basic Audio File 	au,snd 	Yes
Java(TM) Plug-in 1.6.0_06-b02

    File name: libjavaplugin_oji.so
    Java(TM) Plug-in 1.6.0_06

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
application/x-java-applet;jpi-version=1.6.0_06 	Java 		Yes
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
application/x-java-bean;jpi-version=1.6.0_06 	Java 		Yes

---

### Post by abn91c on 2008-06-18
cnn video does not like firefox or linux

---

### Post by fenian on 2008-06-18
CNN uses flash you need to install the nonfree version...

> sudo apt-get install flashplugin-nonfree

please link the url you are trying to view all the cnn videos I have tried worked and I only have the flashplugin-nonfree installed.

---

### Post by jlambeth1 on 2008-06-18
I already have the nonfree plugin install.  I used to watch videos when I was running Gutsy Gibbon but can't seem to figure it out on Hardy Heron.

---

### Post by fenian on 2008-06-18
Make sure you don't have gnash installed as it will make itself the default flash player...
> 
sudo apt-get remove gnash

---

### Post by jlambeth1 on 2008-06-18
I have confirmed that gnash is not installed.

---

### Post by fenian on 2008-06-18
go to the directory...

/usr/lib/flashplugin-nonfree

Is it there?
Is libflashplayer.so there?

---

### Post by jlambeth1 on 2008-06-18
Yes, they are both there.

---

### Post by fenian on 2008-06-18
Please post the link you are trying to view.
Also you can try going to you tube and viewing a video there to see if the flash plugin is working.Or just click [this link]("http://www.youtube.com/watch?v=Yu_moia-oVI").

---

### Post by jlambeth1 on 2008-06-18
Here is the link- [http://www.cnn.com/video/#/video/world/2008/06/17/roth.ny.scooter.craze.cnn](http://www.cnn.com/video/#/video/world/2008/06/17/roth.ny.scooter.craze.cnn)

I also tried the youtube link you sent and it does not work either.  I am kind of glad that one didn't work since it was a Rick Astley song! ;)

---

### Post by z0mbie on 2008-06-18
The links worked for me, however it didn't work for me when I had the Adobe Flash 10 beta installed. It seems like you have Flash 10 beta installed:

> File name: npwrapper.libflashplayer.so
Shockwave Flash 10.0 b218

I would remove it and install Flash 9 from the Ubuntu repositories.

---

### Post by ubuntu1sttimer on 2008-06-18
Having same problem with CNN videos as our are,jlambeth1. Fenian's link does work. Using 8.04 and have had this problem for some time. Am also having some other problems with FF3 but they are not associated with Flash.

Even my old "junker" WIN98 machine does the CNN videos but Ubuntu with FF just doesn't want to.

---

### Post by jlambeth1 on 2008-06-18
OK, I removed flashplayer 10 with the packet manager and it shows that 9 is installed.  Now when I click on the cnn link, I get a brief black flash and then the same message that says I don't have the plugin installed.  How do I remove npwrapper.libflashplayer.so?

---

### Post by jlambeth1 on 2008-06-18
Anyone?

---

### Post by fenian on 2008-06-18
I think that its in the directory...

/var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so

you can use the command...

> sudo nautilus

to open nautilus as root then navigtate  to /var/lib/flashplugin-nonfree/
then delete the file npwrapper.libflashplayer.so.

---

### Post by Yuki_Nagato on 2008-06-19
When I installed Flash, I completely forgot about the repositories.

I downloaded the stuff from the Adobe website.

[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash]("http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash")


Directions from the Adobe website:

> 1. Click the "Download .tar.gz" link. A dialog box will appear asking you where to save the file.
2. Save the .tar.gz file to your desktop and wait for the file to download completely.
3. Unpackage the file. A directory called install_flash_player_9_linux will be created.
(Or ```
tar -xvzf packagename.tar.gz
``` in the terminal.)
4. In terminal, navigate to this directory and type ./flashplayer-installer to run the installer. Click Enter. The installer will instruct you to shut down your browser(s).
5. Once the installation is complete, the plug-in will be installed in your Mozilla browser. To verify, launch Mozilla and choose Help > About Plug-ins from the browser menu.


Flash works flawlessly for me.

---

### Post by jlambeth1 on 2008-06-19
I tried to navigate to the npwrapper.libflashplayer.so file but it was not there so I assume it is gone. I tried to unpack the tar.gz file and this is what I got in the terminal.
[IMG]http://i293.photobucket.com/albums/mm44/jlambeth1/Screenshot-Terminal.png[/IMG]

---

### Post by swisscow on 2008-06-19
Having the same problem as yourself and have to go to work now so will mess around later.

But after you untar the flash package you need to "cd" to the new folder that has been made before you run the installer

---

### Post by jlambeth1 on 2008-06-19
OK, I finally figured it out.  I extracted the install_flash_player_9_linux package and then went into the folder.  I clicked on the flashplayer installer file and chose to open it in a terminal.  Everyone went smooth after that and now I can see video!  Thanks to everyone for all of your help.  As an added bonus, I can now see my streaming baseball games grom mlb.com!

---

