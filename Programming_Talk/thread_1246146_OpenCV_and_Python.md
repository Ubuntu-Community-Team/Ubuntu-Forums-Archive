---
title: "OpenCV and Python"
date: 2009-08-21
forum: Programming Talk
---

### Post by andy_boy on 2009-08-21
Hi all, 

I'm trying to use OpenCV in Python as part of a uni project. I installed gtk (actaully called gtk-sharp2 in synaptic) and libgtk2.0-cil. I then installed OpenCV  along with the python bindings (all using synaptic, I'm new to Linux...). If I double click on one of the example OpenCV python scripts, I'm asked if I want to run in terminal or display it. If I run in terminal, everything works just fine. However, if I try to run the same python script in the terminal (python logpolar.py), I get an error message:

Traceback (most recent call last):
  File "logpolar.py", line 32, in <module>
    cvNamedWindow( "original",1 );
  File "/var/lib/python-support/python2.6/opencv/highgui.py", line 107, in cvNamedWindow
    return _highgui.cvNamedWindow(*args)
RuntimeError:  openCV Error:
        Status=Unspecified error
        function name=cvNamedWindow
        error message=The function is not implemented. Rebuild the library with Windows, GTK+ 2.x or Carbon support
        file_name=window.cpp
        line=71


I need to sort this out, as it is stopping me writing my own code. Any help would be much appreciated :)

---

### Post by smartbei on 2009-08-22
Hello, could you add as much of the following information as possible - it will help us reproduce your problem and then solve it.

[list]
[*] Could you post the code that is giving you an error?
[*] The exact names of the packages you installed.
[/list]

---

### Post by andy_boy on 2009-08-24
Hi, thanks for the reply. 

It seems that one of the CV functions is causing the trouble, it's called   cvNamedWindow( "original",1 );

The full code of logpolar.py:

#!/usr/bin/python
import sys
from opencv.cv import *
from opencv.highgui import *

src=None
dst=None
src2=None

def on_mouse( event, x, y, flags, param ):

    if( not src ):
        return;

    if event==CV_EVENT_LBUTTONDOWN:
        cvLogPolar( src, dst, cvPoint2D32f(x,y), 40, CV_INTER_LINEAR+CV_WARP_FILL_OUTLIERS );
        cvLogPolar( dst, src2, cvPoint2D32f(x,y), 40, CV_INTER_LINEAR+CV_WARP_FILL_OUTLIERS+CV_WARP_INVERSE_MAP );
        cvShowImage( "log-polar", dst );
        cvShowImage( "inverse log-polar", src2 );

if __name__ == "__main__":
    
    filename = "usr/share/doc/opencv-doc/examples/c/fruits.jpg"
    if len(sys.argv)>1:
        filename=argv[1]
    
    src = cvLoadImage(filename,1)
    if not src:
        print "Could not open %s" % filename
        sys.exit(-1)
        
    cvNamedWindow( "original",1 );
    cvNamedWindow( "log-polar", 1 );
    cvNamedWindow( "inverse log-polar", 1 );
  
    
    dst = cvCreateImage( cvSize(256,256), 8, 3 );
    src2 = cvCreateImage( cvGetSize(src), 8, 3 );
    
    cvSetMouseCallback( "original", on_mouse );
    on_mouse( CV_EVENT_LBUTTONDOWN, src.width/2, src.height/2, None, None)
    
    cvShowImage( "original", src );
    cvWaitKey();



I can't remember exactly which packages I installed, but among them are:

gtk-sharp2
libgtk2.0-cil
gtk-sharp2-gapi


All version 1.0.0-6.1:

python-opencv
libcv1
lighighgui1
libcvaux1
libcv-dev
libcvaux-dev
libhighgui-dev

Seeing that the example files do work (when double-clicked, and not run from the command line), I would presume that it's not an install issue, but there is some kind of link/path missing. 

Thanks in advance for any help!

---

### Post by andy_boy on 2009-08-24
Edit:

The original problem was that the only python scripts which would work with openCV functions were the ones in the examples directory, and they would only work if double clicked on. 

I've just tried copying one of them to another directory, and then chmod +x. It now works when I double click on it, which means i can start writing my own code, but they still won't run from terminal (eg. python logpolar.py, or ./logpolar.py). It's now just annoying, instead of preventing me working. Any answers would still be much appreciated. :)

---

### Post by andy_boy on 2009-08-25
Edit, part 2:

I'm still trying to make this work. 

The python scripts I am trying to write contain functions from two sources: openCV, and some proprietary software for our research robot. 

If I just enter "python example.py", the openCV functions create the error shown above. 

If I enter "sudo python example.py", the openCV functions work just fine, but now the robot software complains that:

ImportError: libboost_program_options-mt.so: cannot open shared object file: No such file or directory

It seems that somehow, openCV has been installed only for admin account, and the robot software for a normal user. 

How do I copy the settings across from one to the other? I'd prefer to run everything as a normal user.....

Thanks.

---

