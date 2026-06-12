---
title: "Sound programming (as in audio)"
date: 2011-02-08
forum: Programming Talk
---

### Post by captnemo on 2011-02-08
Not sure if this is the right forum.  I'm looking for information / expertise on accessing the sound system/card in Linux.

I develop using C and Gtk but have never needed to access the sound system in Linux until now.  I have decades of experience with digital audio but the last time I needed to get to the sound card was under DOS when such things were extremely easy.

I've done a lot of reading but can't find what I need.  Since this particular program may someday want to be compiled for Windoze, it seems that using Pulse rather than ALSA is the right way to go, but I don't know.

My needs are very simple.  I have a buffer in RAM containing 16,000 8-bit samples of audio.  I want to point the sound card at the buffer and tell it to pump it out to the DAC at 8 ksps.  Extremely simple stuff but from what I've read it seems that I need to write hundreds of lines of code just to perform this simple operation.

Can anyone suggest a simple tutorial or example that will get me going?

Thanks in advance,
Phil

---

### Post by Arndt on 2011-02-08
> **captnemo said:**
> Not sure if this is the right forum.  I'm looking for information / expertise on accessing the sound system/card in Linux.

I develop using C and Gtk but have never needed to access the sound system in Linux until now.  I have decades of experience with digital audio but the last time I needed to get to the sound card was under DOS when such things were extremely easy.

I've done a lot of reading but can't find what I need.  Since this particular program may someday want to be compiled for Windoze, it seems that using Pulse rather than ALSA is the right way to go, but I don't know.

My needs are very simple.  I have a buffer in RAM containing 16,000 8-bit samples of audio.  I want to point the sound card at the buffer and tell it to pump it out to the DAC at 8 ksps.  Extremely simple stuff but from what I've read it seems that I need to write hundreds of lines of code just to perform this simple operation.

Can anyone suggest a simple tutorial or example that will get me going?

Thanks in advance,
Phil

Maybe the portaudio package is what you want. Or not - I'm not experienced enough to even judge that. I got it to play sine waves anyway.

---

### Post by worksofcraft on 2011-02-08
> **captnemo said:**
> Not sure if this is the right forum.  I'm looking for information / expertise on accessing the sound system/card in Linux.

I develop using C and Gtk but have never needed to access the sound system in Linux until now.  I have decades of experience with digital audio but the last time I needed to get to the sound card was under DOS when such things were extremely easy.

I've done a lot of reading but can't find what I need.  Since this particular program may someday want to be compiled for Windoze, it seems that using Pulse rather than ALSA is the right way to go, but I don't know.

My needs are very simple.  I have a buffer in RAM containing 16,000 8-bit samples of audio.  I want to point the sound card at the buffer and tell it to pump it out to the DAC at 8 ksps.  Extremely simple stuff but from what I've read it seems that I need to write hundreds of lines of code just to perform this simple operation.

Can anyone suggest a simple tutorial or example that will get me going?

Thanks in advance,
Phil

One of the most versatile and well thought out projects that already has multi-platform support is [gstreamer]("http://gstreamer.freedesktop.org/documentation/")

There is a tutorial there for how to [write a plug-in]("http://gstreamer.freedesktop.org/data/doc/gstreamer/head/pwg/html/part-building.html") and the very first example is an audio filter that does nothing but fill a buffer and send it through... all you have to do is put your own buffer in and you can then use it in any application as an element in your audio pipe.

---

### Post by captnemo on 2011-02-08
> **worksofcraft said:**
> One of the most versatile and well thought out projects that already has multi-platform support is [gstreamer]("http://gstreamer.freedesktop.org/documentation/")

There is a tutorial there for how to [write a plug-in]("http://gstreamer.freedesktop.org/data/doc/gstreamer/head/pwg/html/part-building.html") and the very first example is an audio filter that does nothing but fill a buffer and send it through... all you have to do is put your own buffer in and you can then use it in any application as an element in your audio pipe.

Hmm, that sounds close to what I'm looking for.  gstreamer was one of the first packages I looked into but in the documentation I ran into dire warnings about not touching or modifying the streams and buffers or terrible things will happen.  Gstreamer seems like a really cool system designed for patching together all kinds of audio and video streaming tools but the most basic thing, playing raw data samples that I already have in a buffer, seemed to be missing and not recommended.

I'll check out your recommendation.  Thank you.

---

### Post by captnemo on 2011-02-08
> **captnemo said:**
> Hmm, that sounds close to what I'm looking for.  gstreamer was one of the first packages I looked into but in the documentation I ran into dire warnings about not touching or modifying the streams and buffers or terrible things will happen.  Gstreamer seems like a really cool system designed for patching together all kinds of audio and video streaming tools but the most basic thing, playing raw data samples that I already have in a buffer, seemed to be missing and not recommended.

I'll check out your recommendation.  Thank you.

With your input as direction and more googling and digging I found this, which appears to be what I've been looking for.  I'll report back after I get it working:

[http://gstreamer.freedesktop.org/data/doc/gstreamer/head/gst-plugins-base-plugins/html/gst-plugins-base-plugins-appsrc.html](http://gstreamer.freedesktop.org/data/doc/gstreamer/head/gst-plugins-base-plugins/html/gst-plugins-base-plugins-appsrc.html)

---

### Post by captnemo on 2011-02-08
Finally found what I was looking for after another 4 hours of Googling and reading documentation.  (At least I now have a decent understanding of gstreamer, Pulse, ALSA, and countless other sound gizmos that are out there.)

The dirt simple solution is libao which is included in the base Ubuntu distro.

The examples I found had a couple of minor problems so I posted source code that compiles clean on Ubuntu 10.04 on my blog:

[http://shuttersparks.blogspot.com/2011/02/simplest-way-to-play-raw-pcm-audio-on.html](http://shuttersparks.blogspot.com/2011/02/simplest-way-to-play-raw-pcm-audio-on.html)

---

### Post by worksofcraft on 2011-02-08
> **captnemo said:**
> Finally found what I was looking for after another 4 hours of Googling and reading documentation.  (At least I now have a decent understanding of gstreamer, Pulse, ALSA, and countless other sound gizmos that are out there.)

The dirt simple solution is libao which is included in the base Ubuntu distro.

The examples I found had a couple of minor problems so I posted source code that compiles clean on Ubuntu 10.04 on my blog:

[http://shuttersparks.blogspot.com/2011/02/simplest-way-to-play-raw-pcm-audio-on.html](http://shuttersparks.blogspot.com/2011/02/simplest-way-to-play-raw-pcm-audio-on.html)

Nice!
I'll keep it in mind... I'm trying to work on Mpeg streams and having more problems with images than audio atm, but it could come in handy :)

---

