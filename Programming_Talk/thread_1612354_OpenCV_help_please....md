---
title: "OpenCV help please..."
date: 2010-11-03
forum: Programming Talk
---

### Post by -A- on 2010-11-03
I had asked this before, but got no reply...anyway...

How exactly do you access the individual channel elements using the IPL image structure in python? I mean, it doesn't have the widthStep or the imageData members right?

Also, are there any resources that can start you off on using OpenCV with Python?

Also, currently I'm using OpenCV on windows because when I built it from the source in ubuntu 10.04, whenever I import it says it cant find the module. Iread the installation wiki where they tell you to relocate the 'cv.so' file, but I can't find the cv.so file. I tried running a search in Nautilus but it didn't find it.

Any solutions please? It's really important. 

Thanks.

---

### Post by DanielWaterworth on 2010-11-03
[http://opencv.willowgarage.com/documentation/python/index.html](http://opencv.willowgarage.com/documentation/python/index.html)

A quick google search will help you find more information.

---

### Post by -A- on 2010-11-03
Thank you for replying. I've already seen those and from what I could fathom I can access the individual elements of a cvMat structure and so on, but I'm still confused. For example, teh small code snippet: 

```
void saturate_sv( IplImage* img ) {
for( int y=0; y<img->height; y++ ) {
uchar* ptr = (uchar*) (
img->imageData + y * img->widthStep
);
for( int x=0; x<img->width; x++ ) {
ptr[3*x+1] = 255;
ptr[3*x+2] = 255;
}
}
}
```

It just increases the saturation and value of each pixel to its max of 255. But how would I do the same using Python?

Thank you.

---

