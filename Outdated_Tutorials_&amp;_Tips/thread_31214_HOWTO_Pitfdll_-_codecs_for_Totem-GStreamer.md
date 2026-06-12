---
title: "HOWTO: Pitfdll - codecs for Totem-GStreamer"
date: 2005-05-02
forum: Outdated Tutorials &amp; Tips
---

### Post by doclivingston on 2005-05-02
Recently I discovered a library called Pitfdll ([http://ronald.bitfreak.net/pitfdll.php](http://ronald.bitfreak.net/pitfdll.php)) which lets GStreamer use .dll files for codecs. This will let you use (some of) the codecs found in the w32codecs package, without having to install totem-xine.

Currently it only supports Windows Media Video 9 (wmv3), QDesign Music 2 (qdm2) and Intel Indeo 5 (iv50), but hopefully it will support more inthe future. I've tested some random WMV clips I had around as well as the [Serenity Trailer](http://www.apple.com/trailers/universal/serenity/) (which uses qdm2) - and all worked very well.

Currently I don't know of any .debs around which you can install, so you will have to compile it yourself. On to the instructions:


First you will need to have the dependencies installed, the GStreamer development packages, and w32codecs.
```
sudo apt-get install libgstreamer0.8-dev w32codecs
```

Next download the source tarball([http://prdownloads.sourceforge.net/pitfdll/pitfdll-0.8.1.tar.bz2?download)](http://prdownloads.sourceforge.net/pitfdll/pitfdll-0.8.1.tar.bz2?download)), and extract it somewhere. The do the usual ```
./configure --prefix=/usr && make && sudo make install
```

Repeating - you *must* have already install w32codecs _before_ you compile it. It will compile and install successfully if you don't, but none of the codecs will work.

Once that has been done you need to run ```
gst-register-0.8
``` and then you should be able to view movies with totem-gstreamer that you couldn't before.

---

### Post by Nis on 2005-05-02
While everything compiles and installs successfully (and gst-inspect-0.8 pitfdll works) I have never gotten this to work.  It keeps segfaulting.  You milage may vary.  I will suggest something though: if you install checkinstall then you can install pitfdll with 'sudo checkinstall' and then it can easily be uninstalled if necessary.

---

### Post by darrenadams on 2005-05-02
A warning for Breezy users here (like myself)

Make sure that you use GCC 3.3 to compile this (or, at least, don't use GCC 4.0) by setting the CC environment variable before running ./configure like so:```
CC=gcc-3.3 ./configure --prefix=/usr
```

I didn't at first and got this when compiling ext.c.

```
ext.c: In function 'HEAP_strdupAtoW':
ext.c:205: warning: pointer targets in return differ in signedness
ext.c: In function 'VirtualAlloc':
ext.c:472: error: invalid lvalue in assignment
ext.c:501:2: warning: #warning FIXME

```

I suppose the thing to do would be to file a bug against this (if one hasn't already been filed).

Also, would running ```
sudo gst-register-0.8 --gst-registry=/var/lib/gstreamer/0.8/registry.xml
``` be a better bet as it would update the gstreamer registry for the entire system?

---

### Post by Darrena on 2005-05-30
I created a .deb for this, I'll ask Jdong if it can be included in the backports if it is wanted but just so that people are aware, this only works with WMV9 and a few other formats.  This means that you still will not be able to play a lot of older wmv, wma, etc...  formats.

My suggestion to people wanting to play movies using totem, use totem-xine until pitfdll is expanded to more formats.

---

### Post by kaput on 2005-05-31
In case people are interested, Paul Drain (GNOME packager) has created .debs for nearly every Gstreamer package available, including pitfdll. 

You can find info about his repository [here]("http://ubuntuforums.org/showthread.php?t=35480").

---

