---
title: "Need help in an undefined reference linker error"
date: 2007-05-24
forum: Programming Talk
---

### Post by yinglcs2 on 2007-05-24
I am getting the following undefined reference linker error when I
compile my program:

FileModule.o: In function `DoFile':
/home/herman/src/FileModule.cpp:665: undefined reference to `VLC_Init'
collect2: ld returned 1 exit status

I have added libvlc.so file to my 'LIBFILES in my Makefile:
LIBFILES =      QTFileLib/libQTFileLib.a \
                                /home/herman/bin/lib/libvlc.so

And I have added '-Llibvlc' to the LINKOPTS:
LINKOPTS += -Llibvlc

and my program compiles like this:

MyServer: $(CFILES:.c=.o) $(CPPFILES:.cpp=.o)  $(LIBFILES)
        $(LINK) -o $@ $(CFILES:.c=.o) $(CPPFILES:.cpp=.o) $(COMPILER_FLAGS) $
(LINKOPTS) $(LIBS)

Can you please tell me what am I missing?

Thank you.

---

### Post by dsl on 2007-05-24
The syntax is
-L/path/to/library -llibrary-without-initial-lib-and without-extension
example with /usr/lib/libm.so:
-L/usr/lib -lm

---

### Post by yinglcs2 on 2007-05-24
Thanks for your help.

I have added libvlc.so file to my 'LIBFILES in my Makefile:

LIBFILES = QTFileLib/libQTFileLib.a \
/home/herman/bin/lib/libvlc.so

I added the line "/home/herman/bin/lib/libvlc.so"

---

### Post by psusi on 2007-05-24
You aren't telling the linker to use LIBFILES, you only told make that LIBFILES must exist before it can build MyServer.

---

