---
title: "OpenCV Sobel edge detection"
date: 2010-04-29
forum: Programming Talk
---

### Post by mcweaver1 on 2010-04-29
Hello everyone,

I'm currently writing a C++ program to find the edges in an image using the OpenCV function cvSobel.  However, I've come across an error that I can't seem to find the solution of... 

```

IplImage * imageL = cvLoadImage("image1.pgm");

IplImage * Gx = cvCreateImage(cvGetSize(imageL),IPL_DEPTH_16S,1);

cvSobel(imageL, Gx, 1, 0, 3); //this line is failing

```

I have seen that the destination image Gx needs to be IPL_DEPTH_16S otherwise it causes the exact error I'm getting; however I'm pretty sure that I *have* set Gx to be IPL_DEPTH_16S (unless the second line is wrong....?).

Here is the error:

```

OpenCV Error: Assertion failed (src.size() == dst.size() && src.channels() == dst.channels() && ((src.depth() == CV_8U && (dst.depth() == CV_16S || dst.depth() == CV_32F)) || (src.depth() == CV_32F && dst.depth() == CV_32F))) in cvSobel, file /home/melissa/opencv/src/cv/cvderiv.cpp, line 347
terminate called after throwing an instance of 'cv::Exception'
  what():  /home/melissa/opencv/src/cv/cvderiv.cpp:347: error: (-215) src.size() == dst.size() && src.channels() == dst.channels() && ((src.depth() == CV_8U && (dst.depth() == CV_16S || dst.depth() == CV_32F)) || (src.depth() == CV_32F && dst.depth() == CV_32F)) in function cvSobel

```

Looking this up online the only reason people seem to have had this error is because the destination image wasn't IPL_DEPTH_16S.  

Can anyone spot my stupidity?  Would be much appreciated :)

---

### Post by mcweaver1 on 2010-04-29
AHA, I have worked out what the problem is.  For future reference, I had to convert the input image to greyscale (even though it looked like it was in b&w anyway).

---

