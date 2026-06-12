---
title: "Installation problem with Eclipse with C++ and OpenC"
date: 2011-03-25
forum: Programming Talk
---

### Post by joehc on 2011-03-25
Hey guys.

I&#7743; having trouble compiling some code in Eclipse. I'm writing a c++ project with the use os OpenCV. But when I'm trying to run the system says unable to launch. If I go to the console I see: 

**** Build of configuration Debug for project Opencvdemo ****

make all 
make: echo: Command not found
make: *** [src/main.o] Error 127

I have g++ and build-essential installed. Can you guys help me please?

I'm running ubuntu 10.04
thanks in advanced.

/Joe

---

### Post by Zugzwang on 2011-03-25
Can you copy&paste the file "Makefile" that eclipse generates for compiling here?

For the time being, I have one wild guess what could have went wrong. For this, try to start eclipse from a terminal window rather than from the "Applications" menu of Ubuntu. Does the problem still persist if you try to build your application then?

---

### Post by joehc on 2011-03-25
> **Zugzwang said:**
> Can you copy&paste the file "Makefile" that eclipse generates for compiling here?

For the time being, I have one wild guess what could have went wrong. For this, try to start eclipse from a terminal window rather than from the "Applications" menu of Ubuntu. Does the problem still persist if you try to build your application then?

It did not help by running eclipse from the terminal.

I can copy paste but it is pretty long. Can insert a link from dropbox, so you can see the Makefile?

---

### Post by Zugzwang on 2011-03-25
> **joehc said:**
> I can copy paste but it is pretty long. Can insert a link from dropbox, so you can see the Makefile?

I would suggest using [http://pastebin.com](http://pastebin.com) for this purpose.

---

### Post by joehc on 2011-03-25
> **Zugzwang said:**
> I would suggest using [http://pastebin.com](http://pastebin.com) for this purpose.
Okay, here you go: [http://pastebin.com/1sTingbx](http://pastebin.com/1sTingbx)

---

### Post by Zugzwang on 2011-03-25
The interesting stuff is probably in the file "CMakeFiles/Makefile2". 

What happens if you run the make utility from the terminal?

---

### Post by joehc on 2011-03-25
> **Zugzwang said:**
> The interesting stuff is probably in the file "CMakeFiles/Makefile2". 

What happens if you run the make utility from the terminal?
Sorry about that: here you go: [http://pastebin.com/K2ZBci9W](http://pastebin.com/K2ZBci9W)

You mean if I run make from the terminal? Nothing happens: make: *** No targets specified and no makefile found.  Stop.


But actually, mane times when I try to compile some code with make, it comes up with this message above.

Am I missing some something from my system?

Hope you can help...

---

### Post by joehc on 2011-03-28
bump

---

### Post by dwhitney67 on 2011-03-28
Enter the following command from a terminal:
```

which make

```
The result should be: /usr/bin/make

If you did not get a result, then install build-essential.
```

sudo apt-get install build-essential

```

Now, to test to see if you are able to build a C++ program, run the following from a terminal:
```

cat > Test.cpp << EOF
#include <iostream>
int main() { std::cout << "hello world." << std::endl; }
EOF
make Test && ./Test

```
If you see the output "hello world", then not only is 'make' working, but so is the 'g++' compiler.

Now, wrt your project, skipping all notions of using an IDE, can you try to build it in a similar fashion as above?  If you have multiple modules and/or require the linking to a specialized library, please let me know.  I can assist with putting together the appropriate 'g++' command statement and a Makefile.

---

### Post by joehc on 2011-03-28
> **dwhitney67 said:**
> Enter the following command from a terminal:
```

which make

```The result should be: /usr/bin/make

If you did not get a result, then install build-essential.
```

sudo apt-get install build-essential

```Now, to test to see if you are able to build a C++ program, run the following from a terminal:
```

cat > Test.cpp << EOF
#include <iostream>
int main() { std::cout << "hello world." << std::endl; }
EOF
make Test && ./Test

```If you see the output "hello world", then not only is 'make' working, but so is the 'g++' compiler.

Now, wrt your project, skipping all notions of using an IDE, can you try to build it in a similar fashion as above?  If you have multiple modules and/or require the linking to a specialized library, please let me know.  I can assist with putting together the appropriate 'g++' command statement and a Makefile.
Hey, thanks for answering. 

I was able to to get /usr/bin/make and the print-out: hello world, from the terminal. So then nothing is missing from my system?
I'm not sure what you mean regards my project. In Eclipse I'm linking to some OpenCV libraries...

---

### Post by dwhitney67 on 2011-03-28
Ok, that's good.

Go to the directory (folder) where your project resides.  Please list the names of the files that you wish to compile/link into an executable program.

As for OpenC, my only knowledge on this is from [here]("http://wiki.forum.nokia.com/index.php/Open_C_library").  There is nothing there on how one obtains the library, much less how to build with it.  Do you have any documentation?

EDIT: Nevermind; the thread title states "OpenC", but your opening post stated "OpenCV".  OpenCV can be obtained using:
```

sudo apt-get install libavformat-dev

sudo apt-get install ffmpeg

sudo apt-get install libcv2.1 libcvaux2.1 libhighgui2.1 python-opencv opencv-doc libcv-dev libcvaux-dev libhighgui-dev

```

---

### Post by joehc on 2011-03-28
Well I think I have OpenCV install...I'm pretty sure.

The problem is that when I have build some code in Eclipse it comes up with this error:
**** Build of configuration Debug for project Opencvdemo ****

make all 
make: echo: Command not found
make: *** [src/main.o] Error 127
[[IMG]http://img25.imageshack.us/img25/9139/screenshotuvs.th.png[/IMG]]("http://img25.imageshack.us/i/screenshotuvs.png/")

Uploaded with [ImageShack.us]("http://imageshack.us")

i don't know if it is Eclipse, OpenCV, cpp or my system which is the problem... :(

EDIT:
Actually in Eclipse is says it is a C++ problem?

[[IMG]http://img819.imageshack.us/img819/6773/screenshot1td.th.png[/IMG]]("http://img819.imageshack.us/i/screenshot1td.png/")

Uploaded with [ImageShack.us]("http://imageshack.us")
[URL="http://imageshack.us"]
[/URL]

---

### Post by dwhitney67 on 2011-03-28
From the error you posted, I get the impression that "make" is complaining that it cannot find the command "echo".

It could be an issue with your working environment; what does "echo $SHELL" indicate?

Can you not build your application via a terminal?  A simple call to g++ for a single module is like:
```

g++ -c -Wall Module_1.cpp

```
If you have multiple modules, then repeat for each one.

Then to link, something like:
```

g++ Module_1.o Module_2.o -o myapp 

```
Use the -l (lowercase L) option to specify any libraries that you wish to link against.  For example, if the OpenCV library is libcv.so, then you would do something like:
```

g++ Module_1.o Module_2.o -o myapp -lcv

```
Within Eclipse, you should be able to specify something very similar.  There are two areas within the Eclipse configuration that are important: the compiler flags and the linker flags.  For the former, -Wall would be a good candidate.  For the latter, "cv" (or possibly "-lcv"... can't remember) would be a good candidate.

My advice... stay away from an IDE until you learn how to build the project from the command line.

---

