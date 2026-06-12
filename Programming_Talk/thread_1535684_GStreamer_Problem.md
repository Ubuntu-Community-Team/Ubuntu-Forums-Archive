---
title: "GStreamer Problem"
date: 2010-07-21
forum: Programming Talk
---

### Post by Tahakki on 2010-07-21
I'm having trouble getting GStreamer to combine audio and video into one file. The Python code looks like this:

```
filmPipe = gst.Pipeline("filmPipe")
                filmSrc = gst.element_factory_make("multifilesrc", "filmSrc")
                filmSrc.set_property("location", "pictures/%d.png")
                filmFilt1 = gst.element_factory_make("capsfilter", "filmFilt1")
                filmCap1 = gst.Caps("image/png,framerate=5/1,pixel-aspect-ratio=1/1")
                filmFilt1.set_property("caps", filmCap1)
                filmPngDec = gst.element_factory_make("pngdec", "filmPngDec")
                filmff = gst.element_factory_make("ffmpegcolorspace", "filmff")
                filmFilt2 = gst.element_factory_make("capsfilter", "filmFilt2")
                filmCap2 = gst.Caps("video/x-raw-yuv")
                filmFilt2.set_property("caps", filmCap2)
                filmTheora = gst.element_factory_make("xvidenc", "filmTheora")
                filmQue = gst.element_factory_make("queue", "filmQue")
                filmOggmux = gst.element_factory_make("ffmux_mp4", "filmOggmux")
                filmFilesink = gst.element_factory_make("filesink", "filmFilesink")
                filmFilesink.set_property("location", self.movPath)
                musicSrc = gst.element_factory_make("filesrc", "musicSrc")
                musicSrc.set_property("location", self.musicPath)
                musicDec = gst.element_factory_make("ffdec_mp3", "musicDec")
                musicEnc = gst.element_factory_make("lame", "musicEnc")
                musicQue = gst.element_factory_make("queue", "musicQue")

                filmPipe.add(filmSrc, filmFilt1, filmPngDec, filmff, filmFilt2, filmTheora, filmQue, filmOggmux, filmFilesink)
                filmPipe.add(musicSrc, musicDec, musicEnc, musicQue)
                gst.element_link_many(filmSrc, filmFilt1, filmPngDec, filmff, filmFilt2, filmTheora, filmQue, filmOggmux, filmFilesink)
                gst.element_link_many(musicSrc, musicDec, musicEnc, musicQue, filmOggmux, filmFilesink)
                filmPipe.set_state(gst.STATE_PLAYING)
```

This returns the error:
```
Traceback (most recent call last):
  File "app.py", line 100, in movGen
    gst.element_link_many(musicSrc, musicDec, musicEnc, musicQue, filmOggmux, filmFilesink)
gst.LinkError: failed to link filmOggmux with filmFilesink

```

---

### Post by SledgeHammer_999 on 2010-07-21
You can't just link all the elements together. You should read a little bit on the theory. Each element has some pads. Linking elements is done by linking pads. The are three types of pads. always/sometimes/on request.
Always->the pad is always present (eg a filesrc element)
Sometimes->the pad is sometimes present depending on some factors. eg a demuxer element may make available only two pads if the stream has video+audio. it will produce a third pad if the stream has subtitles or a second audio track. etc (eg oggdemux element)
On request-> the pad is created only when the user requests it. eg on muxer elements. you may need 2 pads for video+audio. or 3 video+audio+subtitle. (eg oggmux).

I don't know if pygst has specific guides on this, but the general C guide helps a lot. (just ignore the C code, but it is simple in most cases).

About pads and how to request a 'request' pad-->[http://gstreamer.freedesktop.org/data/doc/gstreamer/head/manual/html/chapter-pads.html#section-pads](http://gstreamer.freedesktop.org/data/doc/gstreamer/head/manual/html/chapter-pads.html#section-pads)

The contents of the guide--->[http://gstreamer.freedesktop.org/data/doc/gstreamer/head/manual/html/index.html](http://gstreamer.freedesktop.org/data/doc/gstreamer/head/manual/html/index.html)

---

### Post by Tahakki on 2010-07-21
Linking elements together has always worked in the past though?

Have you any idea what exactly I should do to get this working?

---

### Post by Tahakki on 2010-08-05
Bumpybump.

---

### Post by Tahakki on 2010-08-06
Bump again.

---

### Post by ggaaron on 2010-08-07
Maybe this examples will help: [http://wiki.laptop.org/go/GStreamer](http://wiki.laptop.org/go/GStreamer)
Somewhere there is an example combining video and audio.

Happy hacking

---

### Post by Tahakki on 2010-08-13
There doesn't seem to be one for actually combining audio and video?

---

### Post by ggaaron on 2010-08-14
And what are this pipelines?

Encode video+audio as ogg:

v4l2src ! queue ! ffmpegcolorspace ! theoraenc ! queue ! \
  oggmux name=mux  alsasrc ! queue ! audioconvert ! vorbisenc ! queue ! mux. mux. ! queue ! ...


A long version of videotestsrc ! ximagesink &; audiotestsrc ! alsasink:

videotestsrc ! ffmpegcolorspace ! theoraenc ! queue ! \
  oggmux name=mux audiotestsrc ! audioconvert ! vorbisenc ! queue ! mux. mux. ! queue ! \
  oggdemux name=demux ! queue ! theoradec ! ffmpegcolorspace ! \
    ximagesink demux. ! queue ! vorbisdec ! audioconvert ! alsasink

---

### Post by ggaaron on 2010-08-14
gst-inspect says that sink pad is added dynamically to the muxer, your problem is probably similar to this one:

[http://stackoverflow.com/questions/2993777/gstreamer-of-pythons-gst-linkerror-problem](http://stackoverflow.com/questions/2993777/gstreamer-of-pythons-gst-linkerror-problem)

---

