---
title: "converting video error"
date: 2013-01-08
forum: New to Ubuntu
---

### Post by hnf a on 2013-01-08
hi all i have question how to convert and extract audio from video file, i
have try avconv but it says the codec was unknown i also write -acodec mp3 libx264 h264 and other codec but but the avconv always says unknown codec and so the winff, winff however can convert to wma or audio file but its corrupted, am i should download the codec?

---

### Post by deadflowr on 2013-01-08
If you want an easy to use way to extract the audio from your video file, install audacity.
It will automatically convert the video file into an audio file which you can export as any of a number of formats, including mp3,ogg,flac,wav, and so on.

---

### Post by sudodus on 2013-01-08
+1

***Audacity*** is a good tool for audio (extraction, conversion, 'any' treatment)

install it from the repos, and if it doesn't work, try to install more codecs and such things.

I find the following packages useful

gstreamer0.10-plugin-ugly
gstreamer0.10-plugin-bad

If you have the appropriate program sources activated, you can find and install them with ***Synaptic*** (and you can select the program sources with Synaptic too).

I have them from 
precise/universe: 'ugly'
precise-updates/universe: 'bad'

---

### Post by hnf a on 2013-01-09
thanks for the reply,i think audcity great for it but how about resizing video?

---

### Post by sudodus on 2013-01-09
> **hnf a said:**
> thanks for the reply,i think audcity great for it but how about resizing video?

Then you need another tool.

I use ***Openshot*** to edit the video clips from my camera and export to a suitable format. It is a GUI application.

I use ***ffmpeg*** to convert video clips (resizing, changing codec etc). It is a command line tool. There is a GUI frontend, ***WinFF***, than can do some of the tasks that can be done with ffmpeg.

---

### Post by hnf a on 2013-01-09
the problem is in the end of converting process the terminal write "unknown encoder 'libmp3lame'"

---

### Post by sudodus on 2013-01-09
> **hnf a said:**
> the problem is in the end of converting process the terminal write "unknown encoder 'libmp3lame'"
You need to install the codecs that you plan to use. Use ***Synaptic*** to search for the codec or see this link

[[COLOR="Red"]http://askubuntu.com/questions/13737/what-packages-do-i-install-for-ffmpeg-and-libmp3lame[/COLOR]]("http://askubuntu.com/questions/13737/what-packages-do-i-install-for-ffmpeg-and-libmp3lame")

---

### Post by hnf a on 2013-01-10
oh thanks for the reply now i can convert to avi

---

### Post by dannyboy79 on 2013-01-10
i use handbrake or avidemux to convert video formats. for video editing I use kdenlive from sunab's ppa's for either stable kdenlive-release or latest from git kdenlive-svn

---

