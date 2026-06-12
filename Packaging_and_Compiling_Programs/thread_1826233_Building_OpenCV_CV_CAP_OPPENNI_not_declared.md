---
title: "Building OpenCV: CV_CAP_OPPENNI not declared"
date: 2011-08-16
forum: Packaging and Compiling Programs
---

### Post by jonim8or on 2011-08-16
I'm trying to compile OpenCV 2.3.0 on my Natty installation. I've already compiled it on my Lucid installation, and that worked fine out of the box. btw I'm compiling a patched version that uses the newest ffmpeg, which I also compiled myself. 

Now there are two main differences between my Natty system and my Lucid system:

On Natty I don't use /usr/local but a different directory as prefix dir for all my code. Therefore I also export the corresponding lib and pkgconfig paths before calling cmake and make.
On Natty I've installed boost 1.42, on Lucid 1.40 (in both cases the repository version) 


However, on Natty I get the following compile error:
```

/home/jonatan/Development/src/OpenCV-2.3.0/modules/highgui/src/cap.cpp: In function &#8216;CvCapture* cvCreateCameraCapture(int)&#8217;:
/home/jonatan/Development/src/OpenCV-2.3.0/modules/highgui/src/cap.cpp:130:9: error: &#8216;CV_CAP_OPENNI&#8217; was not declared in this scope
/home/jonatan/Development/src/OpenCV-2.3.0/modules/highgui/src/cap.cpp:131:9: error: &#8216;CV_CAP_ANDROID&#8217; was not declared in this scope

```

This is very strange, since the rest of the values of the enum to which these two values belong, are recognized correctly.

Googling the error only gave me sites of mac-users having the same problem, but didn't give a solution.

Any ideas for next step? (except for waiting for OpenCV 2.3.1 for linux)

---

