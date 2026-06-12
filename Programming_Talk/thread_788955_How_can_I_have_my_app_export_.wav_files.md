---
title: "How can I have my app export .wav files?"
date: 2008-05-10
forum: Programming Talk
---

### Post by Envergure on 2008-05-10
This past winter I discovered my dad's record collection and fell in love with the sound of analog synthesizers.  Now that I understand the theory of them pretty well I want to make a software synth, but I'm finding it rather difficult to find tutorials on how to create audio files.

Language is C++.

---

### Post by WW on 2008-05-10
What language will you use to create your synth?  The C library [libsndfile](http://www.mega-nerd.com/libsndfile/) has worked for me.

A Python wrapper for libsndfile is available here: [https://savannah.nongnu.org/projects/pysndfile/](https://savannah.nongnu.org/projects/pysndfile/)

---

### Post by eldragon on 2008-05-10
i dont know if building the wav from scratch is what you are looking, i bet there is a c library already able to do that, but to get into the guts of a wav file, i found this
[http://ccrma.stanford.edu/courses/422/projects/WaveFormat/](http://ccrma.stanford.edu/courses/422/projects/WaveFormat/)

it should give you complete control over what ends in the file :D

---

