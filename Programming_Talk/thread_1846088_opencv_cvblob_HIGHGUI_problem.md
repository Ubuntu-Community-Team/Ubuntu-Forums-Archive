---
title: "opencv cvblob HIGHGUI problem"
date: 2011-09-18
forum: Programming Talk
---

### Post by kaloasd on 2011-09-18
I'm kind of new to programming and would like to try opencv, but when I start the sample program I get this error. Can someone explain what it means and what i have to do.
It might be because I don't have drivers for my webcam.

```
$ ./red_object_trackingHIGHGUI ERROR: V4L2: Pixel format of incoming image is unsupported by OpenCV
Unable to stop the stream.: Bad file descriptor
HIGHGUI ERROR: V4L: device /dev/video0: Unable to query number of channels
OpenCV Error: Bad argument (Array should be CvMat or IplImage) in cvGetSize, file /build/buildd/opencv-2.1.0/src/cxcore/cxarray.cpp, line 1233
terminate called after throwing an instance of 'cv::Exception'
  what():  /build/buildd/opencv-2.1.0/src/cxcore/cxarray.cpp:1233: error: (-5) Array should be CvMat or IplImage in function cvGetSize
```

Also I cant find cxarray.cpp

---

### Post by skytreader on 2011-09-18
What sample program is this? My OpenCV installation came with the following sample programs:

```
ls *.c *.cpp
adaptiveskindetector.cpp  camshiftdemo.c     demhist.c   facedetect.cpp  image.cpp    letter_recog.cpp  mushroom.cpp            stereo_calib.cpp
bgfg_codebook.cpp         contours.c         dft.c       ffilldemo.c     inpaint.cpp  lkdemo.c          peopledetect.cpp        tree_engine.cpp
bgfg_segm.cpp             convert_cascade.c  distrans.c  find_obj.cpp    kalman.c     minarea.c         polar_transforms.c      watershed.cpp
blobtrack.cpp             convexhull.c       drawing.c   fitellipse.cpp  kmeans.c     morphology.c      pyramid_segmentation.c
calibration.cpp           delaunay.c         edge.c      houghlines.c    laplace.c    motempl.c         squares.c

```

Also, if you are just sanity-checking your installation (I'm assuming you installed one of the latest builds, with Python support), I find that the Python examples are easier to get up-and-running than the C ones. If you can get a Python example to run, you are most likely good, with only a few compiler/system issues that needs to be addressed to run the examples.

---

### Post by kaloasd on 2011-09-19
It's from cvblob

---

