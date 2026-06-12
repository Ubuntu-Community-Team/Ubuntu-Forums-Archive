---
title: "Logitech C160 camera help"
date: 2011-08-15
forum: Programming Talk
---

### Post by TehDude on 2011-08-15
Hello, 
I've just a few days ago started working with Ubuntu 10.10. I had no previous experience with Linux OS.
I've installed Eclipse(downloaded the g++ compiler too) in order to do some c++ coding, and also downloaded and configured openCV for the Eclipse.
After I've ran and read some of the examples openCV provides, I've decided to try and write a simple code that would capture an image and and display it on a window. The code is:

```
# include "highgui.h"
# include "cvaux.h"
# include "cv.h"
# include <stdio.h>

int main()
{
        IplImage*       p_Image = NULL;
        CvCapture*      p_Cam = NULL;

        p_Cam = cvCaptureFromCAM(0);

        if( !p_Cam )
        {
            return 0;
        }

        p_Image = cvQueryFrame(p_Cam);
        if(!p_Image)
        {
            return 0;
        }
        cvNamedWindow("MyWIndow", 1);
        cvShowImage("BG", p_Image);
        cvReleaseCapture(&p_Cam);
        return 1;
}
```

it was built with no errors but when I ran it, it didn't show any window. So I debugged it and when it came to cvNamedWindow("MyWIndow", 1); it gave me an error: 
.gdbinit: No such file or directory.
Reading symbols from /home/dvirh/workspace/LineTracking/Debug/LineTracking...done.

Stopped due to shared library event
[Thread debugging using libthread_db enabled]
Stopped due to shared library event 
and then also a lot more of Stopped due to shared library event.

I find it weird because I did install the CDT and followed the instruction how of what to include and where.

Then I copied the bgfg_segm example, it was built and ran well.
The example code is:
```
#include "cvaux.h"
#include "highgui.h"
#include <stdio.h>

//this is a sample for foreground detection functions
int main(int argc, char** argv)
{
    IplImage*       tmp_frame = NULL;
    CvCapture*      cap = NULL;
    bool update_bg_model = true;

    if( argc < 2 )
        cap = cvCaptureFromCAM(0);
    else
        cap = cvCaptureFromFile(argv[1]);
    
    if( !cap )
    {
        printf("can not open camera or video file\n");
        return -1;
    }
    
    tmp_frame = cvQueryFrame(cap);
    if(!tmp_frame)
    {
        printf("can not read data from the video source\n");
        return -1;
    }

    cvNamedWindow("BG", 1);
    cvNamedWindow("FG", 1);

    CvBGStatModel* bg_model = 0;
    
    for( int fr = 1;tmp_frame; tmp_frame = cvQueryFrame(cap), fr++ )
    {
        if(!bg_model)
        {
            //create BG model
            bg_model = cvCreateGaussianBGModel( tmp_frame );
            //bg_model = cvCreateFGDStatModel( temp );
            continue;
        }
        
        double t = (double)cvGetTickCount();
        cvUpdateBGStatModel( tmp_frame, bg_model, update_bg_model ? -1 : 0 );
        t = (double)cvGetTickCount() - t;
        printf( "%d. %.1f\n", fr, t/(cvGetTickFrequency()*1000.) );
        cvShowImage("BG", bg_model->background);
        cvShowImage("FG", bg_model->foreground);
        char k = cvWaitKey(5);
        if( k == 27 ) break;
        if( k == ' ' )
            update_bg_model = !update_bg_model;
    }


    cvReleaseBGStatModel( &bg_model );
    cvReleaseCapture(&cap);

    return 0;
}
```

So the example works, the camera works well, I checked using Cheese and I also checked using 
```
ls /dev/video*
``` and it showed my laptop camera and the logitech camera.

So can anyone please help me?(sorry for writing so much)

---

