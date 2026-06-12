---
title: "Opencv take webcam snapshot problem!"
date: 2011-06-02
forum: Programming Talk
---

### Post by hakermania on 2011-06-02
That's the code, I have reading and writing permissions to the folder in which the executable is running.
I cannot figure out what I am doing wrongly.....

Please, see the code:
```

#include "opencv/cv.h"
#include "opencv/highgui.h"
#include <iostream>
using namespace std;
 int main() {
   CvCapture* capture = cvCaptureFromCAM( CV_CAP_ANY );
   if ( !capture ) {
     cerr << "Couldn't capture!\n";
     return 1;
   }
     // Get one frame
     IplImage* frame = cvQueryFrame( capture );
     if ( !frame ) {
        cerr << "Couldn't capture!\n";
        return 1;
     }
   cvReleaseCapture( &capture );
   cvSaveImage("test.jpg" ,frame);
   return 0;
 }
```I get:
```

[COLOR=#be1414][FONT=Monospace]OpenCV Error: Null pointer (The image has NULL data pointer) in cvGetMat, file /home/alex/OpenCV-2.1.0/src/cxcore/cxarray.cpp, line 2391[/FONT][/COLOR]
 [COLOR=#be1414][FONT=Monospace]terminate called after throwing an instance of 'cv::Exception'[/FONT][/COLOR]
 [COLOR=#be1414][FONT=Monospace]  what():  /home/alex/OpenCV-2.1.0/src/cxcore/cxarray.cpp:2391: error: (-27) The image has NULL data pointer in function cvGetMat[/FONT][/COLOR]
 
 [COLOR=#be1414][FONT=Monospace]The program has unexpectedly finished.[/FONT][/COLOR]


```

---

### Post by hakermania on 2011-06-03
its a bump

---

### Post by Petrolea on 2011-06-03
Error kind of explains it. NULL pointer means that there is nothing in it. And when you pass it to a function it throws an error (you're lucky that it doesn't just throw a seg fault, would be a lot harder to find out where the error is).

That means there is a part in your code when some pointer gets no value and is passed to a function. Maybe put some more ifs to check if pointers are empty. I would check but I don't know anything about OpenCV.

[PHP]
if(somepointer == NULL)
{
    printf("Error\n");
}
[/PHP]

---

### Post by hakermania on 2011-06-03
Yes OK, thx for the answer, I got it that there's something null over there, I know how to check it, but I don't know why I get this error, it's sure because of the cvSaveImage function, because exactly the same code running on a while(1) loop and displaying the 'frame' on a cvwindow runs perfectly...I just don't know where the error is actually...

---

### Post by hakermania on 2011-06-03
Ok, found the solution, just call saveimage before release :)

---

