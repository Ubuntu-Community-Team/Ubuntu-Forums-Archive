---
title: "gstreamer (playbin) - how to get bitrate?"
date: 2009-01-09
forum: Programming Talk
---

### Post by alxlabs on 2009-01-09
I have a simple application which plays an URI audio stream thru playbin. I need to extract bitrate and I understood that I have to extract "stream-info" property from playbin, something like ```
g_object_get (G_OBJECT (pipeline), "stream-info", &aaa, NULL);
```
where "aaa" is the pointer to "..GList of stream info objects" (I can't find what it is from [http://gstreamer.freedesktop.org](http://gstreamer.freedesktop.org)) 
Can anyone point me to the example on how to do it (read&parse "stream-info") or explain in simple words?

---

### Post by SledgeHammer_999 on 2009-01-09
Read here-->[http://gstreamer.freedesktop.org/data/doc/gstreamer/head/manual/html/chapter-metadata.html](http://gstreamer.freedesktop.org/data/doc/gstreamer/head/manual/html/chapter-metadata.html)

> GStreamer makes a clear distinction between two types of metadata, and has support for both types. The first is stream tags, which describe the content of a stream in a non-technical way. Examples include the author of a song, the title of that very same song or the album it is a part of. The other type of metadata is stream-info, which is a somewhat technical description of the properties of a stream. This can include video size, audio samplerate, codecs used and so on. Tags are handled using the GStreamer tagging system. Stream-info can be retrieved from a GstPad.

So you basically need to find every element in playbin and read the GstPad of the correct element. Keep in mind that "playbin" element is a bin/container of other elements. If you don't know what I am talking about read this [_guide_](http://gstreamer.freedesktop.org/data/doc/gstreamer/head/manual/html/index.html).
Maybe there is a simpler solution to your problem, if anyone knows please post(i wanna know too).

---

