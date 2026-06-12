---
title: "xlib, do a fast scrolling"
date: 2007-06-13
forum: Programming Talk
---

### Post by tanozfood on 2007-06-13
Hello,
I am trying to develop a small piece of code that display the waveform while playing a song.
My idea was this: build an offscreen representation of all the audio samples while loading the
song in the buffer (keep entire song in memory), and then display the current part scrolling
it while playing (in sync).
However, I do not know how to do it in a good way.
Using Xlib I cannot use Pixmaps as offscreen containers because they seems to be limited in
dimension or memory. Moreover, I cannot find a way to do scrolling with a simple library call
(or analogous efficient way).
So, what could be a *good and fast* solution to my problem?
I suppose having direct rendering enabled in X could help me.
OpenGL?
Please point me to a direction..
Thanks,
                    Gaetano

---

