---
title: "Sound bug?"
date: 2008-09-30
forum: New to Ubuntu
---

### Post by rojodojo on 2008-09-30
I've noticed a very strange bug involving sound. 
Normally my sound files and video(mp3, wma, wmv, etc) files work perfectly, but if I go to a website that has sound like youtube or even MEEBO, my multimedia files bug up and don't work at all. I've tried using different programs, but it has something to do with the files themselves. Furthermore, if I was listening to an music file and went to youtube, the youtube video would not have sound.

After i log out/back in, everything is ok, but ultimately is a big annoyance.

Has this ever happened to anyone?

---

### Post by oldsoundguy on 2008-09-30
Just remember the old computer axiom:

G.I.G.O.  Garbage in / garbage out.

If the YouTube upload is junk, no playback system in the world can fix it.  So sometimes you just have to accept the fact that on line uploaded stuff is trash.

But you should make sure you have the latest browser/flash combo (FF 3.03 and Flash RC 10 are the ones right now.)

---

### Post by Nepherte on 2008-09-30
There's a bug in pulseaudio that, in general, denies access to every other app than the first one that tries to access the sound card. The rest of the applications is denied access. There are 2 possible solutions. The first one is just using alsa directly instead of pulseaudio (system > preferences > sound, change everything to alsa). The second solution involves fixing the bug in pulseaudio. There's a very simply straightforward copy/paste tutorial here (still no reason not to read everthing very carefully though): [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

