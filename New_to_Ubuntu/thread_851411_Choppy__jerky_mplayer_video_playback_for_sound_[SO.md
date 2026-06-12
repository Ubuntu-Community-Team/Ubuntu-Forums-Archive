---
title: "Choppy / jerky mplayer video playback for sound [SOLVED]"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by balmar on 2008-07-06
It took pretty long to google why my mplayer got choppy on both my Hardy computers. (It worked completely fine in Gutsy, then updating started the trouble on one of the machines, the other was a clean Hardy install.) So I thought it might make sense to summarize: the problem in my case seemed to be PulseAudio. To get mplayer use alsa, do
```
mplayer -ao alsa
```
or select alsa in the audio section if you use a gui. You can also make it default by removing "pulse," from the line
```
ao=pulse,alsa,
```
of /etc/mplayer/mplayer.conf (and in fact I also needed to change
```
vo=xv
```
to
```
vo=x11
```
in the same file on one of the machines but that's a completely separate issue). It's probably a brutal solution, and one should tune PulseAudio properly, see the refs I found:

[http://ubuntuforums.org/showthread.php?t=776739]("http://ubuntuforums.org/showthread.php?t=776739")
[http://ubuntuforums.org/showthread.php?t=844222]("http://ubuntuforums.org/showthread.php?t=844222")
[http://ubuntuforums.org/showthread.php?t=790634&page=2]("http://ubuntuforums.org/showthread.php?t=790634&page=2")

---

