---
title: "Playstation Emulators"
date: 2008-06-21
forum: New to Ubuntu
---

### Post by subaruwrc01 on 2008-06-21
Does anyone using Ubuntu 8.04 have a working Playstation emulator?  I tried the two big ones available (PCSX, ePSXe) with the proper downloaded plugins, but I can't get either one to work.  I'm really bored and need something to do since none of the games I have will run on Linux or wine.

---

### Post by subaruwrc01 on 2008-06-21
Bump

---

### Post by subaruwrc01 on 2008-06-22
Hmm, does anyone know any good emulators that will run under wine?

---

### Post by DGortze380 on 2008-06-22
> **subaruwrc01 said:**
> Hmm, does anyone know any good emulators that will run under wine?

snes9x (native in linux, not wine)

---

### Post by bumanie on 2008-06-22
Can't help with snes games, but here is a a list of games native to linux.
[http://ubuntuforums.org/showthread.php?t=427205](http://ubuntuforums.org/showthread.php?t=427205) Hope that helps your boredom.

---

### Post by subaruwrc01 on 2008-06-22
Thanks!

That helps a little. Unfortunately it doesn't bring me any closer to playing FFVII.

Are there any MMORPG's that run well in Linux?  Free or not.

---

### Post by RomeReactor on 2008-06-22
> **subaruwrc01 said:**
> Thanks!

That helps a little. Unfortunately it doesn't bring me any closer to playing FFVII.

Are there any MMORPG's that run well in Linux?  Free or not.

Hi. You could try [Regnum Online]("http://www.regnumonline.com.ar/index.php?sec=0&l=1"), [PlaneShift]("http://www.planeshift.it/") or [Eternal Lands]("http://www.eternal-lands.com/").

---

### Post by NightCrawler03X on 2008-06-27
If you're having problems getting ePSXe up and running, you might find my installer useful:

[http://ubuntuforums.org/showthread.php?t=550304](http://ubuntuforums.org/showthread.php?t=550304)

It automatically downloads epsxe and all of it's plugins, before automatically sorting everything into the correct folders. It doesn't configure the plugins for you, but that part is easy (like I said, it just puts everything in the right place). It doesn't download a bios image (for obvious reasons), but those are pretty easy to find with a bit of googling.

---

### Post by imasickboy on 2008-06-27
I use [pSX]("http://psxemulator.gazaxian.com/"). Works well.

---

### Post by Venko on 2008-07-01
> **imasickboy said:**
> I use [pSX]("http://psxemulator.gazaxian.com/"). Works well.


I've had no luck getting pSX to run in Hardy Heron. Are you still using Gutsy or something?

---

### Post by roffemuffe on 2008-07-03
> **RomeReactor said:**
> Hi. You could try [Regnum Online]("http://www.regnumonline.com.ar/index.php?sec=0&l=1"), [PlaneShift]("http://www.planeshift.it/") or [Eternal Lands]("http://www.eternal-lands.com/").

[Eve Online]("http://www.eve-online.com") is a very popular MMORPG.
Recently ported to be a native-Linux game as well as it runs on both native-Windows and native-Mac.

---

### Post by RomeReactor on 2008-07-03
> **roffemuffe said:**
> [Eve Online]("http://www.eve-online.com") is a very popular MMORPG.
Recently ported to be a native-Linux game as well as it runs on both native-Windows and native-Mac.

Well, it's not really native in either Linux or Mac since it uses Wine's libraries to run (Cedega/Cider, respectively).

---

### Post by NightCrawler03X on 2008-07-06
[quote="Venko"]I've had no luck getting pSX to run in Hardy Heron. Are you still using Gutsy or something?[/quote]
Tell me what the terminal says when trying to run pSX.
Chances are all you need to install is libgtkglext.

---

### Post by Venko on 2008-07-06
> **NightCrawler03X said:**
> Tell me what the terminal says when trying to run pSX.
Chances are all you need to install is libgtkglext.

```
venko@Natalie:~$ .pSX/pSX/pSX 
[src/linux/sound.cpp, line 215]: 'snd_pcm_hw_params_set_access(pcm_handle,hwparams,SND_PCM_ACCESS_MMAP_INTERLEAVED)' returned 'Invalid argument'
pad=0
Segmentation fault
```

From what I've read pSX won't work with a PulseAudio Linux distro.

---

### Post by NightCrawler03X on 2008-07-07
Well, the reasoning behind Ubuntu now using Pulse Audio for anything is beyond me. I mean, OSS4 is so much better.
And if OSS4 isn't suitable, just use ALSA.

---

### Post by Venko on 2008-07-07
> **NightCrawler03X said:**
> Well, the reasoning behind Ubuntu now using Pulse Audio for anything is beyond me. I mean, OSS4 is so much better.
And if OSS4 isn't suitable, just use ALSA.

Um, as far as I know pSX requires ASLA and won't work with OSS. I assumed for a moment that you had pSX working on Hardy Heron but I must have been mistaken.

Just checked back through the thread and imasickboy uses pSX but I assume he must still be using Gutsy.

---

### Post by NightCrawler03X on 2008-07-07
If I'm not mistaken, ALSA emulates OSS and OSS emulates ALSA.
So if pSX requires alsa and you have oss, it'll still work (theoretically).

---

