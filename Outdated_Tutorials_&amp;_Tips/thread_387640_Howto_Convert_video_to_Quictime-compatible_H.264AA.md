---
title: "Howto: Convert video to Quictime-compatible H.264/AAC MP4 using the video2mp4 GUI"
date: 2007-03-18
forum: Outdated Tutorials &amp; Tips
---

### Post by tuxcantfly on 2007-03-18
**Description**

video2mp4 is an easy-to-use graphical GUI application (no command-line needed) that can convert any video files supported by mencoder and ffmpeg to the MP4 format, with H.264 video and AAC audio, which can be playable by players such as Apple Quicktime, iPod, PSP Blu-ray players, and HD-DVD players. H.264 provides better compression than any other video codec currently available. This guide provides instructions on installing the .deb package for video2mp4, and using its graphical interface to convert video files.

**Requirements**

Don't bother installing these manually; GDebi will handle this all automatically.. video2mp4 depends on the following packages:

zenity, ffmpeg, mencoder, faac, gpac

**Installation**

1. Download the attached file, or if you're not a forum member, download from [http://st0rage.org/~ubuntu/video2mp4_1.0_all.deb](http://st0rage.org/~ubuntu/video2mp4_1.0_all.deb)

2. Double-click the file you just downloaded, and it should launch the GDebi package installer.

3. Click "Install Package"

**Usage**

1. Launch video2mp4 (Applications -> Sound & Video -> video2mp4)

2. Select the video file you would like to convert

3. Select a location to save the mp4 file to

4. Wait while the video file is being converted. If your file is very large, it may take a while.

**Removal**

1. Launch Synaptic Package Manager (System -> Administration -> Synaptic Package Manager)

2. Scroll down the list and find "video2mp4"

3. Right-click, and select "Mark for Complete Removal"

4. Click on "Installed (auto-removable)" on the left-hand sidebar

5. Select all the packages under this section, right-click, and select "Mark for Complete Removal"

6. Click Apply
[B]
Command-line version[/B]

In case any of you are interested, there is a command-line version that may fix audio problems. To install it:

1. Download the attached video2mp4-nogui.sh or, if you're not a forum member, from [http://st0rage.org/~ubuntu/video2mp4-nogui.sh](http://st0rage.org/~ubuntu/video2mp4-nogui.sh)

2. Open a terminal (Applications -> Accessories -> Terminal)

3. Install necessary packages:

```
sudo apt-get update
sudo apt-get install zenity ffmpeg mencoder faac gpac
```

4. cd to the directory you downloaded the file to, and enter (replace filetoconvert.mpg with the path to the video):

```
sh video2mp4-nogui.sh filetoconvert.mpg
```

5. To remove video2mp4 and the packages it depends on from the terminal, type in:

```
sudo dpkg --purge ffmpeg mencoder faac gpac video2mp4
```

**Notes**

This guide and the video2mp4 program is written from scratch by me, although video2mp4 uses mencoder, ffmpeg, faac, and gpac to convert video, and zenity as the GUI. The command-line version was created by moaxey, based on the my GUI version. video2mp4 is licensed under the GNU GPL, and source can be obtained by viewing /usr/bin/video2mp4 (it's plain-text shell script). I have only tested this on Ubuntu 6.10 (Edgy) and Ubuntu 7.04 (Feisty) 32-bit, on Gnome, though it should work on other versions and desktop environments as well. Use this at your own risk.

---

### Post by tuxcantfly on 2007-03-19
subscribing to this thread

---

### Post by mwolfzorn on 2007-03-20
Your program does not work if a filename has spaces or other chars in it.

The path to my first test file was: /home/matt/Rocko's Modern Life/Season 1/1x02 - Leap Frogs ~ Bedfellows.avi

I ran it from console and got this output:

```
matt@pandora ~ $ video2mp4
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --enable-gpl --enable-pp --enable-pthreads --enable-libogg --e
nable-a52 --enable-dts --enable-dc1394 --enable-libgsm --disable-debug --enable-
mp3lame --enable-faad --enable-faac --enable-xvid --enable-x264 --enable-vorbis
  libavutil version: 49.0.0
  libavcodec version: 51.11.0
  libavformat version: 50.5.0
  built on Mar 18 2007 16:55:55, gcc: 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-
13ubuntu5)
/home/matt/Rocko's: I/O error occured
Usually that means that input file is truncated and/or corrupted.
Freeware Advanced Audio Coder
FAAC 1.24

Cannot encode several input files to one output file.
/usr/bin/video2mp4: line 7:  7718 Terminated              zenity --progress --pe
rcentage 10 --text "Audio is being converted, please wait" --title "Convert Audi
o"
MEncoder 1.0rc1-4.1.2 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Pentium(R) D CPU 3.00GHz (Family: 15, Model: 6, Stepping: 2)
CPUflags: Type: 15 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 3DNow 3DNowEx SSE SSE2

File not found: '/home/matt/Rocko's'
Failed to open /home/matt/Rocko's.
Cannot open file/device.

Exiting...
/usr/bin/video2mp4: line 12:  7722 Terminated              zenity --progress --p
ercentage 30 --text "Video is being converted, please wait" --title "Convert Vid
eo"
Error - 2 input names specified, please check usage
rm: cannot remove `/home/matt/Rocko\'s': No such file or directory
rm: cannot remove `Modern': No such file or directory
rm: cannot remove `Life/Season': No such file or directory
rm: cannot remove `1/1x02': No such file or directory
rm: cannot remove `-': No such file or directory
rm: cannot remove `Leap': No such file or directory
rm: cannot remove `Frogs': No such file or directory
rm: cannot remove `~': No such file or directory
rm: cannot remove `Bedfellows.avi.wav': No such file or directory
rm: cannot remove `/home/matt/Rocko\'s': No such file or directory
rm: cannot remove `Modern': No such file or directory
rm: cannot remove `Life/Season': No such file or directory
rm: cannot remove `1/1x02': No such file or directory
rm: cannot remove `-': No such file or directory
rm: cannot remove `Leap': No such file or directory
rm: cannot remove `Frogs': No such file or directory
rm: cannot remove `~': No such file or directory
rm: cannot remove `Bedfellows.avi.aac': No such file or directory
rm: cannot remove `/home/matt/Rocko\'s': No such file or directory
rm: cannot remove `Modern': No such file or directory
rm: cannot remove `Life/Season': No such file or directory
rm: cannot remove `1/1x02': No such file or directory
rm: cannot remove `-': No such file or directory
rm: cannot remove `Leap': No such file or directory
rm: cannot remove `Frogs': No such file or directory
rm: cannot remove `~': No such file or directory
rm: cannot remove `Bedfellows.avi.h264': No such file or directory
/usr/bin/video2mp4: line 17:  7725 Terminated              zenity --progress --p                                                            ercentage 80 --text "Video is being muxed, please wait" --title "Mux Video"
```

But when I ran it copied over on the same file with the path /home/matt/Desktop/hi.avi it worked fine.


So I looked at your script and added a few quotes:

```
REMOVED, DOWNLOAD VERSION ABOVE
```

Thanks for your script!


Note: Using Ubuntu 6.10 Edgy AMD64 KDE

---

### Post by tuxcantfly on 2007-03-20
Thanks for the notice, mwolfzorn, I've updated the deb file with your adjustments to the script

---

### Post by drews_blunted on 2007-03-21
I love you script its the easyest way to get your movies to mp4!

The only downside is that i have not been able to watch them on my playstaion3? they dont show up on the ps3's XMB. Has the ps3 support been tested by anyone else to work? Or did i do something incorrectly? any response would be great! Thanks.

---

### Post by tuxcantfly on 2007-03-21
> The only downside is that i have not been able to watch them on my playstaion3? they dont show up on the ps3's XMB. Has the ps3 support been tested by anyone else to work? Or did i do something incorrectly? any response would be great! Thanks.

Whoops, just noticed there was a little bug in the script that messes up the audio when playing under quicktime, I've fixed it, perhaps that was the issue with the PS3 as well? I've uploaded an updated version; try again with the PS3 on that. PS3 can supposedly play mp4 files, though I've never tested it (I don't have a PS3)

---

### Post by mwolfzorn on 2007-03-22
Hmm maybe we should get some kind of version scheme setup...

Also I was thinking it would be nice to be able to be able to use the script from command line, so if a file is passed to it from command line it skips calling zenity.

I think we could add a lot of options to the program:

```
--input  Select input file
--output Select output file
--dir Convert entire directory
--tmp Change temporary file directory
--help Show help
```

I'll start working on the command line options if you want me to :)

---

### Post by SmiLey497 on 2007-03-22
hey I tried this out, the audio is not synced when i play it on my comp and all i get is a black screen when i play it on my ipod

---

### Post by tuxcantfly on 2007-03-30
> hey I tried this out, the audio is not synced when i play it on my comp

Are you using the latest Quicktime 7? What format did you convert from? What ubuntu version are you using?
> 
and all i get is a black screen when i play it on my ipod

Whoops, seems like some resolution issue, will fix it once I have time

>  	Hmm maybe we should get some kind of version scheme setup...

Also I was thinking it would be nice to be able to be able to use the script from command line, so if a file is passed to it from command line it skips calling zenity.

I think we could add a lot of options to the program:

Code:

--input  Select input file
--output Select output file
--dir Convert entire directory
--tmp Change temporary file directory
--help Show help

I'll start working on the command line options if you want me to 

Idea sounds great, go for it, feel free to make a commandline version, will really appreciate it

---

### Post by Heatwole on 2007-04-07
> and all i get is a black screen when i play it on my ipod

same here, conversion seems to go fine, loads fine onto ipod, but will not play on ipod. really need a program like this, what could be the solution?

---

### Post by Heatwole on 2007-04-07
using gtkpod also, if that makes any difference

---

### Post by finite9 on 2007-04-07
This is truly amazing....thankyou so much!!  I have been trying to figure out how to transcode my DV files for months.  Really, I want both x264/AAC and XviD/MP3, the latter for playback on "legacy" DVD players ;)  But this is a great start for me.

I had been reading the following thread for months trying to figure out how best to apply it to my home made videos...

[http://ubuntuforums.org/showthread.php?t=273635&highlight=ffmpeg](http://ubuntuforums.org/showthread.php?t=273635&highlight=ffmpeg)

As you can see Heinz specifies many more options for Mencoder, but I do not know if they make the quality better?  A tip that I read about sound syncing is that you need to specifc -copy instead of -nosound for mencoder.  I have absolutely no idea what this means, but there you go.  Heinz also mentios that maybe you need to use ALSA with Mencoder to squash lip sync issues.

Another tip for dual core users is to specify threads=auto for the x264opts to make use of both cores.

Now I can *finally* edit my videos in Kino then export them back to DV and transcode to x264/AAC with this script!  As a plus, it ran so fast, I thought it had crashed!!

One question though...I see a bit of interlacing in the videos i transcode, especially during movement...is there a way to remove this?

---

### Post by cvmostert on 2007-04-09
Thanks for the effort, would It be possible to convert from file-made-on-mobile.mp4 to editable-videofile.mpg?

Take Care
Chris

---

### Post by tuxcantfly on 2007-04-09
> Thanks for the effort, would It be possible to convert from file-made-on-mobile.mp4 to editable-videofile.mpg?

Most likely ffmpeg can do that (depends on the file, though, it might not always work); to convert to mpg, just do:
```

ffmpeg -i file.mp4 file.mpg
```

---

### Post by balance07 on 2007-04-12
i'm trying to convert WMV files to something more usable in Ubuntu, but the results i get with this script have some A/V sync issues. any ideas about how to fix that?

here's some info regarding my input and output:
original wmv length = 5:54
extracted wav length = 5:49
converted aac length = 5:49
completed video length = 5:49, but reaches it's end at 5:35. for the last 14 seconds, the final frame is displayed as audio continues.

could this have something to do with FPS?

also, what does the following in your script do:?
```
-vf scale=-10:-1
```

---

### Post by tuxcantfly on 2007-04-12
> i'm trying to convert WMV files to something more usable in Ubuntu

Are you talking about vc-1 (windows media 9) videos, or some of the other, older WMV formats (msmpeg4v2, msmpeg4v3, wmv2, wmv1)? From what I've heard, ffmpeg and mencoder (which I'm using as the backend for video2mp4) have rather shaky support for those formats, especially for vc-1; chances are, this is probably an ffmpeg bug on the audio side, not much I can do about it (since ffmpeg's doing the audio extraction, and you said the audio gets out of sync) so you might want to report it on their bugzilla, and a mencoder bug on the video side (since that's doing the video encoding).

> also, what does the following in your script do
Code:

-vf scale=-10:-1


That adjusts the video resolution to be a size the quicktime can play; some of the really funky resolutions make it display just a white screen while playing a video, so that fixes that issue by resizing irregular resolutions.

---

### Post by balance07 on 2007-04-12
my video is WMV8 and plays correctly in VLC (except for the crappy seeking i've come to expect from wmv's). is there any way to pipe the output of VLC to the input for mencoder? or something like that?

also, what exactly does the -10 and -1 mean?

---

### Post by moaxey on 2007-04-15
here's my input for what its worth...

i found that doing many conversions at the same time with this script would mess up the audio.
and i need to convert many 1gb dv files from dvgrab at a time.

so i hacked this version that has no gui, and accepts command line arguments of files to convert (.dv) to mp4 one by one and in order into the same folders. with no audio problems

shell script attached :D

---

### Post by tuxcantfly on 2007-04-15
hmm interesting problem, moaxey, I have no idea why zenity would screw up the audio, in any case, I've edited my first post to include your nifty script, in case it fixes this problem for other users as well...

---

### Post by oldmanuk on 2007-04-20
you must specify video fps to MP4Box otherwise it defaults to 25 fps (hence audio will not be properly synced)
add this to the script:

FPS=`mplayer -identify -frames 0 -vo null $infile | gawk '/[0-9.]\ fps/ { print $6 }'`
MP4Box "$file" -add "$file.h264" -add "$file.m4a" -fps $FPS

However, if you want to also support things like iPod, PSP, PS3 then you need to work with the H.264 Level (set by level_idc). For the PS3 you would use the following x264encopts:

mencoder "$infile" -ovc x264 -x264encopts bframes=1:level_idc=41:threads=auto -nosound -of rawvideo -vf scale=-10:-1,harddup -o "$file.h264"

This will produce an H.264 file at Level 4.1 which is PS3 compatible.

iPod needs level 1.3 (level_idc=13) and PSP needs level 2.1 (level_idc=21)

---

### Post by finite9 on 2007-04-21
it was very easy to edit this script to make a video2XviD menu option.  I use mencoder but simply comment out all the audio stuff.  I am very happy with this setup as I can now make XviDs to view on my TV and have x264/AAC videos for my computer video archive, and when I buy a BluRay player, these files should hopefully play OK.

I have one question though...There are many options for xvid and x264...do you know of any that would increase the quality of the video?  I do not want best compression, but best quality.  At the moment I have to specify in xvid opts for mencoder that -xy 640 or it won't play on my DVD player.    It then does not show properly, as the original DV was widescreen 1.77:1 or whatever it is, but now it looks more like 2.00:1 and I get black bars at top and bottom of screen, whereas original DV filled up widescreen TV with no bars.

---

### Post by neonmagnolia on 2008-04-21
I'm also having issues with the audio. The first video I attempted has about a three second delay in the audio, while the second one has no audio whatsoever. I haven't tried putting it on my ipod though.

---

