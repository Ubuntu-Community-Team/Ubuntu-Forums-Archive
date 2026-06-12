---
title: "Editing ld.so.conf not making a difference in opencv"
date: 2008-10-26
forum: Programming Talk
---

### Post by darthshak on 2008-10-26
Hi

I compiled opencv from source and installed it on Ubuntu Hardy. I kept getting the following error each time i tried to compile : 

first.cpp:1:21: error: highgui.h: No such file or directory
first.cpp: In function ‘int main(int, char***)’:
first.cpp:4: error: ‘IplImage’ was not declared in this scope
first.cpp:4: error: ‘img’ was not declared in this scope
first.cpp:4: error: ‘cvLoadImage’ was not declared in this scope
first.cpp:5: error: ‘CV_WINDOW_AUTOSIZE’ was not declared in this scope
first.cpp:5: error: ‘cvNamedWindow’ was not declared in this scope
first.cpp:6: error: ‘cvShowImage’ was not declared in this scope
first.cpp:7: error: ‘cvWaitKey’ was not declared in this scope
first.cpp:8: error: ‘cvReleaseImage’ was not declared in this scope
first.cpp:9: error: ‘cvDestroyWindow’ was not declared in this scope

I then found out that I have to add /usr/local/lib to the /etc/ld.so.conf and then run ldconfig as root.

Well, it doesnt seem to make a difference at all. Is there any way I can check to see if the compiler is even searching /usr/local/lib? What am I doing wrong?

---

### Post by nvteighen on 2008-10-26
I'd rather think it's not finding the header file. Where have you copied highgui.h and how are you #include'ing it?

---

### Post by darthshak on 2008-10-26
Well, I tried both #include "highgui.h" and #include <highgui.h> separately, still no luck
I searched /usr and found it sitting in /usr/include/opencv/

Do you think that's the problem? Shouldnt it be in /usr/include directly?

---

### Post by nvteighen on 2008-10-26
Ah, then what you need is to compile specifying where the include header is. Use #include <highgui.h> and to compile:

```

gcc *(stuff you need)* -I/usr/include/opencv

```

---

### Post by darthshak on 2008-10-26
Ok

That solved the highgui.h problem
Here's what i get now : 
```

/tmp/ccoyocn6.o: In function `main':
first.cpp:(.text+0x27): undefined reference to `cvLoadImage'
first.cpp:(.text+0x3e): undefined reference to `cvNamedWindow'
first.cpp:(.text+0x51): undefined reference to `cvShowImage'
first.cpp:(.text+0x5d): undefined reference to `cvWaitKey'
first.cpp:(.text+0x68): undefined reference to `cvReleaseImage'
first.cpp:(.text+0x74): undefined reference to `cvDestroyWindow'
collect2: ld returned 1 exit status

```

I tried g++ first.cpp -I /usr/include/opencv -L /usr/local/lib but no luck.

---

### Post by sillv0r on 2008-10-26
I'm still a noob to linking libraries and such so correct me if I'm wrong.

[Strikeout]
/etc/ld.so.conf
Doesn't really come into play until runtime of the program. (As in if the library you're linking into your program is a shared library.)
[/Strikeout]

If you're getting compile-time errors be sure that you're specifying the library with a -l switch.
```

g++ first.cpp -I /usr/include/opencv -l<opencvlibname>

```

Where <opencvlibname> is the name of the shared library you're attempting to get from /usr/local/lib. (Excluding the lib prefix and .so extension.)

For example, if <opencvlibname> = libopencv.so, then use the following command.
```

g++ first.cpp -I /usr/include/opencv -lopencv

```

[Add]The -l switch tells the compiler that your program requires the given library.[/Add]

---

### Post by darthshak on 2008-10-26
Well, yeah, that worked. I just manually linked *all* the libraries.

---

### Post by Game_Ender on 2008-10-26
> **darthshak said:**
> Well, yeah, that worked. I just manually linked *all* the libraries.

You **always** have to do that.  That file you are editing is for the runtime loading of library not the compile linking of them.

---

### Post by nvteighen on 2008-10-26
Actually, ld.so.conf shouldn't be touched. It includes /lib, /usr/lib and /usr/local/lib by default...

---

### Post by darthshak on 2008-10-26
Would changing the LD_LIBRARY_PATH environment variable make a difference? And is it advisable to do so without affecting other components that use that environment variable?

---

### Post by JupiterV2 on 2008-10-26
Whenever you change (read: add directories to) ld.so.conf, you need to run /sbin/ldconfig as root:

```
$ sudo /sbin/ldconfig
```

...in order to update the library lookup reference.

---

### Post by dwhitney67 on 2008-10-26
> **darthshak said:**
> Would changing the LD_LIBRARY_PATH environment variable make a difference? And is it advisable to do so without affecting other components that use that environment variable?
One can set LD_LIBRARY_PATH when they run their application without affecting the value set in other shells.

From the command-line, enter something like:
```
LD_LIBRARY_PATH=/some/dir/path myExecutable
```

Of course, if you do not like to type this command over and over again, you can slap it into a script.

---

### Post by skullmunky on 2008-10-31
Actually now there's a whole /etc/ld.so.conf.d directory, so you can cleanly add and remove conf files to add search paths for the linker without having to edit a single ld.so.conf file, which is dangerous.  If the linker's not searching /usr/local/lib, which it probably isn't because (i think) that's against Debian policy, you can put a file into /etc/ld.so.conf called, say, "opencv.conf", and just put the line "/usr/local/lib" into it.

then run ldconfig.

however there's a little more to the story.  You need 3 compile flags to make everything work out ok:

1. the -I flag, to tell the compiler where to search for headers
-I/usr/include/opencv

2. sometimes the -L flag, to tell the linker where to find libraries:
-L/usr/local/lib

3. the -l flag to tell the linker WHICH libraries to link:

-lopencv -lhighgui 

or similar to link libopencv.so and libhighgui.so.

you do always have to specify all the libraries you want to link to with -l, regardless of where they are.  that's why makefiles are good.

---

### Post by dwhitney67 on 2008-10-31
> **skullmunky said:**
> ...
If the linker's not searching /usr/local/lib, which it probably isn't because (i think) that's against Debian policy
...

I was under the impression that Ubuntu follows the Debian style of Linux.  On my system, /etc/ld.so.conf.d/libc.conf contains an entry for /usr/local/lib.

---

### Post by skullmunky on 2008-10-31
> **dwhitney67 said:**
> I was under the impression that Ubuntu follows the Debian style of Linux.  On my system, /etc/ld.so.conf.d/libc.conf contains an entry for /usr/local/lib.

heh heh, so it is.  I just checked the debian policy manual to confirm :)  I was just speaking from past experiences, where I've had ubuntu installations that didn't include /usr/local/lib by default.  sometimes when I ask about this I kind of get polite lectures about the debian filesystem policy so I thought that something to do with it ... ;)

*shrug* 

anyway, how did the opencv compilation work out?

---

### Post by darthshak on 2008-11-01
Yeah, it worked out fine. I didnt bother modifying ld.so.conf at all. Just manually linked all libraries. Used the following command :

```
g++ <filename> -I /usr/local/include/opencv -L /usr/local/lib -lm -lcv -lhighgui -lcvaux
```

---

