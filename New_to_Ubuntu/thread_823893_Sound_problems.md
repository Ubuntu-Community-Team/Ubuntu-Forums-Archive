---
title: "Sound problems"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by Thelasko on 2008-06-09
I rebooted my machine a few days ago and lost audio.  It doesn't even make the little drumbeat noise before I login.  I went to the system monitor and it said aplay, gnome-settings-daemon, and mixer_applet2 were running with "status: uninterruptible".  I tried to close them but it wouldn't let me.  When I try to shutdown my machine it freezes when it says it's shutting down ALSA.

Thanks in advance:)

---

### Post by Xiong Chiamiov on 2008-06-10
Take a peep through [this guide]("http://ubuntuforums.org/showthread.php?t=205449") and tell us where you have problems.

---

### Post by Thelasko on 2008-06-10
What does it mean when it freezes on step one?

---

### Post by raghothams on 2008-06-10
I installed Hardy.
But the audio isn't working. If i play song in vlc or rythm it just plays. But no music at all.. :confused:
Pl reply fast

---

### Post by GaussianMonk on 2008-06-10
> the audio isn't working. If i play song in vlc or rythm it just plays. But no music at all.. 

I had a similar problem with my first install. 
Try:
```
sudo alsamixer
```

and make sure the PCM volume is all the way up. If it is, try looking through [here]("http://ubuntuforums.org/showthread.php?t=205449") (same page that Xiong posted).

---

### Post by Thelasko on 2008-06-11
Bump, please stay on topic.

---

### Post by Thelasko on 2008-06-12
Bump again

---

### Post by Nepherte on 2008-06-12
Just try that 'Comprehensive Sound Problem Solutions Guide' as far as you can get and post the results of every step in here. You'll have to give us more details than 'what does it mean if it fails on step one'.

The first step in that guide is:
```
aplay -l
```
It clearly says that in case of a failure, you have to move on to step 2.

---

### Post by Langleyo on 2008-06-12
> **raghothams said:**
> I installed Hardy.
But the audio isn't working. If i play song in vlc or rythm it just plays. But no music at all.. :confused:
Pl reply fast


You might need to download relevant up to date media codecs....I think they're in the medibuntu repository. Search for other people with sound problems in the forums or for "codecs"

---

### Post by Nepherte on 2008-06-12
It's certainly not a codec problem if it fails on aplay -l

---

### Post by Thelasko on 2008-06-13
> **Nepherte said:**
> 
It clearly says that in case of a failure, you have to move on to step 2.
No, it says:
> Failure - You will get a message like

```
aplay: device_list:221: no soundcard found...
```


I received no such message, the terminal simply froze.  It seems any program that tries to produce sound freezes.

I moved on to step two and had success.  I was unable to find my driver in step 3, but it worked before, so I know it must exist.

---

### Post by Thelasko on 2008-06-13
I should also point out that I booted into Windows yesterday and the sound worked great.  It's not a hardware issue.

---

### Post by Nepherte on 2008-06-14
I'd simply recompile the alsa drivers. If it worked before, recompiling the alsa drivers correctly should bring your sound back.

---

### Post by Thelasko on 2008-06-16
> I'd simply recompile the alsa drivers. If it worked before, recompiling the alsa drivers correctly should bring your sound back.
How would one go about doing this?

---

### Post by Thelasko on 2008-06-19
Never mind, I used an old trick from back in my days of using Windows.  Reformat and reinstall the OS.  It's a shame I had to resort to that.  I took it as an opportunity to install Hardy Heron.  

Thanks for the help!  Should I leave this thread open since the problem was never really solved?

---

