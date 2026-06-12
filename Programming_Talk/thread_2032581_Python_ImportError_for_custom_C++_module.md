---
title: "Python ImportError for custom C++ module"
date: 2012-07-24
forum: Programming Talk
---

### Post by rajeshja on 2012-07-24
Hi,

I've been developing a Python module in C++ using OpenCV 2.3 through 2.4.2, on Ubuntu 11.04. OpenCV was built from source. I'm not using the version of OpenCV from the Ubuntu repositories.

The module compiles with no issues and is loaded in Python properly.

However, when I compile this module on Ubuntu 11.10 or 12.04, I get an ImportError when trying to load it in Python.

This is how I compile the module:

```
g++ -fPIC -shared `pkg-config --cflags --libs python` `pkg-config --cflags --libs opencv` -I/usr/local/include/opencv2/legacy -o mymodule.so mymodule.cpp
```

This is the output of "pkg-config --cflags --libs opencv"

```
-I/usr/local/include/opencv -I/usr/local/include  /usr/local/lib/libopencv_calib3d.so /usr/local/lib/libopencv_contrib.so /usr/local/lib/libopencv_core.so /usr/local/lib/libopencv_features2d.so /usr/local/lib/libopencv_flann.so /usr/local/lib/libopencv_gpu.so /usr/local/lib/libopencv_highgui.so /usr/local/lib/libopencv_imgproc.so /usr/local/lib/libopencv_legacy.so /usr/local/lib/libopencv_ml.so /usr/local/lib/libopencv_nonfree.so /usr/local/lib/libopencv_objdetect.so /usr/local/lib/libopencv_photo.so /usr/local/lib/libopencv_stitching.so /usr/local/lib/libopencv_ts.so /usr/local/lib/libopencv_video.so /usr/local/lib/libopencv_videostab.so
```

The error I get is:

```
ImportError: /path/to/service/mymodule.so: undefined symbol: _ZN5CvSVMD1Ev
```

My understanding is that the ImportError generally means that the given symbol can't be found in any of the linked libraries. But I know that this symbol is there in libopencv_ml.so because when I run this: 

```
$ nm -g  /usr/local/lib/libopencv_ml.so | grep _ZN5CvSVMD1Ev

```

I get:

```
000000000002fd40 T _ZN5CvSVMD1Ev

```

So can you give me any clue what I might be doing wrong? Has something changed between 11.04 and 11.10 in the manner in which shared libraries are loaded when running Python?
Or is this a problem with OpenCV?

Thanks,
Rajesh

---

### Post by rajeshja on 2012-07-25
Can anyone give me a clue about where to continue debugging?

---

### Post by mevun on 2012-07-25
You did not run the "nm" command on your mymodule.so so I would assume the symbol really is missing.

I have no idea how you can fix that.  That is a really strange name for a symbol.

---

### Post by the_unforgiven on 2012-07-25
Most likely, your libopencv_ml.so is not found in the LD_LIBRARY_PATH for your python process.
As an experiment to confirm it, you could try the following:
```
$ LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/lib python
```
And at the python prompt, try importing your module.

If this solves the problem, check if /usr/local/lib is included in one of the files under /etc/ld.so.conf.d/ (or in /etc/ld.so.conf).

---

### Post by rajeshja on 2012-07-25
ld.so.conf.d did contain a reference to /usr/local/lib, so that wasn't the problem.

The problem was apparently in the way I was compiling the module. Running 'ldd' on my module, I got only five linked libraries, and libopencv_ml.so wasn't one of them.

Instead of 

```
g++ -fPIC -shared `pkg-config --cflags --libs python` `pkg-config --cflags --libs opencv` -I/usr/local/include/opencv2/legacy -o mymodule.so mymodule.cpp
```

I needed to change it to 

```
g++ -fPIC -shared -o mymodule.so mymodule.cpp `pkg-config --cflags --libs python` `pkg-config --cflags --libs opencv` -I/usr/local/include/opencv2/legacy
```

ldd then gave me 75 linked libraries, and the code now works.

I still don't understand WHY it behaves this way, so if someone can throw some light on that, that would be helpful.

---

