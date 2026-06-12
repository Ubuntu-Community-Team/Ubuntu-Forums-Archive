---
title: "dll from VS"
date: 2007-11-06
forum: Programming Talk
---

### Post by nbo10 on 2007-11-06
A while back I wrote a little dll, in c++, with microsoft visual studio. The dll called a c function in another library.  I used this dll to call the c function from c# programs. Now I want to use this dll in a c++ program under linux. Can I do this and if so how do I do this? Thanks

---

### Post by Wybiral on 2007-11-06
I don't think you can. Linux uses a different different dynamic library format and since it was compiled in VS it's likely the machine code wouldn't even be compatible.

---

### Post by nbo10 on 2007-11-07
Is there a way I can recompile it into something usefull for linux? I can also recomplie it on a Sun station under unix if that would help me out. Thanks

---

### Post by dashnak on 2007-11-07
You could try something with the mono project:
[SIZE=-1]www.**mono**-**project**.com/[/SIZE]

---

### Post by nbo10 on 2007-11-07
I don't want to use .net.

---

### Post by pmasiar on 2007-11-07
> **dashnak said:**
> You could try something with the mono project:
[SIZE=-1]www.**mono**-**project**.com/[/SIZE]

Don't mind this advice - it is just another example how misleading advice here can be. 

dashnak did not bothered to explain hos mono, written in C#, could be helpful to compile C++ .DLL.

I am not expert, but IIRC mingw or something is compatibility library between Linux and Windows. As all these efforts, it is far from perfect: it is hard to make systems compatible if profits of MSFT are based on being incompatible :-)

IMHO you are experiencing a case of vendor lock-in. maybe this lesson will teach you to avoid it next time... :-)

---

### Post by DMills on 2007-11-07
Ok, so you have a dll written in C++, first question:

Is it really straight C++ without any compiler specific extensions?
If so, you should be able to compile it to an object file with something like: 

 ```
g++ -W -Wall -g -c dll.cpp -odll.o
```

If that works then just use the normal process for linking a shared library (google for it, this is too long already).

Now, in all probability that will fail with many pages of error messages, all that __DLLSPEC__ and stdcall cruft is unnecessary under Linux, some suitable #defines will get rid of it for you, but now comes the interesting bit, any use of Microsoft specific functions and classes will have to be revised to use  either standard C++ or the Posix (or even Linux specific) equivalents. 

Some things have no direct equivalent, because the whole architecture is so different, WaitForMultipleObjects for example is a pain in the **** to implement under Linux, and obviously all the MFC stuff is missing.

There **MIGHT** be an easier (If horribly clunky) way.... 
The WINE project has a library that can load (and provide linux native access to) windows DLLs on X86 hardware, and it even sometimes works, but it is a fairly hideous way to do such things. 

Note that DLLs and ELF shared libraries have rather different run time symbol resolution behaviour and while this is unlikely to bite you for something simple, it can be a problem if doing anything hairy. 

Regards, Dan.

---

