---
title: "Using opencv after installation"
date: 2013-05-14
forum: Programming Talk
---

### Post by Avisek003 on 2013-05-14
I installed opencv 2.4 from Ubuntu Software Centre. Now what do I need to do so that I can write programs. Do I need to set library paths for the system to find opencv, and in my program how should I include the libraries I need, like highgui

---

### Post by steeldriver on 2013-05-14
I think the easiest way is to use pkg-config to expand the appropriate paths / libs on your compiler command line e.g. to compile the CannyDetector demo program from the tutorials

```
gcc -o CannyDetector_Demo `pkg-config --cflags opencv` CannyDetector_Demo.cpp `pkg-config --libs opencv`
```

If you're using a Makefile, you can can add them to CFLAGS and LIBS using 

```
CFLAGS += $(shell pkg-config --cflags opencv)
```
 
and so on

DISCLAIMER: I'm only just starting to use OpenCV though

---

### Post by Avisek003 on 2013-05-14
Cool, that worked, thanks!

---

