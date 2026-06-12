---
title: "OpenCV 2.4.2 Netbean 7.2.1 on ubuntu problen"
date: 2012-10-25
forum: Programming Talk
---

### Post by raimuucka on 2012-10-25
Hi, 

I have used linux just for a bit. I have programmed on windows with VS C++ and OpenCV 2.0 and 2.4.1. In windows you have to include .h files depending on functions you use and in project settings in LINKER section you have to add files .lib. And to run the project you have to add .dll files next to .exe
I have decided to start programming on linux (ubuntu while I wait for my raspbery py). I googled a bit and found that NetBean is some way similar to VS. So I have chosen it as my development platform. 
I cant install build-essential, because I have Acer aspire one D250 ant is has no CDROM and if I try instaling build-essential it is asking for ubuntu instalation disk in CDROM and instalation flash does not work in this part. So I had hard work on instaling all needed compilers. I think I have compiled and installed OpenCV 2.4.2 corecctly. 
Tested neatbean with simple apllication and with sockets sammple. Works fine.
Now I'm trying to compile OpenCV test project, but is does not work. My code:
```

/* 
 * File:   main.cpp
 * Author: raimondas
 *
 * Created on October 24, 2012, 10:56 PM
 */
#include <opencv/cv.h>
#include <opencv/cxcore.h>
#include <opencv/highgui.h>
#include <stdio.h>


/*
 * 
 */

IplImage* kadras;
CvCapture* kamera;
char klavisas;


int main(int argc, char** argv) {
    kamera = cvCaptureFromCAM(0);
 
    // Couldn't get a device? Throw an error and quit
    if(!kamera)
    {
        printf("Could not initialize capturing...\n");
        return -1;
    }
    
    cvNamedWindow("Kameros vaizdas");
    while(1){
       kadras = cvQueryFrame(kamera); 
       cvShowImage("Kameros vaizdas", kadras);
       klavisas = cvWaitKey(10);
       if(klavisas == 27){
           break;
       }
      
    }

    cvReleaseCapture(&kamera);
    return 0;
}

```

But something is wrong, because I get this:
> 
"/usr/bin/make" -f nbproject/Makefile-Debug.mk QMAKE= SUBPROJECTS= .build-conf
make[1]: Entering directory `/home/raimondas/NetBeansProjects/OpenCV_test1'
"/usr/bin/make"  -f nbproject/Makefile-Debug.mk dist/Debug/GNU-Linux-x86/opencv_test1
make[2]: Entering directory `/home/raimondas/NetBeansProjects/OpenCV_test1'
mkdir -p dist/Debug/GNU-Linux-x86
g++     /usr/local/lib/libopencv_core.so /usr/local/lib/libopencv_highgui.so /usr/local/lib/libopencv_ts.so -o dist/Debug/GNU-Linux-x86/opencv_test1 build/Debug/GNU-Linux-x86/main.o -L/usr/local/include/opencv/ 
build/Debug/GNU-Linux-x86/main.o: In function `main':
/home/raimondas/NetBeansProjects/OpenCV_test1/main.cpp:27: undefined reference to `cvCreateCameraCapture'
/home/raimondas/NetBeansProjects/OpenCV_test1/main.cpp:36: undefined reference to `cvNamedWindow'
/home/raimondas/NetBeansProjects/OpenCV_test1/main.cpp:38: undefined reference to `cvQueryFrame'
/home/raimondas/NetBeansProjects/OpenCV_test1/main.cpp:39: undefined reference to `cvShowImage'
/home/raimondas/NetBeansProjects/OpenCV_test1/main.cpp:40: undefined reference to `cvWaitKey'
/home/raimondas/NetBeansProjects/OpenCV_test1/main.cpp:44: undefined reference to `cvReleaseCapture'
collect2: error: ld returned 1 exit status
make[2]: *** [dist/Debug/GNU-Linux-x86/opencv_test1] Error 1
make[2]: Leaving directory `/home/raimondas/NetBeansProjects/OpenCV_test1'
make[1]: *** [.build-conf] Error 2
make[1]: Leaving directory `/home/raimondas/NetBeansProjects/OpenCV_test1'
make: *** [.build-impl] Error 2


BUILD FAILED (exit value 2, total time: 891ms)


Can anyone help me to understand what I'm missing and what is wrong? Do I have to add something in to linker like on windows? Tryed adding /usr/local/lib/libopencv_core.so.2.4.2 and /usr/local/lib/libopencv_highgui.so.2.4.2 but I do not know where axacly add them, so maybe I did something wrong. Can anyone Help me? 
Thnx. :)

---

### Post by raimuucka on 2012-10-25
By the way I'm using ubuntu 12.10 :)

---

### Post by spjackson on 2012-10-25
> 
```

g++ /usr/local/lib/libopencv_core.so /usr/local/lib/libopencv_highgui.so /usr/local/lib/libopencv_ts.so -o dist/Debug/GNU-Linux-x86/opencv_test1 build/Debug/GNU-Linux-x86/main.o -L/usr/local/include/opencv/ 

```

This is wrong in a number of respects.

Where are the libraries? Are they in /usr/local/lib/ or /usr/local/include/opencv/ ? I assume that since you don't get a "file not found" error, they must be in /usr/local/lib/.

That -L/usr/local/include/opencv/ is pointless unless you list any libraries with -l<library-name>.

If you put the library before the object files that call functions in the library, then you will get sort of error you are seeing.

So it would probably be enough to move all the .so files to the end of the line. But better would be:

```

g++ -o dist/Debug/GNU-Linux-x86/opencv_test1 build/Debug/GNU-Linux-x86/main.o -L/usr/local/include/opencv/ -lopencv_core -lopencv_highgui -lopencv_ts

```

This assumes that the libraries are in the right order.

---

### Post by raimuucka on 2012-10-26
cv.h and other .h are in /usr/local/include/opencv/
libopencv_core.so.2.4.2 and others similar files are in /usr/local/lib/
I do not write all this in one line:
```
g++ /usr/local/lib/libopencv_core.so /usr/local/lib/libopencv_highgui.so /usr/local/lib/libopencv_ts.so -o dist/Debug/GNU-Linux-x86/opencv_test1 build/Debug/GNU-Linux-x86/main.o -L/usr/local/include/opencv/
```

I fill some lines in project properties like LINKER and all. So now I'm trying to figure out vat line in where makes needed order. And I have don it, thnx spjackson. :)
So I have managed to to make it like this:
```
g++     -o dist/Debug/GNU-Linux-x86/opencv_test1 build/Debug/GNU-Linux-x86/main.o -L/usr/local/lib -lopencv_highgui 
```
It built the project. Yes!!! :D
But I can't run the app correctly, I get:
```
Could not initialize capturing...

RUN FAILED (exit value 255, total time: 579ms)
```
This means linux cant see my netbooks integrated camera? Can I install it somehow? I have connected external camera Logitech C525 and do not  know if it is installed correctly, but skype can use bouth of them.
Or do I have to use memset() for opencv variables?
I have seen this function is used in samples but with char, int and similar, but didn't see any samples with opencv

---

### Post by raimuucka on 2012-10-26
this seams to be alot harder then I thought... :(

---

### Post by raimuucka on 2012-10-27
I can read and display .jpg image from hdd and to display it, but cant get image from camera... :( Whys is that?there is no error. Just when I lounch application I get this part:
```
printf("Could not initialize capturing...\n");
```
Can anyone say why is that?

---

