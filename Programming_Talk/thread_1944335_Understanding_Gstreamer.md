---
title: "Understanding Gstreamer"
date: 2012-03-21
forum: Programming Talk
---

### Post by Ubuntee1 on 2012-03-21
Hi Everybody,
Can any one explain me what the below calls do.
Actually i have gone through the description available at 
gstreamer Base Plugings Reference Manual, but the description is very limited.
some one please explain or give some references where i can find more 
information for understanding the below calls or related.
Thanks in Advance.
Ubuntee1
 
```

 
[FONT=Arial]           pipeline[/FONT][FONT=Arial]=[/FONT][FONT=Arial]gst_pipeline_new[/FONT][FONT=Arial]("audio-player");[/FONT]
[FONT=Arial]           source[/FONT][FONT=Arial]=[/FONT][FONT=Arial]gst_element_factory_make[/FONT][FONT=Arial]("filesrc",[/FONT][FONT=Arial]"file-source");[/FONT]
[FONT=Arial]           demuxer[/FONT][FONT=Arial]=[/FONT][FONT=Arial]gst_element_factory_make[/FONT][FONT=Arial]("oggdemux",[/FONT][FONT=Arial]"ogg-demuxer");[/FONT]
[FONT=Arial]           decoder[/FONT][FONT=Arial]=[/FONT][FONT=Arial]gst_element_factory_make[/FONT][FONT=Arial]("vorbisdec",[/FONT][FONT=Arial]"vorbis-decoder");[/FONT]
[FONT=Arial]           conv[/FONT][FONT=Arial]=[/FONT][FONT=Arial]gst_element_factory_make[/FONT][FONT=Arial]("audioconvert",[/FONT][FONT=Arial]"converter");[/FONT]
[FONT=Arial]           sink[/FONT][FONT=Arial]=[/FONT][FONT=Arial]gst_element_factory_make[/FONT][FONT=Arial]("autoaudiosink",[/FONT][FONT=Arial]"audio-output");[/FONT]
 

```

---

### Post by HiImTye on 2012-03-21
each of them is a single piece in the process of separating, assigning and decoding a media stream. I'm not sure what more you need, are you planning on writing software that uses them or just curious?

---

### Post by Ubuntee1 on 2012-03-21
> **HiImTye said:**
> each of them is a single piece in the process of separating, assigning and decoding a media stream. I'm not sure what more you need, are you planning on writing software that uses them or just curious?
 
 
Yes Sir, you are right.
 
I am actually planning to develop a small media player.

---

### Post by HiImTye on 2012-03-21
then you should look for resources outside of gStreamer, as gStreamer is just a framework built on top of other resources, look at demuxing, codecs, pipelines, etc

you might have better luck in the [Development & Programming]("http://ubuntuforums.org/forumdisplay.php?f=310") forum

---

### Post by Zugzwang on 2012-03-21
@OP: Read an article about the "factory" design pattern. That should give you some background on what the factory functions are good for: [http://en.wikipedia.org/wiki/Factory_design_pattern](http://en.wikipedia.org/wiki/Factory_design_pattern)

---

### Post by CynicRus on 2012-03-21
[http://code.google.com/p/v4lsink/](http://code.google.com/p/v4lsink/) - read this sources, [http://gstreamer.freedesktop.org/data/doc/gstreamer/head/pwg/html/index.html](http://gstreamer.freedesktop.org/data/doc/gstreamer/head/pwg/html/index.html) and this manual.

---

### Post by nothingspecial on 2012-03-21
*Thread moved to **Programming Talk**.*

---

