---
title: "Embedded WMV's won't play in FireFox"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by Yellowbelly on 2008-08-11
I have to take defensive driving to get rid of a ticket I got. So anyway it uses all wmv videos embedded. It looks like the player comes up but it's like the video doesn't load. I click play and nothing happens. Here's what I see: A big black box with an overly large, pixelized, out of focus play button sorta in the middle of the box with the normal play button, progress bar and volume thing. I tried switching players through preferences but it didn't do anything. I figured I'd try opera but it doesn't work because it needs a wmv plugin and I have NO CLUE where to get that even after searching. Is there anyway to fix this?

---

### Post by Crafty Kisses on 2008-08-11
Do you have the proper codecs installed?

---

### Post by Yellowbelly on 2008-08-11
I should. Usually it finds those things automatically right? I guess i'll check synaptic to see if I can find anything it might have left out.

btw, this is firefox3 with the latest updates.

---

### Post by Yellowbelly on 2008-08-11
I installed Ubuntu-Restriced-Extras just to make sure and it did nothing. In fact, it took a step backward and said there was no video. I checked it on a windows comp on IE and it worked so the video is there. But apparently this codec is flat out broke or something. Is there a different codec that I could try? Is there a wmv plugin for Opera? I tried looking for one with no luck...for gnu/linux anyway.

---

### Post by mc4100 on 2008-08-11
It sounds like a codec problem, so if you are unable to get the right codecs (look for the gstreamer plugins in synaptic), then you could try a different firefox plugin than the default one (which I'm pretty sure you're using).
You could try **vlc** as it has excellent multimedia codec support
```
sudo apt-get remove totem-mozilla && sudo apt-get install mozilla-plugin-vlc
```

---

### Post by Yellowbelly on 2008-08-11
still nada. Does it matter that the totem wmv codec is still selected as preferred application? VLC wasn't even an option to select. Maybe I could look for it, choose to browse for proper application, but I don't even know where to start.

---

### Post by mc4100 on 2008-08-11
First, to clarify, we want to find out **which** plugin is trying (and failing) to play the WMV. So open Firefox and type, in the address-bar, 
```
about:plugins
```
and either look for "video/x-wmv", then see which plugins its listed under, or better yet, just copy the all the info here.

Edit: Forget that, if you go to Edit -> Preferences in Firefox, and then select "Applications", what options do you have under the type "Windows Media Video"? -- is this what you were referring to earlier?

---

### Post by Yellowbelly on 2008-08-11
it says: use windows media player plugin in firefox
Other options are: Movie Player, Other, Save, and Always Ask


it seems like it used to say in totem during that phrase but i'm not 100%

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

can't hurt any

---

### Post by mc4100 on 2008-08-11
Can you post what it says when you type this:
```
dpkg -s mozilla-plugin-vlc
```
If it says it's not installed, then try
```
sudo apt-get remove totem-mozilla; sudo apt-get install mozilla-plugin-vlc
```
again. And if that doesn't work, it might be good to find out why, and try other alternatives (like the mplayer Firefox plugin).

---

### Post by Yellowbelly on 2008-08-12
Package: mozilla-plugin-vlc
Status: install ok installed
Priority: optional
Section: graphics
Installed-Size: 144
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Architecture: i386
Source: vlc
Version: 0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3.1
Depends: libc6 (>= 2.1.3), libgcc1 (>= 1:4.1.1-21), libice6 (>= 1:1.0.0), libsm6, libstdc++6 (>= 4.1.1-21), libvlc0 (>= 0.8.6.release.e+x264svn20071224+faad2.6.1), libx11-6, libxt6, vlc, vlc-nox (= 0.8.6.release.e+x264svn20071224+faad2.6.1-0ubuntu3.1)
Description: multimedia plugin for web browsers based on VLC
 This plugin adds support for MPEG, MPEG2, DVD, DivX, Ogg/Vorbis and many
 more formats to your Gecko-based web browser (Firefox, Galeon, etc.). The
 decoding process is done by VLC and the output window is embedded in a
 webpage or directly in the browser window. There is also support for
 fullscreen display and javascript control.
 .
 VLC is the VideoLAN project's media player. It plays MPEG, MPEG2, MPEG4,
 DivX, MOV, WMV, QuickTime, mp3, Ogg/Vorbis files, DVDs, VCDs, and multimedia
 streams from various network sources.
Npp-Applications: ec8030f7-c20a-464f-9b0e-13a3a9e97384, 92650c4d-4b8e-4d2a-b7eb-24ecf4f6b63a
Npp-Mimetype: audio/mpeg, audio/x-mpeg, video/mpeg, video/x-mpeg, video/mpeg-system, video/x-mpeg-system, video/mpeg4, audio/mpeg4, application/mpeg4-iod, application/mpeg4-muxcodetable, video/x-msvideo, video/quicktime, application/x-ogg, application/ogg, application/x-vlc-plugin, video/x-ms-asf-plugin, video/x-ms-asf, application/x-mplayer2, video/x-ms-wmv, application/x-google-vlc-plugin, audio/wav, audio/x-wav, audio/3gpp, video/3gpp, audio/3gpp2, video/3gpp2
Npp-Name: VLC Multimedia Plugin
Original-Maintainer: Sam Hocevar (Debian packages) <sam+deb@zoy.org>

---

### Post by Archmage on 2008-08-12
Kindly note that this WMV could be DRM-Protected. Than you can't play it at all. Did you try to play it in Totem in the non-emblemed way?

---

### Post by LowSky on 2008-08-12
do you have w32codecs installed? the more codecs the merrier

```
wget -c http://packages.medibuntu.org/pool/non-free/w/w32codecs/w32codecs_20071007-0medibuntu2_i386.deb
sudo dpkg -i w32codecs_20071007-0medibuntu2_i386.deb
```

---

### Post by Yellowbelly on 2008-08-12
> **Archmage said:**
> Kindly note that this WMV could be DRM-Protected. Than you can't play it at all. Did you try to play it in Totem in the non-emblemed way?

good point. I played in firefox but on windows last year though. What's teh totem non-emblemed way?

---

### Post by Archmage on 2008-08-13
> **Yellowbelly said:**
> good point. I played in firefox but on windows last year though. What's teh totem non-emblemed way?

I did mean that you simply open it in totem. You can do this sometimes. E.g. if you did a right-click and see that the location is http//:[www.video.com/cool_video.wmv](www.video.com/cool_video.wmv) you can simply open in totem the location http//:[www.video.com/cool_video.wmv](www.video.com/cool_video.wmv) and see what is happening.

---

### Post by Yellowbelly on 2008-08-14
says it's not found...

---

