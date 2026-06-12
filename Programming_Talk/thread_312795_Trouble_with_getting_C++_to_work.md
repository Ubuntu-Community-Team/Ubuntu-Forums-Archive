---
title: "Trouble with getting C++ to work"
date: 2006-12-05
forum: Programming Talk
---

### Post by run1206 on 2006-12-05
Hi, i'm new to Linux (started in Sept. 06) and just started getting some programming apps running, (Anjuta, Eclipse, etc.) for Java and C++.  I'm trying to do the simple "Hello World" program that you all might know. It works fine in Eclipse in Java, but i can't get it to work in Anjuta with C++. I try to build (or compile) and i get the message the libgnomeuimm-2.0 cannot be found, and that it suggests "to adjust the PKG_CONFIG_PATH if you installed software on a non-standard prefix.  Alternatively, you may set the environment variables PACKAGE_CFLAGS and PACKAGE_LIBS to avoid the need to call pkg-config. I tried to look up libgnomeuimm-2.0 in synaptic, yet i can't find it. My question is how do i find and install gnomeuimm-2.0 and get it to  fix the whole PKG_CONFIG_PATH problem for my program to work?  Any help is greatly appreciated. thanks much everyone:)

---

### Post by Wybiral on 2006-12-05
Well, why not give the command line a shot? Open up GEdit or some other text editor and paste the hello world program...

```

#include <iostream>

using namespace std;

int main(){
   cout << "Hello World!" << endl;
   return 0;
}

```

Then save that as something like "hello.cpp"

Then, open up your trusty command line (dont scream) and navigate to the directory your program is in (using the cd command) and when you're in the directory enter...

```

g++ hello.cpp -o hello

```

Its very simple. Whatever you put after the "-o" will be the output program (if you dont put a "-o" with something after it, the output is "a.out").

To create an object file for linking, just use "g++ hello.cpp -c" and you'll get "hello.o"

Then, to link all of your object files, just use "g++ objFile1.o objFile2.o objFile3.o -o outFile"

Anything an IDE can do, you can do with the command line (you can also try Makefiles and shell scripts to compile)

---

### Post by daniminas on 2006-12-05
and you can write your own Makefiles too 8)

---

### Post by run1206 on 2006-12-06
thanks daniminas and Wybiral, i put in the code and tried the command line. placed them both in my home directory and ran them. the program worked perfectly as you said. once again, thanks much!!!!:-D :-D

---

