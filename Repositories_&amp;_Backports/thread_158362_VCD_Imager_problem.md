---
title: "VCD Imager problem"
date: 2006-04-11
forum: Repositories &amp; Backports
---

### Post by 3rdalbum on 2006-04-11
I tried to install vcdimager through Synaptic and apt-get, but some of the packages it requires seem to be broken. Here's my apt-get output:

```

chris@iMac:~$ sudo apt-get install vcdimager
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  vcdimager: Depends: libcdio0 but it is not installable
             Depends: libiso9660-0 (> 0.67) but it is not installable
             Depends: libvcdinfo0 but it is not going to be installed

```

I have the multiverse and universe repos enabled, and I'm using Breezy PPC.

Where do I file a bug report against this package? (or does one of the MOTU check here?)

---

