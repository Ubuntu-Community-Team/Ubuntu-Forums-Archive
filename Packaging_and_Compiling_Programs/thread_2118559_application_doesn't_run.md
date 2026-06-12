---
title: "application doesn't run"
date: 2013-02-21
forum: Packaging and Compiling Programs
---

### Post by oujeboland on 2013-02-21
hi , i'm new in opencv applications programming . i want to play a movie with a simple code(second excercise of bradski & kaehler book) , but the application doesn't play the movie and doesn't show any windows. everything seem to be good. no error exists . but i don't exactly know what happens?did i forget something?

---

### Post by melfnt on 2013-03-01
Can you post the code?

---

### Post by oujeboland on 2013-03-20
```
#include "highgui.h"

int main( int argc, char** argv )
{
    cvNamedWindow( "Example2", CV_WINDOW_AUTOSIZE );
    //CvCapture* capture = cvCaptureFromAVI( argv[1] ); // either one will work
    CvCapture* capture =
            cvCreateFileCapture( "/home/ubuntu12/workspace-opencv/excC/excC/Debug/test.avi" );
    IplImage* frame;
    while(1) {
        frame = cvQueryFrame( capture );
        if( !frame ) break;
        cvShowImage( "Example2", frame );
        char c = cvWaitKey(33);
        if( c == 27 ) break;
    }
    cvReleaseCapture( &capture );
    cvDestroyWindow( "Example2" );
    return 0;
}
```

---

### Post by melfnt on 2013-03-22
On my computer it runs flawlessly.
How do you compile?

I use:
```

g++ cv.cpp -o cv `pkg-config --libs --cflags opencv`

```

And execute with
```

./cv

```

Did you install the library?
Do you have any compilation error?

---

