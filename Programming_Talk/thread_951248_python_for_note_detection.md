---
title: "python for note detection?"
date: 2008-10-17
forum: Programming Talk
---

### Post by h12 on 2008-10-17
Hi. I'm not sure if the ubuntu forums are the best place to ask this, but here it is: Are there any python librarys that can be used to detect the pitches of sounds being played either on the sound card or from an audio input device? I'm trying to make a program that would use a musical insturment to type, instead of a keyboard.

---

### Post by ericesque on 2008-10-18
I was just thinking of the same thing this afternoon.  Figured I might work on a Rhythmbox plugin similar to iTunes Genius... let me know if you find anything.

---

### Post by Bichromat on 2008-10-18
I guess you could use **pyaudio** and **scipy** to read a sound, do an FFT on it, and find the largest peak.

---

### Post by NoBugs! on 2010-08-17
Denemo has the ability to identify notes.
It would be nice to be able to do this in python, but it looks like Denemo's source code is all C...

---

### Post by DanielWaterworth on 2010-08-17
There's also waon, but it's another C program. You could use numpy for finding the fourier transform.

---

### Post by ssam on 2010-08-17
if you do FFT the you will probably want to use scipy

---

