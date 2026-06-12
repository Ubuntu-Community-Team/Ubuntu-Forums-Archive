---
title: "can't hear mp3s in Hardy"
date: 2008-09-26
forum: New to Ubuntu
---

### Post by tee2 on 2008-09-26
Just installed Hardy and I can't hear mp3s in any program. I can stream radio and watch youtube videos, etc but I can't hear mp3s.

---

### Post by Sef on 2008-09-26
> Just installed Hardy and I can't hear mp3s in any program. I can stream radio and watch youtube videos, etc but I can't hear mp3s.


Try this:

Applications > Add/Remove > Show: Change to "All Available Applications" > Search type in: Restricted > click on Ubuntu Restricted Extras > click apply changes > apply >  close

---

### Post by oldsoundguy on 2008-09-26
I have to mark the mp3's in the file that I want to play and do a right click and then select which player I want to use (open with) .. I use Amarok.  I am playing some mp3's that are on a Windows box in another room. Sound very good on my digital surround system in here.

---

### Post by tee2 on 2008-09-26
> **Sef said:**
> Try this:

Applications > Add/Remove > Show: Change to "All Available Applications" > Search type in: Restricted > click on Ubuntu Restricted Extras > click apply changes > apply >  close

Just tried that, I still can't hear anything... any other ideas? :confused:

---

### Post by 50words on 2008-09-26
If you have all the codecs installed now, and you still can't hear them, it may have something to do with PulseAudio. For example, I cannot use Rhythmbox to listen to music if I am also watching a YouTube video or listening to Last.fm.

Sometimes, I have to close Firefox and Rhythmbox and start it up again before I can listen to music.

---

### Post by melojo on 2008-09-26
> **tee2 said:**
> Just installed Hardy and I can't hear mp3s in any program. I can stream radio and watch youtube videos, etc but I can't hear mp3s.

I had a similar problem and had to change the sound playback to oss open sound system instead of alsa "I think"  but can't be sure.

Goto system>prefernces>Sounds Look for sound playback.

---

### Post by tee2 on 2008-09-26
> **50words said:**
> If you have all the codecs installed now, and you still can't hear them, it may have something to do with PulseAudio. For example, I cannot use Rhythmbox to listen to music if I am also watching a YouTube video or listening to Last.fm.

Sometimes, I have to close Firefox and Rhythmbox and start it up again before I can listen to music.

Still can't hear anything :/

---

### Post by tee2 on 2008-09-26
> **melojo said:**
> I had a similar problem and had to change the sound playback to oss open sound system instead of alsa "I think"  but can't be sure.

Goto system>Sounds Look for sound playback.

That did  it! Thanks

---

### Post by ad_267 on 2008-09-26
> **50words said:**
> If you have all the codecs installed now, and you still can't hear them, it may have something to do with PulseAudio. For example, I cannot use Rhythmbox to listen to music if I am also watching a YouTube video or listening to Last.fm.

Sometimes, I have to close Firefox and Rhythmbox and start it up again before I can listen to music.

Install libflashsupport and this problem will go away.

---

### Post by 50words on 2008-09-26
> **ad_267 said:**
> Install libflashsupport and this problem will go away.

Nope, that just makes Firefox crash whenever I try to watch a flash player video in Firefox.

---

