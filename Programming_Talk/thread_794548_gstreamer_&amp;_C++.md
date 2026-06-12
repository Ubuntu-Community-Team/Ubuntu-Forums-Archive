---
title: "gstreamer &amp; C++"
date: 2008-05-14
forum: Programming Talk
---

### Post by mkoehler on 2008-05-14
Hey guys,

    I was wondering if anyone could enlighten me with a few good resources (tutorials and/or examples) about recording with gstreamer & C++.  Note: I have sifted through the gstreamer documentation ([http://gstreamer.freedesktop.org/documentation/](http://gstreamer.freedesktop.org/documentation/)), but it gets a little sparse from time to time. :)

---

### Post by SledgeHammer_999 on 2008-05-14
as far as I can tell the examples are using C. You can mix them(C) with C++ code. 

As for the recording, if you understand how gstreamer works(sinks/sources/elements/bins/pads) maybe you should look for the "recording" plugin in the documentation(try base-plugins).

---

### Post by mkoehler on 2008-05-14
Ok, it's hard for me to believe that I'm running into trouble already.  After reading over the documentation for a while, I decided to run a few of their simple programs, with the expectation that they would work (considering that I have all of the -dev files).  Anyway, this is their first example program:

```
#include <gst/gst.h>

int
main (int   argc,
      char *argv[])
{
  const gchar *nano_str;
  guint major, minor, micro, nano;

  gst_init (&argc, &argv);

  gst_version (&major, &minor, &micro, &nano);

  if (nano == 1)
    nano_str = "(CVS)";
  else if (nano == 2)
    nano_str = "(Prerelease)";
  else
    nano_str = "";

  printf ("This program is linked against GStreamer %d.%d.%d %s\n",
          major, minor, micro, nano_str);

  return 0;
}
```

I get two errors when I try to build the program: undefined references to "gst_init" and "gst_version", aka the functions that should be defined within "gst.h" (and yes, it knows where "gst.h" is).  I was just wondering if anyone had experimented with gstreamer before and/or where I might be going wrong - thanks.

---

### Post by SledgeHammer_999 on 2008-05-15
Well for me this example was compilable in Gutsy. Can you give the command you use to build it and the error output?

---

### Post by mkoehler on 2008-05-15
Thanks for your help, but I was able to figure out the problem myself.

---

