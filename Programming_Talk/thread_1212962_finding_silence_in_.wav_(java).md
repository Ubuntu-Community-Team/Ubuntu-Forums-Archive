---
title: "finding silence in .wav (java)"
date: 2009-07-14
forum: Programming Talk
---

### Post by vruum on 2009-07-14
Hi
I'm writing a small program to detect short periods of silence in a .wav file, using the javax.sound.sampled library, but I'm kind of lost on the math or missing something fundamental or overcomplicating it.Anyway, what I do right now, is get an audioInputStream, and read from that, to an array of bytes, like: 
```

bites = new byte[format.getFormat().getFrameSize() * (int)(format.getFormat().getFrameRate()/4)];
audioInputStream.read(bites,0,bites.length);

```
which should give me a byte array for 1/4 second of sound. 
the audio file I use for testing is:
PCM_SIGNED 44100.0 Hz, 16 bit, stereo, 4 bytes/frame, little-endian
With nothing but silence in the right channel. and a second of silence at the beginning of the left. 
if I print the first four bytes (which, if I understand it correctly, should be the first frame of audio) I get [2,0,-2,-1]. however, this being 16 bit, the first two bytes (2,0) is the left channel and the next two (-2,-1) is the right. as 16 bit 2's complement signed integers. so -2, -1 is actually the stream 1000001010000001 (-2 = 10000010; -1 = 10000001), or, in decimal 32127, which, I take it, means I'm doing something completely wrong.

---

