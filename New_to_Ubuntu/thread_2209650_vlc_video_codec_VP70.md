---
title: "vlc video codec VP70"
date: 2014-03-06
forum: New to Ubuntu
---

### Post by micahpage on 2014-03-06
I have a bunch of avi files that when started with VLC, pops up this error:
> No suitable decoder module:
VLC does not support the audio or video format "VP70". Unfortunately there is no way for you to fix this.

After googling around i found the same error on ubuntu which others say the fix seems to be the package
```
ubuntu-restricted-extras
```

but after trying that it still doesnt work.

This is on an ubuntu 12.04 distro

---

### Post by andrew.46 on 2014-03-06
Some discussion of this previously:

[http://ubuntuforums.org/showthread.php?t=1719370](http://ubuntuforums.org/showthread.php?t=1719370)

with not a great resolution I am afraid, unless you are using a 32bit installation of Ubuntu?

---

### Post by mc4man on 2014-03-06
Probably just one way - a 32bit mplayer with w32codecs installed
(missed Andrew's post, ....

---

### Post by micahpage on 2014-03-06
no it is a 64 bit OS

I have it running in windows 8 OK with the K Lite Codec pack. I was wondering if i would be able to rencode it in a normal format that both windows and linux can read?

---

### Post by andrew.46 on 2014-03-06
> **micahpage said:**
> I have it running in windows 8 OK with the K Lite Codec pack. I was wondering if i would be able to rencode it in a normal format that both windows and linux can read?

Unfortunately not from within your current 64bit Linux installation, only a 32bit MPlayer / MEncoder has a chance there. This can be done on a 64bit installation of Ubuntu (a compiled and installed 32bit MPlayer/MEncoder)  but it would be unnecessarily complex I suspect...

---

### Post by mc4man on 2014-03-06
I would suspect that you could find something for Windows to re-encode this files,  you should be able to search out solutions pretty easily.

---

### Post by mc4man on 2014-03-06
There is a 'possible', see "But" below,  Ubuntu solution, at least for playback, maybe re-encodin thru mencoder.

However it may depend on what release of Ubuntu & will require installing quite a number of i386 packages so I'd look to Windows as mentioned.

Anyway I had a new 14.04 install so decided to see if mplayer:i386 would install. took a couple of min.
Apt can't resolve all the deps directly so had to help it out to start, then it did install the 32 bit bit mplayer. After adding w32codecs it plays a sample vp7 file fine as far as video. So on that thought adding mencoder:i386 may work, ect.

(then if re-encoding was successful I'd remove 4 i386 packages & autoremove the rest.
screen shows - if inclined I'll lay out, BUT - 
If you look below you'll notice no audio "Cannot find codec for audio format 0x500.", I forget if we ever figured that out, though it's possible your files use something different for audio...


> $ mplayer '/home/doug/Videos/starsky-700.vp7' 
MPlayer 1.1-4.8 (C) 2000-2012 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/doug/Videos/starsky-700.vp7.
libavformat version 54.20.3 (external)
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
VIDEO:  [VP70]  704x272  12bpp  23.976 fps  695.0 kbps (84.8 kbyte/s)
Load subtitles in /home/doug/Videos/
Failed to open VDPAU backend libvdpau_i965.so: cannot open shared object file: No such file or directory
[vdpau] Error when calling vdp_device_create_x11: 1
==========================================================================
Opening video decoder: [vfwex] Win32/VfWex video codecs
Loading codec DLL: 'vp7vfw.dll'
Win32 LoadLibrary failed to load: /usr/lib/codecs/vp7vfwLOC.dll
Loaded DLL driver vp7vfw.dll at 10000000
[PP] Using codec's postprocessing, max q = 9.
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 704x272 => 704x272 Packed YUY2 
Selected video codec: [vp7] vfm: vfwex (On2 VP7 Personal Codec)
==========================================================================
==========================================================================
Cannot find codec for audio format 0x500.
Audio: no sound
Starting playback...
V:   3.5  84/ 84  8%  0%  0.0% 0 0 


---

### Post by micahpage on 2014-03-07
im not really savy on the codecs/media.

Its an .avi file, the audio plays in both linux/windows, the video does not for linux. Im not even sure on how to determine the audio type of the avi file. The only reason i assumed the video type was VP70 was that the text file that came with the media said that he encoded it with this to save space. And he gave a windows solution only, the K Lite Codec pack solution. 

But because im not really good at this, i could bypass a google soution to re-encode (via windows or linux) to fix it, without even knowing that i am looking at the answer. I am looking for the simplest solution. My media player is running ubuntu 12.04 (soon to be 14.04), so i need the end result to play on linux. But since i have a windows desktop as well, i dont have to re-encode it with linux. If it is easier and more effective to re-encode it to something else in wodinws, then i can do that as well. My question then is: Would it be easier? What would I use in windows to re-encode it? What would i re-encode the video part as?

The sample that is with it is:
[http://www.mediafire.com/download/eyjw35jeleea2y2/Sample.avi](http://www.mediafire.com/download/eyjw35jeleea2y2/Sample.avi)

---

### Post by mc4man on 2014-03-07
I would look for a windows means to re-encode
(using mplayer:i386/mencoder:i386 on an Ubuntu install that allows would probably work as your audio is ac-3 but I did that as more of a curiosity than practical solution. You can't have both i386 & amd64 versions of some libraires at the same time, libavcodec for example, so you'd lose anything depending on those amd64 libs

Your sample is corrupted or something for first couple of seconds, then is ok. Maybe this weekend I'll see if I can re-encode on windows but again I think you could search out a windows solution/method

---

### Post by micahpage on 2014-03-08
the sample for me plays the audio all the way thoguh, but never plays the video.

---

### Post by andrew.46 on 2014-03-08
> **micahpage said:**
> the sample for me plays the audio all the way thoguh, but never plays the video.

Just tried this sample at work (Windows) with mpc and it is unplayable. Has there been a glitch in the upload?

---

### Post by mc4man on 2014-03-08
Pretty simple to convert in windows, only complicated here by using my new laptop which has win8 which I'm somewhat lost on.
Anyway simply just use virtualdub, used xvid (installed virtualdub, on2 v7, xvid (use 32 bit virtualdub, doesn't matter if on 64 bit windows, it works fine

Converted sample.avi is here, just converted the video & copied audio, (should play in browser though larger than it should be  or better  just wget it or r.click > save link as
(note that I didn't look into any thing concerning vid quality, ect., just to see. Whether there are other programs, encoders could be investigated by you.

As mentioned before there is an issue with the first few seconds of the video, didn't try to fix...

[http://ubuntuone.com/0M7M9YO20QmexSKoVxLf1a](http://ubuntuone.com/0M7M9YO20QmexSKoVxLf1a)

---

### Post by micahpage on 2014-03-09
I am not sure if this is suppose to be like this. The video shown on virtualdub is all blocky the entire way through. If i try to play it in vrtualdub i get a new error for no audio decompressor found

I have been following along this thread
[http://forum.videohelp.com/threads/300187-VirtualDub-No-audio-decompressor-could-be-found](http://forum.videohelp.com/threads/300187-VirtualDub-No-audio-decompressor-could-be-found)
but the process does not work as it did for them

I am not concerned at all with video quality.

EDIT:
OK i am not sure what exactly the propblem was there, but i started posting the AC3ACM files all over, in plugins directory and outside, and it finally worked. So now the video plays in Videodub as any media player. OK so how do you now convert to xvid? I am assuming that is what i want to convert the video to?

EDIT2:
I havent really came across anything explaining how to convert a VP70 to XVID tutorial. I tried Video -> Comvpression -> and change it to Xvid and then export it as raw video, but the file doesnt play at all after that.

EDT3:
OK IT was save as avi not export. Figured it out. Took awhile, but whatever.

 oh, wow...this takes a loooong time. Is there a way to do every episode of every season, or do you have to actually do one episode at a time? Or is there away to automate the process?

---

### Post by andrew.46 on 2014-03-25
Looks like some good news is here:

On2 VP7 decoder
[http://git.videolan.org/?p=ffmpeg.git;a=commit;h=89f2f5dbd7a23e7ec1073d3c08d46093a01a4135](http://git.videolan.org/?p=ffmpeg.git;a=commit;h=89f2f5dbd7a23e7ec1073d3c08d46093a01a4135)

and on my system:

```

andrew@ilium~$ **[COLOR="#FF0000"]ffmpeg -codecs 2>/dev/null | grep -i vp7[/COLOR]**
 D.V.L. vp7                  On2 VP7

```

and ffplay plays this file (sound and video) on my 64bit system :)

---

### Post by Rob Sayer on 2014-03-26
This is why I use 2 programs for video playback.  People assume vlc will play everything and it won't.  SMplayer will play some video codecs that nothing else I've tried will.  It has all the mplayer codecs (obviously) and it's own additional library.  It's worth a try.

---

### Post by mc4man on 2014-03-26
> **andrew.46 said:**
> Looks like some good news is here:

On2 VP7 decoder
[http://git.videolan.org/?p=ffmpeg.git;a=commit;h=89f2f5dbd7a23e7ec1073d3c08d46093a01a4135](http://git.videolan.org/?p=ffmpeg.git;a=commit;h=89f2f5dbd7a23e7ec1073d3c08d46093a01a4135)

and on my system:

```

andrew@ilium~$ **[COLOR="#FF0000"]ffmpeg -codecs 2>/dev/null | grep -i vp7[/COLOR]**
 D.V.L. vp7                  On2 VP7

```

and ffplay plays this file (sound and video) on my 64bit system :)
Should be good to go with an updated ffmpeg in ones mplayer source, as long as audio isn't vp7

---

### Post by andrew.46 on 2014-03-26
> **Rob Sayer said:**
> This is why I use 2 programs for video playback.  People assume vlc will play everything and it won't.  SMplayer will play some video codecs that nothing else I've tried will.  It has all the mplayer codecs (obviously) and it's own additional library.  It's worth a try.

vlc / SMPlayer / MPlayer *all *depend on FFmpeg's libavcodec so much depends on the version of this and the way in which libavcodec has been implemented by each application. And the additional wildcard of the 32bit external codecs for MPlayer / SMPlayer...

---

### Post by andrew.46 on 2014-03-26
And now MPlayer has come to the party:

```

------------------------------------------------------------------------
r37065 | cehoyos | 2014-03-25 23:41:35 +1100 (Tue, 25 Mar 2014) | 1 line

Support FFmpeg's VP7 decoder.
------------------------------------------------------------------------

```

which should show as follows:

```

andrew@ilium~$ mplayer -vc help | grep -i vp7

**[COLOR="#FF0000"]ffvp7       ffmpeg    working   FFmpeg VP7  [vp7][/COLOR]**
vp7         vfwex     working   On2 VP7 Personal Codec  [vp7vfw.dll]
andrew@ilium~$ 

```

Don't you love Open Source :)

---

### Post by Navneet_Kumar on 2014-03-27
First don't download the latest version of VLC from its website..just go along with the version present in the ubuntu store...............re-installing may fix the problem....or just download the ubuntu restricted extras package using :
sudo apt-get install ubuntu-restricted-extras

---

### Post by andrew.46 on 2014-03-27
> **Navneet_Kumar said:**
> First don't download the latest version of VLC from its website..just go along with the version present in the ubuntu store...............re-installing may fix the problem....or just download the ubuntu restricted extras package using :
sudo apt-get install ubuntu-restricted-extras

Have you been able to play back vp7 videos using this technique? The OP has posted a sample file for a test earlier in this thread or this is this one:

```

wget samples.mplayerhq.hu/V-codecs/VP7/potter-500.vp7

```

It is my suspicion that you may have some trouble.

---

### Post by David D. on 2014-03-27
I was doing some searches on this subject and one of the links was to the Ask VideoLan site.  The person making the query was asking VideoLan to include the VP7 codec in VLC.  The response was to "ask Google to make it open-source".

---

### Post by FakeOutdoorsman on 2014-03-27
Despite Google's lack of action VP7 decoding has recently been reverse engineered by FFmpeg without their help.

---

### Post by mc4man on 2014-03-27
> **andrew.46 said:**
> 
```

wget samples.mplayerhq.hu/V-codecs/VP7/potter-500.vp7

```
.
Have you been able to get audio on that one?

---

### Post by andrew.46 on 2014-03-27
> **mc4man said:**
> Have you been able to get audio on that one?

No unfortunately :(

---

### Post by andrew.46 on 2014-03-28
> **FakeOutdoorsman said:**
> Despite Google's lack of action VP7 decoding has recently been reverse engineered by FFmpeg without their help.

Remember when Google used to be the good guys?  :(

---

### Post by Navneet_Kumar on 2014-03-28
Ya Once there used to be a giant good army of googlers............:D

---

### Post by andrew.46 on 2014-04-24
> **mc4man said:**
> Have you been able to get audio on that one?

Almost :). FFmpeg now has [an On2 avc decoder ]("http://git.videolan.org/?p=ffmpeg.git;a=commit;h=e2834567d73bd1e46478ba67ac133cb8ef5f50fd")which fails with this sample but soon perhaps...

Also in MPlayer:

```

------------------------------------------------------------------------
r37160 | cehoyos | 2014-04-24 16:42:02 +1000 (Thu, 24 Apr 2014) | 1 line

Add decoding support for On2 AVC audio codec.
------------------------------------------------------------------------

```

which is compiling as I type :)

---

### Post by Prince_Tom on 2014-11-23
[COLOR=#000000][FONT=Verdana]For MS Windows Operating Systems:

VP7 or VP70 is a compressed video data created by On2 Technologies Inc. Further details about this can be found in the link below.[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]http://www.mediafire.com/download/g87u1nycag83i8g/VP7_or_70_Data_Format_and_Decoder_Overview.pdf[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]You can play this type of file by downloading and installing following audio/video codec pack: [/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]http://www.mediafire.com/download/u919ueuakmbiclw/Audio_Codec_Pack_-_VP70.exe[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]This solve the [/FONT][/COLOR][Windows Media Player]("http://www.videohelp.com/tools/Windows-Media-Player")[COLOR=#000000][FONT=Verdana] error C00D10D1: On2 VP70 (VP70) or Missing codec: On2 VP70 (VP70) error.[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]These play file in Windows Media Player only after installing codec pack above.[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]I hope it helps. Thanks for reading and plz like.[/FONT][/COLOR]

[COLOR=#000000][FONT=Verdana]GUDLUK [/FONT][/COLOR][IMG]http://forum.videohelp.com/images/smilies/smile.gif[/IMG]

---

### Post by Evil Wayz on 2015-07-21
> **andrew.46 said:**
> Looks like some good news is here:

On2 VP7 decoder
[http://git.videolan.org/?p=ffmpeg.git;a=commit;h=89f2f5dbd7a23e7ec1073d3c08d46093a01a4135](http://git.videolan.org/?p=ffmpeg.git;a=commit;h=89f2f5dbd7a23e7ec1073d3c08d46093a01a4135)

and on my system:

```

andrew@ilium~$ **[COLOR=#FF0000]ffmpeg -codecs 2>/dev/null | grep -i vp7[/COLOR]**
 D.V.L. vp7                  On2 VP7

```

and ffplay plays this file (sound and video) on my 64bit system :)

Running 14.04.2
OK, when I type that command in terminal I get the same output.  But what Am I supposed to do with that git ink?  I read in an article that ffmpeg AND vlc 2.2 support on2 and VP7.  I tried upgrading to VLC 3 and i ending up hosing my system with broken packages.  So I'm back to VLC 2.2.1 but all i get is audio.  Normally it wouldn't be a big thing but I just found all six seasons of chips and of course the guy who encoded it used an obscure codec that Google owns now.  Mplayer/smplayer is supposed to support it to, but this is what I get when I try that:
```
/usr/bin/mplayer -noquiet -slave -identify -nofs -sub-fuzziness 1 -ao pulse -nodr -double -stop-xscreensaver -nomouseinput -input nodefault-bindings:conf=/dev/null -nokeepaspect -wid 88080433 -monitorpixelaspect 1 -subfont-osd-scale 3 -ass -embeddedfonts -ass-line-spacing 0 -ass-font-scale 1 -ass-styles /home/wolf/.config/smplayer/styles.ass -subcp ISO-8859-1 -subpos 100 -volume 2 -cache 2048 -osdlevel 0 -vf-add screenshot -noslices -channels 2 -af-add scaletempo -af-add equalizer=0:0:0:0:0:0:0:0:0:0 -softvol -softvol-max 110 /home/wolf/CHiPs DVD Extra.avi

MPlayer2 2.0-701-gd4c5b7f-2ubuntu2 (C) 2000-2012 MPlayer Team
Terminal type `unknown' is not defined.

Playing /home/wolf/CHiPs DVD Extra.avi.
Cache size set to 2048 KiB

Cache fill:  0.00% (0 bytes)   

Detected file format: AVI (Audio Video Interleaved) (libavformat)
[avi @ 0x7f6176d2d600]max_analyze_duration reached
ID_VIDEO_ID=0
[lavf] stream 0: video (unknown), -vid 0
ID_AUDIO_ID=0
[lavf] stream 1: audio (ac3), -aid 0
Clip info:
 TCOD: 0
ID_CLIP_INFO_NAME0=TCOD
ID_CLIP_INFO_VALUE0=0
 TCDO: 9220800000
ID_CLIP_INFO_NAME1=TCDO
ID_CLIP_INFO_VALUE1=9220800000
ID_CLIP_INFO_N=2
Load subtitles in /home/wolf/
ID_FILENAME=/home/wolf/CHiPs DVD Extra.avi
ID_DEMUXER=lavfpref
ID_VIDEO_FORMAT=VP70
ID_VIDEO_BITRATE=0
ID_VIDEO_WIDTH=512
ID_VIDEO_HEIGHT=384
ID_VIDEO_FPS=25.000
ID_VIDEO_ASPECT=0.0000
ID_AUDIO_FORMAT=8192
ID_AUDIO_BITRATE=128000
ID_AUDIO_RATE=48000
ID_AUDIO_NCH=2
ID_START_TIME=0.00
ID_LENGTH=922.08
ID_SEEKABLE=1
ID_CHAPTERS=0
Failed to open VDPAU backend libvdpau_nouveau.so: cannot open shared object file: No such file or directory
[vdpau] Error when calling vdp_device_create_x11: 1
[VO_XV] Could not grab port 63.
[VO_XV] Could not grab port 64.
[VO_XV] Could not grab port 65.
[ass] auto-open
Opening video filter: [screenshot]
Requested video codec family [vp7] (vfm=vfwex) not available.
Enable it at compilation.
No Libav codec ID known. Generic lavc decoder is not applicable.
Video decoder init failed for codecs.conf entry "lavc".
Cannot find codec matching selected -vo and video format 0x30375056.
Selected audio codec: ATSC A/52A (AC-3) [libavcodec]
AUDIO: 48000 Hz, 2 ch, floatle, 128.0 kbit/4.17% (ratio: 16000->384000)
ID_AUDIO_BITRATE=128000
ID_AUDIO_RATE=48000
ID_AUDIO_NCH=2
AO: [pulse] 48000Hz 2ch floatle (4 bytes per sample)
ID_AUDIO_CODEC=ffac3
[Mixer] No hardware mixing, inserting volume filter.
Video: no video
Starting playback...

Cache not responding!
[ass] auto-open
Opening video filter: [screenshot]
Requested video codec family [vp7] (vfm=vfwex) not available.
Enable it at compilation.
No Libav codec ID known. Generic lavc decoder is not applicable.
Video decoder init failed for codecs.conf entry "lavc".
Cannot find codec matching selected -vo and video format 0x30375056.
ID_VIDEO_TRACK=0
ID_AUDIO_TRACK=0
```

---

### Post by mc4man on 2015-07-21
> **Evil Wayz said:**
> Running 14.04.2
OK, when I type that command in terminal I get the same output.  But what Am I supposed to do with that git ink?  I read in an article that ffmpeg AND vlc 2.2 support on2 and VP7.  I tried upgrading to VLC 3 and i ending up hosing my system with broken packages.  So I'm back to VLC 2.2.1 but all i get is audio.  Normally it wouldn't be a big thing but I just found all six seasons of chips and of course the guy who encoded it used an obscure codec that Google owns now.  Mplayer/smplayer is supposed to support it to, but this is what I get when I try that:
vlc that use libav9 cannot decode vp7, you'll need a vlc that uses either libav11 or ffmpeg. Also note that vlc cannot decode vp7 audio though not all vp7 vids uses vp7 audio. (- yours seem to use something else.

As far as mplayer you are using mplayer2 with libav9, not going to work.

(- where did you get vlc from?

---

### Post by papibe on 2015-07-21
For what I can tell, mpv (mplayer2's successor) plays VP7 on 14.04

Some details:
[LIST]
[*]Installed from this ppa: ppa:mc3man/trusty-media
[*]ppa is the official ppa for FFmpeg static builds.
[*]I had already installed FFmpeg. I don't know if it is a dependency.
[*]Only VP7 I could test was [this]("http://ubuntuforums.org/showthread.php?t=2209650&page=2&p=12969224#post12969224").
[*]You can use SMPlayer with mpv underneath.
[/LIST]
Regards.

---

### Post by mc4man on 2015-07-21
> **papibe said:**
> For what I can tell, mpv (mplayer2's successor) plays VP7 on 14.04

Some details:
[LIST]
[*]Installed from this ppa: ppa:mc3man/trusty-media
[*]ppa is the official ppa for FFmpeg static builds.
[*]I had already installed FFmpeg. I don't know if it is a dependency.
[*]Only VP7 I could test was [this]("http://ubuntuforums.org/showthread.php?t=2209650&page=2&p=12969224#post12969224").
[*]You can use SMPlayer with mpv underneath.
[/LIST]
Regards.
That mpv & the one in[ this ppa ]("https://launchpad.net/~mc3man/+archive/ubuntu/mpv-tests")both have ffmpeg embedded so no dependency on. (some add. info in the dedicated ppa on mpv use..
The difference between the 2 is the one in trusty-media has been from stable releases where the other one is updated weekly or more from the git master.
(though because no one is working on the next release I'll likely push a tested git master to the multimedia ppa soon..

A recent mplayer can also decode vp7 & vp7 audio if present but it has to built off of ffmpeg or libav11+, mplayer2 itself is dead & no sense using...

---

