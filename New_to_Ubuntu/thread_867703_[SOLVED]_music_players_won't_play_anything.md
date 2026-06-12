---
title: "[SOLVED] music players won't play anything"
date: 2008-07-23
forum: New to Ubuntu
---

### Post by ELD on 2008-07-23
Any idea how i can find out why none of my music plays?

---

### Post by northern lights on 2008-07-23
Do the players complain or do you not have audio output? I.e. if you double-click an .mp3, does it open in aplayer and does the slider move?

Did your music ever play before on your current install?

1. As for players, not opening the files:

Do you have the package "ubuntu-restricted-extras" installed?
--> You can check in Synaptic or run ```
aptitude search ubuntu-restricted-extras
``` and check whether it's flagged as "i".

2. In case of missing output:

Maybe something's muted (simple, but happens). Run "alsamixer" in a terminal and check. "MM" stands for muted...

Do you have multiple sound cards? Please post the output of ```
cat /proc/asound/cards
```

---

### Post by rockerphil on 2008-07-23
my suggestion would be to check the alsa mixer GUI, if you don't have it installed you can install it from Synaptic or the command prompt with:

sudo apt-get install alsagui

then make sure as stated above nothing is muted, hope it helps, and much luck,


Phil

----------------
Now playing: [South Park Mexicans (SPM) - You Know My Name](http://www.foxytunes.com/artist/south+park+mexicans/track/you+know+my+name)
via [FoxyTunes](http://www.foxytunes.com/signatunes/)

---

### Post by ELD on 2008-07-23
Strange rebooting fixed it.

---

### Post by billgoldberg on 2008-07-23
Could it be related to the pulseaudio + flash bug?

Try switching to ALSA instead of pulseaudio (default) in "system -> preferences -> sound".

---

