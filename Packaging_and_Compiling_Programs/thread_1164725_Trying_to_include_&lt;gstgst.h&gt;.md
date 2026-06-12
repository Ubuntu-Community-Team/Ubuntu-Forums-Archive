---
title: "Trying to include &lt;gst/gst.h&gt;"
date: 2009-05-19
forum: Packaging and Compiling Programs
---

### Post by jfinkels on 2009-05-19
Trying to include the GStreamer header, as described in the GStreamer manual, in a test file as follows:
```
#include <gst/gst.h>

int
main(int argc,
    char *argv[])
{
  // initialize GStreamer
  gst_init(&argc, &argv);

  return 0;
}

```

Compiling with "gcc test.c" yields the error:
```
test.c:1:21: error: gst/gst.h: No such file or directory
```
However, I have installed libgstreamer0.10-dev, which includes the file "/usr/include/gstreamer-0.10/gst/gst.h".

How do I get the C preprocessor to understand where that header file is?

**SOLVED:**

I wasn't including the directory containing the gst/gst.h header file.

The easiest way to do this is by using "pkg-config gstreamer-0.10 --cflags" and "pkg-config gstreamer-0.10 --libs" to determine the necessary "-I" (header file include path) options and "-L"/"-l" (library file include path) options. For example, if the file above is named "test.c", create a "Makefile" containing the following:
```
CC=gcc
LIBS=`pkg-config gstreamer-0.10 --libs`
CFLAGS=`pkg-config gstreamer-0.10 --cflags`

all:
        $(CC) $(LIBS) $(CFLAGS) test.c

```
Then, to compile the file, use the command```
make
```

---

