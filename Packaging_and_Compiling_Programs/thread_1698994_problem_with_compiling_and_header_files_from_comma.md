---
title: "problem with compiling and header files from command line"
date: 2011-03-03
forum: Packaging and Compiling Programs
---

### Post by chris1497 on 2011-03-03
So I wanted to mess around with some programming with openCV.  I went to synaptic package manager and installed all the openCV libraries (including the dev ones).  restarted my computer then tried compiling a beginners program that I found in a tutorial using the g++ cmd.  The error I get is:

cv1.cpp:2: fatal error: highgui.h: No such file or directory
compilation terminated.

I have the most recent libraries for openCV (2.1.0-2).  I tried upgrading/reinstalling the gnu toolchain using sudo apt-get, but that didn't install anything new because it said it was the most recent.  I've also looked under the properties of the highgui (in synaptics) to discover taht the header file is indeed installed on my computer in /usr/include/opencv/highgui.h.

So why wouldn't the compiler be able to link to it?  Any help would be much appreciated.  Thanks.

---

### Post by SevenMachines on 2011-03-03
/usr/include is on the compiler header search path, the opencv subdirectory is not. You can add the path to the header search dirs, eg
with #include <highgui.h>
```
 $ g++ -o test test.cpp -I/usr/include/opencv
```

---

### Post by rocsteady on 2012-12-04
ccheney@fab09:~/ti/trafficintelligence/c$ make
g++ -I../include -I/u/ccheney/ti/OpenCV-2.4.0/include/opencv -I/usr/local/include -I/usr/local/include/opencv -Wall -W -Wextra -DUSE_OPENCV -DLINUX -O3 --fast-math -DNDEBUG   -c -o test-pixels.o test-pixels.cpp
test-pixels.cpp:4:28: fatal error: opencv/highgui.h: No such file or directory
compilation terminated.
make: *** [test-pixels.o] Error 1 

Trying to get the following software to work [https://bitbucket.org/Nicolas/trafficintelligence/wiki/Home](https://bitbucket.org/Nicolas/trafficintelligence/wiki/Home)

:confused:

wat do?

---

### Post by madhater on 2012-12-05
What happens when you manually link the opencv library? 
```

g++ -o test test.cpp -I/usr/include/opencv

```
becomes:
```

g++ -o test test.cpp -lopencv

```

James

---

