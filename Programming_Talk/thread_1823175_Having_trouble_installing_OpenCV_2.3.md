---
title: "Having trouble installing OpenCV 2.3"
date: 2011-08-11
forum: Programming Talk
---

### Post by skytreader on 2011-08-11
I'm installing OpenCV 2.3 using [this]("http://www.samontab.com/web/2011/06/installing-opencv-2-2-in-ubuntu-11-04/") tutorial. Somewhere, it asks me to add the following lines to my bash.bashrc:

```
PKG_CONFIG_PATH=$PKG_CONFIG_PATH:/usr/local/lib/pkgconfig
export PKG_CONFIG_PATH

```

The thing is, I don't have anything names pkgconfig in /usr/local/lib. Running ls on that folder, all I get are

```
python2.6  python3.1  site_ruby
```

Except for ffmpeg (which I won't be really using), the cmake call for OpenCV went fine.

However, make calls fail with the following message:

```
Linking CXX shared library ../../lib/libopencv_highgui.so
CMakeFiles/opencv_highgui.dir/src/cap.o: file not recognized: File truncated
collect2: ld returned 1 exit status
make[2]: *** [lib/libopencv_highgui.so.2.3.0] Error 1
make[1]: *** [modules/highgui/CMakeFiles/opencv_highgui.dir/all] Error 2
make: *** [all] Error 2
```

Any thoughts?

---

### Post by nmaster on 2011-08-11
> **skytreader said:**
> I'm installing OpenCV 2.3 using [this]("http://www.samontab.com/web/2011/06/installing-opencv-2-2-in-ubuntu-11-04/") tutorial. 
why not use this? seems simpler to me...
[https://help.ubuntu.com/community/OpenCV](https://help.ubuntu.com/community/OpenCV)

---

### Post by skytreader on 2011-08-12
Thanks for the link nmaster. But, apparently, plainly following the instructions on the link won't work, especially the last apt-get install (the one you use to install OpenCV libraries). To install OpenCV, in lieu of the last apt-get install, apt-get install the packages mentioned [here]("http://packages.ubuntu.com/source/lucid/opencv") (links to packages for Lucid, since I'm in Lucid. But from there you can easily choose from among the supported distros, if anything differs).

---

### Post by skytreader on 2011-08-14
Uhhmmm...removed the [SOLVED] tag as I'm having problems compiling the C examples.

The Python examples ran as expected. Well, not all, but figuring that it's just some system quirk (I've been tinkering with my Python installation a lot), I didn't bother with those that didn't. However, compiling the C examples, I run into the following error:

```
gcc -o squares squares.c
squares.c:12:16: error: cv.h: No such file or directory
squares.c:13:21: error: highgui.h: No such file or directory
```

Then, followed by loads of other errors which I hope to be resolved, if only I could import the two headers above.

Again, I installed using the instructions from the [Community Docs]("https://help.ubuntu.com/community/OpenCV") though I replaced the final sudo apt-get install with everything mentioned in the [Ubuntu package directory]("http://packages.ubuntu.com/source/lucid/opencv").

---

### Post by skytreader on 2011-08-14
*bump*

---

### Post by nmaster on 2011-08-15
> **skytreader said:**
> *bump*
sorry for not responding. i sort of forgot about this thread :( my mistake.

are those header files somewhere in the system by not in your gcc path? execute the following to find out:
```
sudo find / -name cv.h
```
```
sudo find / -name highgui.h
```

if you find the directory where these files are located you just need to them to the gcc path: [http://www.network-theory.co.uk/docs/gccintro/gccintro_23.html](http://www.network-theory.co.uk/docs/gccintro/gccintro_23.html)

---

