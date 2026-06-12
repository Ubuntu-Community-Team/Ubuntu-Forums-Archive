---
title: "Video lags/freezes in SMPlayer and VLC."
date: 2012-06-21
forum: New to Ubuntu
---

### Post by ranrag on 2012-06-21
Hi,

When I try to play my video files in SMPlayer it works fine but as soon as I switch to* fullscreen mode(16:9)* following thing happens:

1) Video starts lagging.
2) Audio and video goes out of sync.
3) CPU  usage rises to ~50%.
4) SMPlayer starts to hang.

**My current SMPlayer configuration:**

1)Video Output Driver = x11(slow)
2)Audio Output Driver = alsa(0.0-HDA Intel)
3)Cache               = 8192 KB
4)Threads for decoding(MPEG-1/2 and H.264 only = 2

**Things I tried solve this problem:**

1) Tried changing video o/p driver to xv,gl.
2) Tried changing audio o/p driver to pulse.
3) Tried increasing cache size and also tried using nocache.

Everything works fine on windows but I don't want to switch to windows just to play video files.



**My system config:**

Acer Aspire One D270
Atom N2600(Cedar Trail) 1.6GHz
2GB Memory
**Intel GMA 3600 graphics.**
Ubuntu 12.04
**Kernel Release: 3.2.0-23-generic-pae**


Rest all things are working fine I have **no resolution issue**, bluetooth, wireless also working fine.

Just ask me to submit any other log file I will be happy to post.


[**SMPlayer log**]("http://sprunge.us/hAHA")

[**MPlayer terminal output**]("http://sprunge.us/ARIL")

**Codec Information(Current playing file)**

[IMG]http://i.stack.imgur.com/KGR2F.png[/IMG]

---

### Post by SeijiSensei on 2012-06-21
Try playing the file from the command line with mplayer and see if it complains. 

```
mplayer /path/to/file.flv
```

Usually the xv or opengl drivers work best.

Is this just true for files in the flv container?  What about something like XviD in the AVI container?  How about H.264 files in the MKV container?

Atoms are, in general, pretty underpowered to decode H.264 content, and Intel isn't known for its graphics drivers either.  The supplied Windows driver might be better designed than the Linux one.

---

### Post by ranrag on 2012-06-21
When I try to play the file using mplayer from terminal it works fine as long as I don't try to make it full screen.

One thing I observe with mplayer is when I try to make it full screen the aspect ratio
doesn't change. Aspect ratio is same as when video is started for the first time i,e before making it fullscreen.

**My mplayer o/p(notice the black background)**

[IMG]http://imgur.com/K29OR.png[/IMG]





I faced this problem with .mkv file also. I didn't tried xvid and avi. I can play flv(ok
quality) with no problem.

---

