---
title: "How to include libraries?"
date: 2012-07-21
forum: Programming Talk
---

### Post by Angus1 on 2012-07-21
Hi, I've been (slowly) getting the hang of the very basics of c/c++ recently, with very little prior programming experience (MQL4 and programming arduinos). I haven't had too many problems writing simple programs to solve mathmatical problems, but for the life of me, I can't make the FANN library work. I've tried with Visual Studio and had no luck, so thought I'd give the suggested CMake install on linux a try. The installation went fine, but when I try to use any FANN functions I get something along the lines of this:

```
angus@angus-Rev-1-0:~$ cd /home/angus/fanntest
angus@angus-Rev-1-0:~/fanntest$ cmake .
-- Configuring done
-- Generating done
-- Build files have been written to: /home/angus/fanntest
angus@angus-Rev-1-0:~/fanntest$ make
[100%] Building CXX object CMakeFiles/hello.dir/fann1.o
/home/angus/fanntest/fann1.cpp: In function ‘int main()’:
/home/angus/fanntest/fann1.cpp:4:56: error: ‘fann_create’ was not declared in this scope
make[2]: *** [CMakeFiles/hello.dir/fann1.o] Error 1
make[1]: *** [CMakeFiles/hello.dir/all] Error 2
make: *** [all] Error 2
```

when all relevent include files are placed in the same folder as the code I get this:

```
angus@angus-Rev-1-0:~$ cd /home/angus/fann1
angus@angus-Rev-1-0:~/fann1$ cmake .
-- Configuring done
-- Generating done
-- Build files have been written to: /home/angus/fann1
angus@angus-Rev-1-0:~/fann1$ make
Scanning dependencies of target fann1
[100%] Building C object CMakeFiles/fann1.dir/fann1.o
/home/angus/fann1/fann1.c: In function ‘main’:
/home/angus/fann1/fann1.c:8:24: warning: initialization makes pointer from integer without a cast [enabled by default]
Linking C executable fann1
CMakeFiles/fann1.dir/fann1.o: In function `fann_run':
fann1.c:(.text+0x1ac2): undefined reference to `exp'
fann1.c:(.text+0x1b06): undefined reference to `exp'
fann1.c:(.text+0x1f70): undefined reference to `exp'
fann1.c:(.text+0x1f99): undefined reference to `exp'
fann1.c:(.text+0x2087): undefined reference to `sin'
fann1.c:(.text+0x209c): undefined reference to `cos'
fann1.c:(.text+0x20b1): undefined reference to `sin'
fann1.c:(.text+0x20de): undefined reference to `cos'
CMakeFiles/fann1.dir/fann1.o: In function `fann_init_weights':
fann1.c:(.text+0x384d): undefined reference to `pow'
CMakeFiles/fann1.dir/fann1.o: In function `fann_save_internal_fd':
fann1.c:(.text+0x5919): undefined reference to `floor'
fann1.c:(.text+0x597b): undefined reference to `floor'
fann1.c:(.text+0x59dd): undefined reference to `floor'
fann1.c:(.text+0x5bae): undefined reference to `floor'
fann1.c:(.text+0x61a5): undefined reference to `floor'
CMakeFiles/fann1.dir/fann1.o:fann1.c:(.text+0x62fd): more undefined references to `floor' follow
CMakeFiles/fann1.dir/fann1.o: In function `fann_activation_derived':
fann1.c:(.text+0x85dc): undefined reference to `cos'
fann1.c:(.text+0x85f5): undefined reference to `sin'
fann1.c:(.text+0x8617): undefined reference to `cos'
fann1.c:(.text+0x8639): undefined reference to `sin'
CMakeFiles/fann1.dir/fann1.o: In function `fann_activation':
fann1.c:(.text+0x8760): undefined reference to `exp'
fann1.c:(.text+0x87a0): undefined reference to `exp'
fann1.c:(.text+0x8bcf): undefined reference to `exp'
fann1.c:(.text+0x8bf4): undefined reference to `exp'
fann1.c:(.text+0x8cd3): undefined reference to `sin'
fann1.c:(.text+0x8ce4): undefined reference to `cos'
fann1.c:(.text+0x8cf5): undefined reference to `sin'
fann1.c:(.text+0x8d1e): undefined reference to `cos'
CMakeFiles/fann1.dir/fann1.o: In function `fann_compute_MSE':
fann1.c:(.text+0x91cf): undefined reference to `log'
CMakeFiles/fann1.dir/fann1.o: In function `fann_update_weights_sarprop':
fann1.c:(.text+0xa701): undefined reference to `sqrt'
fann1.c:(.text+0xa7ed): undefined reference to `exp'
fann1.c:(.text+0xa9af): undefined reference to `exp'
CMakeFiles/fann1.dir/fann1.o: In function `fann_save_train_internal_fd':
fann1.c:(.text+0xccbf): undefined reference to `floor'
fann1.c:(.text+0xcd09): undefined reference to `floor'
fann1.c:(.text+0xce63): undefined reference to `floor'
fann1.c:(.text+0xcead): undefined reference to `floor'
CMakeFiles/fann1.dir/fann1.o: In function `fann_set_input_scaling_params':
fann1.c:(.text+0xdeb2): undefined reference to `sqrt'
CMakeFiles/fann1.dir/fann1.o: In function `fann_set_output_scaling_params':
fann1.c:(.text+0xe3de): undefined reference to `sqrt'
CMakeFiles/fann1.dir/fann1.o: In function `fann_initialize_candidates':
fann1.c:(.text+0xfb30): undefined reference to `pow'
CMakeFiles/fann1.dir/fann1.o: In function `main':
fann1.c:(.text+0x112b4): undefined reference to `fann_create'
collect2: ld returned 1 exit status
make[2]: *** [fann1] Error 1
make[1]: *** [CMakeFiles/fann1.dir/all] Error 2
make: *** [all] Error 2

```

Which seems to imply to me that I need to set it up to use math.h.

The code that gives the second terminal result is:

```
#include "math.h"
#include "stdio.h"
#include "doublefann.c"


int main()
{
    struct fann *ann = fann_create(1, 0.7, 3, 26, 13, 3);
    fann_train_on_file(ann, "frequencies.data", 200, 10, 0.0001);
    fann_save(ann, "language_classify.net");
    fann_destroy(ann);
    return 0;
}
```

Can anyone shed any light? I'm gussing it's something simple like I need to add a reference to the library to the CMakeLists.txt file, which currently just reads:

```
cmake_minimum_required(VERSION 2.0)
project(FANN1)
add_executable(fann1 fann1.c)
```

The FANN library can be found here - [http://leenissen.dk/](http://leenissen.dk/)

Thanks for any help you can give,
Angus

---

### Post by MadCow108 on 2012-07-21
the errors you are getting come from the linker, not the compiler, so the source compiled fine just connecting the binary objects did not work.

you need to link with libm for the math functions and fann for the other stuff
in cmake linking libm looks like this:
```
find_library(M_LIB m)
target_link_libraries(fann1 ${M_LIB})
```

you similarly need to find libfann and add it to the target_link_libraries

---

### Post by Bachstelze on 2012-07-21
I suggest you don't use cmake for now since your project is probably very simple. cmake adds an additional layer of complexity for no real benefit. In particular, it might make it harder for you to get help; for example I know how to link a library to a program, but I am not familiar with cmake, so I can't help you if you want to use it.

---

### Post by Bachstelze on 2012-07-21
Also this:

```

/home/angus/fann1/fann1.c: In function &#8216;main&#8217;:
/home/angus/fann1/fann1.c:8:24: warning: initialization makes pointer from integer without a cast [enabled by default]
```

probaby indicates a mistake in your code. Finally, you need to decide if you want to learn C or C++. "C/C++" makes about as much sense as "English/German".

---

### Post by steeldriver on 2012-07-21
Hi - like Bachstelze says, the first thing is to understand the difference between compile errors and link errors:

1. compile errors - things like 

```
/home/angus/fanntest/fann1.cpp: 
In function ‘int main()’: 
/home/angus/fanntest/fann1.cpp:4:56: error: ‘fann_create’ was not declared in this scope 
make[2]: *** [CMakeFiles/hello.dir/fann1.o] Error 1
```suggests your fann1.cpp file is not including the header (.h) file where the declaration of fann_create resides - you can likely fix that with an appropriate #include directive

BTW I noticed you have a #include "doublefann**.c**" which is highly unusual - are you sure you are not meant to #include "doublefann**.h**"? Although header files *are* syntactically 'C' files they usually have a particular structure that makes them suitable for preprocessing (which .c files usually don't) 

2. linker errors - thinks like

```
Linking C executable fann1
CMakeFiles/fann1.dir/fann1.o: In function `fann_run':
fann1.c:(.text+0x1ac2): undefined reference to `exp'
fann1.c:(.text+0x1b06): undefined reference to `exp'
```says the linker can't find the object code module where the functions are defined - this indicates a missing library not a missing header file - in this case for 'exp' you will probably need to link the math library 'libm' by adding '-lm' to your gcc command line

Hope this helps - without delving into your makefile it is hard to be more specific about the fixes

---

### Post by Angus1 on 2012-07-21
Thanks guys, firstly the c/c++ thing, when I couldn't make the library work in c++ I tried c as it's written in c natively, and the examples are in c, my intention was to learn c++.

I used CMake because it was the suggested method to install the FANN library, but yes, for now at least, I have no need to use CMake, I'll try compiling the code in the more normal way. 

The .c file is included as this is what the FANN website suggests if all else fails, I think if I get the maths library to work, this should work for most FANN functions, although probably not the best way to do it...

So including the maths library helped, this is what I get now:
```
angus@angus-Rev-1-0:~/fann1$ gcc -o fann1 fann1.c -lm
fann1.c: In function ‘main’:
fann1.c:8:24: warning: initialization makes pointer from integer without a cast [enabled by default]
/tmp/ccw19sRb.o: In function `main':
fann1.c:(.text+0x112b4): undefined reference to `fann_create'
collect2: ld returned 1 exit status
```

For now I'm not to concerned about the ```
fann1.c:8:24: warning: initialization makes pointer from integer without a cast [enabled by default]
``` message, the code doesn't do a lot anyway, I'm just using some FANN functions to see if the libraries working. So the error I'm trying to sort out is the linker error, I need to somehow reference the FANN library when I compile it, like with the -lm? How do I find what code I need to add on the end to get the FANN library to be included, or will I have to specify the location of the library files as it's not a standard library?

Thanks again,
Angus

---

### Post by Bachstelze on 2012-07-21
About the warning: your usage of the fann_crete() function is correct, so a possible problem is that you are not including the correct header. You can get more informative warnings by running gcc like this:

```
gcc -std=c99 -pedantic -Wall -Wextra
```

which is really how you should *always* compile C. Replace -std=c99 with -ansi if you want to compile ANSI C (C89). If you really need GNU extensions, replace with -std=gnu99 or -std=gnu89.

To link with libfann, add something like *-lfann* at the end of your command. If that doesn't work, the documentation should give you the correct flag, or you can find it out from the library filenames.

---

### Post by steeldriver on 2012-07-21
Yes you almost certainly need to link the actual fann library - a quick google search suggests it's libfann (-lfann)

[http://old.nabble.com/Compiling-FANN-samples-td25099366.html](http://old.nabble.com/Compiling-FANN-samples-td25099366.html)

Also you probably need to #include "fann.h" in your source code file

---

### Post by Angus1 on 2012-07-21
I don't know how I missed that post about compiling fann, been looking for a while now, but using the exact code posted in that link, and entering the same thing into the terminal (using fann1.cpp rather than fann.cpp), I still get this:
```
angus@angus-Rev-1-0:~/fann1$ gcc fann1.cpp -l fann -o fann
fann1.cpp: In function &#8216;int main()&#8217;:
fann1.cpp:14:54: error: &#8216;fann_create&#8217; was not declared in this scope
```The only thing I can think it would be is the library files being in the wrong place, but surely then it would say it couldn't find them?

---

### Post by MadCow108 on 2012-07-21
your missing the signature for the function you are using
normally they are provided in system installed header files and included like this:
```
#include "fann.h"
```

---

### Post by Bachstelze on 2012-07-21
.cpp files should be compiled with g++, not gcc.

Again, check that you include the correct headers, and compile with all warnings enabled.

---

### Post by Angus1 on 2012-07-21
Sorry, I should have posted the code with it, that error came from this code, including the fann.h file:

```
#include "fann.h"

int main()
{
const float connection_rate = 1;
const float learning_rate = 0.7;
const unsigned int num_input = 2;
const unsigned int num_output = 1;
const unsigned int num_layers = 3;
const unsigned int num_neurons_hidden = 4;
const float desired_error = 0.0001;
const unsigned int max_iterations = 500000;
const unsigned int iterations_between_reports = 1000;
struct fann *ann = fann_create(connection_rate, learning_rate,
num_layers, num_input, num_neurons_hidden, num_output);
fann_train_on_file(ann, "xor.data", max_iterations,
iterations_between_reports, desired_error);
fann_save(ann, "xor_float.net");
fann_destroy(ann);
return 0;
}
```

---

### Post by Bachstelze on 2012-07-21
You should include the header where fann_create() is declared. Apparently it is not fann.h, so you need to find out which one it is from the documentation, or by grep'ing the files.

---

### Post by Angus1 on 2012-07-21
> **Bachstelze said:**
> .cpp files should be compiled with g++, not gcc.

Again, check that you include the correct headers, and compile with all warnings enabled.
Sorry, missed your reply, thats what I thought, but I was trying to copy exactly what was done in the link MadCow posted, as that apparently worked, i'll try with the warning and g++ now.

---

### Post by Angus1 on 2012-07-21
Get the same thing with warnings and g++:
```
angus@angus-Rev-1-0:~/fann1$ g++ -o fann1 fann1.cpp -lfann -pedantic -Wall -Wextra
fann1.cpp: In function &#8216;int main()&#8217;:
fann1.cpp:15:54: error: &#8216;fann_create&#8217; was not declared in this scope

```

I don't understand how it worked for the guy in the link though, with the fann.h header, and exact same code and compiler settings? There must be something different...

---

### Post by steeldriver on 2012-07-21
it may be an old link - I just pulled it off a google search to get you started

you really need to do what Bachstelze suggested - grep the source tree to find which header file includes the declaration of fann_create

---

### Post by Angus1 on 2012-07-22
Problem solved, fann_create doesn't exist, that code must have been from a past realease of fann, it's now fann_create_standard, changed to that it compiles and links fine! Thanks for the help, now I've just got to figure out how to make it actually do soemthing usefull...

---

### Post by Angus1 on 2012-07-22
Maybe not so solved, when trying to compile c++, using the g++ compiler, it now gives this error:
```
angus@angus-Rev-1-0:~/fann1$ g++ -o fann1 fann1.cpp -lm -lfann
/usr/local/lib/libfann.so: undefined reference to `sin'
/usr/local/lib/libfann.so: undefined reference to `exp'
/usr/local/lib/libfann.so: undefined reference to `cos'
/usr/local/lib/libfann.so: undefined reference to `log'
/usr/local/lib/libfann.so: undefined reference to `pow'
/usr/local/lib/libfann.so: undefined reference to `sqrt'
/usr/local/lib/libfann.so: undefined reference to `floor'
collect2: ld returned 1 exit status

```

Is this because its linking to the c++ math library, and as the fann libarary is written in c, this doesn't work? The fann site seems to suggest you just have to include "fann_cpp.h" after "doublefann.h" to make it work with c++, and lose the fann_ prefix on the commands, although when I tried that it didn't recognise the functions, which makes me think i'm using the languide wrapper wrong...

---

### Post by steeldriver on 2012-07-22
That's likely a link-order thing - try moving the math library (-lm) to the end of the line AFTER -lfann

```
g++ -o fann1 fann1.cpp -lfann -lm
```

---

### Post by Angus1 on 2012-07-22
No luck, I get the exact same message. Although it compiles fine using gcc...

---

### Post by dwhitney67 on 2012-07-22
> **Angus1 said:**
> No luck, I get the exact same message. Although it compiles fine using gcc...

I had my doubts about your statement, so I decided to test your findings, and to my surprise I was able to duplicate the issue.

I wrote my own little C library that employs the use of a math-library function.  I built the library using gcc.

I then developed a C++ program that uses the library, and it failed when attempting to link.

Here's my library code...

Function.h
```

#ifndef FUNCTION_H
#define FUNCTION_H

#ifdef __cplusplus
extern "C"
{
#endif

void function();

#ifdef __cplusplus
}
#endif

#endif

```
Function.c:
```

#include "Function.h"
#include "math.h"

void function()
{
    double x = 10;
    double y = sqrt(x);
    x -= y;
}

```
For the test program:
```

#include "Function.h"

int main()
{
    function();
}

```
To build the library and test program:
```

gcc -fPIC -c Function.c

gcc -shared -o libfunc.so Function.o

g++ Test.cpp -L. -lfunc -lm
./libfunc.so: undefined reference to `sqrt'
collect2: ld returned 1 exit status

```

The solution I found was to build the test library using the math-library, before attempting to use the test library elsewhere:
```

gcc -shared -o libfunc.so Function.o **-lm**

```

---

### Post by Bachstelze on 2012-07-22
It works with

```
g++ Test.cpp -L. -lm -lfunc -lm
```

*EDIT:* and of course another way is

```
g++ Test.cpp -Wl,-no-as-needed -L. -lm -lfunc
```

---

### Post by Angus1 on 2012-07-22
Thanks for the replies, Backstelze, you method did work, although I get FANN Error 11 - Unable to allocate memory when I run the file, but it compiles fine. Is there a document somewhere listing gcc commands? It seems like I need to read one. Compiling with gcc rather than g++ gets me the exact same Error 11 message, the code must be basic enough for it to work with c or c++.

Anyway, although I can now make it compile, I think I'm going to try to work towards writing some very simple neural networks from scratch, that way I should learn far more, rather than just trying to make other peoples code work and not really understanding what's going on.

---

