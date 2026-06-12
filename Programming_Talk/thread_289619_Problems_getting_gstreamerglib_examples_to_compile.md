---
title: "Problems getting gstreamer/glib examples to compile"
date: 2006-10-31
forum: Programming Talk
---

### Post by jfxx on 2006-10-31
I've problems getting gstreamer examples to compile. Typical basic example starts with:

#include <gst/gst.h>

To try to get this to compile, I've added the following to the include directory list:

-I/usr/include/glib-2.0 -I/usr/include/gstreamer-0.10 

However, this include consistently throws up hundreds of errors which all seem to relate to the inability to find glibconfig.h within the glib headers. Specifically the line "#include <glibconfig.h>" in gtypes.h - so on face value this is probably an issue with glib itself.

Now glibconfig.h is not installed within /usr/include/glib-2.0 but as /usr/lib/glib-2.0/include/glibconfig.h. I'd have expected this file to be copied or linked into /usr/include/glib-2.0 on installation, but I suppose the issue is that I don't know.

Question: is this an installation issue, or am I supposed to handle it. If the latter, what do other people do - copy themselves or add this folder to the include path too?

At the back of my mind is a feeling this is not correct.

I'm running 6.10 and using 2.12.4-0ubuntu1 version of both libglib2.0-0 and libglib2.0-dev.

---

### Post by duff on 2006-10-31
pkg-config is a tool to help you include the directories when you compile and which libraries you need during the link stage.

```
# pkg-config --cflags gstreamer-0.10
-pthread -I/usr/include/gstreamer-0.10 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libxml2  

# pkg-config --libs gstreamer-0.10
-Wl,--export-dynamic -pthread -lgstreamer-0.10 -lgobject-2.0 -lgmodule-2.0 -ldl -lgthread-2.0 -lxml2 -lglib-2.0
```

---

