---
title: "JavaCV and WebCam"
date: 2012-01-30
forum: Programming Talk
---

### Post by RobikShrestha on 2012-01-30
I tried the following code using JavaCV library:

public class JavaCVSample {

    public static void main(String[] args) throws Exception {
        String classifierName = "/usr/local/OpenCV/data/haarcascades/haarcascade_frontalface_alt.xml";

        Loader.load(opencv_objdetect.class);
        CvHaarClassifierCascade classifier = new 

        CvHaarClassifierCascade(cvLoad(classifierName));

        CanvasFrame frame = new CanvasFrame("Some Title");

        // OpenCVFrameGrabber uses opencv_highgui, but other more versatile FrameGrabbers
        // include DC1394FrameGrabber, FlyCaptureFrameGrabber, OpenKinectFrameGrabber,
        // PS3EyeFrameGrabber, VideoInputFrameGrabber, and FFmpegFrameGrabber.
        FrameGrabber grabber = new OpenCVFrameGrabber(0);
        grabber.start();
    }
}

Following is the output:

VIDIOC_QUERYMENU: Invalid argument
VIDIOC_QUERYMENU: Invalid argument
VIDIOC_QUERYMENU: Invalid argument
HIGHGUI ERROR: V4L: Property <unknown property string>(16) not supported by device

What is the problem? Is it due to the driver? If so, how do I upgrade the driver? The webcam I have is "PC Camera" (according to the manual of my SIS laptop).

---

### Post by RobikShrestha on 2012-01-30
However, I am still able to grab the image from webcam and display it by using the following code:


import com.googlecode.javacpp.Loader;
import com.googlecode.javacv.*;
import static com.googlecode.javacv.cpp.opencv_core.*;
import static com.googlecode.javacv.cpp.opencv_imgproc.*;
import static com.googlecode.javacv.cpp.opencv_calib3d.*;
import static com.googlecode.javacv.cpp.opencv_objdetect.*;

public class MotionDetector {

    public static void main(String[] args) throws Exception {
        OpenCVFrameGrabber grabber = new OpenCVFrameGrabber(0);
        grabber.start();

        IplImage image = grabber.grab();

        
        CanvasFrame canvasFrame = new CanvasFrame("Web Cam Detection Going on");
        canvasFrame.setCanvasSize(image.width(), image.height());
        canvasFrame.setDefaultCloseOperation(CanvasFrame.EXIT_ON_CLOSE);

//        CvMemStorage storage = CvMemStorage.create();

        while (true) {
            image=grabber.grab();
            canvasFrame.showImage(image);
        }
        
    }
   
}

---

