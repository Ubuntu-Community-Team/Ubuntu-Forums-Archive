---
title: "Something is corrupting my audio files?"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by tabithaboof on 2008-05-21
Since I upgraded to Hardy I have noticed that many of my audio files have glitches for split seconds at a time almost like a sqeak or a CD skipping. I have tried to play the audio files multiple times and they always skip in the same place. I have also tried to play these audio files on different playback software and I have the same skip in the same place. 

Does anyone have any idea what could be causing this or how to go able troubleshooting/solving the problem?

---

### Post by Watchtow3r on 2008-05-21
If you downloaded them from limewire or something it probably is the mp3 file that's the problem. Nothing corrupted it, they just got copied and re-distributed on Linewire so many times that they begin to degrade in audio quality.

---

### Post by tabithaboof on 2008-05-21
Thanks for the idea but I dont think so. I have been using many of these files for years from various sources and haven't had a problem. I keep them all backed up on an external drive which they seem to play from ok. It isnt until they get onto my laptop that they start to glitch,

---

### Post by wdaniels on 2008-05-21
> **tabithaboof said:**
> I have also tried to play these audio files on different playback software and I have the same skip in the same place.

A lot of different audio programs use the same backend libraries (e.g. gstreamer) to actually playback the files, so it still may be a software issue rather than some problem with the files. You could try to play the files with something like VLC Media Player which has entirely its own code (I think).

But if it's definitely the same with other decoders then I'm not sure what would cause such exactly repeatable playback glitches. Widespread file corruption like that would surely be noticeable in other files too, unless perhaps you've used some kind of software to edit tags in the files that's faulty and caused corruption?

---

### Post by tabithaboof on 2008-05-22
> **wdaniels said:**
> A lot of different audio programs use the same backend libraries (e.g. gstreamer) to actually playback the files, so it still may be a software issue rather than some problem with the files. You could try to play the files with something like VLC Media Player which has entirely its own code (I think).

Thats a good idea, I tried VLC and a bunch of other players, all had the same issue. So I moved some problem files from my PC to my IPOD and my PSP, the Ipod glitches in the exact same place and the PSP won't even play the files. I am guessing that means either the disk is corrupt or something I am doing is damaging the files?

> **wdaniels said:**
> unless perhaps you've used some kind of software to edit tags in the files that's faulty and caused corruption?

The only thing I have done is used Amarok to edit the MP3 tags. I have edited ALOT of files over the past couple of weeks before I upgraded I dont know if that would affect things? Also I dont know if this matters or not but I have noticed a few of my mp3 files will play the END of one song at the START of the next song in the album so for example I have the last split second of 01 - XXXXXXX as the start of the file for 02 - YYYYYY any ideas anyone?

---

### Post by wdaniels on 2008-05-23
> **tabithaboof said:**
> a few of my mp3 files will play the END of one song at the START of the next song in the album so for example I have the last split second of 01 - XXXXXXX as the start of the file for 02 - YYYYYY any ideas anyone?

Some players allow you to "crossfade" between tracks, which may be what you're talking about here. Or do you mean that playing one track by itself you sometimes get fragments of the next/previous one?

Just to be clear, are we talking about audio files that used to work fine until recently, or new ones that you've ripped recently?

---

### Post by guildofghostwriters on 2008-05-23
What about copying the okay copies from your external to your laptop and changing the permissions of the files to 'read only' before you play them - surely in order to 'corrupt' or damage the mp3 some change must be made to it and then the changed/damaged version saved. So if they're read only, and the glitches keep happening, you can rule out corrupted files and start looking elsewhere for solutions?

---

### Post by tabithaboof on 2008-05-25
> **wdaniels said:**
> Some players allow you to "crossfade" between tracks, which may be what you're talking about here. Or do you mean that playing one track by itself you sometimes get fragments of the next/previous one?

Just to be clear, are we talking about audio files that used to work fine until recently, or new ones that you've ripped recently?

Thanks for the continuing help. Its is definitly not crossfading. There are little skips and glitches in various places through (although the start is more common) various tracks as well as fragments of tracks being copied/written (or something) to the start of other tracks.


> **guildofghostwriters said:**
> What about copying the okay copies from your external to your laptop and changing the permissions of the files to 'read only' before you play them - surely in order to 'corrupt' or damage the mp3 some change must be made to it and then the changed/damaged version saved. So if they're read only, and the glitches keep happening, you can rule out corrupted files and start looking elsewhere for solutions?

Thats a good idea for trouble shooting but I have something like 9500 audio files and its very hard to establish which ones have problems and which are ok. 

The files take up about 55GB all together and I wondered if moving them to  my external USB HD for backup or when restoring them to my laptop after reinstalling would cause problems?

---

### Post by diablo75 on 2008-05-25
This glitching is likely Pulse Audio.  See the dev's blog about this here:

[http://0pointer.de/blog/projects/pulse-glitch-free.html](http://0pointer.de/blog/projects/pulse-glitch-free.html)

---

### Post by tabithaboof on 2008-05-26
> **diablo75 said:**
> This glitching is likely Pulse Audio.  See the dev's blog about this here:

[http://0pointer.de/blog/projects/pulse-glitch-free.html](http://0pointer.de/blog/projects/pulse-glitch-free.html)

Thanks for the input but, I wouldnt have thought pulse audio glitching would acctually damage the files for they played back "glitched" on my ipod/psp though?

---

### Post by anarchyuk on 2008-07-05
i have the exact same issue, they are fine for a while then start jumping and skipping the whole song only lasts for 20 secs max, the only program i have found that plays them is elisa!! strange

---

