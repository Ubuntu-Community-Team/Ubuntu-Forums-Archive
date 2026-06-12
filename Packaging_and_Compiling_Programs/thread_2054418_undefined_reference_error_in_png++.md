---
title: "undefined reference error in png++"
date: 2012-09-07
forum: Packaging and Compiling Programs
---

### Post by salmanmanekia on 2012-09-07
Hi All,

I am new to C++ on linux enviroment and am trying to use the png++ library for a project. The problem i am facing is that that a simple program i write using png++ incudes does not work and shows me the following errors

AProg.o: In function `png::info_base::info_base(png::io_base&, png_struct_def*)':
AProg.cpp:(.text._ZN3png9info_baseC2ERNS_7io_baseEP14png_struct_def[_ZN3png9info_baseC5ERNS_7io_baseEP14png_struct_def]+0x21): undefined reference to `png_create_info_struct'
AProg.o: In function `png::info::write() const':
AProg.cpp:(.text._ZNK3png4info5writeEv[png::info::write() const]+0xd4): undefined reference to `png_set_PLTE'
AProg.cpp:(.text._ZNK3png4info5writeEv[png::info::write() const]+0x137): undefined reference to `png_set_tRNS'
AProg.cpp:(.text._ZNK3png4info5writeEv[png::info::write() const]+0x14f): undefined reference to `png_write_info'
AProg.o: In function `png::info::sync_ihdr() const':
AProg.cpp:(.text._ZNK3png4info9sync_ihdrEv[png::info::sync_ihdr() const]+0x79): undefined reference to `png_set_IHDR'
AProg.o: In function `png::end_info::destroy()':
AProg.cpp:(.text._ZN3png8end_info7destroyEv[png::end_info::destroy()]+0x48): undefined reference to `png_destroy_info_struct'
AProg.o: In function `png::end_info::write() const':
AProg.cpp:(.text._ZNK3png8end_info5writeEv[png::end_info::write() const]+0x1a): undefined reference to `png_write_end'
AProg.o: In function `png::io_base::set_swap() const':
AProg.cpp:(.text._ZNK3png7io_base8set_swapEv[png::io_base::set_swap() const]+0x1b): undefined reference to `png_set_swap'
.............. (and it goes on).

The background of what i have done so far.

1 : I have gcc/g++ configured correctly.

2 : I have followed the following instructions ( [http://www.techsww.com/tutorials/libraries/libpng/installation/installing_libpng_on_ubuntu_linux.php](http://www.techsww.com/tutorials/libraries/libpng/installation/installing_libpng_on_ubuntu_linux.php) ) and correctly install libpng-1.2.50. The result seems to be correct.

This is how my usr/local folder looks now

:/usr/local/include$ ls
libpng12  libpng15  png++  pngconf.h  png.h  pnglibconf.h

:/usr/local/lib$ ls
libpng12.a   libpng12.so    libpng12.so.0.50.0  libpng15.la  libpng15.so.15       libpng.a   libpng.so    libpng.so.3.50.0  python2.7
libpng12.la  libpng12.so.0  libpng15.a          libpng15.so  libpng15.so.15.12.0  libpng.la  libpng.so.3  pkgconfig

:/usr/local/bin$ ls
eclipse  libpng-1.2.50  libpng12-config  libpng-1.5.12  libpng15-config  libpng-config  png++-0.2.5

3 : After that i followed the following ( [http://www.nongnu.org/pngpp/doc/0.2.5/](http://www.nongnu.org/pngpp/doc/0.2.5/) ) to install the png++-0.2.5 and all the five steps didnt gave any error.

But after that when i tried to compile a simple program (with the instructions given at the same site : [http://www.nongnu.org/pngpp/doc/0.2.5/](http://www.nongnu.org/pngpp/doc/0.2.5/) ) it would not compile.

:~/workspace/AProg$ g++ -o AProg AProg.o 'libpng-config --ldflags'
g++: error: libpng-config --ldflags: No such file or directory

Then i tried to solve the problem and google it and gave this command which seems to work fine at compile but when i tried to run it. I got the error as mentioned at the top of the post

~/workspace/AProg$ g++ -c AProg.cpp -I/usr/local/include/libpng12 -L/usr/local/lib -lpng -I/usr/local/include/png++
~/workspace/AProg$ 

I am sorry for such a long post. But i just wanted to explain anything /everything related to my problem. Hope somebody helps me here.

---

### Post by spjackson on 2012-09-07
> **salmanmanekia said:**
> 
AProg.o: In function `png::info_base::info_base(png::io_base&, png_struct_def*)':
AProg.cpp:(.text._ZN3png9info_baseC2ERNS_7io_baseEP14png_struct_def[_ZN3png9info_baseC5ERNS_7io_baseEP14png_struct_def]+0x21): undefined reference to `png_create_info_struct'

These are linker errors.

> 
This is how my usr/local folder looks now

:/usr/local/include$ ls
libpng12  libpng15  png++  pngconf.h  png.h  pnglibconf.h

:/usr/local/lib$ ls
libpng12.a   libpng12.so    libpng12.so.0.50.0  libpng15.la  libpng15.so.15       libpng.a   libpng.so    libpng.so.3.50.0  python2.7
libpng12.la  libpng12.so.0  libpng15.a          libpng15.so  libpng15.so.15.12.0  libpng.la  libpng.so.3  pkgconfig

:/usr/local/bin$ ls
eclipse  libpng-1.2.50  libpng12-config  libpng-1.5.12  libpng15-config  libpng-config  png++-0.2.5

I haven't used png++ or read it's documentation. However, I've looked at the next document you refer to.

> 
But after that when i tried to compile a simple program (with the instructions given at the same site : [http://www.nongnu.org/pngpp/doc/0.2.5/](http://www.nongnu.org/pngpp/doc/0.2.5/) ) it would not compile.

:~/workspace/AProg$ g++ -o AProg AProg.o 'libpng-config --ldflags'
g++: error: libpng-config --ldflags: No such file or directory

That is the link step. Your mistake is using the single-quote character ' when you should be using the back-quote character ` Note also that this will only work if /usr/local/bin is in your path.


> 
~/workspace/AProg$ g++ -c AProg.cpp -I/usr/local/include/libpng12 -L/usr/local/lib -lpng -I/usr/local/include/png++
~/workspace/AProg$ 

That is the compilation step. You don't need the link options for this step but it doesn't do any harm. You do need the link options for the link step that you mentioned at the top of your post.
```

either
g++ -o AProg AProg.o `libpng-config --ldflags`
or
g++ -o AProg AProg.o -L/usr/local/lib -lpng

```
should suffice. (Again the first option requires /usr/local/bin to be in your path.)

---

### Post by salmanmanekia on 2012-09-07
Thank you for such a descriptive answer and explanation. It worked :)

---

