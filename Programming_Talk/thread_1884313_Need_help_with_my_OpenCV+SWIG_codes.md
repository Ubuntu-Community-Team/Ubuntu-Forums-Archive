---
title: "Need help with my OpenCV+SWIG codes"
date: 2011-11-21
forum: Programming Talk
---

### Post by baldiehead on 2011-11-21
I am trying to write a simple image viewer in C++ using OpenCV, then use SWIG to build wrappers to change it to Java. However, after compiling and everything, Java is giving me this error:** java: symbol lookup error: /home/baldie/Documents/SWIG5(Experimental)/libDisplayImageClass.so: undefined symbol: cvLoadImage**. I have already tried importing all the OpenCV libraries, but doesn't seem to work. 

Here are the codes and makefile. Thanks in advance, it's a long and hefty question. :popcorn:

DisplayImage.cpp:
```
#include "cv.h" //main OpenCV header
#include "highgui.h" //GUI header
#include "DisplayImageClass.h"

int initiate_display()
{
    IplImage* img = cvLoadImage( "Viva.jpg" );
    cvNamedWindow( "Viva La Vida", CV_WINDOW_AUTOSIZE );
    cvShowImage("Viva La Vida", img);
    cvWaitKey(0);
    cvReleaseImage( &img );
    cvDestroyWindow( "Viva La Vida" );
    return 0;
};

```DisplayImageClass.cpp:
```
#ifndef DisplayImageClass
#define DisplayImageClass

#include "DisplayImage.cpp" // Include the main C/C++ program
#include "DisplayImageClass.h"
#include "highgui.h"
#include "cv.h"

void Display::do_display() {
initiate_display(); // Calls the function "initiate_capture()" in main_capture.cpp
}

#endif
```DisplayImageClass.h:
```
#ifndef DISPLAYIMAGECLASS_H
#define DISPLAYIMAGECLASS_H

class Display {
public:
void do_display();
};

#endif
```DisplayImageClass.i:
```
%module DisplayImageClass
%{
#include "DisplayImageClass.h"
%}

%Display::do_display();

%include "DisplayImageClass.h"
```Makefile:
```
CC = g++

all:     cpp java

cpp:
    swig -java -c++ DisplayImageClass.i 
    
    
    g++ -fpic -c DisplayImageClass.cpp \
        -I/home/baldie/Downloads/OpenCV-2.3.1/include/opencv

    g++ -fpic -c DisplayImageClass_wrap.cxx \
        -I/usr/lib/jvm/java-6-openjdk/include/ 

    g++ -shared DisplayImageClass.o DisplayImageClass_wrap.o -o libDisplayImageClass.so 

java:
    javac *.java 

clear:
    @echo "Deleting excess files"
    rm -rf DisplayImageClass.o libDisplayImageClass.so DisplayImageClass_wrap.o DisplayImageClass.java DisplayImageClassJNI.java DisplayImageClass_wrap.cxx *.class SWIGTYPE_p_p_char.java

    echo "Done Deleting"
```DisplayTest.java:
```
public class DisplayTest {

DisplayTest() {
System.load("/home/baldie/Documents/SWIG5(Experimental)/libDisplayImageClass.so");
System.load("/home/baldie/Downloads/OpenCV-2.3.1/build/lib/libopencv_highgui.so.2.3.1");
System.load("/home/baldie/Downloads/OpenCV-2.3.1/build/lib/libopencv_video.so.2.3.1");
System.load("/home/baldie/Downloads/OpenCV-2.3.1/build/lib/libopencv_ts.so.2.3.1");
System.load("/home/baldie/Downloads/OpenCV-2.3.1/build/lib/libopencv_objdetect.so.2.3.1");
System.load("/home/baldie/Downloads/OpenCV-2.3.1/build/lib/libopencv_ml.so.2.3.1");
System.load("/home/baldie/Downloads/OpenCV-2.3.1/build/lib/libopencv_legacy.so.2.3.1");
System.load("/home/baldie/Downloads/OpenCV-2.3.1/build/lib/libopencv_imgproc.so.2.3.1");
System.load("/home/baldie/Downloads/OpenCV-2.3.1/build/lib/libopencv_gpu.so.2.3.1");
System.load("/home/baldie/Downloads/OpenCV-2.3.1/build/lib/libopencv_flann.so.2.3.1");
System.load("/home/baldie/Downloads/OpenCV-2.3.1/build/lib/libopencv_features2d.so.2.3.1");
System.load("/home/baldie/Downloads/OpenCV-2.3.1/build/lib/libopencv_core.so.2.3.1");
System.load("/home/baldie/Downloads/OpenCV-2.3.1/build/lib/libopencv_contrib.so.2.3.1");
System.load("/home/baldie/Downloads/OpenCV-2.3.1/build/lib/libopencv_calib3d.so.2.3.1");
}

public void doDisplay() {
Display disp = new Display();
disp.do_display();
}

public static void main(String args[]) {
DisplayTest dt = new DisplayTest();
dt.doDisplay();
}
}
```

---

### Post by 11jmb on 2011-11-21
OK, I have a few questions for you to help clarify your problem.

where, exactly, is this error occurring? at compile time or runtime?

Is there a specific reason that you are using swig and not jni?


From looking at your code, I'm not sure that you are calling the libraries correctly. you will want to use System.loadlibrary("($path)/DisplayImageClass")

Check out the simple tutorial on Java/SWIG if you have not yet:

[http://www.swig.org/tutorial.html](http://www.swig.org/tutorial.html)


There should be no need to load the opencv libraries in your java code, those will be handled by your c++ objects

---

### Post by baldiehead on 2011-11-21
Thanks for replying. Free cookie! **( :: )** But here are the replies to the questions.......

Question 1: It's happening at runtime, after you use the makefile and everything's compiled and stuff. When you try to run DisplayTest.java, it will give that error. (I just tried it again, same error.)

Question 2: I am kinda working on my mentor's instructions, to make a program using SWIG and OpenCV. (Despite the availability of JavaCV and stuff like that.)

Question 3:I tried to call the library with your suggestion.
```
public class DisplayTest {

DisplayTest() {
System.loadlibrary("DisplayImageClass");
}

public void doDisplay() {
Display disp = new Display();
disp.do_display();
}

public static void main(String args[]) {
DisplayTest dt = new DisplayTest();
dt.doDisplay();
}
}
```Sigh. Same error pops up again, after recompiling everything.

Question 4: Yes, I have looked thru the tutorials and documentation on the SWIG website, but didn't see anything that helps.

If it helps, all my files are in the same directory, compiled and placed in the same directory again. And my project is more or less a modification of this tutorial: [HTML]http://mathiasirwans.blogspot.com/2008/04/idiots-way-of-wrapping-cc-opencv-code.html[/HTML] And i removed the whole stack of OpenCV libraries, they were not doing much good anyway.

---

### Post by baldiehead on 2011-11-21
OK, turns out my code was slightly wrong, the library is System.loadLibrary. Ok, now the error has disappeared, only to be replaced by a new one......

```
Exception in thread "main" java.lang.UnsatisfiedLinkError: DisplayImageClassJNI.new_Display()J
    at DisplayImageClassJNI.new_Display(Native Method)
    at Display.<init>(Display.java:42)
    at DisplayTest.doDisplay(DisplayTest.java:8)
    at DisplayTest.main(DisplayTest.java:14)
make: *** [java] Error 1

```

Oh. My. God. This is a real headache.

---

### Post by baldiehead on 2011-11-22
:( Solved the previous error, evidently you need to structure the thing into packages and import into the files, or there'll be a lot of linking problems. However, new error comes out now.```
java.lang.UnsatisfiedLinkError: no DisplayImageClass in java.library.path
``` How do you export the library (libDisplayImageClass.so) into java.library.path?

---

### Post by baldiehead on 2011-11-22
Oh god, solved the library problem, now got the initial problem again. I cleaned up my codes a bit, hopefully it helps. I'll repost it.

DisplayImage.cpp
```
#include "cv.h" //main OpenCV header
#include "highgui.h" //GUI header
#include "DisplayImageClass.h"

using namespace std;

int Display::initiate_display()
{
    IplImage* img = cvLoadImage( "Viva.jpg" );
    cvNamedWindow( "Viva La Vida", CV_WINDOW_AUTOSIZE );
    cvShowImage("Viva La Vida", img);
    cvWaitKey(0);
    cvReleaseImage( &img );
    cvDestroyWindow( "Viva La Vida" );
    return 0;
};

```

DisplayImageClass:
```
#ifndef DisplayImageClass
#define DisplayImageClass


#include "DisplayImage.cpp" // Include the main C/C++ program
#include "DisplayImageClass.h"
#include "highgui.h"
#include "cv.h"

using namespace std;

void Display::do_display() {
initiate_display(); // Calls the function "initiate_capture()" in main_capture.cpp
}

#endif
```

DisplayImageClass.h
```
#ifndef DISPLAYIMAGECLASS_H
#define DISPLAYIMAGECLASS_H

class Display 
{
public:
    void do_display();
    int initiate_display();
};

#endif
```

DisplayImageClass.i
```
%module DisplayImageClass;

%{
#include "DisplayImageClass.h"
%}

%include "DisplayImageClass.h"
```

Makefile:
```
CC = g++

all:     cpp java

cpp:
    swig -java -c++ -package com.mySwig -outdir com/mySwig DisplayImageClass.i 
    
    
    g++ -fpic -c DisplayImageClass.cpp -I/home/baldie/Downloads/OpenCV-2.3.1/include/opencv -I/usr/lib/jvm/java-6-openjdk/include/ -L/usr/lib/pkgconfig -L/home/baldie/Downloads/OpenCV-2.3.1/include/opencv

    g++ -fpic -c DisplayImageClass_wrap.cxx -I/usr/lib/jvm/java-6-openjdk/include/ -I/home/baldie/Downloads/OpenCV-2.3.1/include/opencv -L/usr/lib/pkgconfig -L/home/baldie/Downloads/OpenCV-2.3.1/include/opencv

    g++ -shared DisplayImageClass.o DisplayImageClass_wrap.o -I/usr/local/pkgconfig -I/usr/lib/jvm/java-6-openjdk/include/ -L/usr/lib/pkgconfig -L/home/baldie/Downloads/OpenCV-2.3.1/include/opencv -I/home/baldie/Downloads/OpenCV-2.3.1/include/opencv -o libDisplayImageClass.so

java:
    javac com/mySwig/*.java 
    javac com/myMain/*.java
    java com.myMain.DisplayTest
    

clear:
    @echo "Deleting excess files"
    rm -rf DisplayImageClass.o libDisplayImageClass.so DisplayImageClass_wrap.o DisplayImageClass.java DisplayImageClassJNI.java DisplayImageClass_wrap.cxx *.class SWIGTYPE_p_p_char.java Display.java

    echo "Done Deleting"
```

DisplayTest.java
```
package com.myMain;

import com.mySwig.Display;

public class DisplayTest {
    DisplayTest() {    
        try{    
            System.loadLibrary("DisplayImageClass");
        }
            catch (UnsatisfiedLinkError e) {
                  System.err.println("Native code library failed to load. See the chapter on Dynamic Linking Problems in the SWIG Java documentation for help.\n" + e);
                  System.exit(1);
            }
        }

    
    public void doDisplay() {
        Display disp = new Display();
        disp.do_display();
    }

    public static void main(String args[]) {
        DisplayTest dt = new DisplayTest();
        dt.doDisplay();
    }
}
```

---

### Post by baldiehead on 2011-11-22
Finally got it. The error was with the compiling,you needed to include the PKG_CONFIG files inside, like what it says here: [http://opencv.willowgarage.com/wiki/CompileOpenCVUsingLinux](http://opencv.willowgarage.com/wiki/CompileOpenCVUsingLinux)

The correct makefile in my case is this:```
CC = g++

all:     cpp java

cpp:
    swig -java -c++ -package com.mySwig -outdir com/mySwig DisplayImageClass.i 
    
    
    g++  -fpic -c DisplayImageClass.cpp `pkg-config --cflags --libs opencv` -I/home/baldie/Downloads/OpenCV-2.3.1/include/opencv -I/usr/lib/jvm/java-6-openjdk/include/ -L/usr/lib/pkgconfig -L/home/baldie/Downloads/OpenCV-2.3.1/include/opencv

    g++ -fpic -c DisplayImageClass_wrap.cxx `pkg-config --cflags --libs opencv` -I/usr/lib/jvm/java-6-openjdk/include/ -I/home/baldie/Downloads/OpenCV-2.3.1/include/opencv -L/usr/lib/pkgconfig -L/home/baldie/Downloads/OpenCV-2.3.1/include/opencv

    g++ -shared DisplayImageClass.o DisplayImageClass_wrap.o -I/usr/local/pkgconfig -I/usr/lib/jvm/java-6-openjdk/include/ -L/usr/lib/pkgconfig -L/home/baldie/Downloads/OpenCV-2.3.1/include/opencv -I/home/baldie/Downloads/OpenCV-2.3.1/include/opencv `pkg-config --cflags --libs opencv` -o libDisplayImageClass.so

java:
    javac com/mySwig/*.java 
    javac com/myMain/*.java
    java com.myMain.DisplayTest
    

clear:
    @echo "Deleting excess files"
    rm -rf DisplayImageClass.o libDisplayImageClass.so DisplayImageClass_wrap.o DisplayImageClass.java DisplayImageClassJNI.java DisplayImageClass_wrap.cxx *.class SWIGTYPE_p_p_char.java Display.java

    echo "Done Deleting"
```

THANKS 11jmb for tolerating my crappy codes and helping me. FREE POPCORN! :popcorn:

---

### Post by 11jmb on 2011-11-22
Glad you got it working on your own, and sorry that work/timezones got in the way of me being more helpful. 

As a follow-up to your answer to my second question, swig will allow you to port your C++ code to many other languages with a bit of fine-tuning, whereas JNI is obviously just for java. So JNI would probably have been easier for porting directly to java, but you now have the ability to use opencv wrappers for just about any language.

---

