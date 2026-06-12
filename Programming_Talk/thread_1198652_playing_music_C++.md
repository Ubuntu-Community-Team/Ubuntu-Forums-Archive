---
title: "playing music C++"
date: 2009-06-27
forum: Programming Talk
---

### Post by Woody1987 on 2009-06-27
Im writing a program which at some point will play any number of mp3 files. I want to use Alsa or pulseaudio (which do you recommend?) as the backend. I have the headers for both installed. Could someone write some basic C++ showing how to load an mp3 file and play it using either alsa or pulse or point me to a tutorial elsewhere? Thanks.

---

### Post by monraaf on 2009-06-27
I would recommend using a higher level framework such as GStreamer :) But if the choice is between alsa and pulse, I would probably use alsa since it seems more widespread, at least in the Linux world that is.

---

### Post by Woody1987 on 2009-06-27
how would gstreamer work? does it use alsa? or can i specify what it uses? or is it different entirely to both alsa and pulse?

---

### Post by monraaf on 2009-06-27
GStreamer is different, what you do is create a pipeline, put elements in it (e.g filesrc decodebin audioconvert alsasink) link the elements together and run the pipeline, it will run the whole media pipeline in a different thread.

---

### Post by Woody1987 on 2009-06-27
ok thx, could you point me to any good tutorials on this?

---

### Post by monraaf on 2009-06-27
Sure.

[http://gstreamer.freedesktop.org/data/doc/gstreamer/head/manual/html/index.html](http://gstreamer.freedesktop.org/data/doc/gstreamer/head/manual/html/index.html)

---

### Post by Woody1987 on 2009-06-27
sweet, thx

---

### Post by SledgeHammer_999 on 2009-06-27
> **Woody1987 said:**
> how would gstreamer work? does it use alsa? or can i specify what it uses? or is it different entirely to both alsa and pulse?

yes you can specify Gstreamer what to use. The sink-element of your pipeline controls where the audio is outputted(when you're familiar with gstreamer terminology you'll understand what I am talking about).

---

### Post by Woody1987 on 2009-06-27
Having looked over some of the documentation ive noticed that its all in C, im hoping to make a QT app which requires c++. Is it possible to use gstreamer with c++?

---

### Post by monraaf on 2009-06-28
Surely you can use C in a C++ program.

---

### Post by JordyD on 2009-06-28
> **monraaf said:**
> Surely you can use C in a C++ program.

It's ugly, in my experience. At least if you're trying to do something Object-Oriented.

---

### Post by gorilla on 2009-06-29
> **Woody1987 said:**
> im hoping to make a QT app which requires c++.

Assuming you're not talking about Quicktime, a good choice for you might be Phonon instead of GStreamer, as it is Qt's and Kde's own sound API, included in Qt since v4.4. You'll find examples and short demo applications in the Qt documentation, and there are a number of audio players using Phonon to be found at qt-apps.org

---

### Post by poisonkiller on 2009-06-29
You may try Gstreamermm, C++ bindings for Gstreamer. Unfortunately it is not in Jaunty's repositorys, but is in Karmic's, so you'll have to download it from there.

---

