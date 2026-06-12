---
title: "Some Bad Error in G++"
date: 2010-10-06
forum: Programming Talk
---

### Post by ebrahim-hk on 2010-10-06
Hello all.
i want to make a program with c++ in Ubuntu. 
below i have put the  source code, this source code is simple tutorial in CImageLib website; which you can download and use. And i have downloaded Debian version and others all of them make following error
-------------------------------------------------------------------------------
#include "CImg.h"
using namespace cimg_library;

int main() {
    CImg<unsigned char> image("lena.jpg"), visu(500,400,1,3,0);
    const unsigned char red[] = { 255,0,0 }, green[] = { 0,255,0 }, blue[] = { 0,0,255 };
    image.blur(2.5);
    CImgDisplay main_disp(image,"Click a point"), draw_disp(visu,"Intensity profile");
    while (!main_disp.is_closed() && !draw_disp.is_closed()) {
      main_disp.wait();
      if (main_disp.button() && main_disp.mouse_y()>=0) {
        const int y = main_disp.mouse_y();
        visu.fill(0).draw_graph(image.get_crop(0,y,0,0,image.width()-1,y,0,0),red,1,1,0,255,0);
        visu.draw_graph(image.get_crop(0,y,0,1,image.width()-1,y,0,1),green,1,1,0,255,0);
        visu.draw_graph(image.get_crop(0,y,0,2,image.width()-1,y,0,2),blue,1,1,0,255,0).display(draw_disp);
        }
      }
    return 0;


/*
    cimg_usage("Simple captcha generator.");
    std::cout << "Hello world!" << std::endl;
    return 0;
*/
}
-------------------------------------------------------------------------------
after i compile it, appear so many errors like the next one:
/usr/include/CImg.h:6685: undefined reference to `XOpenDisplay'

absolutely i have seen CImg.h and in its header there is following include files:

// Include display-specific headers.
#if cimg_display==1
#include <X11/Xlib.h>
#include <X11/Xutil.h>
#include <X11/keysym.h>
#include <pthread.h>
#ifdef cimg_use_xshm
#include <sys/ipc.h>
#include <sys/shm.h>
#include <X11/extensions/XShm.h>
#endif
#ifdef cimg_use_xrandr
#include <X11/extensions/Xrandr.h>
#endif
#endif

and at end i will be glad if someone can answer my question: 
what should i do to solve this problem.

---

### Post by Zugzwang on 2010-10-06
You are likely not to have linked against the required libraries. 

I suggest using the search functions of this forum and google to find out more about what this means, why you have to link against a library and so on (because "undefined reference to...." errors are subject of discussion at least twice a week here, so there's plenty of material to find).

Here's a hint to get you started: there's the "-l" (That's a lower-case L) parameter for gcc and g++, which will be of service for this.

---

### Post by ebrahim-hk on 2010-10-07
Hello 
thank you *Zugzwang*.
excuse me. you say true.
i have search, and finally i could solve my problem

---

