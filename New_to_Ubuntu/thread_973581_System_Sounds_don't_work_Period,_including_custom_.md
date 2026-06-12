---
title: "System Sounds don't work Period, including custom ones"
date: 2008-11-06
forum: New to Ubuntu
---

### Post by Yori on 2008-11-06
Hello World.

I'm in a bit of a predicament here.  I'm trying to change the system sound you get when you log on, but when I go to System > Preferences > Sound, none of the sounds work when I press play, even the none-custom ones.  I went the Devices Tab, and used the test to see which device worked for my laptop speakers.  The test made a sound, so I knew it worked, but system sounds still don't work.  Any help?

---

### Post by davidsrsb on 2008-11-06
Try turning up the volume, on my machine the System sounds are a bit quiet

---

### Post by kansasnoob on 2008-11-06
> **Yori said:**
> Hello World.

I'm in a bit of a predicament here.  I'm trying to change the system sound you get when you log on, but when I go to System > Preferences > Sound, none of the sounds work when I press play, even the none-custom ones.  I went the Devices Tab, and used the test to see which device worked for my laptop speakers.  The test made a sound, so I knew it worked, but system sounds still don't work.  Any help?

That's quite vague. How is sound in other programs? What version of Ubuntu are you using?

---

### Post by kansasnoob on 2008-11-06
BTW, one of the first things I install in every Ubuntu installation is:

```
sudo apt-get install gnome-alsamixer
```

You'll then find it in Sound & Video. Pay special attention to the first three toggles and the last four toggles!

---

### Post by hictio on 2008-11-06
> **kansasnoob said:**
> That's quite vague. How is sound in other programs? What version of Ubuntu are you using?

++
Can you listen to the audio, of say, videos, for instance?
I had a similar problem than yours, on Intrepid, audio was working for everything, except system.
It turned out that the 'PCM' got muted, I don't recall why, tho.
Check it thru:
- Right click on the speaker icon, select "Open Volume Control", Playback tab, check the level of the "PCM" one.

---

### Post by Yori on 2008-11-07
I'm running Ubuntu 8.04 Hardy Heron.

I don't know why, but it seems to be fixed now.  It might've been that the .wav file that I used messed something up, and since I replaced it, now everything works.

I don't have a "PCM" choice for my volumes, but I guess it doesn't matter anymore.  I'll go ahead and install gnome-alsamixer, just to be ready for any future problems.

I thank you all for your help.

---

