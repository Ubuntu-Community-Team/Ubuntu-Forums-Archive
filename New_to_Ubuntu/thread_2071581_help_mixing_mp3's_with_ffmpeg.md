---
title: "help mixing mp3's with ffmpeg"
date: 2012-10-15
forum: New to Ubuntu
---

### Post by tommyleeds on 2012-10-15
hi can ffmpeg mix 2 mp3's so like i can hear 1 mp3 in me left ear and the other mp3 in me right ear ?

---

### Post by audiomick on 2012-10-15
going by this
[http://en.wikipedia.org/wiki/Ffmpeg]("http://en.wikipedia.org/wiki/Ffmpeg")

I'd reckon it can't. 

However, what you describe is actually not that hard. You just need to import the files into a Digital Audio program and pan them respectively. I don't know for absolute sure, but I reckon Audacity should be able to sort that out. 

Just out of curiosity, why do you want to do that?

---

### Post by FakeOutdoorsman on 2012-10-16
FFmpeg can do this. I'm assuming you have two mono inputs since you didn't specify:
```
ffmpeg -i left.mp3 -i right.mp3 -filter_complex "amovie=left.mp3 [l] ; amovie=right.mp3 [r] ; [l] [r] amerge" -q:a 4 output.mp3
```
I'm not sure if the so-called "ffmpeg" from the repository has the *amovie* and *amerge* filters. If not you can use a [static build](http://ffmpeg.gusari.org/static/) or compile it: [How To Compile FFmpeg and x264 on Ubuntu](https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide).

---

### Post by tommyleeds on 2012-10-17
> **audiomick said:**
> 
Just out of curiosity, why do you want to do that?
im making some mp3's for a halloween party
i want to mix songs with scarey sound fx

---

### Post by tommyleeds on 2012-10-17
> **FakeOutdoorsman said:**
> 
```
ffmpeg -i left.mp3 -i right.mp3 -filter_complex "amovie=left.mp3 [l] ; amovie=right.mp3 [r] ; [l] [r] amerge" -q:a 4 output.mp3
```
dude that works
cheers

> **FakeOutdoorsman said:**
> I'm assuming you have two mono inputs since you didn't specify:
how can you make ffmpeg work with stereo input's ?

---

### Post by audiomick on 2012-10-17
> **tommyleeds said:**
> im making some mp3's for a halloween party
i want to mix songs with scarey sound fx

> **tommyleeds said:**
> 
how can you make ffmpeg work with stereo input's ?

Hmm, sounds even more like a job for audicity or something along those lines. That's just me thinking like a sound engineer, though....

---

### Post by FakeOutdoorsman on 2012-10-17
> **tommyleeds said:**
> how can you make ffmpeg work with stereo input's ?

It probably "works" with stereo inputs, but I don't know how it will fit 4 channels into 2. Perhaps a channel is discarded or the inputs are made mono? I didn't really investigate.

---

### Post by tommyleeds on 2012-10-20
cheers dudes
i have finished making me mp3's with sound fx's
did'nt have to use audicity.......ffmpeg did the job just great

---

