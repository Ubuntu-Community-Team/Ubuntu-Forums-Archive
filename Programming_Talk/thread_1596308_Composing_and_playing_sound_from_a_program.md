---
title: "Composing and playing sound from a program"
date: 2010-10-14
forum: Programming Talk
---

### Post by Arndt on 2010-10-14
I collect some data in real time (say, values between 0 and 2000 arriving 100 times a second), and also store the data to files in order to analyze later. One way of studying the data is by drawing curves in a window, zooming in, filtering, etc.

One other that seems useful to me, especially in the real time situation when I can't always be looking at the screen while things are happening, is to have the computer make sounds derived from the data (a ping when a threshold is reached, for example, or sine waves corresponding to elements in the data).

In the simplest case, I just want to play an existing sound file with a ping in it. How do I do that? If calling an external program turns out to be too slow, how can I read in the sound file in my program and send it to the sound hardware? What format would be best?

In the more complex case, I want to play some specific sound, composed on the fly out of sine waves. What libraries exist for that?

I took a look at the 'snack' package, which seemed to be what I wanted, but the latest hurdle when trying to use it is that I seem to have to apply a patch to alsa, and I don't know whether it will work after that. In my experience, it's easy to make the usual sound applications stop working by doing something new.

I use varying programming languages (C++, python, etc.) and it doesn't matter which language the solution is in.

What I can do also ultimately depends on the hardware, and I'm not sure even what to check for. I have a /dev/media device, but not a /dev/sound (which 'snack' wanted to use at first). It's an ordinary laptop, and what I usually do with sound on it is play web radio.

Thank you in advance for any help.

---

### Post by worksofcraft on 2010-10-14
I have used gstreamer to play sounds both from C++ and from python.
The really good thing about gstreamer is that the sound files don't transit your program and the gstreamer bits only need to be loaded once and then can play any number of files.

There are some really good tutorials and wiki's about gstreamer in C C++ and Python and I posted [some gstreamer sample code]("http://ubuntuforums.org/showthread.php?p=9877038#post9877038") on this thread as well as some links. I didn't quite understand why they were no use to the OP of that thread, but perhaps they serve you better ;)

---

