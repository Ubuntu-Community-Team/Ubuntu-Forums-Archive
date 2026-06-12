---
title: "Simple GCC library and .h question (I hope)"
date: 2009-04-23
forum: Packaging and Compiling Programs
---

### Post by Aped on 2009-04-23
I'm trying to compile something which uses curl - #include "curl/curl.h" is the line that seems to be causing a lot of problems. 

Pretty new to linux and this is a fairly basic program, just hitting a wall with the location and installing of libraries and resources; DL'd and installed libcurl and everything that looked even a little bit related from synaptic; no go. 

Should I copy/paste these files into a specific directory? What am I doin wrong here. 

Thanks for the help! 

PS Yeah I'm a fairly noob when it comes to this stuff.


EDIT: [http://curl.haxx.se/libcurl/c/libcurl-tutorial.html](http://curl.haxx.se/libcurl/c/libcurl-tutorial.html) helped me a lot, nevermid I think!

---

### Post by tom66 on 2009-04-23
Check the quotes -- they should be <angle brackets> for library headers.

---

