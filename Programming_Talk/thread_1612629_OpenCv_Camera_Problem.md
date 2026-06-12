---
title: "OpenCv Camera Problem"
date: 2010-11-03
forum: Programming Talk
---

### Post by TPWT on 2010-11-03
Hello

I am trying to get video output from my webcam on my laptop using OpenCv. However Eclipse/OpenCV cannot find my webcams.

The code I am using is

```
#include <stdio.h>
#include "cv.h"
#include "highgui.h"

int main( int argc, char **argv){
    CvCapture *capture = 0;
    IplImage  *frame = 0;
    int       key = 0;

    /* initialize camera */
    capture = cvCaptureFromCAM(0);

    /* always check */
    if ( !capture ) {
        fprintf( stderr, "Cannot open initialize webcam!\n" );
        return 1;
    }

    /* create a window for the video */
    cvNamedWindow( "result", CV_WINDOW_AUTOSIZE );

    while( key != 'q' ) {
        /* get a frame */
        frame = cvQueryFrame( capture );

        /* always check */
        if( !frame ) break;

        /* display current frame */
        cvShowImage( "result", frame );

        /* exit if user press 'q' */
        key = cvWaitKey( 1 );
    }

    /* free memory */
    cvDestroyWindow( "result" );
    cvReleaseCapture( &capture );

    return 0;
}

```This returns "Cannot open initialize webcam!" suggesting cvCaptureFromCAM is NULL.

As such I tracked back the webcameras (all of which work on cheese) and got this infomation:

```

/dev/video0: OK                         [ -device /dev/video0 ]
    type : v4l2
    name : USB Camera-B4.04.27.1
    flags:  capture  

/dev/video1: OK                         [ -device /dev/video1 ]
    type : v4l2
    name : USB 2.0 Camera
    flags:  capture  

/dev/video2: OK                         [ -device /dev/video2 ]
    type : v4l2
    name : USB Camera-B4.04.27.1
    flags:  capture 

```As the cameras are running under v4l2 I added in the line:

```

LD_PRELOAD="/usr/lib/libv4l/v4l2convert.so"

```However the cameras are still not recognised. 

I am new to Eclipse, OpenCv, C++ and Linux so any help and advice would be wonderful

Thanks for your help :)

---

### Post by fng44 on 2010-11-14
I think have the same problem in python.
the cam works with cheese or gstreamer-properties. 
I get a redlight in front so i can see the cam is running. When closing the application, le redlight switches off.
By the way, when trying to run captureFromCam with python nothing happens (no red light). This leads me to the conclusion that cam is not started. 
I don't know where to find any logs about that.
Can someone help us ?

Running python 2.6 with openCV 2.1 on lucid.

---

### Post by TPWT on 2010-11-14
Turns out that OpenCV was not installed properly :redface:

Reinstalled it and all is fine :)

---

### Post by tony99 on 2010-11-28
> **TPWT said:**
> Turns out that OpenCV was not installed properly :redface:

Reinstalled it and all is fine :)

Could you tell me your setup and/or how you installed? i.e. which versions of opencv, highgui, v4l etc. I am having the same problem. I just installed opencv using apt-get. I tried using both 2.0 and 2.1 from the repos on Lucid, neither work with the camera. The program I wrote is similar to yours and works fine on my windows machine, my camera works on Ubuntu as well, I just can't get it to work with opencv.

---

### Post by TPWT on 2010-11-28
[http://opencv.willowgarage.com/wiki/InstallGuide_Linux](http://opencv.willowgarage.com/wiki/InstallGuide_Linux)

Start from the top and work your way down. This page solved 2 weeks of head scratching.

Good luck!

---

### Post by Gouz on 2010-12-07
hey there..

I ma having the same problem I reinstalled using the link you suggested but it still does not want to work. I am getting the same error I also run all the test that the link provides and nothing.

any ideas?

---

### Post by TPWT on 2010-12-07
What error are you getting. Did you install the packages listed in the link?

---

### Post by Gouz on 2010-12-07
yeah I did

I get the same error that video can not be init.

and funny thing I wrote some extra code and created a new file in gedit compile run and it worked so clearly the prob is somewhere in Eclipse
can you send me the eclipse configs you have?

like paths and files and libs and incs ?

---

### Post by Gouz on 2010-12-08
Okay folks

for the rest of you. Problem solved.

It was eclipse, the fix is get a fresh package from the eclipse.org I took the newer version and simple move your code not the project.

copy paste the code and link the project again to the libs and includes.

Good luck!

Gouz

---

### Post by hnkulkarni on 2012-03-04
I also had a problem detecting my laptop camera on Ubuntu 11.10 and Opencv 2.3.1 it was solved after installing/re-installing the following

[LIST=1]
[*]ffmpeg
[*]gstreamer
[*]v4l
[/LIST]
Once done that you should delete previous installation of OpenCV, and then compile it again from the source, make sure that you make adequate changes in the config using USE_V4L=ON, I used the following cmake config statement

```

cmake -D CMAKE_BULD_TYPE=RELEASE -D CMAKE_INSTALL_PREFIX=/usr/local -D BUILD_PYTHON_SUPPORT=ON USE_V4L=ON WITH_TBB=ON -D BUILD_NEW_PYTHON_SUPPORT=ON USE_GStreamer=ON ..

```


Hope this helps some of you out there.


Regards, 

Hrushikesh N. Kulkarni

---

