---
title: "I can't seem to play flv files"
date: 2013-05-07
forum: New to Ubuntu
---

### Post by emes85 on 2013-05-07
Hello

I just installed Ubuntu 13.04 and am using the gnome 3 desktop.

when I try to open it on vlc player I get a dialog box 

 [COLOR=#ff0000]No suitable decoder module:[/COLOR]
 [COLOR=#000000]VLC does not support the audio or video format "h264". Unfortunately there is no way for you to fix this.
Only the sound is playing.

With other media players I'm getting only sound as well, mplayer doesn't give an error but only plays sound.

I have installed the restricted drivers and all but still am having problems.

When I right click to see properties on the file I can only get audio information but not video information; I'm a 100% certain that its a video file I've used it before.

Before I used linux mint debian edition and did not have any problems, I'm not sure what's so different.


Thanks in advance for the suggestions.
[/COLOR]
Emes

---

### Post by alphacrucis2 on 2013-05-07
When you say restricted drivers did you mean the ubuntu-restricted-extras or proprietary drivers?

---

### Post by Jason Kuzhively on 2013-05-08
Go to the Terminal and try type in "*sudo apt-get install ffmpeg*."

---

### Post by slickymaster on 2013-05-08
My advise to you is to install FF-Multi Converter. Run the following commands in a terminal window:
```
sudo add-apt-repository ppa:ffmulticonverter/stable
sudo apt-get update
sudo apt-get install ffmulticonverter
```
If you can't find after installation, just open the terminal and write **ffmulticonverter** to open it.

---

### Post by emes85 on 2013-05-08
yup that's what I mean ubuntu-restricted-extras

---

### Post by emes85 on 2013-05-08
The multiconverter is not converting, this is the detailed output.

 Seems stream 0 codec frame rate differs from container frame rate: 2000.00 (2000/1) -> 25.00 (25/1)
 Input #0, flv, from '/home/emes/Videos/5 Mutations/Mutations 1.flv':
   Metadata:
     audiochannels   : 1
     videoframerate  : 25
     aacaot          : 2
     avclevel        : 30
     avcprofile      : 100
     moovposition    : 262504505
   Duration: 01:02:24.83, start: 0.000000, bitrate: N/A
     Stream #0.0: Video: h264, 25 tbr, 1k tbn, 2k tbc
     Stream #0.1: Audio: aac, 16000 Hz, mono, s16
 [buffer @ 0x20ff1e0] Invalid pixel format string '-1'
 Error opening filters!

---

### Post by FakeOutdoorsman on 2013-05-08
If you can find out the ffmpeg command and get the complete ffmpeg console output it may provide additional clues as to what the issue is.

---

### Post by monkeybrain2012 on 2013-05-08
Is this similar to this thread ? (guy couldn't play some .flv files with vlc mplayer and everything )

[http://ubuntuforums.org/showthread.php?t=2137057](http://ubuntuforums.org/showthread.php?t=2137057)

Based on some experiments done for that thread I think it might have something to do with Ubuntu's (Debian's) version of ffmpeg (which is actually a fork called avcon) The solution to that thread is to compile mplayer and/or vlc against a static version of ffmpeg from git (see Andrew46's posts)

---

### Post by emes85 on 2013-05-08
it seems like he has the problem with the same video (series) as I am using, maybe the problem might be with the videos provided.

---

### Post by monkeybrain2012 on 2013-05-08
If you build vlc according to this guide it will play your video
[http://ubuntuforums.org/showthread.php?t=1398119](http://ubuntuforums.org/showthread.php?t=1398119)

or mplayer
[http://ubuntuforums.org/showthread.php?t=1542240](http://ubuntuforums.org/showthread.php?t=1542240)
If you use gnome-mplayer or smplayer as a front end to mplayer, change the mplayer preference to point to the compiled version (say in /home/username/bin)

---

### Post by emes85 on 2013-05-10
this helped thanks, just an FYI I had some problems when installing the long list of libraries (libvxp1) which I had but sudo wasn't picking up on it, I just unistalled and reinstalled it which seemed to resolve it.

Thanks everybody I really appreaciate the help.

Just a quick question does anybody know why I had this problem in the first place? it seemed to work on LMDE but not ubuntu 13.04.

Thanks again.

---

### Post by Perfect Storm on 2013-05-10
> **emes85 said:**
> this helped thanks, just an FYI I had some problems when installing the long list of libraries (libvxp1) which I had but sudo wasn't picking up on it, I just unistalled and reinstalled it which seemed to resolve it.

Thanks everybody I really appreaciate the help.

Just a quick question does anybody know why I had this problem in the first place? it seemed to work on LMDE but not ubuntu 13.04.

Thanks again.

Properly different versions of x,y,z packages is my guess.

---

### Post by andrew.46 on 2013-05-10
Just a sidenote in this thread:

> **monkeybrain2012 said:**
> If you build vlc according to this guide it will play your video
[http://ubuntuforums.org/showthread.php?t=1398119](http://ubuntuforums.org/showthread.php?t=1398119)

Change of address to:

Howto: Compile the development version of vlc under the latest Ubuntu release
[http://ubuntuforums.org/showthread.php?t=2141949](http://ubuntuforums.org/showthread.php?t=2141949)

and this is for experimenting with perhaps rather than replacing the release version of vlc.


> or mplayer
[http://ubuntuforums.org/showthread.php?t=1542240](http://ubuntuforums.org/showthread.php?t=1542240)
If you use gnome-mplayer or smplayer as a front end to mplayer, change the mplayer preference to point to the compiled version (say in /home/username/bin)

and this one has moved off-Forum:

Howto: Build the svn MPlayer under the latest release version of Ubuntu
[http://www.andrews-corner.org/mplayer.html](http://www.andrews-corner.org/mplayer.html)

Hopefully no more moves now :)

---

### Post by monkeybrain2012 on 2013-05-10
> **emes85 said:**
> 

Just a quick question does anybody know why I had this problem in the first place? it seemed to work on LMDE but not ubuntu 13.04.

Thanks again.

Just a guess, it works in Debian unstable as well, but in Debian I installed ffmpeg from Debian-Multimedia rather than the official repository. DM offers the original ffmpeg instead of avcon and it seems that avcon is not able to play these files somehow. I am not sure what version of Debian is LMDE (unstable, testing?) based on, so maybe it gets ffmpeg from the same source.

---

