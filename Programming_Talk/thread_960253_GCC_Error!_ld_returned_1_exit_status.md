---
title: "GCC Error! ld returned 1 exit status"
date: 2008-10-27
forum: Programming Talk
---

### Post by shimmey on 2008-10-27
The ERROR information is:
/tmp/ccSmkZjg.o:(.eh_frame+0x11): undefined reference to `__gxx_personality_v0'
collect2: ld returned 1 exit status

I write all the code in only one *.cpp file. When typed:
gcc mf.cpp -o mds
the something wrong happened...
I don't know why.


shimmey@shimmey-laptop:~/c$ gcc -v
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,fortran,objc,obj-c++,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --with-gxx-include-dir=/usr/include/c++/4.2 --program-suffix=-4.2 --enable-clocale=gnu --enable-libstdcxx-debug --enable-objc-gc --enable-mpfr --enable-targets=all --enable-checking=release --build=i486-linux-gnu --host=i486-linux-gnu --target=i486-linux-gnu
Thread model: posix
gcc version 4.2.4 (Ubuntu 4.2.4-1ubuntu3)

---

### Post by hod139 on 2008-10-27
Try using the command g++ instead of gcc.  The g++ command is used for compiling C++ code (whereas gcc defaults to C code), and will automatically link against libstdc++.so.  If you really want to use gcc to compile, you must manually tell it to link against the c++ library, e.g. ```
gcc foo.cpp -l stdc++
```

---

### Post by snova on 2008-10-27
If you don't use the C++ library for anything, you could also just link with the language support library (libsupc++).

I don't know what __gxx_personality_v0 does, but it's part of the C++ runtime.

---

### Post by shimmey on 2008-10-28
Thank you very much!
I did as you said, and it worked very well!
Thanks again!!!

---

### Post by ramreddy502 on 2013-02-08
hello,

 how did you solve the problem you are told above "c*ollect2: error: ld returned 1 exit status"*
  i also having the same problem in building of speech tools
please tell me the solution

thanks in advance

---

### Post by r-senior on 2013-02-08
You don't provide enough information for an answer other than to advise you that you are not linking your code properly.

Could you start another thread and give details of the code you are trying to compile and the commands you are using to compile it?

(Please wrap any code you post in code tags, or use the # button in the posting toolbar).

---

### Post by ramreddy502 on 2013-02-08
hello,
thanks for your response. i am building speech tools in the part of text to speech synthesis.
while building speech tools i got few errors in the code  like 
"memcpy" was not declared inthis scope  and  "memset" was not declared in this scope

then i have added "string.h" header file to that particular code so that i have escaped from those errors. at last  i got error as shown below

gcc -O3 -Wall -o ch_lab ch_lab_main.o -L../lib -lestools -L../lib -lestbase -L../lib -leststring -lcurses -ldl -lncurses -lm -lstdc++ -lgcc
/usr/bin/ld: cannot find -lcurses
/usr/bin/ld: cannot find -lncurses
collect2: error: ld returned 1 exit status
make[1]: *** [ch_lab] Error 1
make: *** [main] Error 2

how should i solve this problem
thanks in advance

---

### Post by r-senior on 2013-02-08
It looks like you need to install curses libraries. As a start, you could try:

```
sudo apt-get install libncurses5-dev
```

I don't know if that picks up curses as well as ncurses. We'll see.

I'm assuming you didn't write this code?

---

### Post by ramreddy502 on 2013-02-11
thank you very much it is working

---

