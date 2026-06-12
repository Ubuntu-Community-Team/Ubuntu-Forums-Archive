---
title: "Midi Sequencer"
date: 2008-01-30
forum: Programming Talk
---

### Post by Shinpou on 2008-01-30
Hello everyone!

I'm programming a MIDI-player, no MIDI-recording features, just a program that parses MIDI-files and then sends the commands appropriately to external devices (that consecutively will eventually control robots).  Now what I'd like is to be informed on the MIDI-scene. It is my understanding that everyone uses the readily available ALSA-midi for playing back MIDI - why would that be?

If I created my software to be able to play external devices by sending them midi data in a straight-forward manner, is there any use for me to use ALSA in between and not /dev/midi? As far as simplicity goes, reading MIDI from a file, and then with few modifications and timing writing it to /dev/midi seems to work easier, so is there a reason one should not do it like this? Or could it be that I have been fooled into thinking there is a difference between /dev/midi and the ALSA-way of doing things, while in reality there is none?

Please share every bit of knowledge you might have concerning the topics of this post. I would much appreciate ^^ 

Cheers,
Lari

---

