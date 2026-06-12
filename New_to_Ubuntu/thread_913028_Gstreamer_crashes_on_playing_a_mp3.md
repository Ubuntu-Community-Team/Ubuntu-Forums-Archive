---
title: "Gstreamer crashes on playing a mp3"
date: 2008-09-07
forum: New to Ubuntu
---

### Post by meindian523 on 2008-09-07
```
easwarh@l1nuxr0cks:~$ totem ~/Music/Evanescence/The\ Open\ Door/Evanescence-The\ Open\ Door-02-Call\ Me\ When\ You\'re\ Sober.mp3 

** (totem:8010): CRITICAL **: bacon_video_widget_common_get_vis_quality: assertion `q < G_N_ELEMENTS (vis_qualities)' failed

** (totem:8010): CRITICAL **: bacon_video_widget_common_get_vis_quality: assertion `q < G_N_ELEMENTS (vis_qualities)' failed
** Message: Error: Internal GStreamer error: pad problem.  Please file a bug at http://bugzilla.gnome.org/enter_bug.cgi?product=GStreamer.
gstplaybin.c(1267): gen_vis_element (): /play:
Failed to configure the visualisation element.

```
Gstreamer version 0.10x.Ubuntu 8.04.1.GNOME version 2.22.3.

---

### Post by meindian523 on 2008-09-07
I have filed a bug report,but the GNOME project page advised me to look at my distro's forums,so I posted a thread here,just in case someone has experience correcting this problem,so that I don't clog up the system with a bug that can be easily solved.

---

### Post by Blutack on 2008-09-07
As a workaround you could disable the visualisations in Totem.
You could also try setting your Gstreamer Video output to Xv, by typing
> 
gstreamer-properties

and changing the Default Output to Xv.

---

### Post by meindian523 on 2008-09-08
Thanks,I will try that.

---

### Post by meindian523 on 2008-09-12
When I try to test the output after selecting Xv,it pops with "Couldn't initialise Xv output".And totem when run with Xv selected,returns
> The video output is in use by another application. Please close other video applications, or select another video output in the Multimedia Systems Selector.
Terminal output:
```

easwarh@l1nuxr0cks:~$ totem ~/Desktop/ANTHEM\ MIX.mp3 

** (totem:7945): CRITICAL **: bacon_video_widget_common_get_vis_quality: assertion `q < G_N_ELEMENTS (vis_qualities)' failed

** (totem:7945): CRITICAL **: bacon_video_widget_common_get_vis_quality: assertion `q < G_N_ELEMENTS (vis_qualities)' failed
** Message: Error: Could not initialise Xv output
xvimagesink.c(1333): gst_xvimagesink_get_xv_support (): /video-sink/bin0/xvimagesink0:
No port available



```
Also,playing mp3s from an ntfs partition works fine,ext3 partitions,not.

---

