---
title: "Problems installing gpicview"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by ahorne12 on 2008-04-28
Hi,

   so I'm really new to Ubuntu (under a month), but I'm slowly figuring things out.  That being said, I'm having problems installing gpicview 0.1.9 from the .tar.gz file I downloaded.  I've gotten it extracted, and can navigate to the directory in terminal, but whenever I type ./configure I get a massive scrolling of conditions met, but it ends with:

***
checking pkg-config is at least version 0.9.0... yes
checking for PACKAGE... configure: error: Package requirements (gtk+-2.0 >= 2.6.0) were not met:

No package 'gtk+-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables PACKAGE_CFLAGS
and PACKAGE_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
***

I don't know how to satisfy this requirement.  Does this mean my gtk (whatever that is) is out of date?  Am I doing something wrong, or just missing something?

Thanks in advance

---

### Post by dearingj on 2008-04-28
You can install gpicview using Synaptic (if you prefer a graphical interface) or apt-get (if you prefer to use a terminal).

As for what is meant by "No package 'gtk+-2.0' found", Ubuntu uses a different name for the GTK package; you can probably open configure in a text editor and change it to look for "libgtk2.0-0" but I don't think it would be worth it.

---

### Post by ahorne12 on 2008-04-28
Thanks a lot Dearingj, that was so much easier!  I didn't even know that there were more programs for installation through there that aren't in the repositories.  Even managed to figure out how to set it as the default file association.  Again, much appreciated :)

---

### Post by Ptero-4 on 2008-06-17
Which repository it uses for gutsy? The lxde one bombs in dependencies.

---

