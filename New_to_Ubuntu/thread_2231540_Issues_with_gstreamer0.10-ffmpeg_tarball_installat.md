---
title: "Issues with gstreamer0.10-ffmpeg tarball installation"
date: 2014-06-26
forum: New to Ubuntu
---

### Post by Gerard_Larkin on 2014-06-26
I keep getting this error message when I got to install the gstreamer ffmpeg add-on via the software centre

"There isn’t a software package called “gstreamer0.10-ffmpeg” in your current software sources"

I've downloaded the tarball (gstreamer0.10-ffmpeg_0.10.13.orig.tar.bz2) and have gone the steps to attempt to install and I get this error message at the end of the ./configure command

checking for GST... no
configure: No package 'gstreamer-0.10' found
configure: error: no gstreamer-0.10 >= 0.10.31 (GStreamer) found

Can someone point the way to a solution? Have I downloaded the wrong package? Do I need to add additional repositories to Software & Updates?

---

### Post by cariboo on 2014-06-27
Unless you are running 13.10 or older, the gstreamer0.10-ffmpeg package is no longer available. See [here]("http://packages.ubuntu.com/search?keywords=gstreamer0.10-ffmpeg")

---

### Post by monkeybrain20122 on 2014-06-27
you can install gstreamer-0.1.0-ffmpeg from this ppa
[https://bugs.launchpad.net/~mc3man/+archive/trusty-media](https://bugs.launchpad.net/~mc3man/+archive/trusty-media)

---

