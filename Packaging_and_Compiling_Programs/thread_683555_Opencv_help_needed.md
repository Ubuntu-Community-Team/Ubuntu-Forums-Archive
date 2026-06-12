---
title: "Opencv help needed"
date: 2008-01-31
forum: Packaging and Compiling Programs
---

### Post by Stern on 2008-01-31
Hi I need shelp compiling a simple cpp file and linking it with opencv.
I've installes with sudo apt-get instal "all opencv files". but when i try to compile a simple example i g++ test.cpp -o test -I /usr/include/ -L /usr/lib -lcv 
i get an error message : /usr/bin/ld cannont find -lcv !!

---

### Post by Zugzwang on 2008-01-31
Please copy&paste the *precise* error message here. :-\"

---

### Post by Stern on 2008-01-31
g++ test.cpp -o test -I /usr/include/ - L /usr/lib -lm lcv -lhighgui 
gives this
/usr/bin/ld : cannot find -lcv
collect2: ld returned 1 exit status

in cpp file i have 
#include <opencv/cv.h>
#include <opencv/highgui.h>

other info running on ppc and dapper6.06

---

### Post by amingv on 2008-01-31
> **Stern said:**
> g++ test.cpp -o test -I /usr/include/ - L /usr/lib -lm lcv -lhighgui 
gives this
/usr/bin/ld : cannot find -lcv
collect2: ld returned 1 exit status

in cpp file i have 
#include <opencv/cv.h>
#include <opencv/highgui.h>

other info running on ppc and dapper6.06

I have never used opencv, but don't you have to put a '-' in front of lcv to specify it as a modifier parameter? like this:

```
g++ test.cpp -o test -I /usr/include/ - L /usr/lib -lm **-lcv** -lhighgui 
```

---

### Post by Stern on 2008-01-31
yup you do sorry typing mistake when writing post !! so sorry correct line is

g++ test.cpp -o test -I /usr/include/ - L /usr/lib -lm -lcv -lhighgui

but same message :(

---

### Post by Stern on 2008-01-31
problem solved :) when using package mgt. to install the lib files are named libcv0.9 :) so correct use will be
g++ test.cpp -o test -I /usr/include/  -L /usr/lib -lm -lcv0.9 -lhighgui0.9

:) but tnx for the replies.

---

### Post by Tiboo on 2008-08-13
> **Stern said:**
> problem solved :) when using package mgt. to install the lib files are named libcv0.9 :) so correct use will be
g++ test.cpp -o test -I /usr/include/  -L /usr/lib -lm -lcv0.9 -lhighgui0.9

:) but tnx for the replies.

Hi! I know it has been a long time, but I have exactly the same problem, except that I have the version 1.0.0 of the libcv. The question is : do I necessarily need the libc1.0.0.a , which I do not find ? 
It may be a stupid question, but I really do not find out how to solve my linking problems...

Thank you !

---

### Post by galliumarsenide on 2009-03-02
I struggled with the same problem, unfortunately at our university, a couple of opencv versions are installed or so, that is, -lcv0.9 didn't work and I got the same error. I still don't really get it, but I was able to find the right compiler option with this command:

```
~> pkg-config --libs opencv
-lcxcore0.9.7 -lcv0.9.7 -lhighgui0.9.7 -lcvaux0.9.7

```

found here [http://opencv.willowgarage.com/wiki/CompileOpenCVUsingLinux](http://opencv.willowgarage.com/wiki/CompileOpenCVUsingLinux)

obviously, the version number I had to add was 0.9.7. 

rather dumb, but since nobody seems to really know what lcv/lhighgui/lcvaux is, it took me about an hour to figure that out and maybe this posting helps someone encountering the same problem.

---

