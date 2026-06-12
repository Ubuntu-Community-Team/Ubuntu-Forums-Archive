---
title: "Ubuntu 12.04 64 bit gcc linking problem with static openCV libraries"
date: 2014-01-17
forum: Programming Talk
---

### Post by erotavlas on 2014-01-17
Hi,

I'm trying to compile my code in static way. I know that gcc is able to do that with the flag -static and that the only thing that I need is the static version of all the library (.a). I installed openCV following the official guide of Ubuntu [https://help.ubuntu.com/community/OpenCV](https://help.ubuntu.com/community/OpenCV) and I installed the latest available version of openCV 2.4.8. The only thing that I changed is the flag that enables static compilation -DBUILD_SHARED_LIBS=OFF.
Now I have problem about the compilation of my code. During the linking phase, the linker is not able to find some library even if the library are present in their paths.
My command is this
```

g++ -static file1.o file2.o -L/usr/local/lib -lopencv_highgui -lopencv_imgproc -lopencv_core -L/usr/lib/x86_64-linux-gnu/ -lavformat -lavcodec -lswscale -lavutil -lavdevice  -pthread -lz  -o executable

```
The message that I receive from the linker is very long, I reported only the first error:
```

/usr/local/lib/libopencv_
highgui.a(cap_ffmpeg.cpp.o): In function `InternalFFMpegRegister::~InternalFFMpegRegister()':
cap_ffmpeg.cpp:(.text._ZN22InternalFFMpegRegisterD2Ev[_ZN22InternalFFMpegRegisterD5Ev]+0xa): undefined reference to `av_lockmgr_register'
/usr/local/lib/libopencv_highgui.a(cap_ffmpeg.cpp.o): In function `CvCapture_FFMPEG::init()':
cap_ffmpeg.cpp:(.text._ZN16CvCapture_FFMPEG4initEv+0x124): undefined reference to `av_init_packet'
/usr/local/lib/libopencv_highgui.a(cap_ffmpeg.cpp.o): In function `CvCapture_FFMPEG::close()':
cap_ffmpeg.cpp:(.text._ZN16CvCapture_FFMPEG5closeEv+0x11): undefined reference to `sws_freeContext'
cap_ffmpeg.cpp:(.text._ZN16CvCapture_FFMPEG5closeEv+0x2a): undefined reference to `av_free'
cap_ffmpeg.cpp:(.text._ZN16CvCapture_FFMPEG5closeEv+0x3c): undefined reference to `avcodec_close'
cap_ffmpeg.cpp:(.text._ZN16CvCapture_FFMPEG5closeEv+0x51): undefined reference to `av_close_input_file'
cap_ffmpeg.cpp:(.text._ZN16CvCapture_FFMPEG5closeEv+0x84): undefined reference to `av_free_packet'
/usr/local/lib/libopencv_highgui.a(cap_ffmpeg.cpp.o): In function `CvCapture_FFMPEG::open(char const*)':
cap_ffmpeg.cpp:(.text._ZN16CvCapture_FFMPEG4openEPKc+0x24): undefined reference to `avformat_open_input'
cap_ffmpeg.cpp:(.text._ZN16CvCapture_FFMPEG4openEPKc+0x37): undefined reference to `avformat_find_stream_info'
cap_ffmpeg.cpp:(.text._ZN16CvCapture_FFMPEG4openEPKc+0xdf): undefined reference to `avcodec_find_decoder'
cap_ffmpeg.cpp:(.text._ZN16CvCapture_FFMPEG4openEPKc+0xf1): undefined reference to `avcodec_open2'
cap_ffmpeg.cpp:(.text._ZN16CvCapture_FFMPEG4openEPKc+0x12e): undefined reference to `avcodec_alloc_frame'
cap_ffmpeg.cpp:(.text._ZN16CvCapture_FFMPEG4openEPKc+0x143): undefined reference to `avpicture_get_size'
cap_ffmpeg.cpp:(.text._ZN16CvCapture_FFMPEG4openEPKc+0x169): undefined reference to `avpicture_fill'

```
It is an error related to ffmpeg the linker cannot localize the libraries. I installed ffmpeg following the guide of openCV, it is installed from package.deb. The static library are provided by the process of installation of openCV: they are taken from the tar file of the project under the folder 3rdparty.
I think that the problem is the order in which I pass the libraries to the linker but I'm not able to figure out where is the problem. In particular I verified in the file pkg_config/opencv.pc that the order of the library of openCV is correct.

Any suggestions?

P.S. If I remove the flag -static from gcc command and I compile openCV in shared way all works well.

---

### Post by erotavlas on 2014-01-18
Hi,

to exclude the possibility of more complex behaviour of gcc, I have taken the example from the website of Ubuntu [https://help.ubuntu.com/community/OpenCV](https://help.ubuntu.com/community/OpenCV). 
```

#include<opencv2/highgui/highgui.hpp>
int main()
{
    IplImage* img = cvLoadImage("/home/USER/Pictures/python.jpg",CV_LOAD_IMAGE_COLOR);
    cvNamedWindow("opencvtest",CV_WINDOW_AUTOSIZE);
    cvShowImage("opencvtest",img);
    cvWaitKey(0);
    cvReleaseImage(&img);
    return 0;
}

```

Then I have compiled it with g++ -static example.cpp -L/usr/local/lib -lopencv_highgui -lopencv_imgproc -lopencv_core -o example and I got the following message
```

/usr/local/lib//libopencv_highgui.a(window_QT.cpp.o): In function `GuiReceiver::~GuiReceiver()':
window_QT.cpp:(.text._ZN11GuiReceiverD2Ev+0x49): undefined reference to `QObject::~QObject()'
window_QT.cpp:(.text._ZN11GuiReceiverD2Ev+0x3e): undefined reference to `QObject::~QObject()'
/usr/local/lib//libopencv_highgui.a(window_QT.cpp.o): In function `CvWinModel::~CvWinModel()':
window_QT.cpp:(.text._ZN10CvWinModelD2Ev[_ZN10CvWinModelD5Ev]+0x19): undefined reference to `QWidget::~QWidget()'
/usr/local/lib//libopencv_highgui.a(window_QT.cpp.o): In function `CvWinModel::~CvWinModel()':
window_QT.cpp:(.text._ZN10CvWinModelD0Ev[_ZN10CvWinModelD0Ev]+0x1d): undefined reference to `QWidget::~QWidget()'
/usr/local/lib//libopencv_highgui.a(window_QT.cpp.o): In function `OpenGlViewPort::sizeHint() const':
window_QT.cpp:(.text._ZNK14OpenGlViewPort8sizeHintEv+0x21): undefined reference to `QWidget::sizeHint() const'
/usr/local/lib//libopencv_highgui.a(window_QT.cpp.o): In function `CvWindow::keyPressEvent(QKeyEvent*)':
window_QT.cpp:(.text._ZN8CvWindow13keyPressEventEP9QKeyEvent+0x14): undefined reference to `QTest::keyToAscii(Qt::Key)'
window_QT.cpp:(.text._ZN8CvWindow13keyPressEventEP9QKeyEvent+0x27): undefined reference to `QKeyEvent::modifiers() const'
window_QT.cpp:(.text._ZN8CvWindow13keyPressEventEP9QKeyEvent+0x3f): undefined reference to `QMutex::lock()'
window_QT.cpp:(.text._ZN8CvWindow13keyPressEventEP9QKeyEvent+0x4e): undefined reference to `QMutex::unlock()'
window_QT.cpp:(.text._ZN8CvWindow13keyPressEventEP9QKeyEvent+0x5a): undefined reference to `QWaitCondition::wakeAll()'
window_QT.cpp:(.text._ZN8CvWindow13keyPressEventEP9QKeyEvent+0x65): undefined reference to `QWidget::keyPressEvent(QKeyEvent*)'
window_QT.cpp:(.text._ZN8CvWindow13keyPressEventEP9QKeyEvent+0x7c): undefined reference to `QKeyEvent::nativeVirtualKey() const'
/usr/local/lib//libopencv_highgui.a(window_QT.cpp.o): In function `OpenGlViewPort::setSize(QSize)':
window_QT.cpp:(.text._ZN14OpenGlViewPort7setSizeE5QSize+0x5): undefined reference to `QWidget::updateGeometry()'
/usr/local/lib//libopencv_highgui.a(window_QT.cpp.o): In function `OpenGlViewPort::~OpenGlViewPort()':
window_QT.cpp:(.text._ZN14OpenGlViewPortD2Ev+0x28): undefined reference to `QGLWidget::~QGLWidget()'
/usr/local/lib//libopencv_highgui.a(window_QT.cpp.o): In function `OpenGlViewPort::makeCurrentOpenGlContext()':
window_QT.cpp:(.text._ZN14OpenGlViewPort24makeCurrentOpenGlContextEv+0x1): undefined reference to `QGLWidget::makeCurrent()'
/usr/local/lib//libopencv_highgui.a(window_QT.cpp.o): In function `OpenGlViewPort::updateGl()':
window_QT.cpp:(.text._ZN14OpenGlViewPort8updateGlEv+0x1): undefined reference to `QGLWidget::updateGL()'

```

Also in this case, I think that the problem is the order in which I pass the libraries to the linker but I'm not able to figure out where is the problem. 

Any suggestions?

P.S.
It works in case of shared compilation.

---

### Post by steeldriver on 2014-01-18
Have you tried using pkg-config?

```

g++ -o example example.cpp `pkg-config --static --cflags --libs opencv`

```

---

### Post by erotavlas on 2014-01-18
> **steeldriver said:**
> Have you tried using pkg-config?

```

g++ -o example example.cpp `pkg-config --static --cflags --libs opencv`

```

Great! This works!!! If I have understood well how pkg-config works, I should have to pass all the content of the file opencv.pc to the linker and not only some libraries.
Thank you very much!

---

### Post by steeldriver on 2014-01-18
AFAIK the --static option just tells pkg-config to try to output linker directives suitable for static linking - so it relies on the opencv package maintainers creating a suitable .pc file

```

       --static
              Output  libraries  suitable  for  static  linking.   That  means
              including any private libraries in the output.  This  relies  on
              proper  tagging  in  the  .pc  files, else a too large number of
              libraries will ordinarily be output.

```

You may still need to add the -static gcc compile flag to force *other* libraries to be linked statically - however when I tried that with your example.cpp file it couldn't find a static libbz2

```

$ g++ -static -o example example.cpp `pkg-config --static --cflags --libs opencv`
/usr/bin/ld: attempted static link of dynamic object `/usr/lib/i386-linux-gnu/libbz2.so'
collect2: ld returned 1 exit status

```

I guess it depends whether you want a *completely* statically linked executable, or just one that statically links the OpenCV libs

BTW you can see exactly what pkg-config is generating by running it on the command line without the backticks e.g.

```

$ pkg-config --static --libs opencv

```

---

### Post by erotavlas on 2014-01-19
You are right this is the output code of pkg-config:
```

g++ example.cpp -I/usr/local/include/opencv -I/usr/local/include  /usr/local/lib/libopencv_contrib.a /usr/local/lib/libopencv_stitching.a /usr/local/lib/libopencv_nonfree.a /usr/local/lib/libopencv_superres.a /usr/local/lib/libopencv_ocl.a /usr/local/lib/libopencv_ts.a /usr/local/lib/libopencv_videostab.a /usr/local/lib/libopencv_gpu.a /usr/local/lib/libopencv_photo.a /usr/local/lib/libopencv_objdetect.a /usr/local/lib/libopencv_legacy.a /usr/local/lib/libopencv_video.a /usr/local/lib/libopencv_ml.a /usr/local/lib/libopencv_calib3d.a /usr/local/lib/libopencv_features2d.a /usr/local/lib/libopencv_highgui.a /usr/local/share/OpenCV/3rdparty/lib/liblibjasper.a /usr/local/share/OpenCV/3rdparty/lib/liblibpng.a /usr/local/share/OpenCV/3rdparty/lib/liblibjpeg.a /usr/local/lib/libopencv_imgproc.a /usr/local/lib/libopencv_flann.a /usr/local/lib/libopencv_core.a /usr/local/share/OpenCV/3rdparty/lib/libzlib.a /usr/lib/x86_64-linux-gnu/libQtCore.so /usr/lib/x86_64-linux-gnu/libQtTest.so /usr/lib/x86_64-linux-gnu/libQtGui.so /usr/lib/x86_64-linux-gnu/libQtOpenGL.so /usr/lib/libIlmThread.so /usr/lib/libHalf.so /usr/lib/libIex.so /usr/lib/libIlmImf.so /usr/lib/libImath.so /usr/lib/x86_64-linux-gnu/libtiff.so /usr/lib/x86_64-linux-gnu/libXext.so /usr/lib/x86_64-linux-gnu/libX11.so /usr/lib/x86_64-linux-gnu/libICE.so /usr/lib/x86_64-linux-gnu/libSM.so /usr/lib/x86_64-linux-gnu/libGL.so /usr/lib/x86_64-linux-gnu/libGLU.so -lswscale -lavutil -lavformat -lavcodec -lv4l1 -ldc1394 -lgstvideo-0.10 -lgstapp-0.10 -lglib-2.0 -lxml2 -lgthread-2.0 -lgmodule-2.0 -lgobject-2.0 -lgstreamer-0.10 -lgstbase-0.10 -ltbb -lrt -lpthread -lm -ldl -lstdc++   -o example

```
As you said, if I compile completely static I receive the following error message
```

 g++ -static -o prova prova.cpp $(pkg-config --static --cflags --libs opencv)
/usr/bin/ld: attempted static link of dynamic object `/usr/lib/x86_64-linux-gnu/libQtCore.so'
collect2: error: ld returned 1 exit status

```
I cannot find static version of libQtCore.so. Do you know a package that contains it? For all the other libraries listed in the output of pkg-config command, I have found a package that contains static version.

---

