---
title: "Cimg Errors"
date: 2009-06-15
forum: Programming Talk
---

### Post by kaspar_silas on 2009-06-15
Hi All,

Has anyone tried the examples that come with Cimg. I installed the Cimg-dev package through synaptic. I then tried the image_registration.cpp as an example. It gave:

```

 g++ -o image_registration image_registration.cpp -O2 -L/usr/X11R6/lib -lm -lpthread -lX11
image_registration.cpp: In function &#8216;void animate_warp(const cimg_library::CImg<unsigned char>&, const cimg_library::CImg<unsigned char>&, const cimg_library::CImg<float>&, bool, bool, const char*, int, cimg_library::CImgDisplay&)&#8217;:
image_registration.cpp:67: error: no match for &#8216;operator!&#8217; in &#8216;!disp&#8217;
image_registration.cpp:67: note: candidates are: operator!(bool) <built-in>
image_registration.cpp:67: error: &#8216;struct cimg_library::CImgDisplay&#8217; has no member named &#8216;is_keyQ&#8217;
image_registration.cpp:70: error: &#8216;const struct cimg_library::CImg<unsigned char>&#8217; has no member named &#8216;linear_atXY&#8217;
image_registration.cpp:71: error: &#8216;const struct cimg_library::CImg<unsigned char>&#8217; has no member named &#8216;linear_atXY&#8217;
image_registration.cpp:74: error: &#8216;const struct cimg_library::CImg<unsigned char>&#8217; has no member named &#8216;linear_atXY&#8217;
image_registration.cpp:77: error: could not convert &#8216;disp&#8217; to &#8216;bool&#8217;
image_registration.cpp:77: error: no matching function for call to &#8216;cimg_library::CImg<unsigned char>::draw_image(int, cimg_library::CImg<unsigned char>&)&#8217;
/usr/include/CImg.h:11726: note: candidates are: cimg_library::CImg<T>& cimg_library::CImg<T>::draw_image(const cimg_library::CImg<T>&, int, int, int, int, float) [with T = unsigned char]
...
 
```

Has anyone else had this problem

---

### Post by kaspar_silas on 2009-06-15
Much more baffled now, I just tried this quick little example from the CImg tutorial:

```

#include "CImg.h"

 using namespace cimg_library;

  int main()
  {
    CImg<unsigned char> image("lena.jpg"), visu(500,400,1,3,0);
    const unsigned char red[] = { 255,0,0 }, green[] = { 0,255,0 }, blue[] = { 0,0,255 };
    image.blur(2.5);
    CImgDisplay main_disp(image,"Click a point"), draw_disp(visu,"Intensity profile");
    while (!main_disp.is_closed && !draw_disp.is_closed)
    {
      main_disp.wait();
      if (main_disp.button && main_disp.mouse_y>=0)
      {
        const int y = main_disp.mouse_y;
        visu.fill(0).draw_graph(image.get_crop(0,y,0,0,image.dimx()-1,y,0,0),red,1,1,0,255,0);
        visu.draw_graph(image.get_crop(0,y,0,1,image.dimx()-1,y,0,1),green,1,1,0,255,0);
        visu.draw_graph(image.get_crop(0,y,0,2,image.dimx()-1,y,0,2),blue,1,1,0,255,0).display(draw_disp);
      }
    }
    return 0;
  }
```

Running this with:
g++ -o MAIN main.cpp -O2 -L/usr/X11R6/lib -lm -lpthread -lX11
gives:

```
Compiling: main.cpp
main.cpp: In function ‘int main()’:
main.cpp:17: error: no matching function for call to ‘cimg_library::CImg<unsigned char>::draw_graph(cimg_library::CImg<unsigned char>, const unsigned char [3], int, int, int, int, int)’
main.cpp:18: error: no matching function for call to ‘cimg_library::CImg<unsigned char>::draw_graph(cimg_library::CImg<unsigned char>, const unsigned char [3], int, int, int, int, int)’
main.cpp:19: error: no matching function for call to ‘cimg_library::CImg<unsigned char>::draw_graph(cimg_library::CImg<unsigned char>, const unsigned char [3], int, int, int, int, int)’
Process terminated with status 1 (0 minutes, 3 seconds)
3 errors, 0 warnings

```

Any help is greatly appreciated as I am totally lost at present!

---

### Post by kaspar_silas on 2009-06-16
Hi,

Is there any chance anyonw could repeat what I did, which was:

sudo apt-get install cimg-dev

Copy the simple code above into a file called main.cpp
CD to the directory containing main.cpp and run:

g++ -o MAIN main.cpp -O2 -L/usr/X11R6/lib -lm -lpthread -lX11

Just to see if all ubuntu users get this message.

Thanks

---

### Post by Zugzwang on 2009-06-16
Are you sure that the tutorial you are using is for the current version of that library?

---

### Post by kaspar_silas on 2009-06-17
Spot on Zugzwang!! Thanks for pointing it out. The repository version is slightly out of date and missing the functions used in the tutorial. Dearly me, what a foolish mistake. Why is it always the annoyingly obvious things that waste the most time.

Anyway, just in case anyone else comes across this issue. The solution was pretty obvious:
```
sudo apt-get remove cimg-dev
wget http://cimg.sourceforge.net/cimg-dev.deb
sudo dpkg -i cimg-dev.deb
rm cimg-dev.deb
```

---

