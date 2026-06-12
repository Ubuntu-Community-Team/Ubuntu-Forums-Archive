---
title: "Audio latency/delay in just about every program"
date: 2013-06-02
forum: New to Ubuntu
---

### Post by Jeff07 on 2013-06-02
Bare in mind that I am extremely new to linux, I just installed Ubuntu 13.04 yesterday.  So, feel free to speak in a very noob-friendly fashion.

I'm getting about a 500ms audio latency in just about every program I run.  I've tested out a few games and they all have the same problem, along with all flash stuff in my browser.  I've searched around various forums for answers, but have yet to find a solution that actually works.  I've tried out multiple speakers and headphones, but they all have the same audio latency.

From what I understand, I am using PulseAudio, which is the cause of the delay.  I tried uninstalling it and just using ALSA drivers alone, which actually worked at getting rid of the latency.  Although, when using ALSA alone, audio would only output one program at a time, and a bunch of other features that pulseaudio had weren't available (as far as I know).  So, I ended up just reinstalling PulseAudio.

So, is there a way to fix this problem within PulseAudio?  Any help is appreciated.

---

### Post by sandyd on 2013-06-02
Moved to Absolute Beginners Section

---

### Post by CatKiller on 2013-06-02
Some specifications would be handy, as would the nature of the games you were testing with, ie native or through Wine. This might help track down the problem.

There are sample rate options you can fiddle with if the load is too much for your computer to handle. The only time I've seen latency like that with Pulse is when I had a loopback monitor set up, but I don't think that should be there on a fresh install.

---

### Post by Jeff07 on 2013-06-03
The games I tested were Day of Defeat and Left 4 Dead 2 natively with steam.  I also tested CS:GO through wine.  And as I said before, flash also has this latency.

I'll try and mess around with the sample rate and report back.

---

### Post by Jeff07 on 2013-06-03
I lowered the sample rate but the latency is still there.

---

### Post by CatKiller on 2013-06-03
Hardware specs? Also, knowing how much spare processor time you have when you're suffering from the lag might be useful, that you'd get from top or similar. I'd expect to see broken sound rather than late sound if it just can't keep up, though.

It's not so much the sample rate as the resampling method that I was thinking of; some calculations are just harder than others. JACK has Periods/Buffers settings that directly affect latency - it's a balancing act to keep the buffers sufficiently full that you don't get glitches, but not hold so much that the audio is too late. I don't recall whether Pulse has the same kind of options in this regard. Again, I'd be surprised if this was set too high on a fresh install the same as if there was a monitoring stream, but the audio stream has to be somewhere during that half-second. It's possible that something like that is set by default as a particular quirk of the sound hardware, though.

---

### Post by Jeff07 on 2013-06-03
Specs are:

Intel Core i5 3570k @ 4.3 ghz
Nvidia 550ti
8gb DDR3 RAM @ 1600mhz
Everything is running off a partition on an SSD, and I'm using the integrated sound card on my Asus P8Z77-V LK motherboard.  (it says the audio chipset is[FONT=helvetica][COLOR=#4d4d4d] Realtek ALC892)

I do have some news to report, though.  I uninstalled PulseAudio using the purge command in terminal, and installed it again.  Now, the audio latency is much less severe, but still present.  The delay is more like 70ms to 100ms, which is a lot less noticeable.  I'm curious as to why this lessened the latency, because I purged pulseaudio and reinstalled it the exact same way previously.
[/COLOR][/FONT]

---

