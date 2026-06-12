---
title: "Get PocketSphinx Registered as a GStreamer plugin"
date: 2009-07-11
forum: Programming Talk
---

### Post by DarrenF on 2009-07-11
Hello,
I've spent many hours trying to get PocketSphinx registered as a pluggin to GStreamer.  I've rebuilt both sphinxbase and pocketsphinx a couple of times, but GST-Inspect still cannot see it.  Anyone got this to worked before? Any advice greatfully recieved.
Thanks
Darren.

---

### Post by frenchn00b on 2009-09-12
> **DarrenF said:**
> Hello,
I've spent many hours trying to get PocketSphinx registered as a pluggin to GStreamer.  I've rebuilt both sphinxbase and pocketsphinx a couple of times, but GST-Inspect still cannot see it.  Anyone got this to worked before? Any advice greatfully recieved.
Thanks
Darren.

 
I have just installed the speech reco. under debian stable. I would have a small question.

I install sphinxbase and pocketsphinx, very easy;
but it is not using the alsa by default

would you know where I can find
pocketsphinx_device
to set it to hw:1.0 actually for my alsa usb microphone?

pocketsphinx_device

---

### Post by dhdfoo on 2010-03-19
> I've spent many hours trying to get PocketSphinx registered as a pluggin to GStreamer. I've rebuilt both sphinxbase and pocketsphinx a couple of times, but GST-Inspect still cannot see it. Anyone got this to worked before? Any advice greatfully recieved.

If you built it manually, it will have installed its plugin in /usr/local/lib/gstreamer-0.10, which I believe is not part of the default GStreamer search path.  Also it may be the case that /usr/local/lib is not in your shared library search path either.  In this case you need to set the environment variable

export GST_PLUGIN_PATH=/usr/local/lib

And either add /usr/local/lib to /etc/ld.so.conf, or set:

export LD_LIBRARY_PATH=/usr/local/lib

You can also use the --gst-plugin-path argument to gst-inspect.

Of course, if you just install the pre-built packages, you don't need to do this.

---

### Post by dhdfoo on 2010-03-19
>  would you know where I can find
pocketsphinx_device
to set it to hw:1.0 actually for my alsa usb microphone?

On the command line for pocketsphinx_continuous, just add "-adcdev hw:1,0".  Actually you may need to use plughw:1,0 if your microphone does not support 8kHz mono input.

---

