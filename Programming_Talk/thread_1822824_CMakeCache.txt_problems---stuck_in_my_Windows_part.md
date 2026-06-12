---
title: "CMakeCache.txt problems---stuck in my Windows partition"
date: 2011-08-11
forum: Programming Talk
---

### Post by skytreader on 2011-08-11
I'm trying to install OpenCV in my Ubuntu box. The thing is, I was in my Vista partition when I downloaded OpenCV for Ubuntu.

I'm following [this]("http://www.samontab.com/web/2011/06/installing-opencv-2-2-in-ubuntu-11-04/") tutorial*. The first step, a sudo apt-get install to various programs, among them cmake, was executed on my home folder. However, I untarred OpenCV in my Windows partition and *cmake*d it there.

The installation was successful. However, I realized that I may not be able to use OpenCV without my Windows drive mounted. So, I moved my OpenCV folder to usr/include and then tried to cmake there again. It failed with the following error:

```
CMake Error: The current CMakeCache.txt directory 
/usr/include/OpenCV-2.3.0/CMakeCache.txt is different than the directory 
/media/58BC7C55BC7C2F9C/Users/Me/Documents/Downloads/programming libs/OpenCV/OpenCV-2.3.0
where CMackeCache.txt was created. This may result in binaries 
being created in the wrong place. If you are not sure, reedit the 
CMakeCache.txt
```

How do I "refresh" my CMakeCache.txt ? Why is it stuck in my Windows partition?

Thanks for any guides.

*An extra question to prevent myself from shooting my foot in the future: is it alright to follow a tutorial for OpenCV 2.2 when I'm installing 2.3? I heard that there were significant changes from 2.0 to 2.1 that somehow affected the installation process. Is there such case here?

---

### Post by dwhitney67 on 2011-08-11
I've never done what you are attempting, but my first instinct is to warn you against installing anything within /usr/include.

Typically applications developed for Linux can be built and then installed anywhere.  Thus I would recommend that you build the OpenCV package in your home directory.  As for the CMakeCache.txt, I would remove or rename it, so that you start off with a clean slate.

When you are done building (compiling/linking) the application, surely there will be a way to install it (perhaps using a Makefile) into the target area of your choice (note that this is optional!).  This target area should be relative to /usr/local, or perhaps in /opt.

---

