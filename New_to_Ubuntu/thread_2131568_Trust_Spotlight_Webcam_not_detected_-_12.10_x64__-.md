---
title: "Trust Spotlight Webcam not detected - 12.10 x64  - v4L v2"
date: 2013-04-02
forum: New to Ubuntu
---

### Post by NMeyne on 2013-04-02
Hello all - video for linux can't seem to find my Trust spotlight webcam  (the 640x480 cheapo one, not the pro).  It's not specifically listed at the Linux uvc driver support page, but other Trust models are.  It works under windows xp.

There is another solved thread here:  [http://ubuntuforums.org/showthread.php?t=1499884](http://ubuntuforums.org/showthread.php?t=1499884)
but this did not work for me

Here is my gstreamer output

```
nick@neptune:~$ gstreamer-properties

(gstreamer-properties:2696): Gtk-WARNING **: Unknown property: GtkDialog.has-separator

(gstreamer-properties:2696): Gtk-WARNING **: Unknown property: GtkDialog.has-separator
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosrc'
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Cannot identify device "/dev/video0". [v4l2_calls.c(493): gst_v4l2_open (): /GstPipeline:pipeline0/GstV4l2Src:v4l2src1:
system error: No such file or directory]
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Cannot identify device "/dev/video0". [v4l2_calls.c(493): gst_v4l2_open (): /GstPipeline:pipeline1/GstV4l2Src:v4l2src2:
system error: No such file or directory]
```


I seem to be missing lots of possible plugins here...  is there a source missing, or some other problem?

Best regards,

Nick

---

### Post by NMeyne on 2013-04-02
I think the answer is to get another webcam from the supported list, given the hassle others seem to be having with these.  'Trust' me on this. ;)

Nick

---

