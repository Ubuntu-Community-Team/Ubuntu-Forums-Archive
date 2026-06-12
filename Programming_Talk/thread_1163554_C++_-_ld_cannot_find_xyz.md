---
title: "C++ - ld cannot find xyz"
date: 2009-05-18
forum: Programming Talk
---

### Post by rudeltier on 2009-05-18
That might not be a very uncommon question, but I could not figure out how to solve after sveral hours by now. I am trying to build a very basic programm to try out some API functions. For that, I need to use the header file "AnaGateDllCan.h". This file is present in my project directory aswell as under /usr/lib/. I included it with #include and I did add it with -l for the linker.
Whatever I do, the linker always tells me that it could not find the file.
> /usr/bin/ld: cannot find -lAnaGateDllCanWhen I remove the name from the linker I get a > undefined reference to error for all functions included in this header file. However, the function call is correct since I took it from an example which came with the API.
Since I did tried everthing I could think of and find in the internet I am short on ideas. Can anyone help me?

Using: Ubuntu 8.04, Eclipse 3.5.0, CDT 6.0.0

---

### Post by dwhitney67 on 2009-05-18
A header file... that is, those with a .h extension... generally only provide the definition(s) of functions, not the implementation!  The implementation is generally available in a shared-object or an archive library, which are those files ending in a .so or .a, respectively.

Compiling and linking are two separate steps.  Compiling requires knowledge of the function definitions, which is why you include header files in the program.  When you link your object file(s), then the linker (ld) needs to know where your library is located at.  For system libraries, this is typically /usr/lib, which in this case, you do not need to specify the path since it is already known to ld.  If your library is in a different path, then you need to specify that path using the -L option, and provide the name of your library using the -l (lowercase ell) option.  For example:
```

g++ -I/path/to/special/headerfile MyFile.cpp -L/path/to/special/library -lspecial

```
where '-lspecial' is the short-hand notation for libspecial.so (or .a).

---

### Post by rudeltier on 2009-05-19
Hey, thanks a lot. The -L option was, what I was looking for. I had two .so files installed but did not know that I had to tell the compiler where they are, since I suspected them to be in the right place. Since they obviously were not I needed the -L and now it works fine.
Thank you!

---

### Post by rudeltier on 2009-05-20
Hey, it's me again. Now I, or better my co-worker has a different problem with the same libs. As I said before, for me this works fine now, however we are having some problems 
with his computer. It is the complete same setup, hardware and software. 
However, if he starts the compiled project he always gets this problem:
>     /home/joe/workspace/canTest2/Debug/canTest2: error while loading shared libraries: libAnaCommon-1.0.9.so: cannot open shared object file: No such file or directory
  

The program compiles fine, no problems there. This error appears as he tries to start the program.
The .so is in /usr/local/lib/, consisting of a link "libAnaCommon.so" pointing to the above mentioned exact name of it.
We've restarted eclipse and the system itself, reinstalled the libs. Everything is as it is supposed to be. We have no clue why it is not working since everything seams fine.
Any ideas where this could come from?

---

### Post by dwhitney67 on 2009-05-20
There's a couple of ways to sort this issue out; here's the easy way (if you have root-privileges)...

1.  Create/Edit /etc/ld.so.conf.d/libc.conf, and add the following to it:
```

/usr/local/lib

```

2.  Then run 'ldconfig'
```

ldconfig

```

The "harder" way is not really harder, but just tedious to enter when running an app.  Sometimes though, this is the proper way to do things, especially if you have multiple versions of the same library and you need to pick/choose which to use.  From the command line:
```

LD_LIBRARY_PATH=/usr/local/lib <yourapp>

```
where <yourapp> apparently is /home/joe/workspace/canTest2/Debug/canTest2

---

### Post by rudeltier on 2009-05-26
Hi dwhitney67, thanks again for your help.
We did work it out with an update of our IDE, so I still do not know what the problem was, what is kinda bad. But since it works now it is fine I guess.
Anyway, your comments gave me some clues about this stuff, so thanks a lot for that!

---

