---
title: "SDL_mixer and sample rates"
date: 2011-01-15
forum: Programming Talk
---

### Post by fieryrage on 2011-01-15
I'm currently having trouble finding a way to play .ogg files with different sample rates using SDL_mixer. I've read somewhere that SDL_mixer can only resample multiples of 11025 (22050, 44100 etc).

However the files I want to play might have a different sample rate (e.g. 32000 Hz). If I try to play it when I open the audio with something like 22050 it sounds completely wrong. 

So is there a (hopefully straightforward) solution to this?

---

