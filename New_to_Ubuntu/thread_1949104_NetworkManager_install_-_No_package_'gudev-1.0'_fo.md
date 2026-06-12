---
title: "NetworkManager install - No package 'gudev-1.0' found"
date: 2012-03-29
forum: New to Ubuntu
---

### Post by Bumpalot on 2012-03-29
During the install of NetworkManager-0.9.4.0, using ./configure, the ending terminal entries were:
checking for GUDEV... no
configure: error: Package requirements (gudev-1.0 >= 147) were not met:

No package 'gudev-1.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GUDEV_CFLAGS
and GUDEV_LIBS to avoid the need to call pkg-config.

Synaptic search for gudev lists gir1.0-gudev-1.0 and python-gudev as being installed.
I need to know how to follow either of the above Terminal suggestions, as I have no clue what they mean.

SOLVED: Previously I had no Internet connection. Out of the blue Ubuntu Updates popped up & installed many packages.
WOW! Was able to obtain the missing Internet tools.

---

