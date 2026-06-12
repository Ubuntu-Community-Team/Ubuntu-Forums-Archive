---
title: "[SOLVED] Sound randomly turning off"
date: 2008-08-24
forum: New to Ubuntu
---

### Post by joey_breizh on 2008-08-24
I have the weirdest thing happening with my sound. Sometimes the computer is running and will stop making sound. It's never happened while I was listening to something or watching something, but if I don't play any sound for a while and then come back to the computer, often the sound won't be working anymore.

Usually if I reboot, then the sound is fine again.

I've checked the alsamixer and nothing is unduly muted...

Weirder even, as I'm typing I can't get sound from VLC or Rhythmbox or if I try listening to the radio online, however [this video has sound]("http://www.asianschoolboy.com/vids/videoplayer.php?event=2008_comiccon&video=2008comiccon11").

Anyone has an idea what could be going wrong?

---

### Post by Alaric on 2008-08-24
Post the output of 'lspci' and check your [menu] > system > preferences > sound.

---

### Post by sancho panza on 2008-08-24
Tell us if this happens when you are using firefox/not using firefox. The adobe flash in firefox has the tendency to prevent other apps from using it. So in you are listening to sound in firefox (flash), then other apps wont play sound. They should be able to play when u close firefox. Also, if one app is playing sound, firefox(flash) would be unable to play sound. This is a known bug.

---

### Post by joey_breizh on 2008-08-24
Alaris, I'm not sure how to find out the output of Ispci?

Sancho Panza, thank you. I just tried without Firefox on then with turning it back on etc, and the problem does seem to come from when I have a tab running with that video I linked to. The weird thing is that if I have that video tab open, even my tab with a radio player opened will not work... 

If this is a known bug, I'm assuming there's nothing to do?

---

### Post by SnappyU on 2008-08-24
Sometimes it has to do with a web plugin holding onto the sound device while another player tries to play something.  Certain sound system does *not* support multi-app mixing.  I believe PulseAudio libraries supports it.  :)

---

### Post by bfallik on 2008-08-25
> **sancho panza said:**
> Tell us if this happens when you are using firefox/not using firefox. The adobe flash in firefox has the tendency to prevent other apps from using it. So in you are listening to sound in firefox (flash), then other apps wont play sound. They should be able to play when u close firefox. Also, if one app is playing sound, firefox(flash) would be unable to play sound. This is a known bug.

Can you point me to the existing bug(s)?  I'm also experiencing this problem and would like to track their progress.

Thanks.

---

### Post by sancho panza on 2008-08-25
> **bfallik said:**
> Can you point me to the existing bug(s)?  I'm also experiencing this problem and would like to track their progress.

Thanks.

I cannot locate the exact bug, but its located [in this thread]("http://ubuntuforums.org/showthread.php?p=4928900"), which discusses these issues and some partial workarounds.

The bug is in Flash, not in Pulseaudio. Although pulseaudio supports multiple streams, Flash locks up the audio stream from other apps. The development version of flash does not have this issue.

Cheers!

---

### Post by bfallik on 2008-08-25
> **sancho panza said:**
> I cannot locate the exact bug, but its located [in this thread]("http://ubuntuforums.org/showthread.php?p=4928900"), which discusses these issues and some partial workarounds.

The bug is in Flash, not in Pulseaudio. Although pulseaudio supports multiple streams, Flash locks up the audio stream from other apps. The development version of flash does not have this issue.

Cheers!

Sigh.  Thanks.  I was hoping for a single bug to read, not 50 pages of forum posts.  Though I guess in practice maybe they're not so dissimilar.

Are you saying that flash 10 beta resolves this bug?  I notice that the thread you mentioned speaks of a regression in flash 10 causing ff3 to crash.  Perhaps I'm better off for now just quitting ff3 when I want to force flash to unlock sound.

---

### Post by sancho panza on 2008-08-25
I'm sorry I didnt mention that the bug is one of those listed in the first post of that massive thread that I linked to. You dont have to dig thru all the posts of that thread.
And yes, Flash 10 beta resolves this bug, but it has some other unrelated problems which were unresolved the last time I tried, so I decided to put up with this audio bug.

---

