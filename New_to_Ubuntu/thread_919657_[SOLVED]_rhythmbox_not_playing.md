---
title: "[SOLVED] rhythmbox not playing"
date: 2008-09-14
forum: New to Ubuntu
---

### Post by Zopiac on 2008-09-14
i just reinstalled ubuntu, and now rhythmbox isnt playing any of my songs (mainly mp3s, maybe a few oggs). it isnt giving out any error output in a terminal, either. flash sounds, wmv files, and login/out sounds, etc, work, but not anything in rhythmbox...i havent tried the files in any other mp3 player program yet.

---

### Post by subaruwrc01 on 2008-09-14
Are the codecs installed?

Or is the player just hanging at 0:00 for anything?

---

### Post by aloshbennett on 2008-09-14
Also, there could be a problem with the firefox flash plugin.
Can you try playing after you close firefox?

---

### Post by Zopiac on 2008-09-14
> **aloshbennett said:**
> Also, there could be a problem with the firefox flash plugin.
Can you try playing after you close firefox?

i dont use firefox >.>

@subaruwrc01: it tries to play, and puts an error icon next to it, and tries the next song, going on until its failed all of the songs

---

### Post by Mornedhel on 2008-09-14
Sounds like a missing codec to me.

---

### Post by Zopiac on 2008-09-14
> **Mornedhel said:**
> Sounds like a missing codec to me.

like that tells me anything :P

any idea what codec? does it depend on my chipset? well, i can't check my chipset because im stuck at 640x480 and cant see the part that tells me the chipset in the window :P will look when i get my graphics back.

---

### Post by Mornedhel on 2008-09-14
Did you install the ubuntu-restricted-extras package ? This should install MP3 support. If you need more multimedia stuff (.wmv, .rm, encrypted DVDs, etc), take a look at the Medibuntu repository.

---

### Post by Zopiac on 2008-09-14
ok, i installed the ubuntu-restricted-extras, but its still broken...i relogged in, but didnt restart yet....do i need to?

---

### Post by Mornedhel on 2008-09-14
You never need to reboot unless it's something to do with hardware.

Could you run rhythmbox from the console, try to play a few mp3 files, and post the output ?

---

### Post by Zopiac on 2008-09-14
> **Mornedhel said:**
> You never need to reboot unless it's something to do with hardware./QUOTE]
all right, didnt think so.

[QUOTE=Mornedhel;5788060]Could you run rhythmbox from the console, try to play a few mp3 files, and post the output ?

read my first post :) i said there were no output errors

---

### Post by R_T_H on 2008-09-14
Could it be a problem with rhythmbox itself? Try reinstalling through synaptics, maybe :)

---

### Post by Zopiac on 2008-09-14
> **R_T_H said:**
> Could it be a problem with rhythmbox itself? Try reinstalling through synaptics, maybe :)

nope, still fails

---

### Post by Mornedhel on 2008-09-14
Sorry about that. I'm getting tired (it's in the evening here...)

I just installed Rhythmbox, but realized I don't have any mp3s around. I still think it's a codec/gstreamer problem, though (IIRC, Rhythmbox uses gstreamer, right ? Can a more knowledgeable user confirm ?)

R_T_H : Yup. Might work. Edit : OK, you tried that.

---

### Post by R_T_H on 2008-09-14
> **Zopiac said:**
> nope, still fails

I have not the faintest idea :) I would suggest trying to use a different programs to find whether it is a file- or program-related problem. If you're at 640x480, maybe mplayer-nogui (sp?) might be a good choice :)

---

### Post by Mornedhel on 2008-09-14
As R_T_H says, mplayer-nogui will work even if there's a gstreamer problem, so we could rule out a hardware problem.

Just run mplayer [your mp3 file] .

---

### Post by Zopiac on 2008-09-15
> **Mornedhel said:**
> As R_T_H says, mplayer-nogui will work even if there's a gstreamer problem, so we could rule out a hardware problem.

Just run mplayer [your mp3 file] .

? i dont understand

---

### Post by nowshining on 2008-09-15
open up a terinal and run that command ie:


mplayer /home/username/Desktop/test.mp3

you cna use tab completion.

---

### Post by Zopiac on 2008-09-15
```
zopiac@Zopiac:~$ mplayer /home/zopiac/Music/FrostWire/An_Endless_Sporadic_-_Impulse.MP3
MPlayer 1.0rc2-4.2.3 (C) 2000-2007 MPlayer Team
CPU: AMD Sempron(tm) Processor 3000+ (Family: 15, Model: 79, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/zopiac/Music/FrostWire/An_Endless_Sporadic_-_Impulse.MP3.
Audio file file format detected.
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 44100 Hz, 2 ch, s16le, 128.0 kbit/9.07% (ratio: 16000->176400)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
No protocol specified
E: client-conf-x11.c: XOpenDisplay() failed
AO: [pulse] Failed to connect to server: Invalid argument
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A: 8X.X (1.30.X) of 260.0 (04:20:0) 1.6%
```

at the end there, the Xs are, yes, variables (i couldnt copy/paste that part). The thing is, its playing, but if there is an error somewhere there that might be rhythmbox's culprit, there you go.

---

### Post by Mornedhel on 2008-09-15
The point was to find out if it's a hardware/driver problem, or something else.

Since you heard sound, it's not a hardware problem.

I still have no idea why sound doesn't play with Rhythmbox. Have you tried a different player ?

---

### Post by skipsbro on 2008-09-15
I would suggest installing the gstreamer plugins as well as the ubuntu-restricted-extras, that always worked for me.

Just go into Synaptic and search "gstreamer", I can't remember their names, but there are a bunch, and I know there's one for a variety of music files including mp3

---

### Post by Mornedhel on 2008-09-15
> **skipsbro said:**
> I would suggest installing the gstreamer plugins as well as the ubuntu-restricted-extras, that always worked for me.

Doesn't ubuntu-restricted-extras depend on gstreamer ?

Anyway, parent is right, it might be worth a try to install all gstreamer0.10 packages.

---

### Post by Zopiac on 2008-09-15
> **Mornedhel said:**
> Doesn't ubuntu-restricted-extras depend on gstreamer ?

Anyway, parent is right, it might be worth a try to install all gstreamer0.10 packages.

all right, that fixed it, thx!

---

### Post by Mornedhel on 2008-09-15
Note for the future : ubuntu-restricted-extras does not *depend* on gstreamer, it *recommends* them :

$ apt-cache depends ubuntu-restricted-extras 
ubuntu-restricted-extras
  Recommends: flashplugin-nonfree
  Recommends: gstreamer0.10-ffmpeg
  Recommends: gstreamer0.10-pitfdll
  Recommends: gstreamer0.10-plugins-bad
  Recommends: gstreamer0.10-plugins-bad-multiverse
  Recommends: gstreamer0.10-plugins-ugly
  Recommends: gstreamer0.10-plugins-ugly-multiverse
  Recommends: libdvdread3
  Recommends: liblame0
  Recommends: msttcorefonts
    ttf-liberation
  Recommends: sun-java6-plugin
  Recommends: unrar

Thus installation will have to be manual. Glad to have this sorted.

---

### Post by james.exe on 2009-10-01
-

---

### Post by jackharvest on 2009-10-26
> **Mornedhel said:**
> Did you install the ubuntu-restricted-extras package ? This should install MP3 support. If you need more multimedia stuff (.wmv, .rm, encrypted DVDs, etc), take a look at the Medibuntu repository.

Re-installing ubuntu-restricted-extras solved my problem. I recently installed a codec that would allow for mpeg-aac encoding, which seems to have screwed with my restricted-extras as well.

Thanks.

---

