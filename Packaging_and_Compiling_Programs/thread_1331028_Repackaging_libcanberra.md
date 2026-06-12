---
title: "Repackaging libcanberra"
date: 2009-11-18
forum: Packaging and Compiling Programs
---

### Post by Yellow Pasque on 2009-11-18
Sorry if this seems n00bish. I've made some simple .deb's before, but never tried to reconfigure existing Ubuntu packages.

```
libcanberra can use different backends: null, ALSA, PulseAudio, OSS,
GStreamer.
Since the PulseAudio backend requires PulseAudio >= 0.9.11, this package uses ALSA for testing purposes. It is planned to use PulseAudio as soon as it is released. It is also planned to have different inter-conflicting packages for configurable backend installation.
```

I want to build a libcanberra source package configured to use the gstreamer backend and distribute it in a PPA. Unfortunately, libcanberra is not easily configurable. It checks for outputs in the order - ALSA, PulseAudio, OSS, gstreamer. The first one found is used.

So I have all the dependencies and I download the source package:
```
apt-get source libcanberra
```

Then I edit the debian rules to configure the way I want it. Now what else do I need to do besides cleanup the control file? Then what do I do?

---

### Post by Yellow Pasque on 2009-11-19
Ok, so I've gotten it to build, but a few small questions remain:

1. Looking through the packaging guide, I did not see the place where I could change the version of my packages. For example, I want to make my packages 0.15-0ubuntu8~ppa1, but they all still have the original 0.15-0ubuntu7. Can I simply rename the packages?

2. The signing failed because I didn't have my key installed. Can I just add my key and run debsign?

Thanks.

---

### Post by SevenMachines on 2009-11-19
The package version that will build is taken from the debian/changelog. when you make changes then, from the source dir, 
$dch -i
this adds a new entry to the changelog for you to edit. it automatically bumps the version up but you can also edit it to add ~ppa or whatever you need
you can run debsign on a .changes file that is generated when you debuild the source. of course, you could just install the key corresponding to your name/email address in the changelog and run debuild -S again

---

### Post by Yellow Pasque on 2009-11-21
Thank you for your help. Solved.

---

