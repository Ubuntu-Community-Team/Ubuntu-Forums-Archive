---
title: "Problem loading 3D Model"
date: 2008-11-08
forum: Programming Talk
---

### Post by endless_dark on 2008-11-08
Hello everybody! I'm coding a 3D image & sound application using a Nintendo's Wiimte for my university.

I've made every basic thing and it's working so now I want to improve some details and one of these is changing the box that represents the wiimote. I have downloaded a wiimote .obj model and the GLM library to load it, I'm also using OpenGL OpenAL and GLUT.

To install de GLM I've downloaded the sources, and made a ./configure,make and make install so I suppose it's installed.

Now time for the makefile. I've added -lglm to the LFLAGS section.

And finally in my code I've added these lines:

```

...
#include <glm.h>
...
GLMmodel *wiimodel;
...
wiimodel = glmReadOBJ("wiimote.obj");
...

```

I think it should work but I recieve this error

```
trackingdemo.o: In function `TrackingDemoInit()':
/home/myuser/Desktop/wiimote3Dsound/trackingdemo.cpp:177: undefined reference to `glmReadOBJ'

```

:confused:
Some points I don't understand: This error says something like the glm isn't right installed or linked?
And, if is that's the problem, why I'm not gettig an error in the GLMmodel *wiimodel declaration?

Help will be apreciated!
Thank you!

---

### Post by WW on 2008-11-08
When you installed glm, did you notice where it was installed?  If you compiled it from source, the usual place would be /usr/local/lib, in which case you may have to also add the option **-L/usr/local/lib** to LDFLAGS.

---

### Post by endless_dark on 2008-11-08
> **WW said:**
> When you installed glm, did you notice where it was installed?  If you compiled it from source, the usual place would be /usr/local/lib, in which case you may have to also add the option **-L/usr/local/lib** to LDFLAGS.

Thank you for answering me, but sadly didn't worked. Here is my Makefile:

```
# trackingdemo Makefile

CC = g++
CFLAGS = -g -W -Wall -Wno-unused -O2
LDFLAGS= -L/usr/local/lib
LFLAGS = -lcwiid -lGL -lbluetooth -lm -lglut -lalut -lglm

V = @

all: trackingdemo


trackingdemo.o: trackingdemo.cpp
	@echo + cc trackingdemo.cpp
	$(V)$(CC) $(CFLAGS) -c trackingdemo.cpp

wiiheadtracking.o: wiiheadtracking.cpp
		@echo + cc wiiheadtracking.cpp
		$(V)$(CC) $(CFLAGS) -c wiiheadtracking.cpp

trackingdemo: trackingdemo.o wiiheadtracking.o
	@echo + link main 
	$(V)$(CC) $(CFLAGS) $(LFLAGS) -o $@ trackingdemo.o wiiheadtracking.o

clean:
	@echo + clean
	$(V)rm -rf *.o trackingdemo

```

---

### Post by WW on 2008-11-08
Oops.  Add the -L option to the same macro to which you add the -l options.  In this case, you used LFLAGS, but this macro is traditionally called LDFLAGS.

---

