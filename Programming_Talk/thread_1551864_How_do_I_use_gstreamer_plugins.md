---
title: "How do I use gstreamer plugins?"
date: 2010-08-12
forum: Programming Talk
---

### Post by J05HYYY on 2010-08-12
Hello, I have skimmed through the [GStreamer Application Development Manual]("http://gstreamer.freedesktop.org/data/doc/gstreamer/head/manual/html/index.html") but it does not mention anything about plugins i.e. the good, the bad, and the ugly. Has anyone got any good examples in C which I can look at? I am stuck in a rut.

---

### Post by SledgeHammer_999 on 2010-08-13
Read more carefully. Usually, in gstreamer terms, plugins == gstelements read this: [http://gstreamer.freedesktop.org/data/doc/gstreamer/head/manual/html/chapter-elements.html](http://gstreamer.freedesktop.org/data/doc/gstreamer/head/manual/html/chapter-elements.html)

If you want to learn how to build a simple application then read the "Building an Application" chapter and be patient. If you want to jump to the code already without understanding the concepts then a hello world example code is here: [http://gstreamer.freedesktop.org/data/doc/gstreamer/head/manual/html/chapter-helloworld.html#section-helloworld](http://gstreamer.freedesktop.org/data/doc/gstreamer/head/manual/html/chapter-helloworld.html#section-helloworld)

---

### Post by J05HYYY on 2010-08-13
Like I said, I've skim read the whole thing and it doesn't mention anything about using the good the bad and the ugly plugins. The hello world example doesn't use them either. By the looks of things, it uses only the standard gst-elements. I assume that I have to include something else in order to use the extra elements which are stored inside the plugins.

---

### Post by SledgeHammer_999 on 2010-08-13
That's why I said you should read it CAREFULLY and read the theory. I know it's boring but you will appreciate it later. The bad/good/ugly plugins contain gstelements. Each gstelement is created using a GstElementFactory. Each GstElement has it's own factory which is identified by a name. 

The hello world example uses oggdemux and vorbisdec to playback an oggvorbis file. But what you would you do if you wanted to play a matroska file containing a video stream encoded in h264? You would use matroskademux and ffdec_264 elements. The first is in the "good" package the second is in the "ffmpeg" package. This boils down to knowing which factory name you should use. (use gst-inspect for that).

Eg to create a matroskdemux you should do something like this: 
[php]
GstElement *demuxer = NULL;
demuxer = gst_element_factory_make("matroskademux", NULL); //NULL to automatically receive a unique name for the GstElement
[/php]

---

### Post by J05HYYY on 2010-08-13
Ah, I see. Cheers. One final thing. When I type gst-inspect into the terminal, I can't scroll up beyond a certain point because there are so many elements. Do you know of a way to get around this?

---

### Post by SledgeHammer_999 on 2010-08-13
you can dump the out to a text file. 
```

gst-inspect > myfile.txt

```
(it will be written in the current working dir)
Also, you can do a "gst-inspect matroskademux" to see details about a specific element.
Furthermore, there is a list of all the plugins online on gstreamer's site.

---

