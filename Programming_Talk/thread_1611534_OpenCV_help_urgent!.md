---
title: "OpenCV help urgent!"
date: 2010-11-02
forum: Programming Talk
---

### Post by msakms on 2010-11-02
[COLOR=Blue][FONT=Comic Sans MS]I've recently resumed working on a robotics project but this time on ubuntu. I've installed OpenCV from synaptic package manager and I'm using Code::Blocks IDE. Every time I run the executable file to capture live video from my webcam I get this error:
[/FONT][/COLOR]```
HIGHGUI ERROR: V4L2: Pixel format of incoming image is unsupported by OpenCV
Unable to stop the stream.: Bad file descriptor
HIGHGUI ERROR: V4L: Pixel format of incoming image is unsupported by OpenCV
Cannot open initialize webcam!

```
I've spent so much time trying to find a solution for that issue but with no hope. Any suggestions will be greatly appreciated!

---

### Post by DanielWaterworth on 2010-11-02
Have you been able to capture video before with this camera or is this your first time trying in linux? can you view the video stream in vlc? is there another camera you can try with? I've always found highgui easy to work with and never had any problems, I suspect this is a configuration or hardware issue.

---

### Post by Some Penguin on 2010-11-02
I find it somewhat unlikely that you'll get useful help without mentioning relevant technical details, like what webcam you're actually using, how it's connected, and how you're invoking OpenCV calls.

---

### Post by msakms on 2010-11-02
My webcam is a Logitech one and the "lsusb" command shows " [Bus 001 Device 008: ID 046d:0892 Logitech, Inc. OrbiCam "   ]("http://community.linuxmint.com/hardware/view/2909")
Also it's working fine with "Cheese webcam booth" and I'm able to capture and record videos. My source code I'm trying to run is as follows: 
```
#include <stdio.h>
#include "cv.h"
#include "highgui.h"
 
int main( int argc, char **argv )
{
    CvCapture *capture = 0;
    IplImage  *frame = 0;
    int       key = 0;
 
    /* initialize camera */
    capture = cvCaptureFromCAM( 0 );
 
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
```

This source runs smoothly on windows but for some reason doesn't run on linux although other utilities are able to use the webcam. 
[]("http://community.linuxmint.com/hardware/view/2909")

---

### Post by DanielWaterworth on 2010-11-02
are you sure that you're trying to initialise the right camera (video device 0)?

---

### Post by msakms on 2010-11-02
Yes I am sure because I only have this device and other numerical values show absence of corresponding device.

---

### Post by Some Penguin on 2010-11-02
Perhaps your OpenCV installation wasn't configured to support the required codecs at compile time, in which case you'll want to fetch the source and determine what format your camera actually uses.

---

### Post by msakms on 2010-11-02
> **Some Penguin said:**
> Perhaps your OpenCV installation wasn't configured to support the required codecs at compile time, in which case you'll want to fetch the source and determine what format your camera actually uses.

THANK YOU so much, you just made my day :P. That was an awesome hint now I use the following command to support my webcam 
```
LD_PRELOAD="/usr/lib/libv4l/v4l2convert.so" ./MY-SOURCE.C 
```

---

