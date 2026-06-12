---
title: "Adding a New Struct to the Kernel"
date: 2007-10-24
forum: Programming Talk
---

### Post by DBQ on 2007-10-24
Hey Guys,
    I want to define a struct in the kernel, such that  it will be visible to the user code as well as the kernel code (kind of like timespec and timeval, which are defined in the kernel, but can be accessed by both user code and kernel code).  

I tried almost everything I can think of.  I even tried defining this new struct in time.h, however, the user code refuses to see it.  Any ideas?

---

### Post by dumbsnake on 2007-10-24
Kernel space and userspace are 2 distinct places.  Userspace can't read kernel memory.  Sure, the kernal can map a page so that userspace can see it, but in general, it just doesn't work this way.

I'm not sure I completely understand what you are trying to do.  If you define a structure in a header file and include it (in either kernel or user code), it will be viewable to the rest of the file in which it is included.

Could you post code perhaps to clarify what you are trying to do?

---

### Post by DBQ on 2007-10-24
All I am trying to do is define a new type of struct in the kernel.  I want this struct to be visible to both the user CODE and kernel CODE.  For example, timespec is defined in kernel file time.h, but is visible to both user code and kernel code.  All you have to do it is to include it.  However, even when I declare the struct in time.h it is not visible to the user code, ie compiling the user program gives error saying it does not recognize my struct.

---

### Post by dumbsnake on 2007-10-24
And you are including time.h ?

The only way I could imagine it happening such that you would include time.h in your userspace code and not see the structures you defined is if time.h has some precompiler voodoo so that your struct isn't getting included or your #include statement is including the wrong time.h...

---

### Post by DBQ on 2007-10-24
I use the time.h in include/linux/time.h.  Also, it comes right after the timespec declaration, and that gets included.

---

### Post by dumbsnake on 2007-10-24
what does your userspace code look like?  Do you have something like:

```
#include "linux/time.h"
```


or how are you telling C++ to include the file?  timespec is defined in way more than just time.h so the fact that it is defined doesn't mean that /linux/time.h is being included in your usercode, but I could probably help you more if you provided sourcecode - atleast the #include directives that you think are including or should include linux/time.h

---

### Post by DBQ on 2007-10-25
Right now its simple.  In /include/linux/time.h right after the timespec struct i declare mine.  In the client program i just do #include<time.h>.

---

### Post by dumbsnake on 2007-10-25
change your code to include "linux/time.h" because right now you are including /usr/include/time.h which has the timespec structure defined.

---

### Post by DBQ on 2007-10-25
I get an error which says redefinition of timespec and time val,
and talks about something select.h and types.h

---

### Post by dumbsnake on 2007-10-25
That is because really shouldn't be including linux/time.h in user code because that header is for writing kernel code.  You probably shouldn't be changing the linux/time.h file anyway.  What is your goal?  Perhaps if you explain what you are trying to do, someone will be able to help you figure out how to accomplish it.  But, if you are having problems with these types of errors, you probably don't want to be messing with the linux kernel.  Kernel development is not easy.  I recommend you buy a book on linux kernel development before you start messing with the kernel code.  I hope I have been helpful to you.

---

### Post by DBQ on 2007-10-25
My goal is for the client program and the kernel to be able to communicate using a struct variable. However, in order to acomplish this      
I need for both of them to be able to see the struct of the type.  However, my thing is how do I define this struct so both the kernel and the users can see it.

---

### Post by pmasiar on 2007-10-25
My answer is: "if you need to ask how to do that, you are not ready to do that".

Kernel is special place. Join some project to learn how kernels insides works - ie KGH started big driver project. You have years of study ahead of you untill you learn enough to be worthy.

Subscribe to Linux Weekly news, and read archives. It's editor, Corbet, is accomplished kernel expert, gives talks on international conferences. Loads of deep info about kernel structure and workings.

---

