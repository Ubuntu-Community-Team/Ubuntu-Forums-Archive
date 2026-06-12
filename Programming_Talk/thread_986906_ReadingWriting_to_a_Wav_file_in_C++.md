---
title: "Reading/Writing to a Wav file in C++?"
date: 2008-11-19
forum: Programming Talk
---

### Post by Stochastic on 2008-11-19
Hi I'm just curious the easiest method to read from and write to a wav file (no need for playback) in C++?  I'm kinda new to libraries and such so is a C library like libsndfile useable in C++ code?

---

### Post by StOoZ on 2008-11-19
yes you can use C libraries in C++ code.

---

### Post by Cracauer on 2008-11-19
People use libsndfile, available in Ubuntu.

The API kinda sucks, but it's not rocket science, I think a sucky API won't kill anyone.

This only reads and writes static files, it won't do in-stream real time filtering.

---

### Post by sshuber on 2008-11-19
If you aren't worried about playback in ubuntu, check out mpg123. They have an API written in C and examples for wav conversion and such. They don't have API function for ALSA right now though. I'm working on my own project that plays mp3's and their API doesn't work in ubuntu. It has to be coded using the ALSA API.

Anyways visit [www.mpg123.de](www.mpg123.de)

---

