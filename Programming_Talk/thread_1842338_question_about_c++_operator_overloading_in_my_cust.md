---
title: "question about c++ operator overloading in my custom class"
date: 2011-09-11
forum: Programming Talk
---

### Post by Hetepeperfan on 2011-09-11
Hello Community,

Would anyone of you be so kind to help me out with the following program. I have got a C++ question to ask. The program I'm showing you is a custom build C++ wrapper for capturing video or camera frames with my custom build capture class. I am aware of the fact that openCV has a adequate C++ interface, however I want to improve my C++ therefore I've build a start to my own capture class using the C API of openCV. The program I'm about to show you consist of two files: main.cpp and capture.hpp.

So what I'm trying to do is overload the >> operator for class capture. openCV has an other C structure IplImage. which is usually used as a pointer. Thus a CvCapture* is a C representation of a video stream and IplImage* points to one video frame in that stream. In C one gets one frame from the stream by the next pseudo code so assume we've properly opened the cap:

```
CvCapture *cap
IplImage* img = cvQueryFrame( cap )

```then img = 0x12345678
and img->imageData = some other non NULL pointer

img->imageData points to the pixels of one frame or picture.j

However this is where it goes wrong in my code inside the capture:: operator >> ( Iplmage*& img) img->imageData points to a valid adress but the img->imageData  in main.cpp is NULL.

therefore I've made a other memberfunction:
ImlImage* capture::getImage(void)
 which just returns a pointer and that one works like a charm then the resulting pointer in main.cpp is a valid IplImage with a valid img->imageData pointer which actually points to the image.

So below the are the two files which I'm using. Would some one please explain to me why the function with the overloaded >> doesn't operate like I want to, but the getImage function works exactly like I intend to.

kind regards Maarten

capture.hpp:

```
#ifndef MYCAP
#define MYCAP

#include<cv.h>
#include<highgui.h>
#include<string>
#include<exception>


namespace mycv{

    class mycv_exception : public std::exception{
        std::string msg;
        public:
        virtual const char* what() const throw()
        {
            return msg.c_str();
        }
        mycv_exception (std::string what)
        {
            msg = what;
        }
        mycv_exception ( const char* what)
        {
            msg = std::string (what);
        }
        ~mycv_exception(void) throw()
        {
        }
    };

    class capture{
        CvCapture* cap;
        public:
        IplImage* image;

        public:
        capture(int n)
        {
            cap = cvCaptureFromCAM( n );
            if ( ! cap )
            {
                int err = cvGetErrMode();
                std::string cv_msg = "OpenCV reports: " + std::string( cvErrorStr(err)) +"\n" ;
                std::string msg = "coulnd't open capture from camera\n";
                throw mycv_exception( msg + cv_msg );
            }
        }
        capture ( std::string file )
        {
            cap = cvCaptureFromFile( file.c_str() );
            if ( ! cap )
                throw mycv_exception ("Couldn't open videofile: "+file+'\n');

        }
        ~capture(void)
        {
            if (cap != 0x0){
                cvReleaseCapture(&cap);
            }
        }

        capture operator >> ( IplImage*& im) /*const*/ throw (mycv_exception)
        {
            IplImage* temp = cvQueryFrame(this->cap);
            im = temp;
            //std::cout << "im = "<< im << "It's data = " << (void*) im->imageData <<std::endl;
            if (im == NULL){
                throw mycv_exception( "couldn't query frame\n " );
            }
            return *this;
        }
        IplImage* getImage (void) throw (mycv_exception)
        {
            image = cvQueryFrame(cap);
            if ( image == NULL){
                throw mycv_exception ( "Couldn't get image" );
            }
            else 
                return image;
        }
        int width(void)
        {
            int width;
            width = (int) cvGetCaptureProperty(cap,CV_CAP_PROP_FRAME_WIDTH);
            return width;
        }
        int height(void)
        {
            int height;
            height= (int) cvGetCaptureProperty(cap,CV_CAP_PROP_FRAME_HEIGHT);
            return height;
        }
    };
}

#endif //MYCAP
```and capture.hpp

```
#include<iostream>
#include<string>

#include "capture.hpp"

using namespace std;


int main( int argc, char**argv)
{
    int nth_cam = -1;
    if ( argc != 2){
        cerr << "Please provide the filename of a video." << endl;
        return 0;
    }
    string fname (argv[1]);
    sscanf( argv[1],"%d", &nth_cam);

    try{
        mycv::capture cap(fname);

        const char* win = "win";
        cvNamedWindow(win);

        cout << cap.width() << " " << cap.height() << endl;

        int haatend = 1;
        while ( haatend ){
            IplImage* im = 0;
            try{
                //im = cap.getImage();
                cap >> im;
                
                std::cout << "im = "<< im << "It's data = " << (void*) im->imageData <<std::endl;
            }
            catch(exception& e){
                cerr << e.what() << "Probably end of movie." << endl;
                break;
            }
            cvShowImage (win, im);
            cvWaitKey(1000/25);
        }
    }
    catch ( mycv::mycv_exception& e ){
        cout << e.what();
    }


    return 0;
}
```

---

### Post by dwhitney67 on 2011-09-11
The only issue I can see with your code is the declaration of the operator>>() method.  It should look like:
```

**capture&** operator >> ( IplImage*& im) /*const*/ throw (mycv_exception)
{
   ...
}

```
Note that the instance is returned by reference, instead of a copy of the instance.

Other than that, I cannot tell why it is failing.  I do not have openCV on my system, thus I created a fake interface and tried running something similar to your program; all went well.
```

#include <cassert>

typedef void* CvCapture;

struct IplImage
{
   IplImage() : imgData(0) {}

   char* imgData;
};

IplImage* cvQueryFrame(CvCapture* cap)
{
   IplImage* image = new IplImage;
   image->imgData = new char[1024];
   return image;
}

class Capture
{
public:
   Capture& operator>>(IplImage*& image)
   {
      image = cvQueryFrame(cap);
      return *this;
   }

private:
   CvCapture* cap;
};

int main()
{
   IplImage* image = 0;
   Capture   capture;

   capture >> image;

   assert(image != 0);
   assert(image->imgData != 0);
}

```

---

### Post by Hetepeperfan on 2011-09-11
Hello dwhitney67,

Thank you very much! I can see on my system that adding the & to the declaration of the function did the trick! So I can see, that adding the & makes the difference. however I fail to understand why since, we  put a reference/instance to the function as well. and the  IplImage* inside the function has a non NULL img->imageData inside  the function but back in main the pointer is NULL.

I suppose since we return *this we have to add the &.
( is this supposed to compile flawlessly with -Wall -pedantic? )



At least it works now so thank you.

---

### Post by dwhitney67 on 2011-09-11
> **Hetepeperfan said:**
> Hello dwhitney67,

Thank you very much! I can see on my system that adding the & to the declaration of the function did the trick! So I can see, that adding the & makes the difference. however I fail to understand why since,  put a reference/instance to the function as well. and the  IplImage* inside the function has a non NULL img->imageData inside  the function but back in main the pointer is NULL.

I suppose since we return *this we have to add the &.
( is this supposed to compile flawlessly with -Wall -pedantic? )



At least it works now so thank you.

Btw, unless you plan to do something like the following, there is no need to return anything from the operator>>() method.
```

cap >> image1 >> image2;

```
In other words, this might suffice for your needs:
```

class capture
{
   ...

   void operator>>(IplImage*& image) throw mycv_exception
   {
      image = cvQueryFrame(this->cap);

      if (image  == NULL)
      {
         throw mycv_exception("couldn't query frame\n");
      }
   }
};

```

---

### Post by Hetepeperfan on 2011-09-11
[QUOTE=
```

cap >> image1 >> image2;

```[/QUOTE]

I might want to do something link that. But as i understand you'll  need to return *this in order for the 2nd 3rd >> to work.

Thanks for your relies, it has been very helpfull.

---

