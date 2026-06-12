---
title: "Inkscape 0.46 installation on Maverick"
date: 2013-01-14
forum: New to Ubuntu
---

### Post by barneyjoseph on 2013-01-14
Hi,

I've been trying to install "Inkscape 0.46" with no success (.47 and .48 problems were unsolvable). 

With a lot of errors arising I've managed to install a few of the dependancies. I am stuck without these packages and mostly end up with 404 errors while using "apt-get". Here is the last bit of the output of "./configure"

```

checking for InitializeMagick in -lMagick++... no
checking for INKSCAPE... configure: error: Package requirements (gdkmm-2.4  glibmm-2.4  gtkmm-2.4 >= 2.10.0  gtk+-2.0  libxml-2.0 >= 2.6.11  libxslt >= 1.0.15  cairo  sigc++-2.0 >= 2.0.12    gthread-2.0 >= 2.0 libpng >= 1.2) were not met:

No package 'gdkmm-2.4' found
No package 'glibmm-2.4' found
No package 'gtkmm-2.4' found
No package 'gtk+-2.0' found
No package 'libxml-2.0' found
No package 'libxslt' found
No package 'cairo' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables INKSCAPE_CFLAGS
and INKSCAPE_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```

In synaptic I seem to have cairo installed. I also downloaded the cario package and followed the instructions to install it.... somehow inkscape cannot find it. Hope that someone can help me!

Thanks in advance!
Barney

---

### Post by deadflowr on 2013-01-14
As the 404 errors should have been enough of a clue, maverick is dead, it died a quiet death nearly a year ago.

However you can get the maverick repos by changing your repos to the old-release repos(where the unsupported maverick and other old Ubuntu versions repos are at)

Use this as a guide:

[http://superuser.com/questions/339537/where-can-i-get-therepositories-for-old-ubuntu-versions]("http://superuser.com/questions/339537/where-can-i-get-therepositories-for-old-ubuntu-versions")

Hopefully you'll find what you're looking for.

---

### Post by barneyjoseph on 2013-01-14
I did realize that there are newer versions of ubuntu... but I didn't know that I would be phased out? I'll try the link that you have provided.

Thanks a lot!

---

### Post by barneyjoseph on 2013-01-14
Well... tough luck. Maverick is dead. Tried to tips on the link you provided and it still didn't work. I guess I have to give up and install a newer version. 

Since I've been in this situation should I go for 12.04 since it is LTS or should I just try 12.10?

---

### Post by ajgreeny on 2013-01-14
12.04, all the way as it is now very stable and more configurable. If you don't like unity you can either use the classic desktop, or of course, move to another DE entirely such as xfce (xubuntu).
[12.04 LTS Gnome Classic]("http://ubuntuforums.org/showthread.php?t=1966370")

---

