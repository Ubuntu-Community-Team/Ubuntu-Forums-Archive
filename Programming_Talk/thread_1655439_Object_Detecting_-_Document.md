---
title: "Object Detecting - Document"
date: 2010-12-29
forum: Programming Talk
---

### Post by AlGorism on 2010-12-29
Hi everyone.

I want to learn object detecting, but I couldn't find useful documents for beginners.

I know C well, and Java -more than basics, not perfect-.  Where should I start?

---

### Post by Sub101 on 2010-12-29
If you actual want to do the coding then your gonna need to do a fair amount of research.

The method I am most familiar with are Eigenfaces. It is more for facial recognition but the same principles apply.

If you just want to use the technologies then take a look here:

[http://en.wikipedia.org/wiki/OpenCV](http://en.wikipedia.org/wiki/OpenCV)

It is for C++ but if you are a C developer im sure it will be an easy transition.

---

### Post by AlGorism on 2010-12-29
Thanks. I know C++ a little actually, I can improve it. I'm starting reading from now. 
Is learning Opencv enough, or should I go further?

---

### Post by Sub101 on 2010-12-29
> **AlGorism said:**
> Thanks. I know C++ a little actually, I can improve it. I'm starting reading from now. 
Is learning Opencv enough, or should I go further?

Depends exactly what you want to use it for?

If your thinking along the same lines as the Kinect type stuff youll need a lot more.

---

### Post by AlGorism on 2010-12-30
> **Sub101 said:**
> Depends exactly what you want to use it for?

If your thinking along the same lines as the Kinect type stuff youll need a lot more.
I see. So, you're saying that OpenCV is enough for beginners and for general view. If I want to move on image processing, like you say I'll have a lot more things to read.

---

### Post by Sub101 on 2010-12-30
> **AlGorism said:**
> I see. So, you're saying that OpenCV is enough for beginners and for general view. If I want to move on image processing, like you say I'll have a lot more things to read.

No OpenCV is very advanced, it just depends on what you want to do.

It looks like OpenCV does have object detection.

[http://opencv.willowgarage.com/documentation/cpp/imgproc_object_detection.html](http://opencv.willowgarage.com/documentation/cpp/imgproc_object_detection.html)

[http://opencv.willowgarage.com/documentation/cpp/objdetect__object_detection.html](http://opencv.willowgarage.com/documentation/cpp/objdetect__object_detection.html)

---

### Post by Sub101 on 2011-01-09
Might wana take a look here:

[http://www.openni.org/](http://www.openni.org/)

As I understand it, it is the open source release of the Kinect code.

---

### Post by tuxmanic on 2011-01-20
> It is for C++ but if you are a C developer im sure it will be an easy transition.Opencv is mostly written in C++  but it has got wrappers for C, C++, Python also for octave so C itself is enough for an opencv expedition..  


> Thanks. I know C++ a little actually, I can improve it. I'm starting reading from now. 
Is learning Opencv enough, or should I go further?     In my opinion its really easy to understand &  code with opencv , just look at the samples in the source directory.


> 
Might wana take a look here:

[http://www.openni.org/](http://www.openni.org/)

As I understand it, it is the open source release of the Kinect code.     am using [COLOR=Blue][libfreenect]("https://github.com/OpenKinect/libfreenect")[/COLOR] from [COLOR=Blue][openkinect.org]("http://openkinect.org/wiki/Main_Page")[/COLOR] for kinect hacking. libfreenect has got opencv wrappers , so things are really easy, also i think there is better community support with libfreenect than OpenNI 

Some kinect demos with libfreenect & opencv : [COLOR=Blue][http://www.flickr.com/photos/tuxmanic/sets/72157625654812145/](http://www.flickr.com/photos/tuxmanic/sets/72157625654812145/)[/COLOR]

---

