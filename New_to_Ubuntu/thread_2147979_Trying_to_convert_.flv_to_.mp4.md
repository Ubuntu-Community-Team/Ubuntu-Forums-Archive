---
title: "Trying to convert .flv to .mp4"
date: 2013-05-23
forum: New to Ubuntu
---

### Post by dre3 on 2013-05-23
Hello I'm having a tough time converting my .flv videos to .mp4 on VLC.  I done a search in the forums and ended up at UbuntuCompilationGuideLucid, follow each step and still no luck .  Reading other threads others pointed out use this or that other player but I easily convert the files on Win7 so I know it can be done on ubuntu.  I just want to learn, never, don't know how compile, try last night but no go, so if someone can point me to the right direction I would be grateful.  Thanks.

---

### Post by Feathers McGraw on 2013-05-23
If I understand your question correctly, you mean that you are able to convert .flv to .mp4 in VLC for Windows, but are unable to do so in Ubuntu?

The menus should be the same on both platforms, so the most likely explanation is that the version you are using on Ubuntu is older than the one you are using on Windows... check this using help --> about, and if I'm right you could enable the backports for Lucid to get the newest version of VLC without the newest Ubuntu.

Failing that, you may not be able to do it because of restricted codecs etc. You can install them all in one go using the [Medibuntu](http://www.medibuntu.org) repository (there's an installation guide on there).

Please let me know if either of these solves the problem!

Feathers

---

### Post by linnan on 2013-05-23
I always use Winff, in Windows and in Linux.

---

### Post by BrunoLotse on 2013-05-23
I am using Handbrake, or Avidemux, or AVconvert (nautilus-actions-extra). Though on my personal note, why bother covert from flv to mp4?Cheers,Bruno

---

### Post by dre3 on 2013-05-23
Ok i made it to the Get FFmpeg page and lastest release is 1.2.1 Magic.  On the page it has a bzip2Tarball, gzipTarball, PgP signatures and changelog.  I'm at a lost right now.  I hope I gave enough info so far, i'll stop for now til you can tell me more.

---

### Post by dre3 on 2013-05-23
I want to play my my .flv on my WinPhone.

---

### Post by Feathers McGraw on 2013-05-23
So did the suggestions help?

Feathers

---

### Post by dre3 on 2013-05-23
> **dre3 said:**
> Ok i made it to the Get FFmpeg page and lastest release is 1.2.1 Magic.  On the page it has a bzip2Tarball, gzipTarball, PgP signatures and changelog.  I'm at a lost right now.  I hope I gave enough info so far, i'll stop for now til you can tell me more.  Yes so in a way I check out the site but right now I'm stuck.

---

### Post by dre3 on 2013-05-23
> **BrunoLotse said:**
> I am using Handbrake, or Avidemux, or AVconvert (nautilus-actions-extra). Though on my personal note, why bother covert from flv to mp4?Cheers,Bruno   I want to play my my .flv on my WinPhone.

---

### Post by leunam12 on 2013-05-23
You can also try [TCPMP]("http://forum.xda-developers.com/showthread.php?t=636423") on your winphone, it plays mp4, I'm pretty sure.
For the conversion, I'd use Winff

---

### Post by dre3 on 2013-05-23
> **Feathers McGraw said:**
> So did the suggestions help?  Feathers  Ok not sure if done right, I try to install the Medibuntu's repository but it couldn't connect.

---

### Post by kurt18947 on 2013-05-23
> **dre3 said:**
> Ok i made it to the Get FFmpeg page and lastest release is 1.2.1 Magic.  On the page it has a bzip2Tarball, gzipTarball, PgP signatures and changelog.  I'm at a lost right now.  I hope I gave enough info so far, i'll stop for now til you can tell me more.

You should be able to install both ffmepeg & winff from the repositories.  I just checked my 13.04 and have both installed.  No need to make your life more complicated than it needs to be.

---

### Post by Feathers McGraw on 2013-05-23
> **dre3 said:**
> Ok not sure if done right, I try to install the Medibuntu's repository but it couldn't connect.

Do you mean this one?:

```

sudo -E wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update

```

Feathers

---

### Post by dre3 on 2013-05-23
> **Feathers McGraw said:**
> Do you mean this one?:  ```
 sudo -E wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update 
```  Feathers  Yes!

---

### Post by dre3 on 2013-05-23
> **kurt18947 said:**
> You should be able to install both ffmepeg & winff from the repositories.  I just checked my 13.04 and have both installed.  No need to make your life more complicated than it needs to be.  Not sure about ffmpeg but I install winff, open it but at a lost on how to use.  Dont see nothing how to make video-h264 and audio-mpeg4 acc.

---

### Post by dre3 on 2013-05-24
I install Winff and also checking my home folder I have the ffmeg folder also wit the Lame and Yasm too, so I'am asking it i have to move it to a program folder or something, still at a lost but dont want to give up.

---

### Post by kurt18947 on 2013-05-24
> **dre3 said:**
> Not sure about ffmpeg but I install winff, open it but at a lost on how to use.  Dont see nothing how to make video-h264 and audio-mpeg4 acc.
Winff is just a GUI for ffmpeg I believe.  I'm not at all versed on various audio and video codecs, sorry.

---

### Post by landersohn on 2013-05-24
You can go to winFF.org. WinFF is a nice GUI to convert videos. Following the Download link you get to a Linux Installation Instructions. Follow those and you can install WinFF with Synaptic

---

### Post by andrew.46 on 2013-05-24
Looks like the information you are after concerning the correct formats for the 'WinPhone' is [here]("http://msdn.microsoft.com/en-us/library/windowsphone/develop/ff462087%28v=vs.105%29.aspx"). Several different versions of this phone so this page could do with close reading by the look of it. As for the best copy of FFmpeg for Ubuntu you should perhaps[ look at this page]("https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide").

---

### Post by evilsoup on 2013-05-24
andrew.46's links indicate that the phone supports H.264 video and AAC-LC audio, which are in all likelihood the codecs contained in the FLV file, so all that needs to be done is remuxing the video & audio streams into an MP4 container.

```

ffmpeg -i input.flv -c copy output.mp4

```

This will work on 99% of FLV files produced in the last few years. If that doesn't work, try the following instead (and consider updating to a recent ffmpeg, either compiling with the guide in andrew.46's post, or by downloading a [static copy from the ffmpeg website](http://ffmpeg.org/Download.html)):

```

ffmpeg -i input.flv -acodec copy -vcodec copy output.mp4

```

---

### Post by HiImTye on 2013-05-25
here's the script I made for converting videos
```
#!/bin/bash
if [ -z "$rate" ]; then
 rate="29.985"
fi
echo rate="$rate"

if [ -z "$flags" ]; then
 flags="+aic+mv4"
fi
echo flags="$flags"

# new file name
F="converted/${1%.*}.mp4"
if [ ! -d "converted" ]; then
 mkdir converted
fi

if [ ! -f "$F" ]; then    
 ffmpeg -i "$1" -r "$rate" -acodec libvo_aacenc -b 128k -vcodec mpeg4 -b 1200k -flags "$flags" "$F"
fi
```
make a new folder called Scripts in your home folder, then save it as '2mp4' (with no extension) in that folder. open a terminal and paste the following into it:
```
cd Scripts; chmod +x 2mp4; echo "PATH=$PATH:$HOME/Scripts" >> $HOME/.bashrc
```
then when you want to convrrt a file, simply type
```
2mp4 <file>
```
from the same folder and the .mp4 will be in the 'converted' folder. if you want to specify a framerate, then prefix the command, like so
```
rate=25 2mp4 <file>
```
when I want to convert an entire foldrr, I do this (which is why it outputs to a 'converted' folder)
```
while read -r f; do 2mp4 "$f"; done< <(ls)
```
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

### Post by dre3 on 2013-05-25
> **HiImTye said:**
> here's the script I made for converting videos
```
#!/bin/bash
if [ -z "$rate" ]; then
 rate="29.985"
fi
echo rate="$rate"

if [ -z "$flags" ]; then
 flags="+aic+mv4"
fi
echo flags="$flags"

# new file name
F="converted/${1%.*}.mp4"
if [ ! -d "converted" ]; then
 mkdir converted
fi

if [ ! -f "$F" ]; then    
 ffmpeg -i "$1" -r "$rate" -acodec libvo_aacenc -b 128k -vcodec mpeg4 -b 1200k -flags "$flags" "$F"
fi
```
make a new folder called Scripts in your home folder, then save it as '2mp4' (with no extension) in that folder. open a terminal and paste the following into it:
```
cd Scripts; chmod +x 2mp4; echo "PATH=$PATH:$HOME/Scripts" >> $HOME/.bashrc
```
then when you want to convrrt a file, simply type
```
2mp4 <file>
```
from the same folder and the .mp4 will be in the 'converted' folder. if you want to specify a framerate, then prefix the command, like so
```
rate=25 2mp4 <file>
```
when I want to convert an entire foldrr, I do this (which is why it outputs to a 'converted' folder)
```
while read -r f; do 2mp4 "$f"; done< <(ls)
```




I'm not sure how to get the scripts in the home folder.  I made folder (scripts) in the home folder but right now stuck on how to get it in da folder.

---

### Post by FakeOutdoorsman on 2013-05-25
> **HiImTye said:**
> here's the script I made for converting videos
```
ffmpeg -i "$1" -r "$rate" -acodec libvo_aacenc -b 128k -vcodec mpeg4 -b 1200k -flags "$flags" "$F"
```

Some thoughts:
[list]
[*] -b is shown twice and ffmpeg may ignore one. It is recommended to explicitly tell ffmpeg which bitrate goes where with -b:a (audio) or -b:v (video), or with -vb and -ab with ancient ffmpeg.
[*] Consider using -qscale:v (or -qscale with ancient ffmpeg) instead of -b:v for this encoder (mpeg4). A good range is 2-5 where 2 is probably going to be visually lossless or close to it.
[*] libvo_aacenc is probably the worst, in terms of quality per bitrate, of the four AAC-LC encoders usable by ffmpeg. Unfortunately most are "non-free" and you will have to compile ffmpeg to take advantage of better encoders. See [Compile FFmpeg on Ubuntu](https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide) and [FFmpeg and AAC Encoding Guide](https://ffmpeg.org/trac/ffmpeg/wiki/AACEncodingGuide).
[*] These days H.264 video is usually preferred for MP4 container. See the [FFmpeg and x264 Encoding Guide](https://ffmpeg.org/trac/ffmpeg/wiki/x264EncodingGuide).
[/list]

---

### Post by dre3 on 2013-05-25
> **FakeOutdoorsman said:**
> Some thoughts: 
[list] 
[*] -b is shown twice and ffmpeg may ignore one. It is recommended to explicitly tell ffmpeg which bitrate goes where with -b:a (audio) or -b:v (video), or with -vb and -ab with ancient ffmpeg. 
[*] Consider using -qscale:v (or -qscale with ancient ffmpeg) instead of -b:v for this encoder (mpeg4). A good range is 2-5 where 2 is probably going to be visually lossless or close to it. 
[*] libvo_aacenc is probably the worst, in terms of quality per bitrate, of the four AAC-LC encoders usable by ffmpeg. Unfortunately most are "non-free" and you will have to compile ffmpeg to take advantage of better encoders. See [Compile FFmpeg on Ubuntu](https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide) and [FFmpeg and AAC Encoding Guide](https://ffmpeg.org/trac/ffmpeg/wiki/AACEncodingGuide). 
[*] These days H.264 video is usually preferred for MP4 container. See the [FFmpeg and x264 Encoding Guide](https://ffmpeg.org/trac/ffmpeg/wiki/x264EncodingGuide). 
[/list]
    Hi FakeOutDoor, I did go and to the Ubuntu Compilation page and follow everything on da page and have files on my home folder, understand I don't know how to compile or anything like that so i have the ffmpeg, yasm, and lame folders sitting in my home folder and don't what to do with them, at a complete loss here.

---

### Post by HiImTye on 2013-05-25
@FakeOutdoorsmen, -b is specified after each outout type and works fine as a result, the script is meant to work on as many ffmpeg versions as possible, from the repos, requiring only adding restricted extras and ffmpeg to simplify getting it to work relatively simply, as it's only written to play on devices that don't support .avi, etc.

@dre3, either use gedit (text editor) and save it in the folder, or go to the foldrr in the terminal, type```
nano 2mp4
```paste (shift+ins, or just middle click into the terminal window with it highlighted in thid window)and save the file (using the key combination shown at the bottom - ^ means ctrl), then run the script above to make it executable and add Scripts to your PATH making it executable from any folder. also, thebfolder should be called 'Scripts' (with an uppercase S) or you'll need to modify the script before you run it

---

### Post by dre3 on 2013-05-25
> **HiImTye said:**
> @FakeOutdoorsmen, -b is specified after each outout type and works fine as a result, the script is meant to work on as many ffmpeg versions as possible, from the repos, requiring only adding restricted extras and ffmpeg to simplify getting it to work relatively simply, as it's only written to play on devices that don't support .avi, etc.  @dre3, either use gedit (text editor) and save it in the folder, or go to the foldrr in the terminal, type```
nano 2mp4
```paste (shift+ins, or just middle click into the terminal window with it highlighted in thid window)and save the file (using the key combination shown at the bottom - ^ means ctrl), then run the script above to make it executable and add Scripts to your PATH making it executable from any folder. also, thebfolder should be called 'Scripts' (with an uppercase S) or you'll need to modify the script before you run it    Ok i have the Scripts folder with the 2mp4 exe in it, i just try to convert a .flv file and got this   ajohn@johnson-laptop:~$ 2mp4 file:///home/ajohn/Videos/.SWH/1947709_Monters.flv rate=29.985 flags=+aic+mv4 ffmpeg version git-2012-03-29-282ec72 Copyright (c) 2000-2012 the FFmpeg developers   built on Mar 29 2012 10:16:20 with gcc 4.4.3   configuration: --enable-gpl --enable-libfaac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libvpx --enable-libx264 --enable-nonfree --enable-version3 --enable-x11grab   libavutil      51. 44.100 / 51. 44.100   libavcodec     54. 12.100 / 54. 12.100   libavformat    54.  3.100 / 54.  3.100   libavdevice    53.  4.100 / 53.  4.100   libavfilter     2. 66.101 /  2. 66.101   libswscale      2.  1.100 /  2.  1.100   libswresample   0. 10.100 /  0. 10.100   libpostproc    52.  0.100 / 52.  0.100 Input #0, flv, from 'file:///home/ajohn/Videos/.SWH/1947709_Monters.flv':   Metadata:     audiosize       : 8778481     canSeekToEnd    : true     datasize        : 85624965     hasAudio        : true     hasCuePoints    : false     hasKeyframes    : true     hasMetadata     : true     hasVideo        : true     lasttimestamp   : 1177     metadatacreator : flvtool++ (Facebook, Motion project, dweatherford)     totalframes     : 35290     videosize       : 75517391   Duration: 00:19:37.40, start: 0.033000, bitrate: 581 kb/s     Stream #0:0: Video: h264 (High), yuv420p, 320x240 [SAR 1:1 DAR 4:3], 525 kb/s, 29.97 tbr, 1k tbn, 59.94 tbc     Stream #0:1: Audio: aac, 44100 Hz, stereo, s16, 61 kb/s Please use -b:a or -b:v, -b is ambiguous     Last message repeated 1 times Unknown encoder 'libvo_aacenc' ajohn@johnson-laptop:~$    Don't know if in the right direction or still way off?  Thanks with all the help so far.

---

### Post by HiImTye on 2013-05-25
you're not using ffmpeg from the repos, you'll have to change the file to match the git vrrsions format requirements, in this case, run in the terminal```
 sed -ie 's|b 128k|b:a 128k|;s|b 1200k|b:v 1200k|' $HOME/Scripts/2mp4
```
this should fix it

edit: you'll also need to change the audio encoder, as you don't have 'libvo_aacenc'
run this command and look for one with a capital E at the start```
ffmpeg -codec | grep aac
```
you'll need to substitude this codec in this script:
```
sed -ie 's|libvo_aacenc|CodecGoesHere|' $HOME/Scripts/2mp4
```
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

### Post by dre3 on 2013-05-25
> **HiImTye said:**
> you're not using ffmpeg from the repos, you'll have to change the file to match the git vrrsions format requirements, in this case, run in the terminal```
 sed -ie 's|b 128k|b:a 128k|;s|b 1200k|b:v 1200k|' $HOME/Scripts/2mp4
``` this should fix it  edit: you'll also need to change the audio encoder, as you don't have 'libvo_aacenc' run this command and look for one with a capital E at the start```
ffmpeg -codec | grep aac
``` you'll need to substitude this codec in this script: ```
sed -ie 's|libvo_aacenc|CodecGoesHere|' $HOME/Scripts/2mp4
``` [CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]   I ran the command didnt see anything with a capital E, this is what i got:  ajohn@johnson-laptop:~$ ffmpeg -codec | grep aac ffmpeg version git-2012-03-29-282ec72 Copyright (c) 2000-2012 the FFmpeg developers   built on Mar 29 2012 10:16:20 with gcc 4.4.3   configuration: --enable-gpl --enable-libfaac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libvpx --enable-libx264 --enable-nonfree --enable-version3 --enable-x11grab   libavutil      51. 44.100 / 51. 44.100   libavcodec     54. 12.100 / 54. 12.100   libavformat    54.  3.100 / 54.  3.100   libavdevice    53.  4.100 / 53.  4.100   libavfilter     2. 66.101 /  2. 66.101   libswscale      2.  1.100 /  2.  1.100   libswresample   0. 10.100 /  0. 10.100   libpostproc    52.  0.100 / 52.  0.100 Missing argument for option 'code

---

### Post by HiImTye on 2013-05-25
whoops, that should be```
ffmpeg -codecs | grep aac
```
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

### Post by andrew.46 on 2013-05-25
Syntax has changed for the most recent FFmpeg:

```

andrew@skamandros~$**[COLOR="#B22222"] ffmpeg -encoders 2>/dev/null | grep aac[/COLOR]**
 A..X.. aac                  AAC (Advanced Audio Coding)
 A..... libfaac              libfaac AAC (Advanced Audio Coding) (codec aac)
 A..... libfdk_aac           Fraunhofer FDK AAC (codec aac)

```

The key for the letters at the beginning:


```

Encoders:
 V..... = Video
 A..... = Audio
 S..... = Subtitle
 .F.... = Frame-level multithreading
 ..S... = Slice-level multithreading
 ...X.. = Codec is experimental
 ....B. = Supports draw_horiz_band
 .....D = Supports direct rendering method 1

```

This is of course if you decide to go with FakeOutdoorsman's wiki page...

---

### Post by FakeOutdoorsman on 2013-05-25
> **dre3 said:**
> I ran the command didnt see anything with a capital E, this is what i got

The [[code]](http://ubuntuforums.org/misc.php?do=bbcode#code) tag will make the console outputs much more readable.

---

### Post by dre3 on 2013-05-25
> **HiImTye said:**
> whoops, that should be```
ffmpeg -codecs | grep aac
``` [CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]  This is what i got after:  ajohn@johnson-laptop:~$ ffmpeg -codecs | grep aac ffmpeg version git-2012-03-29-282ec72 Copyright (c) 2000-2012 the FFmpeg developers   built on Mar 29 2012 10:16:20 with gcc 4.4.3   configuration: --enable-gpl --enable-libfaac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libvpx --enable-libx264 --enable-nonfree --enable-version3 --enable-x11grab   libavutil      51. 44.100 / 51. 44.100   libavcodec     54. 12.100 / 54. 12.100   libavformat    54.  3.100 / 54.  3.100   libavdevice    53.  4.100 / 53.  4.100   libavfilter     2. 66.101 /  2. 66.101   libswscale      2.  1.100 /  2.  1.100   libswresample   0. 10.100 /  0. 10.100   libpostproc    52.  0.100 / 52.  0.100  DEA D  aac             Advanced Audio Coding  D A D  aac_latm        AAC LATM (Advanced Audio Codec LATM syntax)   EA    libfaac         libfaac AAC (Advanced Audio Codec)  I see the one that starts with the capitol E so do I type it as "EA libfaac" or just "libfacc" in the part codec goes here?

---

### Post by HiImTye on 2013-05-25
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
use the command Andrew.46 gave, avoiding any with 'X' (it appears that they no longer list decode or encode)

---

### Post by dre3 on 2013-05-25
> **HiImTye said:**
> [CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER] use the command Andrew.46 gave, avoiding any with 'X' (it appears that they no longer list decode or encode)  So how do I write it:  ffmpeg -encoders 2>/dev/null | grep aac  or  ffmpeg -libfaac 2>/dev/null | grep aac  At a lost on what/how to type in terminal.

---

### Post by HiImTye on 2013-05-25
```
ffmpeg -encoders 2>/dev/null | grep aac
```

---

### Post by andrew.46 on 2013-05-26
This is starting to remind me of an old Danny Kaye movie:

[http://www.youtube.com/watch?v=TJ9f2rnjB84](http://www.youtube.com/watch?v=TJ9f2rnjB84)

:)

---

### Post by dre3 on 2013-05-28
Hello to everyone who helped, just couldn't get it going, long time ubuntu user but still not a linux expert with codes, compiling files etc.  So I'm not sure if I should mark this thread solve but i will move on and just convert my .flv vidoes on my Win machine, thanks everyone.

---

### Post by HiImTye on 2013-05-29
you should give Avidemux a try, if you want a point and click type converter. it's not as fast or versatile as ffmpeg, but it's simple and will get the job done

---

### Post by 3rdalbum on 2013-05-29
> **dre3 said:**
> Hello to everyone who helped, just couldn't get it going, long time ubuntu user but still not a linux expert with codes, compiling files etc.  So I'm not sure if I should mark this thread solve but i will move on and just convert my .flv vidoes on my Win machine, thanks everyone.

WinFF
Avidemux
Handbrake
Video editors (such as Kdenlive and Openshot)

All those give comparatively easy ways of converting videos. Most even use FFMPEG as the backend but hide it behind a friendly graphical interface.

---

