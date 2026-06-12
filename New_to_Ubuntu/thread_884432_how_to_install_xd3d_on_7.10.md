---
title: "how to install xd3d on 7.10"
date: 2008-08-09
forum: New to Ubuntu
---

### Post by coolfusion on 2008-08-09
hey ! 
can anybody please tell me how to install xd3d on ubuntu 7.10.
i have got the source file from the website.i extracted it and 
when gave the command $./configure 
it gave me reply 

bash: ./configure: /bin/csh: bad interpreter: No such file or directory
 it require g77 which i have please help !!!!!!!!

---

### Post by SZ07 on 2008-08-09
Damn this was difficult, but I was finally able to compile from source. I'll attach the .deb package I created and you can just install that.

Note: your error is occurring because  you probably don't have csh installed (you can get it from synaptic). Anyway, if the package doesn't work this is how I was able to compile it on Ubuntu 8.04:

1. Make sure you have all of these installed before beginning:
```
cpp-3.4 
g77 
g77-3.4 
gcc-3.4 
gcc-3.4-base
libg2c0 
libg2c0-dev
csh
libxpm-dev
```

2. Extract xd3d and in the terminal browse to its directory

3. Type "./configure" and answer the prompts by typing in the suggested stuff except for libX11.a. The correct directory for that is "/usr/lib/"

4. Type "make clean"

5. Type "make" (hopefully everything works out)

6. Then, if there are no errors, type "make install"

And that's it. Hopefully I didn't miss any steps. If you have an error post it below.

---

