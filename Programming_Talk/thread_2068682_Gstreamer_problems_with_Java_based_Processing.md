---
title: "Gstreamer problems with Java based Processing"
date: 2012-10-09
forum: Programming Talk
---

### Post by BcRich on 2012-10-09
Hi 
I'm using Processing.org which has an IDE (called a PDE) that compiles Java applications, so I'm not using Eclipse (or other IDE). Processing just got built-in support for gstreamer so I'm just simply trying to load a movie into a sketch (processing compiled java application). But I keep getting this error 
```
Exception in thread "Animation Thread" java.lang.UnsatisfiedLinkError: Unable to load library 'gstreamer-0.10': libgstreamer-0.10.so: cannot open shared object file: No such file or directory
    at com.sun.jna.NativeLibrary.loadLibrary(NativeLibrary.java:163)
    at com.sun.jna.NativeLibrary.getInstance(NativeLibrary.java:236)
    at com.sun.jna.Library$Handler.<init>(Library.java:140)
    at com.sun.jna.Native.loadLibrary(Native.java:379)
    at org.gstreamer.lowlevel.GNative.loadNativeLibrary(Unknown Source)
    at org.gstreamer.lowlevel.GNative.loadLibrary(Unknown Source)
    at org.gstreamer.lowlevel.GstNative.load(GstNative.java:42)
    at org.gstreamer.lowlevel.GstNative.load(GstNative.java:39)
    at org.gstreamer.Gst.<clinit>(Gst.java:59)
    at processing.video.Video.initImpl(Unknown Source)
    at processing.video.Video.init(Unknown Source)
    at processing.video.Movie.initGStreamer(Unknown Source)
    at processing.video.Movie.<init>(Unknown Source)
    at movtest.setup(movtest.java:30)
    at processing.core.PApplet.handleDraw(PApplet.java:2103)
    at processing.core.PGraphicsJava2D.requestDraw(PGraphicsJava2D.java:190)
    at processing.core.PApplet.run(PApplet.java:2006)
    at java.lang.Thread.run(Unknown Source)
``` 
the code is pretty simple cause it's just basically an example file included with processing
```
/**
 * Loop. 
 * 
 * Move the cursor across the screen to draw. 
 * Shows how to load and play a QuickTime movie file.  
 *
 */

import processing.video.*;

Movie movie;

void setup() {
  size(640, 360);
  background(0);
  // Load and play the video in a loop
  movie = new Movie(this, "transit.mov");
  movie.loop();
}

void movieEvent(Movie m) {
  m.read();
}

void draw() {
  //if (movie.available() == true) {
  //  movie.read(); 
  //}
  image(movie, 0, 0, width, height);
}
```
I've tried other variations of this code but still get the same error. Any idea why it's doing this? If this is a problem with symlinking or something else please could u tell me how to fix it, I really need some help here!

---

### Post by Zugzwang on 2012-10-09
The error is basically a file-not-found error. Did you try installing the Ubuntu package that provides the requested file? Using the web site packages.ubuntu.com, I have found the requested file in the package "libgstreamer0.10-dev", which you might want to try installing. Probably installing "libgstreamer0.10-0" is actually sufficient, but I'm not sure about that.

---

### Post by BcRich on 2012-10-09
> **Zugzwang said:**
> The error is basically a file-not-found error. Did you try installing the Ubuntu package that provides the requested file? Using the web site packages.ubuntu.com, I have found the requested file in the package "libgstreamer0.10-dev", which you might want to try installing. Probably installing "libgstreamer0.10-0" is actually sufficient, but I'm not sure about that.
Hi Zugzwang
thanks for the reply :)
Yes I do already have libgstreamer0.10-dev and libgstreamer0.10-0 installed

---

### Post by spjackson on 2012-10-10
Are you running on 64-bit Ubuntu? If so, is your java (or PDE if that's an executable) 32-bit?

If that's not it, then I think you can get this error from a failed dependency. Since you installed the Ubuntu package, this should not occur. However, you could run ldd on libgstreamer-0.10.so to check.

---

### Post by BcRich on 2012-10-12
Hi spjackson,
thanks for the reply. I'm running Kubuntu 12.04 64bit but have also tried this on Ubuntu 12.04 64bit with no success. the version of processing i'm using is also 64 bit.Unfortunately the problem was not related to failed dependencies as all dependencies for libgstreamer-0.10.so were satisfied. 
On the other hand I've tried running Processing with GStreamer video support in Ubuntu 10.10 and am not having any issues. shot in the dark here but, could this issue be related to the new hybrid X server?

---

### Post by BcRich on 2012-10-14
Please see this thread for a resolution.
[https://forum.processing.org/topic/how-is-video-on-linux-handled#25080000001764427](https://forum.processing.org/topic/how-is-video-on-linux-handled#25080000001764427)

---

