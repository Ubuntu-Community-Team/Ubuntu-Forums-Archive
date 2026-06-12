---
title: "Missing X Library for Cimg"
date: 2007-12-19
forum: Programming Talk
---

### Post by dejay703 on 2007-12-19
Hi everyone,

I'm fairly new to programming in ubuntu.  Anyway, I am trying to work with Cimg, and I'm having problems compiling my own programs.  It seems like I can compile their examples perfectly fine (running 'make linux' in their examples folder completes fine).  However, when I try to compile my program, I get a lot of errors that look like the following:

main.cpp:(.text._ZN12cimg_library11CImgDisplay6assignEv[cimg_library::CImgDisplay::assign()]+0xe6): undefined reference to `XDestroyWindow'
main.cpp:(.text._ZN12cimg_library11CImgDisplay6assignEv[cimg_library::CImgDisplay::assign()]+0x15c): undefined reference to `XFreeColormap'
main.cpp:(.text._ZN12cimg_library11CImgDisplay6assignEv[cimg_library::CImgDisplay::assign()]+0x184): undefined reference to `XSync'
main.cpp:(.text._ZN12cimg_library11CImgDisplay6assignEv[cimg_library::CImgDisplay::assign()]+0x32a): undefined reference to `pthread_cancel'
main.cpp:(.text._ZN12cimg_library11CImgDisplay6assignEv[cimg_library::CImgDisplay::assign()]+0x354): undefined reference to `pthread_join'
main.cpp:(.text._ZN12cimg_library11CImgDisplay6assignEv[cimg_library::CImgDisplay::assign()]+0x3b7): undefined reference to `XSync'
main.cpp:(.text._ZN12cimg_library11CImgDisplay6assignEv[cimg_library::CImgDisplay::assign()]+0x3ca): undefined reference to `XCloseDisplay'

It looks like I am missing some sort of x library, but I have gone through synaptics and installed everything that I think I need.  Does anyone have any suggestions?

Thanks
Jason

---

### Post by fulgencio on 2008-01-23
I am having the same problems please post any solutions you can find.

Thanks

---

### Post by fulgencio on 2008-01-29
I believe its a problem with the ImageMagick package but I dont know how to solve it...:(

---

### Post by ILoveBobbyMarley on 2008-06-19
Had the same problem,

try 

  g++ -o test main.cpp -lpthread -lX11

or better still add 

  test_LDFLAGS  =  -lpthread -lX11  

to your Makefile.am, so you have something like

  bin_PROGRAMS = test
  test_LDFLAGS = -lpthread -lX11  
  test_SOURCES = main.cpp

I have seen additional switches used by some, eg

  g++ -o test main.cpp -O2 -L/usr/X11R6/lib -lm -lpthread -lX11 

but for me the above was minimal for the hello world app.

PEACE X

---

### Post by JHSaunders on 2008-07-30
Ths worked for me, thanks.

---

### Post by in_rainbow on 2008-08-12
thanks so much. This worked for me too. It was driving me crazy.

---

### Post by ariismail on 2008-10-05
Thank you very much!

---

### Post by AWittyUserName on 2009-09-06
Very helpful.  Thanks!

---

