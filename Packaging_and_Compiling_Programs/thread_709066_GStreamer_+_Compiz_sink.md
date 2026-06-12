---
title: "GStreamer + Compiz sink"
date: 2008-02-27
forum: Packaging and Compiling Programs
---

### Post by furyy on 2008-02-27
I'll drop it here after it 'mysteriously' got lost on gstreamer-devel list :P
Preliminary sink for gstreamer to allow the use of Compiz video plugin as sink. Currently only RGB is supported though and embeded x windows (XOverlay in gstreamer) stay black  :( ( could be video plugin bug as KMplayer, SMplayer have same problems )

I didn't want to mess with automake files any further so i just copy/pasted ximagesink -> xcompizsink and made it part of gst-plugins-base.
Use the script from gstreamer cvs to setup environment for testing ( [http://www.pitivi.org/wiki/GStreamer_CVS_Setup_Page](http://www.pitivi.org/wiki/GStreamer_CVS_Setup_Page)  for help )

Follow the pitivi guide and then cd to gst/head and apply patch to gst-plugins-base by running ```
 patch -p0 < xcompizsink.diff 
```

And for some boost enable xshm ```
./autogen.sh --enable-xshm
```

Gstreamer-properties won't show the sink so you have to select Custom and type **xcompizsink**

---

