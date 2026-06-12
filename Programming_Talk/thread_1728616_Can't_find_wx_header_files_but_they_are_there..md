---
title: "Can't find wx header files but they are there."
date: 2011-04-13
forum: Programming Talk
---

### Post by Yoshi65 on 2011-04-13
Hey guys I am trying to build a sample program using wxWidgets but it can't find the header files.

This is the output:

```

g++ -o myprg hworld.cpp `pkg-config wx-config --libs`
Package wx-config was not found in the pkg-config search path.
Perhaps you should add the directory containing `wx-config.pc'
to the PKG_CONFIG_PATH environment variable
No package 'wx-config' found
hworld.cpp:5: fatal error: wx/wx.h: No such file or directory
compilation terminated.
make: *** [all] Error 1

```


And this is my makefile:


```

SOURCES = hworld.cpp
OBJS    = ${SOURCES:.c=.o}
CFLAGS  = `pkg-config wx-config --cflags` -I /usr/include/wx-2.8
LDADD   = `pkg-config wx-config --libs`
CC      = g++
PACKAGE = myprg

all : ${OBJS}
	${CC} -o ${PACKAGE} ${OBJS} ${LDADD}

.c.o:
	${CC} ${CFLAGS} -c $<


```


Thanks so much!

---

### Post by SevenMachines on 2011-04-14
wx-config is used as a replacement for pkg-config
```
$ wx-config --cflags --libs
-I/usr/lib/wx/include/base-unicode-release-2.8 -I/usr/include/wx-2.8 -D_FILE_OFFSET_BITS=64 -D_LARGE_FILES -DwxUSE_GUI=0 -pthread
-pthread -Wl,-Bsymbolic-functions  -lwx_baseu_xml-2.8 -lwx_baseu_net-2.8 -lwx_baseu-2.8 
```

So,
```
 $ g++ -o myprg hworld.cpp ` wx-config --cflags --libs`
```

---

### Post by Arndt on 2011-04-14
> **Yoshi65 said:**
> Hey guys I am trying to build a sample program using wxWidgets but it can't find the header files.

This is the output:

```

g++ -o myprg hworld.cpp `pkg-config wx-config --libs`
Package wx-config was not found in the pkg-config search path.
Perhaps you should add the directory containing `wx-config.pc'
to the PKG_CONFIG_PATH environment variable
No package 'wx-config' found
hworld.cpp:5: fatal error: wx/wx.h: No such file or directory
compilation terminated.
make: *** [all] Error 1

```


And this is my makefile:


```

SOURCES = hworld.cpp
OBJS    = ${SOURCES:.c=.o}
CFLAGS  = `pkg-config wx-config --cflags` -I /usr/include/wx-2.8
LDADD   = `pkg-config wx-config --libs`
CC      = g++
PACKAGE = myprg

all : ${OBJS}
	${CC} -o ${PACKAGE} ${OBJS} ${LDADD}

.c.o:
	${CC} ${CFLAGS} -c $<


```


Thanks so much!

1) Use just wx-config, not pkg-config with wx-config as an argument;
2) First compile hworld.cpp to get hworld.o, using wx-config --cflags, then link hworld.o with the rest using wx-config --libs.

---

### Post by Yoshi65 on 2011-04-14
Okay thanks guys! That fixed that problem but it isn't finding the wx/wx.h header and it does the for the GTK+ header too. But both of them are there. Why is it not seeing both of the header files? I switched from GTK+ to wxWidgets because of this problem but I see it here too!

---

### Post by Arndt on 2011-04-14
> **Yoshi65 said:**
> Okay thanks guys! That fixed that problem but it isn't finding the wx/wx.h header and it does the for the GTK+ header too. But both of them are there. Why is it not seeing both of the header files? I switched from GTK+ to wxWidgets because of this problem but I see it here too!

What does your compilation command look like now?

---

### Post by Yoshi65 on 2011-04-14
I have this makefile:


```

SOURCES = hworld.cpp
OBJS    = ${SOURCES:.c=.o}
CFLAGS  = `wx-config --cflags`
LDADD   = `wx-config --libs`
CC      = g++
PACKAGE = myprg

all : ${OBJS}
	${CC} -o ${PACKAGE} ${OBJS} ${LDADD}

.c.o:
	${CC} ${CFLAGS} -c $<


```

and then I just type make.

---

### Post by Arndt on 2011-04-14
> **Yoshi65 said:**
> I have this makefile:


```

SOURCES = hworld.cpp
OBJS    = ${SOURCES:.c=.o}
CFLAGS  = `wx-config --cflags`
LDADD   = `wx-config --libs`
CC      = g++
PACKAGE = myprg

all : ${OBJS}
	${CC} -o ${PACKAGE} ${OBJS} ${LDADD}

.c.o:
	${CC} ${CFLAGS} -c $<


```

and then I just type make.

Fine, but it's the actual command that gets executed that I want to see. And, also, the output from wx-config --cflags.

---

### Post by Yoshi65 on 2011-04-14
This is what is executed:

```

g++ -o myprg hworld.cpp `wx-config --libs`
hworld.cpp:5: fatal error: wx/wx.h: No such file or directory
compilation terminated.
make: *** [all] Error 1


```

This is the output of wx-config --libs:

```

-L/usr/local/lib -pthread   -lwx_gtk2_richtext-2.8 -lwx_gtk2_aui-2.8 -lwx_gtk2_xrc-2.8 -lwx_gtk2_qa-2.8 -lwx_gtk2_html-2.8 -lwx_gtk2_adv-2.8 -lwx_gtk2_core-2.8 -lwx_base_xml-2.8 -lwx_base_net-2.8 -lwx_base-2.8 


```

---

### Post by Yoshi65 on 2011-04-14
Sorry for the double post...
I just saw you said wx-config --cflags but here is the output of that.

```

-I/usr/local/lib/wx/include/gtk2-ansi-release-2.8 -I/usr/local/include/wx-2.8 -D_FILE_OFFSET_BITS=64 -D_LARGE_FILES -D__WXGTK__ -pthread


```

---

### Post by Arndt on 2011-04-14
> **Yoshi65 said:**
> Sorry for the double post...
I just saw you said wx-config --cflags but here is the output of that.

```

-I/usr/local/lib/wx/include/gtk2-ansi-release-2.8 -I/usr/local/include/wx-2.8 -D_FILE_OFFSET_BITS=64 -D_LARGE_FILES -D__WXGTK__ -pthread


```

I think I see the error in the Makefile: you have .cpp source files but do

OBJS    = ${SOURCES:.c=.o}

Do

OBJS    = ${SOURCES:.cpp=.o}

instead, and then the building ought to follow the steps outlined in the first answers to your question. Maybe it even works, but if not, we will have a more correct compilation step.

---

### Post by Yoshi65 on 2011-04-14
> **Arndt said:**
> I think I see the error in the Makefile: you have .cpp source files but do

OBJS    = ${SOURCES:.c=.o}

Do

OBJS    = ${SOURCES:.cpp=.o}

instead, and then the building ought to follow the steps outlined in the first answers to your question. Maybe it even works, but if not, we will have a more correct compilation step.

Nope. Sorry it didn't work but thank you for your post!

---

### Post by SevenMachines on 2011-04-14
I take it since it's looking in /usr/local that you're using a manually built version of wx. sorry if you'ce checked but are you *absolutely* sure that 
```
 $ ls /usr/local/include/wx-2.8/wx/wx.h
```
exists?

---

### Post by dwhitney67 on 2011-04-14
> **Yoshi65 said:**
> Nope. Sorry it didn't work but thank you for your post!

Arndt is correct; you have a flaw in your Makefile.  Simply because your Makefile still fails is because you still have other issues (with the Makefile).

You do not use pkg-config to obtains the flags/libs for the wxwidgets package; use wx-config instead.  (I know... very dumb developers, those wxwidget folks are!)

To get you on your way, here's a Makefile that hopefully should work:
```

PACKAGE  = myprg

SRCS     = hworld.cpp
OBJS     = ${SRCS:.cpp=.o}
CXXFLAGS = `wx-config --cxxflags`
LDFLAGS  = `wx-config --libs`


${PACKAGE} : ${OBJS}
	${CXX} -o $@ $^ ${LDFLAGS}

```

---

### Post by Yoshi65 on 2011-04-14
> **dwhitney67 said:**
> Arndt is correct; you have a flaw in your Makefile.  Simply because your Makefile still fails is because you still have other issues (with the Makefile).

You do not use pkg-config to obtains the flags/libs for the wxwidgets package; use wx-config instead.  (I know... very dumb developers, those wxwidget folks are!)

To get you on your way, here's a Makefile that hopefully should work:
```

PACKAGE  = myprg

SRCS     = hworld.cpp
OBJS     = ${SRCS:.cpp=.o}
CXXFLAGS = `wx-config --cxxflags`
LDFLAGS  = `wx-config --libs`


${PACKAGE} : ${OBJS}
	${CXX} -o $@ $^ ${LDFLAGS}

```

Thank you so much it works! Even with the GTK+ library! Thanks again! How does it work though? What is different?

---

### Post by Vox754 on 2011-04-15
> **Yoshi65 said:**
> Okay thanks guys! That fixed that problem but it isn't finding the wx/wx.h header and it does the for the GTK+ header too. But both of them are there. Why is it not seeing both of the header files? **I switched from GTK+ to wxWidgets because of this problem** but I see it here too!

If you switched from one widely-used platform to another widely-used platform, just because of a tiny little problem that you couldn't figure out, I don't think you will be very successful in your programming endeavours.

You do not throw something at the wall and expect it to stick. You need to read more about compilation and Makefiles, before placing the blame on others.

---

