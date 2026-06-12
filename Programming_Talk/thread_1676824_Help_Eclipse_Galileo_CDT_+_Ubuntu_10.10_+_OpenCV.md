---
title: "Help Eclipse Galileo CDT + Ubuntu 10.10 + OpenCV"
date: 2011-01-27
forum: Programming Talk
---

### Post by insecure hyena on 2011-01-27
Hi everyone, at first let me say sorry for my really bad English. That's my first post here in the official Ubuntu Forum.
Second let me say sorry if this post results duplicate or not correctly positioned in the forum.
Here's my problem:
I'm trying to compile C++ programs that use OpenCV library in Eclipse CDT. I've installed libcv from the repositories and it seems that the include files and the library are actually on the system. It seems that the problem is related to the linking phase.
Here's the code:
```

#include <iostream>
#include <opencv/highgui.h>
using namespace std;
using namespace cv;

int main() {

	Mat m;
	cout << "!!!Hello World!!!" << endl;
	return 0;
}

```

And here's what I get:
```

Building target: prova
Invoking: GCC C++ Linker
g++ -L 'pkg-config --libs opencv'  -o"prova"  ./src/prova.o   
./src/prova.o: In function `cv::Mat::release()':
/usr/include/opencv/cxmat.hpp:378: undefined reference to `cv::fastFree(void*)'
collect2: ld returned 1 exit status
make: *** [prova] Error 1

```

In "*Properties->C/C++ Build->Settings*" I've set up, in the section "*Tool Settings->GCC C++ Linker*", -L 'pkg-config --libs opencv' right in the "*Command line pattern:*" between ${COMMAND} and ${FLAGS} but it seems that there's a problem in the linking process.
If someone could help me I'll be grateful to him.

Thanks

---

### Post by SevenMachines on 2011-01-27
Try putting the libs last

```
$ g++ `pkg-config --libs opencv` -o prova  prova.o   

prova.o: In function `cv::Mat::release()':
prova.cpp:(.text._ZN2cv3Mat7releaseEv[cv::Mat::release()]+0x3e): undefined reference to `cv::fastFree(void*)'
collect2: ld returned 1 exit status
```but...
```
$ g++ -o prova prova.o `pkg-config --libs opencv` 
niall@cryodynamic:~/Desktop$ ./prova 
!!!Hello World!!!
```

---

### Post by SevenMachines on 2011-01-27
Just a little note on why from the gcc manual, mainly because i was struggling to fully understand this point myself a few days ago. Mostly the order of libraries doesn't cause any problems so I keep forgetting that it can!
[ ]("http://gcc.gnu.org/onlinedocs/gcc-4.5.2/gcc/Link-Options.html#Link-Options")
[http://gcc.gnu.org/onlinedocs/gcc-4.5.2/gcc/Link-Options.html#Link-Options](http://gcc.gnu.org/onlinedocs/gcc-4.5.2/gcc/Link-Options.html#Link-Options)

> -llibrary
-l library

Search the library named library when linking.  (The second alternative with the library as a separate argument is only for POSIX compliance and is not recommended.)       I**t makes a difference where in the command you write this option; the linker searches and processes libraries and object files in the order they are specified.  Thus, `foo.o -lz bar.o' searches library `z' after file foo.o but before bar.o.  If bar.o refers to functions in `z', those functions may not be loaded.       **
The linker searches a standard list of directories for the library, which is actually a file named liblibrary.a.  The linker then uses this file as if it had been specified precisely by name.       
The directories searched include several standard system directories plus any that you specify with -L.       
Normally the files found this way are library files—archive files whose members are object files.  **The linker handles an archive file by scanning through it for members which define symbols that have so far been referenced but not defined.  But if the file that is found is an ordinary object file, it is linked in the usual fashion.**  The only difference between using an -l option and specifying a file name is that -l surrounds library with `lib' and `.a' and searches several directories.

---

### Post by insecure hyena on 2011-01-28
Thank you for the quick and precise response, it solved my problem!
But there's something that I don't get it yet.
If I use the command 'pkg-config --cflags opencv' for the compiler all works great.
But If I use the command 'pkg-config --libs opencv' with the linker in the position that you specified it don't works.
It only works if I use `pkg-config --libs opencv` without the -l and -L flags.
There's really something that I don't get.
Perhaps I should go back to the basis and restudy appropriately all the linking and compiling flags.
However let me say again thank you for your clear and fast response and for the useful link that you've indicated.

P.S: again sorry for my really really bad English :oops:

---

### Post by SevenMachines on 2011-01-28
> **insecure hyena said:**
> But If I use the command 'pkg-config --libs opencv' with the linker in the position that you specified it don't works.
It only works if I use `pkg-config --libs opencv` without the -l and -L flags.
I'm not sure i understand, are you doing something like
```
 $ gcc -l `pkg-config --libs opencv`
```If so, you don't add -l -L or -I flags with pkg-config. The expression inside the back-quotes ` is evaluated first so
```
 $ gcc `pkg-config --libs opencv`
```actually expands to
>  $ gcc -lml -lcvaux -lhighgui -lcv -lcxcore  before it is run, any -l, -L, -I flags etc are added automatically by pkg-config. Sorry if thats not what you meant.
> P.S: again sorry for my really really bad English :oops:Your english is good don't worry!

---

### Post by insecure hyena on 2011-01-28
Sorry for my late response.
You get it, I've tried with the -l and -L flag not knowing that the pkg-config command doesn't need them.
But there's another point...in the compiler section I've used the pkg-config command in strong quotes '' and not in back-quotes `` and it seems to work. I've simply added 'pkg-config --cflags opencv' in the "Directories" under "GCC C++ Compiler" in "Tool Settings".
On the opposite, in the linker section, without the -l and -L flag and with strong quotes '', it doesn't work. I had to put the pkg-config command between the back-quotes `` as you suggest in your first post.

---

### Post by SevenMachines on 2011-01-29
When you use pkg-config in quotes " ", it doesnt work, 
```
 $ g++ -c -o prova.o prova.cpp "pkg-config --cflags opencv" 
```doesnt add any flags from pkg-config, you'll probably get a warning because "pkg-config --cflags opencv" just adds those terms as parameters that are meaningless. g++ -c keeps going though, and since you have
```
 #include <opencv/highgui.h>
```Then when it searches in the system directory /usr/include/ it finds the header anyway since you've got the opencv/ directory in your include. 

What you'd normally have is...
```
#include <highgui.h>
```and then having "pkg-config --cflags opencv" would fail since the opencv directory is added by pkg-config as a -I include directory, ie
```
$ g++ -c -o prova.o prova.cpp "pkg-config --cflags opencv" 
g++-4.5.real: pkg-config --cflags opencv: No such file or directory
prova.cpp:2:21: fatal error: highgui.h: No such file or directory
compilation terminated.
```When we use back quotes then the pkg-config expression is evaluated first and everything works
```
 $ g++ -c -o prova.o prova.cpp `pkg-config --cflags opencv` 
```evaluates to
```
 $ g++ -c -o prova.o prova.cpp -I/usr/include/opencv
```In short, "pkg-config --cflags opencv" doesn't work in your compilation stage, it just doesnt matter in this case because you dont need to add the cflag parameters anyway due to the way you've included highgui.h. 
"pkg-config --libs opencv" in your linking stage again doesnt work, but this time the parameters it adds are essential to link the libraries so it exits

---

### Post by insecure hyena on 2011-01-29
Perfect, your explanation is perfect. I get it now. :D
What should I say...thank you very much for your disposability and your patience.
Now let me mark this discussion as SOLVED. O:)

P.S: again thank you very much!!!

---

