---
title: "compiling source code in ubuntu using G++"
date: 2008-11-26
forum: Programming Talk
---

### Post by nonzer0 on 2008-11-26
I know this question has to have been answered, but I have yet to find it.  Please keep in mind, for the following example, there will be more to this question based on who responds and how.

I have a wii, and back when I was using XP, I used region frii, rawdump, and other programs.  Now, I have a question. 

If I have the source code for any given program in windows/osx, is it only a matter of cd-ing to the directory of the source code, and using g++ to compile it (example: g++ -o regionfrii_Ubuntu regionfrii.cpp)??
I am almost done with my first programming class, so I know VERY LITTLE when it comes to compiling with ANY IDE.  Is it only a matter of grabbing the source code and compiling, or if different headers are needed.  I am not sure if linux source would be different than windows. I am ignorant at this stage.  

I hope someone can provide a clear, concise answer, as I am an amature, and hope to use this knowlege to help others.

---

### Post by nonzer0 on 2008-11-26
If possible, could someone provide a concrete example of how one would use a source code file and compile and run it under linux?

---

### Post by mdawg414 on 2008-11-26
It seems to me what you are doing would work. That's what I would do at least. You could cd to the directory or just include it in your path name like so:

```

g++ /home/yourname/mycode/code.cpp -o /home/yourname/Desktop/runme

```

---

### Post by samjh on 2008-11-26
> **nonzer0 said:**
> If possible, could someone provide a concrete example of how one would use a source code file and compile and run it under linux?It depends on how the source code is packaged, what build system it uses, etc.


In the simplest case, assuming there is only one source code file (helloworld.cpp):
```
g++ helloworld.cpp -o helloworld
```


If there are multiple source code files (main.cpp contains main(), and greeting.h and greeting.cpp are other files, all in the same directory):
```
g++ main.cpp greeting.cpp -o helloworld
```would compile main.cpp and greeting.cpp, link appropriately, and produce an executable named, helloworld.


If your program uses a library (where the library name is "mylib", headers are located in /home/me/project/src/mylib/headers, and the library file is located in /home/me/project/src/mylib/libs):
```
g++ hellolibrary.cpp -o hellolibrary -I/home/me/project/src/mylib/headers -L/home/me/project/src/mylib/libs/ -lmylib
```


There are other scenarios, too numerous to list here.

Ask away. ;)

---

### Post by nonzer0 on 2008-11-26
Thanks for the reply guys/gals.  Wow samjh, that last example has my head spinning.  I appreciate the info and will be asking more questions, most likely after I am done with finals.

---

