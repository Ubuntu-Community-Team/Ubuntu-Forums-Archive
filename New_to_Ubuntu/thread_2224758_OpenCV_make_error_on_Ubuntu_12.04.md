---
title: "OpenCV make error on Ubuntu 12.04"
date: 2014-05-17
forum: New to Ubuntu
---

### Post by siddharth7 on 2014-05-17
I am trying to install OpenCV 2.4.2 on Ubuntu and am running into errors as below:

```
[12%] Building CXX object  modules/highgui/CMakeFiles/opencv_highgui.dir/src/cap_gstreamer.cpp.o 
In file included from /usr/local/include/glib-2.0/glib/gasyncqueue.h:30:0,                   
from /usr/local/include/glib-2.0/glib.h:32,                   
from /usr/include/gstreamer-0.10/gst/gst.h:27,                   
from /opt/OpenCV-2.4.2/modules/highgui/src/cap_gstreamer.cpp:56:  
/usr/local/include/glib-2.0/glib/gthread.h:233:27: error: variable or  field 'g_static_mutex_init' declared void
```

I checked all dependencies and installed them as below:
> 
  sudo apt-get install build-essential libgtk2.0-dev libjpeg-dev libtiff4-dev libjasper-dev libopenexr-dev cmake python-dev python-numpy python-tk libtbb-dev libeigen2-dev yasm libfaac-dev libopencore-amrnb-dev libopencore-amrwb-dev libtheora-dev libvorbis-dev libxvidcore-dev libx264-dev libqt4-dev libqt4-opengl-dev sphinx-common texlive-latex-extra libv4l-dev libdc1394-22-dev libavcodec-dev libavformat-dev libswscale-dev
  
I also added the following paths to CMakeCache.txt based on where I could locate glibconfig.h

  CMAKE_CXX_FLAGS_RELEASE:STRING=-O3 -DNDEBUG -I/usr/lib/x86_64-linux-gnu/glib-2.0/include/
  Any help is appreciated.


  Thanks,


  Sid

---

