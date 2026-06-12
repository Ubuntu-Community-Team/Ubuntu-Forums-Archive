---
title: "OpenCV linking problems"
date: 2012-09-02
forum: Programming Talk
---

### Post by Mistrpopo on 2012-09-02
Hi everyone.  I turn to this forum for inspiration...
I recently upgraded Ubuntu to 12.04 and re-installed OpenCV 2.4.2 (I managed to make it work on my previous release, 11.04).
Installation went fine, using CMake-make-make install. I activated BUILD_EXAMPLES=ON and examples have been built correctly.
But when I try to compile a simple program:

```

#include "opencv2/core/core.hpp"
#include "opencv2/highgui/highgui.hpp"

using namespace cv;

/** function main **/
int main(int argc, char** argv)
{
  Mat img_object = imread( argv[1], CV_LOAD_IMAGE_GRAYSCALE );
  namedWindow( "window" );
  imshow("window",img_object);
  waitKey(0);
  return 0;
}

```with the following command:

```
g++ `pkg-config --cflags --libs opencv` easyprog.cpp -o easyprog
```I get linker errors:

```

/tmp/ccP0wNBz.o: In function `main':
easyprog.cpp:(.text+0x53): undefined reference to `cv::imread(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, int)'
easyprog.cpp:(.text+0xa4): undefined reference to `cv::namedWindow(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, int)'
easyprog.cpp:(.text+0xcc): undefined reference to `cv::_InputArray::_InputArray(cv::Mat const&)'
easyprog.cpp:(.text+0x103): undefined reference to `cv::imshow(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, cv::_InputArray const&)'
easyprog.cpp:(.text+0x125): undefined reference to `cv::waitKey(int)'
/tmp/ccP0wNBz.o: In function `cv::Mat::~Mat()':
easyprog.cpp:(.text._ZN2cv3MatD2Ev[_ZN2cv3MatD5Ev]+0x2b): undefined reference to `cv::fastFree(void*)'
/tmp/ccP0wNBz.o: In function `cv::Mat::release()':
easyprog.cpp:(.text._ZN2cv3Mat7releaseEv[cv::Mat::release()]+0x3b): undefined reference to `cv::Mat::deallocate()'
collect2: ld returned 1 exit status
```pkg-config works fine:

```
>pkg-config --cflags opencv
-I/usr/local/include/opencv -I/usr/local/include  

>pkg-config --libs opencv
/usr/local/lib/libopencv_calib3d.so /usr/local/lib/libopencv_contrib.so  /usr/local/lib/libopencv_core.so /usr/local/lib/libopencv_features2d.so  /usr/local/lib/libopencv_flann.so /usr/local/lib/libopencv_gpu.so  /usr/local/lib/libopencv_highgui.so /usr/local/lib/libopencv_imgproc.so  /usr/local/lib/libopencv_legacy.so /usr/local/lib/libopencv_ml.so  /usr/local/lib/libopencv_nonfree.so  /usr/local/lib/libopencv_objdetect.so /usr/local/lib/libopencv_photo.so  /usr/local/lib/libopencv_stitching.so /usr/local/lib/libopencv_ts.so  /usr/local/lib/libopencv_video.so /usr/local/lib/libopencv_videostab.so
```And libraries are properly installed in usr/local/lib.

```

>ls /usr/local/lib/ -1
libopencv_calib3d.so
libopencv_calib3d.so.2.4
libopencv_calib3d.so.2.4.2
libopencv_contrib.so
libopencv_contrib.so.2.4
libopencv_contrib.so.2.4.2
libopencv_core.so
[...]
```What could be the source of linker errors here?

---

### Post by MadCow108 on 2012-09-02
libraries must be placed behind objects needing them since 11.10

```
g++ `pkg-config --cflags opencv` easyprog.cpp `pkg-config --libs opencv` -o easyprog
```

---

### Post by Mistrpopo on 2012-09-02
Thanks a lot! The program compiled successfully. Now I am wondering why is that, but that is another question..

---

