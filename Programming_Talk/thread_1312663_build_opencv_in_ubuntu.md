---
title: "build opencv in ubuntu"
date: 2009-11-03
forum: Programming Talk
---

### Post by flylehe on 2009-11-03
Hi,

I got this error (posted in the end) when trying to build opencv from its source on Ubuntu 8.10 via cmake following the installation guide of Opencv website ([http://opencv.willowgarage.com/wiki/InstallGuide](http://opencv.willowgarage.com/wiki/InstallGuide)). 

I thought I had to install the libraries it said as not found. So I looked for the libraries the error mentioned in the repository of Synaptic Package Manager but found nothing. I also tried to search them on Ubuntu website and found some related packages, like libucil2-dev and libunicap2-dev, but a new error says "dependencies not satiable" when trying to install them .

Any hint or advice? 

Thanks and regards!

The error while building opencv:
> 
tim@tim:~/program_files/tim/OpenCV-2.0.0/release$ cmake -D CMAKE_BUILD_TYPE=RELEASE -D CMAKE_INSTALL_PREFIX=/usr/local -D BUILD_PYTHON_SUPPORT=ON ..
-- Detected version of GNU GCC: 43
-- checking for module 'libunicap'
--   package 'libunicap' not found
-- checking for module 'libucil'
--   package 'libucil' not found
-- checking for module 'libv4l1'
--   package 'libv4l1' not found
-- Could NOT find Jasper
-- IPP detected: 
-- Parsing 'cvconfig.h.cmake'
running mkdir -p "/home/tim/program_files/tim/OpenCV-2.0.0/release/unix-install/"  2>&1
-- 
-- General configuration for opencv 2.0.0 =====================================
-- 
--     Compiler:                  
--     C++ flags (Release):         -Wall -pthread -ffunction-sections  -O3 -DNDEBUG  -fomit-frame-pointer -O3 -ffast-math -mmmx -DNDEBUG 
--     C++ flags (Debug):           -Wall -pthread -ffunction-sections  -g  -O0 -DDEBUG -D_DEBUG 
--     Linker flags (Release):     
--     Linker flags (Debug):       
-- 
--   GUI: 
--     GTK+ 2.x:                  1
--     GThread:                   1
-- 
--   Image I/O: 
--     JPEG:                      TRUE
--     PNG:                       TRUE
--     TIFF:                      TRUE
--     JASPER:                    FALSE
-- 
--   Video I/O: 
--     DC1394 1.x:                
--     DC1394 2.x:                1
--     FFMPEG:                    1
--       codec:                   1
--       format:                  1
--       util:                    1
--       swscale:                 1
--       gentoo-style:            1
--     GStreamer:                 1
--     UniCap:                    
--     V4L/V4L2:                  1/1
--     Xine:                      1
-- 
--   Interfaces: 
--     Old Python:                0
--     Python:                    ON
--     Use IPP:                   NO
--     Build Documentation        0
-- 
--     Install path:              /usr/local
-- 
--     cvconfig.h is in:          /home/tim/program_files/tim/OpenCV-2.0.0/release
-- -----------------------------------------------------------------
-- 
-- Configuring done
-- Generatim done
-- Build files have been written to: /home/tim/program_files/tim/OpenCV-2.0.0/release



---

