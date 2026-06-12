---
title: "Problems with QtCreator"
date: 2012-05-20
forum: Programming Talk
---

### Post by Wedontplay on 2012-05-20
Hi, i just installed QtCreator to use it mainly with opencv.
I'm used to program opencv in Osx with Xcode and i have a couple of problems:

1)
When i launch QtCreator i have these error messages:

Cannot overwrite file /home/wedontplay/.config/Nokia/toolChains.xml: Permission denied

Cannot overwrite file /home/wedontplay/.config/Nokia/qtcreator/default.qws: Permission denied

Could not save session to file /home/wedontplay/.config/Nokia/qtcreator/default.qws

And after a while QtCreator just disappears and reappears.
Where do you think is the problem? It seems a permission problem but i can't figure out how to solve it as i'm new to ubuntu.
Also i don't see the Qt icon with the others in the dashboard.


2)
i can't figure the way to tell Qt where my libraries are, it locates correctly the header files but not the libraries, i'm using this:

```


#where the OpenCV header files are
INCLUDEPATH += /usr/local/include \



#where my libraries are
LIBS += -L/usr/local/lib \

    -lopencv_core.so.2.4.0 \
    -lopencv_highgui.so.2.4.0 \
    -lopencv_imgproc.so.2.4.0 \
    -lopencv_features2d.so.2.4.0 \
    -lopencv_calib3d.so.2.4.0 \
    -lopencv_contrib.so.2.4.0 \
    -lopencv_flann.so.2.4.0 \
    -lopencv_gpu.so.2.4.0 \
    -lopencv_legacy.so.2.4.0 \
    -lopencv_ml.so.2.4.0 \
    -lopencv_objdetect.so.2.4.0 \
    -lopencv_ts.so.2.4.0 \
    -lopencv_video.so.2.4.0



```

---

### Post by Zugzwang on 2012-05-21
> **Wedontplay said:**
> 
Cannot overwrite file /home/wedontplay/.config/Nokia/toolChains.xml: Permission denied


Check that your home directory is on a drive that supports the file permission system of Linux. A FAT or NTFS drive will not do here.

Then, if that doesn't work, consider just deleting (better: Rename) the "Nokia" directory. If you didn't do anything important with QTCreator yet, then you can best start afresh. Errors like this can occur if your updated your Ubuntu version and still have personal configuration files for older versions of the application.

> **Wedontplay said:**
> 
#where my libraries are
LIBS += -L/usr/local/lib \

    -lopencv_core.so.2.4.0 \
    -lopencv_highgui.so.2.4.0 \
    -lopencv_imgproc.so.2.4.0 \
    -lopencv_features2d.so.2.4.0 \
    -lopencv_calib3d.so.2.4.0 \
    -lopencv_contrib.so.2.4.0 \
    -lopencv_flann.so.2.4.0 \
    -lopencv_gpu.so.2.4.0 \
    -lopencv_legacy.so.2.4.0 \
    -lopencv_ml.so.2.4.0 \
    -lopencv_objdetect.so.2.4.0 \
    -lopencv_ts.so.2.4.0 \
    -lopencv_video.so.2.4.0
[/CODE]

The "-l" flags passed as-they-are to the linker. Here, you wrote down pretty much the names of the library files. The point is that the linker automatically adds ".so" if you want dynamic linking, and ".a" if you want static linking, so your file name shouldn't contain the extension already. As a rule of thumb, parameters that you pass by "-l" should be such that the ".a" library file that you use when statically linking would also be found. For "opencv_gpu", for example, there is only one .a file: "/usr/lib/libopencv_gpu.a", thus you specify "-lopencv_gpu" for the linker. The same holds for the other libraries.

---

### Post by MiXor on 2012-05-25
Hey, 
I had the exact same issue. I don't understand what was wrong but uninstalling QtCreator and then re-installing it via the ubuntu software center application worked for me...
Best of luck

A.

---

