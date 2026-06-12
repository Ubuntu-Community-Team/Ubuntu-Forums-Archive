---
title: "SDL audio thinks it's smarter than me!"
date: 2008-09-09
forum: Programming Talk
---

### Post by Envergure on 2008-09-09
No matter what specs i request for my audio context SDL gives me the same thing:
```
frequency = 44100
channels = 
samples = 940
SDL_MIX_MAXVOLUME = 127
silence = 
size = 1880 if i ask for mono and 3760 if i ask for stereo
```

I'm trying to write a softsynth, so i really need to be able to get the specs i want.  I do actually get the number of channels i ask for, despite the apparent lack of a value, as long as it's either mono or stereo.  Higher values result in failure to get an audio context.

How can i get the specs i want?  How do i find out the "silence" value?

---

