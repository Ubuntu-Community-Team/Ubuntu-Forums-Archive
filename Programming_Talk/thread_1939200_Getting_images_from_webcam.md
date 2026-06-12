---
title: "Getting images from webcam"
date: 2012-03-11
forum: Programming Talk
---

### Post by mohitdaksh on 2012-03-11
Hello,

I have been working on a small project for college and want some help for that.

I   need connect my webcam feed to my website which I host on my home  computer running on Ubuntu. I tried using many alternatives but could  not get it working. 
So, what I did was I made a [processing]("http://processing.org") program  which takes a frame from my webcam feed and saves it as an image with  the same filename over and over and I auto-reload the webpage in which I have  embedded the image file.

But, processing code runs with its  window which I do not want. Is there a way (or another language,  or bash script perhaps) which will let me do the same thing but as a background process  with no window of its own?

---

### Post by MG&amp;TL on 2012-03-11
This: [http://linux.about.com/od/commands/l/blcmdl1_webcam.htm](http://linux.about.com/od/commands/l/blcmdl1_webcam.htm)

looks promising.

---

### Post by ve4cib on 2012-03-11
Depending on what exactly you need the program to do you can use OpenCV to grab frames from the webcam and save them fairly easily.  OpenCV is maybe overkill for just grabbing frames from a webcam, but you can do lots of other cool stuff with it if you want to.

OpenCV is available for a pretty wide range of languages (I use it mainly with C++ and Python), and the documentation is pretty good.  Here's a really quick-and-dirty C++ program to record a single frame from the camera and save it.

```

#include <opencv/cv.h>
#include <opencv/highgui.h>

using namespace cv;

int main(int argc, char** argv)
{
    CvCapture *camera = cvCaptureFromCAM(-1);

    for(;;)
    {
        if(cvGrabFrame(camera))
        {
            IplImage *frame = cvRetrieveFrame(camera);

            cvSaveImage("webcam_frame.png",frame);
            break;
        }
    }
    
    return 0;
}

```

It would be easy enough to expand this into a larger program that would record a frame at specific intervals, or wait for a keystroke, etc....  It could be run in the background very easily.

---

### Post by mohitdaksh on 2012-03-12
Hello and thanks ve4cib and MG&TL.

I will try both of these options and tell you the results soon :)

---

### Post by PaulM1985 on 2012-03-12
> **mohitdaksh said:**
> But, processing code runs with its  window which I do not want. 

You could just run it as a background task.  In that way you could close the terminal and it would continue to run.  You can do this by adding "&" at the end of the line for execution, like this:
```

>run_camera_thing.sh &

```

Paul

---

### Post by mohitdaksh on 2012-03-12
```
libv4l2: error converting / decoding frame data: v4l-convert: error parsing JPEG header: Not a JPG file ?

```


I am getting this error with every command line tool to capture webcam including the C program.


And getting this error when I start the exported processing standalone application ```
!!! required library not found : no OpenCV in java.library.path
Verify that the java.library.path property is correctly set and 'libcxcore.so', 'libcv.so', 'libcvaux.so', 'libml.so', and 'libhighgui.so' are placed (or linked) in one of your system shared libraries folder

Exception in thread "Animation Thread" java.lang.UnsatisfiedLinkError: hypermedia.video.OpenCV.capture(III)V
    at hypermedia.video.OpenCV.capture(Native Method)
    at hypermedia.video.OpenCV.capture(OpenCV.java:945)
    at websiteVideo.setup(websiteVideo.java:29)
    at processing.core.PApplet.handleDraw(Unknown Source)
    at processing.core.PApplet.run(Unknown Source)
    at java.lang.Thread.run(Thread.java:636)

```

However when I use the run button in the processing IDE it works fine.

Cheese and other webcam softwares are also working fine.

---

### Post by mohitdaksh on 2012-03-12
I exported the processing app with an older version of processing and it is working now. But none of the other methods are working right now

---

### Post by ve4cib on 2012-03-12
> **mohitdaksh said:**
> ```
libv4l2: error converting / decoding frame data: v4l-convert: error parsing JPEG header: Not a JPG file ?

```

I am getting this error with every command line tool to capture webcam including the C program.

It may be that your webcam does not record the frames as a JPG.  What kind of webcam are you using?


> And getting this error when I start the exported processing standalone application ```
!!! required library not found : no OpenCV in java.library.path
Verify that the java.library.path property is correctly set and 'libcxcore.so', 'libcv.so', 'libcvaux.so', 'libml.so', and 'libhighgui.so' are placed (or linked) in one of your system shared libraries folder

Exception in thread "Animation Thread" java.lang.UnsatisfiedLinkError: hypermedia.video.OpenCV.capture(III)V
    at hypermedia.video.OpenCV.capture(Native Method)
    at hypermedia.video.OpenCV.capture(OpenCV.java:945)
    at websiteVideo.setup(websiteVideo.java:29)
    at processing.core.PApplet.handleDraw(Unknown Source)
    at processing.core.PApplet.run(Unknown Source)
    at java.lang.Thread.run(Thread.java:636)

```

However when I use the run button in the processing IDE it works fine.

Cheese and other webcam softwares are also working fine.

Do you have the OpenCV Java library installed?

---

