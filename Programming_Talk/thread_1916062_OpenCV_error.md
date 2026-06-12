---
title: "OpenCV error"
date: 2012-01-27
forum: Programming Talk
---

### Post by RobikShrestha on 2012-01-27
I get the following error:

OpenCV Error: Unspecified error (The function is not implemented. Rebuild the library with Windows, GTK+ 2.x or Carbon support. If you are on Ubuntu or Debian, install libgtk2.0-dev and pkg-config, then re-run cmake or configure script) in cvNamedWindow, file /home/robik/Downloads/Java/OpenCV-2.3.1/modules/highgui/src/window.cpp, line 275
terminate called after throwing an instance of 'cv::Exception'
  what():  /home/robik/Downloads/Java/OpenCV-2.3.1/modules/highgui/src/window.cpp:275: error: (-2) The function is not implemented. Rebuild the library with Windows, GTK+ 2.x or Carbon support. If you are on Ubuntu or Debian, install libgtk2.0-dev and pkg-config, then re-run cmake or configure script in function cvNamedWindow

Aborted

I libgtk2.0-dev and pkg-config both are installed but I still get the error. What is wrong?

---

### Post by RobikShrestha on 2012-01-27
I followed the steps at 
[http://www.samontab.com/web/2011/06/installing-opencv-2-2-in-ubuntu-11-04/](http://www.samontab.com/web/2011/06/installing-opencv-2-2-in-ubuntu-11-04/)
It works.
I also used javacv from:
[http://code.google.com/p/javacv/](http://code.google.com/p/javacv/)

---

