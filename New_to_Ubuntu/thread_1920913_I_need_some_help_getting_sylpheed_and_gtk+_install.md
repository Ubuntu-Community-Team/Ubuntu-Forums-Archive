---
title: "I need some help getting sylpheed and gtk+ installed"
date: 2012-02-05
forum: New to Ubuntu
---

### Post by Crash.hm on 2012-02-05
I'm a bit new and a bit stuck. I really want to try sylpheed. Apparently I also need to install gtk+, which seems to require that I install a bunch of other things. Is there some way to speed this up?

I'm running ubuntu 8.10 (ibex i think).Here is the error I got running the gtk+ configure file.


```
configure: error: Package requirements (glib-2.0 >= 2.29.14    atk >= 2.1.5    pango >= 1.29.0    cairo >= 1.10.0    cairo-gobject >= 1.10.0    gdk-pixbuf-2.0 >= 2.23.5) were not met:

No package 'glib-2.0' found
No package 'atk' found
No package 'pango' found
No package 'cairo' found
No package 'cairo-gobject' found
No package 'gdk-pixbuf-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables BASE_DEPENDENCIES_CFLAGS
and BASE_DEPENDENCIES_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```

---

### Post by Rodney9 on 2012-02-05
8.10 is 4 years old and non LTS versions only have 18 months support.

You would be best to install the latest or at least 10.4.3, the last LST (Long Term Support), so you will be secure. You could wait untill April for 12.04 the next LTS.

If you wish to stay on 8.10, Synaptic would be best to install Sylpheed to work out dependencies.

Another still lightweight Email with more features is Claws Mail -  [http://www.claws-mail.org/](http://www.claws-mail.org/)

Rodney

---

