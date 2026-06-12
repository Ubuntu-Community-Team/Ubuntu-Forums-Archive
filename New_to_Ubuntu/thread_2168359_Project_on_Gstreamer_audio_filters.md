---
title: "Project on Gstreamer audio filters"
date: 2013-08-17
forum: New to Ubuntu
---

### Post by Rahul04789 on 2013-08-17
Hello friends,

I want to make a plug in on Gstreamer 1.0 audio filter.
I got the following filters already built on Gstreamer 1.0 

[TABLE]
[TR]
[TD][audioamplify]("http://gstreamer.freedesktop.org/data/doc/gstreamer/head/gst-plugins-good-plugins/html/gst-plugins-good-plugins-audioamplify.html")
[/TD]
 [TD]Amplifies an audio stream by a given factor[/TD]
 [/TR]
 [TR]
 [TD][audiochebband]("http://gstreamer.freedesktop.org/data/doc/gstreamer/head/gst-plugins-good-plugins/html/gst-plugins-good-plugins-audiochebband.html")

[/TD]
 [TD]Chebyshev band pass and band reject filter[/TD]
 [/TR]
 [TR]
 [TD][audiocheblimit]("http://gstreamer.freedesktop.org/data/doc/gstreamer/head/gst-plugins-good-plugins/html/gst-plugins-good-plugins-audiocheblimit.html")
[/TD]
 [TD]Chebyshev low pass and high pass filter
[/TD]
 [/TR]
 [TR]
 [TD][audiodynamic]("http://gstreamer.freedesktop.org/data/doc/gstreamer/head/gst-plugins-good-plugins/html/gst-plugins-good-plugins-audiodynamic.html")
[/TD]
 [TD]Compressor and Expander[/TD]
 [/TR]
 [TR]
 [TD][audioecho]("http://gstreamer.freedesktop.org/data/doc/gstreamer/head/gst-plugins-good-plugins/html/gst-plugins-good-plugins-audioecho.html")
[/TD]
 [TD]Adds an echo or reverb effect to an audio stream[/TD]
 [/TR]
 [TR]
 [TD][audiofirfilter]("http://gstreamer.freedesktop.org/data/doc/gstreamer/head/gst-plugins-good-plugins/html/gst-plugins-good-plugins-audiofirfilter.html")
[/TD]
 [TD]Generic audio FIR filter with custom filter kernel[/TD]
 [/TR]
 [TR]
 [TD][audioiirfilter]("http://gstreamer.freedesktop.org/data/doc/gstreamer/head/gst-plugins-good-plugins/html/gst-plugins-good-plugins-audioiirfilter.html")
[/TD]
 [TD]Generic audio IIR filter with custom filter kernel[/TD]
 [/TR]
 [TR]
 [TD][audioinvert]("http://gstreamer.freedesktop.org/data/doc/gstreamer/head/gst-plugins-good-plugins/html/gst-plugins-good-plugins-audioinvert.html")
[/TD]
 [TD]Swaps upper and lower half of audio samples[/TD]
 [/TR]
 [TR]
 [TD][audiokaraoke]("http://gstreamer.freedesktop.org/data/doc/gstreamer/head/gst-plugins-good-plugins/html/gst-plugins-good-plugins-audiokaraoke.html")
[/TD]
 [TD]Removes voice from sound[/TD]
 [/TR]
 [TR]
 [TD][audiopanorama]("http://gstreamer.freedesktop.org/data/doc/gstreamer/head/gst-plugins-good-plugins/html/gst-plugins-good-plugins-audiopanorama.html")
[/TD]
 [TD]Positions audio streams in the stereo panorama[/TD]
 [/TR]
 [TR]
 [TD][audiowsincband]("http://gstreamer.freedesktop.org/data/doc/gstreamer/head/gst-plugins-good-plugins/html/gst-plugins-good-plugins-audiowsincband.html")
[/TD]
 [TD]Band pass and band reject windowed sinc filter[/TD]
 [/TR]
 [TR]
 [TD][audiowsinclimit]("http://gstreamer.freedesktop.org/data/doc/gstreamer/head/gst-plugins-good-plugins/html/gst-plugins-good-plugins-audiowsinclimit.html")
[/TD]
 [TD]Low pass and high pass windowed sinc filter[/TD]
[/TR]
[/TABLE]

Please tell me some idea about a new plugin for audio filters as I have searched a lot on the net about this, but not found any idea about aby new type of filters to be implemented.

It is really very urgent for me . Please tell me some idea .

Thanks in advance ....

---

### Post by Frogs Hair on 2013-08-17
This my offer some direction. [http://gstreamer.freedesktop.org/data/doc/gstreamer/head/pwg/html/](http://gstreamer.freedesktop.org/data/doc/gstreamer/head/pwg/html/)

---

