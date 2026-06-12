---
title: "installing and using openCV"
date: 2010-05-28
forum: Packaging and Compiling Programs
---

### Post by pablop on 2010-05-28
Hi,

I'm new to C++ and openCV so any help will be appreciated.

I'm trying to install openCV from a package under ubuntu lucid.
Then, I want to compile a simple program and run it.

What packages do I need to install?
Is installing libcv4 and libhighgui4 enough? maybe opencv-doc too?

Do I need to set an env variable or maybe add opencv to the path?

What should I use to compile my main.c example? gcc? something else?

Do I need to add arguments when compiling to tell the compiler where opencv is?

Thanks

---

### Post by SevenMachines on 2010-05-30
Hi there, i'll quickly try and answer a couple of your questions but I think a short introduction tutorial on gcc might be useful, I'll try to find one and post a link

> **pablop said:**
> 
What packages do I need to install?
Is installing libcv4 and libhighgui4 enough? maybe opencv-doc too?

The package you'll need is libcv-dev, install that and it and the package manager will make sure any other packages that are needed will be installed too. Packages ending in -dev contain headers, ie, the .h files you'll need and other stuff for developing with that package
> 
Do I need to set an env variable or maybe add opencv to the path?
-dev packages from the repositories generally install to the proper system directories (often /usr/include/<package>) so this shouldnt be necessary.
> 
What should I use to compile my main.c example? gcc? something else?
Use gcc, there are other compilers but this is by far the most used
> 
Do I need to add arguments when compiling to tell the compiler where opencv is?
This depends, in this case if you had
#include <opencv/cv.h>
then you dont need to tell the compiler where to look for the header since it will automatically search relative to the system directory /usr/include, so the above line will resolve to /usr/include/opencv/cv.h

but if you had 
#include <cv.h>
then you'd need to add the opencv includes directory to the system path with the -I (capital i) option to gcc, ie
-I/usr/include/opencv

you would also need to add the linking option to gcc in any case, along with all the libraries the open cv library needs. you can add all these libraries manually to the command line with the -l option (lower case L), eg -lcv will link to libcv and so on. but if the library you want to link to needs a number of other libraries, this can get complicated and tricky to remember, luckily.......

More usefully -dev packages often include pkg-config information. This means that you can get both the header include directories and the linking done automatically by including the line 
`pkg-config --cflags --libs opencv` 
into your gcc line. This will resolve to 
-I/usr/include/opencv  -lcv -lhighgui -lcvaux -lml -lcxcore  

so a line like
gcc `pkg-config --cflags --libs opencv` -o myprog myfile.c

is actually equivalent to,
gcc -I/usr/include/opencv  -lcv -lhighgui -lcvaux -lml -lcxcore   -o myprog myfile.c

especially with more connected libraries these lines could become large and complicated, whereas with pkg-config you only need to add the name of the library you want to use, in short, use pkg-config if you can!

---

### Post by pablop on 2010-05-30
Thank you very much for the detailed explanation.

I was able to compile and run a simple program.

---

