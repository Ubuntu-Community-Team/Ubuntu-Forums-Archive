---
title: "video de/-encoding: what is wrong in the software world"
date: 2009-01-21
forum: Programming Talk
---

### Post by Kraut~salat on 2009-01-21
hi,

I need some API that allows me to decode a video and/or v4l Webcam stream, convert the individual frames into jpegs/RGB to manipulate them using QT and then encode it back to a video.

I started out with gstreamer, but I hate it, because it uses GLib and needs a main_loop to work. But that conflicts with my QT main loop. Also I find the doc unsatisfying. For example my pipeline stops after it encoded the first jpeg image. But the doc of the jpegenc module isn't really helpful. It needs a lot more sample code.
Then I tried ffmpeg. It has the worst doc ever, i.e. pretty much none. All there is is the doxygen api doc. With the help of some 3rd party tutorial I managed to do the decoding and importing into a QImage. But how do I do the encoding?  Since the is no reasonable documentation that means trial and error.  Why is there no decent documentation for the ffmpeg packet? Does anyone know any good tutorials on encoding using ffmpeg? Something other that the encode_example.c? Something with some explanations? So far ffmpeg seems to be my best bet. Unless you know how I can make gstreamer continue encoding jpegs after it is done with the first frame.

Using QT's phonon is pointless. It can't do any more than play/pause and stop. Getting individual frames is experimental and not included (yet).

Does anyone have recommendations for my problem? I spent days on this problem so far.

Thanks

---

