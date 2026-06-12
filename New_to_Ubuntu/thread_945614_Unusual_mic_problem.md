---
title: "Unusual mic problem"
date: 2008-10-12
forum: New to Ubuntu
---

### Post by Denny Johnson on 2008-10-12
Dell 1420n, hardy.
Mic had been working fine in kernel 2.6.22-15.
I didn't have sound in kernel 2.6.24-19.
Adding the line "options snd-hda-intel model=dell" in /etc/modprobe.d/alsa-base, got sound working in 2.6.24-19.
The first time I tried using the mic after this it would not work in either kernel, tho I may have changed other things, don't remember what, before finding the mic problem.
When I say no mic........neither of 2 external mics work [no internal mic] and in system/preferences/sound/ when testing SOUND CAPTURE w TEST SOUND, there is crackling in test sound at first [1 -2 sec], then silence w an occasional crackle. The test sound actually starts, very briefly, then sounds like morse code [again very briefly] as the test sound breaks up, then a bit of crackle, then silence. This happens consistently, same exact pattern.
Any suggestions appreciated, thanks.

---

### Post by Sef on 2008-10-14
moved to absolute beginner.

---

