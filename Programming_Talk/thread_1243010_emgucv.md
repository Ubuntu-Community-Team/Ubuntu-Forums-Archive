---
title: "emgucv"
date: 2009-08-17
forum: Programming Talk
---

### Post by my.self on 2009-08-17
Hi,

anybody working with "emgucv" Mono wrapper?
My problem begins at installation ;-(

I tried installing based on the following article:
[http://www.emgu.com/wiki/index.php/Download_And_Installation#Linux](http://www.emgu.com/wiki/index.php/Download_And_Installation#Linux)

CMake Error at CMakeLists.txt:47 (set_target_properties):
  set_target_properties Can not find target to add properties to:
  opencv_ffmpeg


Cheers Stefan

---

### Post by pittle on 2009-09-23
Any solution for this?

---

### Post by directhex on 2009-09-23
It's an upstream bug, you should report it to them. The emgucv/CMakeLists.txt file tries to add properties to a custom target, but that custom target is defined in emgucv/opencv/interfaces/CMakeLists.txt as Windows-only:

if(MSVC)
    add_subdirectory(ffopencv)
endif()

i.e. the target is only there to be added to if compiling with MSVC (MS Visual C++)

---

### Post by pittle on 2009-09-23
> **directhex said:**
> 
It's an upstream bug, you should report it to them.


Okay.

> **directhex said:**
> 
The emgucv/CMakeLists.txt file tries to add properties to a custom target, but that custom target is defined in emgucv/opencv/interfaces/CMakeLists.txt as Windows-only:

if(MSVC)
    add_subdirectory(ffopencv)
endif()


How did you figure out that? Error message says:

> **my.self said:**
> 
CMake Error at CMakeLists.txt:47 (set_target_properties):
  set_target_properties Can not find target to add properties to:
  opencv_ffmpeg


What's the link between "opencv_ffmpeg" (target) and "ffopencv" (subdirectory)?

> **directhex said:**
> 
i.e. the target is only there to be added to if compiling with MSVC (MS Visual C++)


Do you think commenting out CMakeLists.txt:47 could be considered as a workaround to this problem?

---

### Post by directhex on 2009-09-23
> **pittle said:**
> How did you figure out that? Error message says:



What's the link between "opencv_ffmpeg" (target) and "ffopencv" (subdirectory)?

the CMakeLists file in the ffopencv subdirectory defines:
set(the_target opencv_ffmpeg)

> Do you think commenting out CMakeLists.txt:47 could be considered as a workaround to this problem?

Probably - but I don't know whether you actually *want* that ffopencv folder in the build or not. Try it!

---

