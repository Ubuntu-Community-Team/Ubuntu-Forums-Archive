---
title: "Audio Issue"
date: 2008-09-23
forum: New to Ubuntu
---

### Post by sidzoo on 2008-09-23
I have a funny sort of issue. When I play audio / audio-video on my browser, I'm unable to play audio offline (for example, on Amarok) until I log off Ubuntu and log on again. I think that Amarok loses control of the drivers or something. How do I solve this?

Thanks,
Sid.

---

### Post by acidsolution on 2008-09-23
try
```

sudo apt-get install libflashsupport 

```

this must help [:)]

---

### Post by sidzoo on 2008-09-23
The fix didn't work :(

To test, I played a youtube video while amarok was on pause. Then I closed the video and unpaused amarok. No response - the seeker hung. Also, the "mouseover song for preview" feature on 8.04 doesn't work. Any other ideas?

---

### Post by Nepherte on 2008-09-23
here's a bug in pulseaudio that, in general, denies access to every other app than the first one that tries to access the sound card. The rest of the applications is denied access. There are 2 possible solutions. The first one is just using alsa directly instead of pulseaudio (system > preferences > sound, change everything to alsa). The second solution involves fixing the bug in pulseaudio. There's a very simply straightforward copy/paste tutorial here (still no reason not to read everthing very carefully though): [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by sidzoo on 2008-09-23
@Nepherte: Thanks. Changing them all to ALSA worked. 
Sid.

---

### Post by markbuntu on 2008-09-23
> **Nepherte said:**
> here's a bug in pulseaudio that, in general, denies access to every other app than the first one that tries to access the sound card. The rest of the applications is denied access. There are 2 possible solutions. The first one is just using alsa directly instead of pulseaudio (system > preferences > sound, change everything to alsa). The second solution involves fixing the bug in pulseaudio. There's a very simply straightforward copy/paste tutorial here (still no reason not to read everthing very carefully though): [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

Actually, it is not a bug in Pulseaudio. It is a problem with using autodetect in System/Preferences/Sound since OSS apps will do the same thing. The solution is to get all the applications to use the same sound server. Choosing alsa in Sound works for many applications but not quite all. I have written a guide for sound troubleshooting that includes a section for setting up your sound so all your applications can share the sound card:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

