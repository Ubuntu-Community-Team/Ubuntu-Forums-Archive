---
title: "Lines in videos while playing"
date: 2012-11-04
forum: New to Ubuntu
---

### Post by wingrider78 on 2012-11-04
Hello, I am having a problem while playing video files.  It appears that the files aren't being interlaced/deinterlaced properly, so I change the options in VLC and it doesn't seem to fix the issues.  As long as there isn't much fast motion movement in the video, everything is fine, but once the camera pans quickly or something moves fast, the video has lines going through it.  It happens in VLC and parole.  I am running xubuntu 12.04.  Is there anything to try???

---

### Post by Paari on 2012-11-05
I guess you should install some basic codecs... If not you can install it from here
```
sudo apt-get install non-free-codecs libxine1-ffmpeg gxine mencoder totem-mozilla icedax tagtool easytag id3tool lame nautilus-script-audio-convert libmad0 mpg321 mpg123libjpeg-progs

```

---

### Post by wingrider78 on 2012-11-05
It looks like a lot of those item you wanted me to install have nothing to do with video codecs...tagtool easytag id3tool nautilus-script-audio-convert etc...so I didn't install them.  If you can please explain why you feel such items would be pertinent to fixing a video display problem, I will consider trying them to fix the issue.  But I just can't see how a program for ID3 tags could possibly help me with this issue. 

I already had mencoder and libxine1-ffmpeg installed so I only installed non-free-codecs and it seems to have made a slight difference, but I will have to watch some videos to see the full effects.  I will post back with results

---

### Post by wingrider78 on 2012-11-10
After watching several more videos, it appears that the issue is not resolved.  I have the same issue playing the same videos on my laptop.  Both computers are running xubuntu 12.04.  Neither computer had issues like this when running Ubuntu 10.04.  I have recently upgraded and switched to xubuntu since I didn't like Unity in Ubuntu...any other ideas?

---

### Post by pqwoerituytrueiwoq on 2012-11-10
what video player? what video (assuming you can legally link to it)?
you can try smplayer

---

### Post by Merrattic on 2012-11-10
Turn off the compositor. This will cure your problem. You can do it through Settings>WindowManagerTweaks>Compositor or

Here is a script you can add to a launcher to turn it on and off when you need to:

```
#!/bin/sh
#componoff.sh
#xubuntu 12.04
#turns compositor on and off

comp=$(xfconf-query --channel=xfwm4 --property=/general/use_compositing)

if [ $comp = "true" ]; then
xfconf-query --channel=xfwm4 --property=/general/use_compositing --set=false
else
xfconf-query --channel=xfwm4 --property=/general/use_compositing --set=true
fi
```

---

### Post by wingrider78 on 2012-11-11
> **pqwoerituytrueiwoq said:**
> what video player? what video (assuming you can legally link to it)?
you can try smplayer

It is all videos, from 720p videos recorded on my phone, to flv videos taken from youtube, to personal backups of our dvds...they are acting the same way.

I have been using VLC and Parole, both act the same way.

---

### Post by wingrider78 on 2012-11-11
> **Merrattic said:**
> Turn off the compositor. This will cure your problem. You can do it through Settings>WindowManagerTweaks>Compositor or

Here is a script you can add to a launcher to turn it on and off when you need to:

```
#!/bin/sh
#componoff.sh
#xubuntu 12.04
#turns compositor on and off

comp=$(xfconf-query --channel=xfwm4 --property=/general/use_compositing)

if [ $comp = "true" ]; then
xfconf-query --channel=xfwm4 --property=/general/use_compositing --set=false
else
xfconf-query --channel=xfwm4 --property=/general/use_compositing --set=true
fi
```

Okay, I just turned off the compositor manually and sampled several videos.  This has apparently fixed the video issue.  Is there any reason to NOT keep this turned off?  What does this compositor function actually do?

EDIT: oh yeah, thanks for fixing the problem :)

---

### Post by Merrattic on 2012-11-22
Don't know of any functional reason to have the compositor, it is just gentle eye candy AFAIK. Glad it fixed the problem.

---

