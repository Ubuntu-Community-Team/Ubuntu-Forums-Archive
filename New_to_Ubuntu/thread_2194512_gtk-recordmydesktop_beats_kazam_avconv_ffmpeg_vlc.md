---
title: "gtk-recordmydesktop beats kazam avconv ffmpeg vlc"
date: 2013-12-18
forum: New to Ubuntu
---

### Post by Kevin McCready on 2013-12-18
Info for the community:

I've spent a couple of hours today learning how to capture a video stream.

After much trouble I stumbled on:
gtk-recordmydesktop
which works fine for me (gets vid and sound and I can adjust rates with advanced - the button for ending the recording is in a little coloured square on the taskbar)

The others I tried without success were:
vlc (it crashed my computer)
avconv (I couldn't figure out all the parameters)
ffmpeg (linux gave me a deprecated message)
kazam (waste of time).

Have fun!

---

### Post by ajgreeny on 2013-12-19
Just for your info here are the commands I have used for ffmpeg and avconv on my machine.  I'm not sure about sound on these, but I'm sure you could build on those commands for sound if you need it, or you could change the output resolution which I reduced to half my screen size just to show you how it can be done .
```
avconv -f x11grab -s 1440x900 -i :0.0 -s 720x450 -q 5 Desktop/video.avi
``` will make an avi with resolution of 720x450, ie half my screen resolution of 1440x900, and at the default refresh rate (25fps?)
```
avconv -f x11grab -s 1440x900 -r 15 -i :0.0 -s 720x450 -r 15 -q 5 Desktop/video.avi
``` the -r 15 reduces refresh rate to 15fps, but otherwise all is the same.
```
ffmpeg -f x11grab -s 1440x900 -r 15 -i :0.0 -s 720x450 -r 15 -sameq Desktop/video.avi
```note the minor change to the command output quality of -sameq which does exactly what it suggests, makes output the same quality as input.

---

### Post by FakeOutdoorsman on 2013-12-20
> **Kevin McCready said:**
> 
ffmpeg (linux gave me a deprecated message)


That misleading message refers to the fake "ffmpeg" from a fork of FFmpeg. See [Who can tell me the difference and relation between ffmpeg, libav, and avconv?](http://stackoverflow.com/a/9477756/1109017) and [The FFmpeg/Libav situation](http://blog.pkh.me/p/13-the-ffmpeg-libav-situation.html) for info.

For a good guide for capturing the screen with ffmpeg see: [HOWTO: Proper Screencasting on Linux](http://ubuntuforums.org/showthread.php?p=8746719#post8746719).

> **ajgreeny said:**
> note the minor change to the command output quality of -sameq which does exactly what it suggests, makes output the same quality as input.
[-sameq does not mean "same quality"](http://superuser.com/a/478550/110524), and has been removed from ffmpeg (unless you're using something ancient). -sameq only worked in some situations; specifically where the input and outputs use the same quantizer scale.

---

