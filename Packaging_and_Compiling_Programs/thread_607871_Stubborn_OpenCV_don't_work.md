---
title: "Stubborn OpenCV don't work"
date: 2007-11-09
forum: Packaging and Compiling Programs
---

### Post by zybler on 2007-11-09
I'm trying to get OpenCV to work. **apt-cache search opencv** gives me:

```

libcv-dev - development files for libcv
libcv1 - computer vision library
libcvaux-dev - development files for libcvaux
libcvaux1 - computer vision extension library
libhighgui-dev - development files for libhighgui
libhighgui1 - computer vision GUI library
opencv-doc - OpenCV documentation and examples
python-opencv - Python bindings for the computer vision library

```

I installed all of them using **sudo apt-get install libcv-dev libcv1 libcvaux-dev libcvaux1 libhighgui-dev libhighgui1 opencv-doc python-opencv**

I know the header files are in /usr/include/opencv/,
the libraries are in /usr/lib/.

I wrote a test program and stored it in /home/zybler/Documents/opencv/
```

#include <stdlib.h>
#include <stdio.h>
#include <cv.h> // an OpenCV header file
#include <highgui.h> // another OpenCV header file

int main() {
IplImage* img = 0;
// img : variable for the image
// IplImage is a data type for images in OpenCV

img = cvLoadImage(&#8220;photo.jpg&#8221;, 1);
// load image &#8220;photo.jpg&#8221;

cvNamedWindow(&#8220;mainWin&#8221;, CV_WINDOW_AUTOSIZE);
// create a window named &#8220;mainWin&#8221; to display the loaded image &#8211; set on autosize so it matches the dimensions of the image

cvMoveWindow(&#8220;mainWin&#8221;, 100, 100);
// place the window in the coordinates (x: 100, y: 100) -- the origin (0, 0) is the top left corner of the screen

cvShowImage(&#8220;mainWin&#8221;, img);
// display the loaded image (photo.jpg) in the created window (mainWin)

cvWaitKey(0);
// do nothing/wait until a key is pressed &#8211; then continue to the next line

if (img) printf(&#8220;success!&#8221;);
// if the image is successfully loaded, print &#8220;success!&#8221; on the screen

cvReleaseImage(&img);
}

```

And I compiled it using the command

**g++ loadimage.cpp -o loadimage -I /usr/include/opencv/ -L /usr/lib -lcv -lhighgui**

Even though the compilation gives no error, **./loadimage** gives me:

```

OpenCV ERROR: Unspecified error (The function is not implemented. Rebuild the library with Windows, GTK+ 2.x or Carbon support)
        in function cvNamedWindow, window.cpp(71)
Terminating the application...
        called from cvUnregisterType, cxpersistence.cpp(4933)
Terminating the application...
        called from cvUnregisterType, cxpersistence.cpp(4933)
Terminating the application...
        called from cvUnregisterType, cxpersistence.cpp(4933)
Terminating the application...
        called from cvUnregisterType, cxpersistence.cpp(4933)
Terminating the application...
        called from cvUnregisterType, cxpersistence.cpp(4933)
Terminating the application...
        called from cvUnregisterType, cxpersistence.cpp(4933)
Terminating the application...
        called from cvUnregisterType, cxpersistence.cpp(4933)
Terminating the application...
        called from cvUnregisterType, cxpersistence.cpp(4933)
Terminating the application...
        called from cvUnregisterType, cxpersistence.cpp(4933)
Terminating the application...

```

**ldd loadimage** gives me:

```

zybler@zybler-tpc:~/Documents/opencv$ ldd loadimage
        linux-gate.so.1 =>  (0xffffe000)
        libcv.so.1 => /usr/local/lib/libcv.so.1 (0xb7ef1000)
        libhighgui.so.1 => /usr/local/lib/libhighgui.so.1 (0xb7ecb000)
        libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0xb7dd7000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7db2000)
        libgcc_s.so.1 => /lib/libgcc_s.so.1 (0xb7da7000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7c5d000)
        libcxcore.so.1 => /usr/local/lib/libcxcore.so.1 (0xb7b3d000)
        libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb7b25000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7b20000)
        libz.so.1 => /usr/lib/libz.so.1 (0xb7b0b000)
        /lib/ld-linux.so.2 (0xb7fe1000)

```


What am I missing?

---

### Post by syxbit on 2008-03-07
i don't think you've installed openCV
it doesn't seem openCV is in the repos
you'll have to compile it

---

### Post by thezman on 2008-05-09
I had the same problem. Here is how I solved it: 

[http://softwarecommunity.intel.com/isn/Community/en-US/forums/thread/30234949.aspx](http://softwarecommunity.intel.com/isn/Community/en-US/forums/thread/30234949.aspx)

Basically you need to install libgtk2.0-dev first. Then configure, make and sudo make install again

---

### Post by vsegers on 2009-04-07
Thank you thezman!!!

---

