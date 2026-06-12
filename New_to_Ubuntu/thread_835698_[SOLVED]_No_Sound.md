---
title: "[SOLVED] No Sound"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by BGFG on 2008-06-20
Hi,
I currently have no sound on my system. Basically  i'd like to try removing all sound packages ALSA and PULSEAUDIO, then re-installing them, Before i attempt anything else Can anyone provide me with the commands ?

If it's sudo apt-get remove alsa and such, feel free to throw a brick.. :)

Thanks....

---

### Post by oldsoundguy on 2008-06-20
try going into system> administration> package manager  and UNCHECK the items.  If that fails, applications> add/remove.

then do a control/alt/backspace and go back in and install Alsa FIRST.

But before you do that .. double check all of your speaker connections and make sure that they are plugged in right .. maybe even swap out the cables if you have some spares around.

---

### Post by sdennie on 2008-06-20
Hello again BGFG,

Before trying a brute force reinstall of alsa and pulse audio, I would try the following command in a terminal:

```

lsmod | grep snd

```

If you get a bunch of output, you shouldn't need to re-install alsa or pulse audio.  Instead, go to System->Preferences->Sound and see if changing any of the sound output options enables sound for you (specifically, switching back and forth between alsa and pulse audio).  If that doesn't work then, in a terminal again try:

```

alsamixer

```

And make sure all of the channels are unmuted and at full volume.

---

### Post by BGFG on 2008-06-20
Hey VOR,OLDSOUNDGUY
You guys rock, lol,thanks I'll let you know how it goes.

Laters...

---

### Post by BGFG on 2008-06-20
Ok so this was just careless, I got the output as VOR said i would and checked my volume settings. most were up at two thirds or higher so when i checked it before i didn't think that would be it. Turns out it was. 
Tested sound with "Big Buck Bunny" and all was beautiful.
I should mention though, that whenever i hibernate, once restarted, the system has no sound.Going to test again now that i know my sound is fine....

Thanks! be back soon.

---

