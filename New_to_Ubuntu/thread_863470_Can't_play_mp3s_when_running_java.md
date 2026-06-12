---
title: "Can't play mp3s when running java"
date: 2008-07-18
forum: New to Ubuntu
---

### Post by 449 on 2008-07-18
Whenever I am using java(Runescape) I get no sound for anything else. When I try to play an mp3 in rhythmbox, the song slider doesn't move when played. Vlc player can play videos, but there will be no sound. 

Also when I try to stream video through Firefox3, the video will not load.

:confused:

However as soon as I close out rs everything works like it normally should. Weird.

---

### Post by LittleLORDevil on 2008-07-18
I have a bug as well that if something else is producing sound I can't use anything else.

---

### Post by SlalomMan on 2008-07-18
I'm pretty sure this is a bug with AlSA. It seems that you can only have one source of sound running at a time; although maybe totem and rhythmbox can run simotaneously. 

A few situations that demonstrate this:
- Try opening up a flash game in firefox, then running rhythmbox. Rhythmbox won't play.
- Open rhythmbox and then navigate to a youtube video or other flash app with sound; the sound on flash won't work.

I'm not sure if this is a problem with ALSA or just Ubuntu in general, I'm using the PulseAudio sound settings and it still won't work. Just something we'll have to work around for now, I guess.

---

### Post by BGFG on 2008-07-18
Hey Guys, you should check this thread. Fixed my problem.

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

Option 'A' is what you need.

---

