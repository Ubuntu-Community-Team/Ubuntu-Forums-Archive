---
title: "gstreamer compile problem"
date: 2006-11-30
forum: Programming Talk
---

### Post by falkenberg_cph on 2006-11-30
Hi
I wanna learn gstreamer, but untill now i have only had problems. It will not compile correctly.
Some of the text below is danish, but i think you get the point. It appears to me the there is something wrong with the gst library?

Hope you can help me
/Carsten

This is the "program":
> #include <gstreamer-0.10/gst/gst.h>

int
main (int   argc,
      char *argv[])
{
  guint major, minor, micro;

  gst_init (&argc, &argv);

  gst_version (&major, &minor, &micro);
  printf ("This program is linked against GStreamer %d.%d.%d\n",
          major, minor, micro);

  return 0;
}


And this is the consol in Eclipse:
> 
**** Build of configuration Debug for project gstreamer ****

make -k all 
Building file: ../hello.cpp
Invoking: GCC C++ Compiler
g++ -O0 -g3 -Wall -c -fmessage-length=0 -MMD -MP -MF"hello.d" -MT"hello.d" -o"hello.o" "../hello.cpp"
/usr/include/gstreamer-0.10/gst/gst.h:78: error: expected constructor, destructor, or type conversion before ‘void’
/usr/include/gstreamer-0.10/gst/gst.h:79: error: ‘gboolean’ does not name a type
/usr/include/gstreamer-0.10/gst/gst.h:81: error: expected constructor, destructor, or type conversion before ‘*’ token
/usr/include/gstreamer-0.10/gst/gst.h:84: error: variable or field ‘gst_version’ declared void
/usr/include/gstreamer-0.10/gst/gst.h:84: error: ‘guint’ was not declared in this scope
/usr/include/gstreamer-0.10/gst/gst.h:84: error: ‘major’ was not declared in this scope
/usr/include/gstreamer-0.10/gst/gst.h:84: error: ‘guint’ was not declared in this scope
/usr/include/gstreamer-0.10/gst/gst.h:84: error: ‘minor’ was not declared in this scope
/usr/include/gstreamer-0.10/gst/gst.h:85: error: ‘guint’ was not declared in this scope
/usr/include/gstreamer-0.10/gst/gst.h:85: error: ‘micro’ was not declared in this scope
/usr/include/gstreamer-0.10/gst/gst.h:85: error: ‘guint’ was not declared in this scope
/usr/include/gstreamer-0.10/gst/gst.h:85: error: ‘nano’ was not declared in this scope
/usr/include/gstreamer-0.10/gst/gst.h:85: error: initializer expression list treated as compound expression
/usr/include/gstreamer-0.10/gst/gst.h:86: error: expected constructor, destructor, or type conversion before ‘*’ token
/usr/include/gstreamer-0.10/gst/gst.h:88: error: ‘gboolean’ does not name a type
/usr/include/gstreamer-0.10/gst/gst.h:89: error: variable or field ‘gst_segtrap_set_enabled’ declared void
/usr/include/gstreamer-0.10/gst/gst.h:89: error: ‘gboolean’ was not declared in this scope
/usr/include/gstreamer-0.10/gst/gst.h:91: error: ‘gboolean’ does not name a type
/usr/include/gstreamer-0.10/gst/gst.h:92: error: variable or field ‘gst_registry_fork_set_enabled’ declared void
/usr/include/gstreamer-0.10/gst/gst.h:92: error: ‘gboolean’ was not declared in this scope
../hello.cpp:3: error: expected constructor, destructor, or type conversion before ‘int’
make: *** [hello.o] Fejl 1
make: Målet 'all' ikke genskabt på grund af fejl.
Build complete for project gstreamer

---

### Post by duff on 2006-11-30
It may be a path problem.  I'm not sure how Eclipse does it, but you souldn't provide the full path to gst.h.  So my guess is that one of the header files gst.h is trying to include isn't being found (most likely glib and other gst files).

```
# pkg-config --cflags gstreamer-0.10
-pthread -I/usr/include/gstreamer-0.10 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libxml2
```

^^ That is what you should be compiling with

---

### Post by falkenberg_cph on 2006-11-30
I think you&#341;e right. I would prefer using Eclipse/CDT. So i gotta figure out how to add the header folder into my project.

/Carsten

---

