---
title: "eclpse c++"
date: 2009-01-18
forum: Programming Talk
---

### Post by elad2109 on 2009-01-18
hey all,

I would appreciate help with some questions:

1. I was given a compiled already lib (X.so)a and it's header (X.h).
I'm supposed to create a new instance of class Y which is implemented  in file X. how can I do this? I mean i added X.h to the file of function main(). I entered the project properties::C/C++ Build::Setting::
added the X.so to the compiler dir and to the linker lib. I guess I did it right because building the project doesn't retrieve errors. but running fails... 

2. In that case above and in other cases, after compiling and building the project with success - I try to debug or run the project but neither of them works. It says: "Binary not found". what does that mean?

Many Thanks

---

### Post by Zugzwang on 2009-01-18
Can you find out which binary hasn't been found? Did you install the build-essentials package?

---

### Post by elad2109 on 2009-01-18
how can i find out with binary is missing?

how can i re-install the essentials package just to make sure it's installed?

the thing is, that other small programs are running properly...

---

### Post by Zugzwang on 2009-01-18
> **elad2109 said:**
> 
how can i re-install the essentials package just to make sure it's installed?


You don't need to.

So you are saying that the build process went correctly. Try to locate the executable produced and run it from the terminal.

---

### Post by elad2109 on 2009-01-18
found the problem...
but don't know how to fix it

the program don't find the path to the X.so (the Linker or the Compiler...i guess)
could you help me in a step-by-step instructions how to define the path to that X.so ?

---

### Post by Namtabmai on 2009-01-18
If you right click on the project folder in the navigator window and select properties that'll bring up the project properties windows.

You should see a section called "C++ Project paths", click on this and then on the "libraries" tab.

---

### Post by elad2109 on 2009-01-18
> **Namtabmai said:**
> 
You should see a section called "C++ Project paths", click on this and then on the "libraries" tab.

I entered properties.
entered the path to the libraries tab..

still doesn't work...

I added printscreen of the my  unsuccessful tries...
retrieve error:

Description	Resource	Path	Location	Type
cannot find -lFactoryReport	ConfTest		0	C/C++ Problem


FactoryReport.so is the compiled in advance file

---

### Post by Namtabmai on 2009-01-18
Hmm o.k. and the FactoryReport library is directly inside that directory, rather than a subdirectory of that directory?

---

### Post by elad2109 on 2009-01-19
yes,

I copied it from the properties of the FactoryReport.so 
its location is /home/elad/.../ConfTest/FactoryReport.so

I have troed to put it with the whole name as well (meaning the file's name as well in the location)

---

