---
title: "g++ header trouble"
date: 2009-10-28
forum: Programming Talk
---

### Post by balagosa on 2009-10-28
here's the prob:

```

#include "cvhaartraining.h"

int main( int argc, char* argv[] )
{
    //some piece of code
}


```

Apparently, in that piece of code is to call a function from cvhaartraining.h. The problem is, it can't locate the header file. I compiled with this parameters.

```

g++ createsamples.cpp -o createsamples -L/home/daniel/Desktop/opencv/cvhaartraining

```

I even tried not including the -L option and copying the entire cvhaartraining.h inside the createsamples.cpp. Still an error occurs.

```

The Error:

/tmp/cczlgy9l.o: In function `main':
createsamples.cpp:(.text+0x8ad): undefined reference to `cvCreateTrainingSamples(char const*, char const*, int, int, char const*, int, int, int, double, double, double, int, int, int)'
createsamples.cpp:(.text+0x94e): undefined reference to `cvCreateTestSamples(char const*, char const*, int, int, char const*, int, int, int, double, double, double, int, int, int)'
createsamples.cpp:(.text+0x9a5): undefined reference to `cvCreateTrainingSamplesFromInfo(char const*, char const*, int, int, int, int)'
createsamples.cpp:(.text+0x9ef): undefined reference to `cvShowVecSamples(char const*, int, int, double)'
collect2: ld returned 1 exit status

```

---

### Post by dwhitney67 on 2009-10-28
You are missing the -I (uppercase 'eye') option to specify the location of the header file(s); as for the -L option, it is usually followed by one or more -l (lowercase 'ell') options indicating the library to use.

For example:
```

g++ -I/home/daniel/Desktop/opencv/cvhaartraining createsamples.cpp -o createsamples -L/home/daniel/Desktop/opencv/cvhaartraining -lcvhaartraining

```
Of course, I do not know the exact location of your header file(s) or your library file(s), much less the name of the library file(s).  Use the statement above merely as a reference for what you must do to build the application.

P.S.  You need to employ LD_LIBRARY_PATH when you run your application.
```

export LD_LIBRARY_PATH=/home/daniel/Desktop/opencv/cvhaartraining
./myprog

```

---

### Post by balagosa on 2009-10-28
much thanks, I will be trying it. But I got a question.

Why the constant repetition of "-I","-L","-l"??

The header file and the cpp file are located in the same directory. I double checked the path after "-L", it is correct.

---

### Post by MadCow108 on 2009-10-28
because the I, L, l flags mean different things
-I: include search path
-L: library search path
-l: library name to link without lib an extension

that it is all the same in your case is coincidence
often the libraries and headers are located in separate folders

---

### Post by Arndt on 2009-10-28
> **balagosa said:**
> much thanks, I will be trying it. But I got a question.

Why the constant repetition of "-I","-L","-l"??

The header file and the cpp file are located in the same directory. I double checked the path after "-L", it is correct.

The header files don't seem to be the problem, since you get so far as the linker complaining. You probably don't need -I, since the header files are in the same directory, and you could write -L. instead of the absolute path, but the important thing is that you need to specify the library you want to link with.

(When running, giving the absolute path for the entry in LD_LIBRARY_PATH is best, of course; otherwise you can only run the program in that particular directory.)

I don't know what you mean with "constant repetition". Generally, if files are spread out, and you do everything in one step (from .cpp to executable), you need all of -I, -L and -l. If you compile first and link later, you supply -I to the compilation step, and -L and -l to the linking step.

When I read this, the -l (lower case L) and -I (upper case i) appear the same way with the font I use, so some care is needed to pick the correct letter.

---

