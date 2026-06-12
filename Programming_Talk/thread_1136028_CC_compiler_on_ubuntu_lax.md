---
title: "CC compiler on ubuntu lax?"
date: 2009-04-24
forum: Programming Talk
---

### Post by lurikeen on 2009-04-24
I've noticed that ubuntus CC compiler is not as strict as it should be. I can incorrectly free pointers which no longer exist, ect. Any other distro, or cygwin, will core dump when this happens, but for some reason ubuntu doesnt. I need a legitimate compiler to do my work on, but I'd like to keep working on ubuntu. Is there a way I can standardize my compiler or something? I've done sudo apt-get install build-essentials, but that hasn't helped.

---

### Post by Namtabmai on 2009-04-24
Err gcc is a legitimate compiler.

As defined by the standard, [here]("http://www.opengroup.org/onlinepubs/009695399/functions/free.html") free'ing a address that wasn't allocated by malloc causes undefined behaviour, while free'ing a NULL pointer is fine.

The real question is why aren't you clearing your pointers after free'ing them?

---

### Post by lurikeen on 2009-04-24
I'm a student so I'm still in the learning process. My project worked fine under ubuntu, but when demoing it on the Solaris machines at school (with gcc), it failed to work. It also failed to work under linux mint and Cygwin, but I assumed ubuntu was the only OS that got it right, since Cygwin is prone to errors and mint seems like it complies with linux standards a bit less.

I can post the code if it would help; I just need to wait a few hours for the due date to pass on it (the chance is low, but if my code is copied, im screwed).

---

### Post by lurikeen on 2009-04-24
I might be completely wrong here, since I don't fully know what I'm talking about, but could it just be a difference in how the kernel handles deallocated memory? I.E, in ubuntu, you can still access the data at address x after it is freed (as long as it has not been overwritten yet), whereas other kernels would consider that a segmentation fault, since the program no longer owns the memory yet is attempting to read it?

---

### Post by Namtabmai on 2009-04-24
ah o.k.

The site I linked to contains the standard for the basic C functions ( such as malloc/free/etc ). They're fairly dry reading but it's worth taking a look through when you are familiarising yourself with new functions as they will tell you how the standards expect them to work.

For example the link I gave you tells you that ( in a round about way, as I said they are dry documents ) you can free a pointer created with calloc, malloc, posix_memalign, realloc or strdup. And you can also free a NULL pointer. But if you try to free something else, such as a pointer that you have already previously free'd, the behaviour is undefined.
It's this undefined behaviour you have to watch out for on different compilers, as it implies, each compiler can do what ever it likes in this circumstance. For example, while not likely to happen, it's possible that free'ing a previously free'd pointer in one compiler would turn your entire room pink. Very unlikely, but that is the nature of undefined behaviour. :)

For me, I try to think of malloc and free'ing in the same way as I think of braces. You have to put a { and a } around your functions, and around for loops. In the same way you have to free everything you malloc. Too many braces/frees is just as bad as too few braces/frees.

It does sound like something is wrong in your code so posting it will help track it down.

---

### Post by lurikeen on 2009-04-24
Ah, I didn't realize that undefined meant it could differ from compiler to compiler. I will post the code when I can. However is there some way to put the Mint version of gcc (I thought this was standard but I guess distro has something to say about it) onto ubuntu? Memory errors are fairly common so I'd like to encounter the same errors I would on a test machine here at school.

---

### Post by Namtabmai on 2009-04-24
Actually undefined can not only differ from compiler to compiler, but also theoretically differ each time you run the program. Again the beauty of undefined.

Much simpler in the long run to find the errors in your code and learn from them.

---

### Post by CptPicard on 2009-04-24
> **lurikeen said:**
> I might be completely wrong here, since I don't fully know what I'm talking about, but could it just be a difference in how the kernel handles deallocated memory?

The combination of kernel and standard library to be exact, but yes, this is the point. It is not the job of the *C compiler* to produce code to keep track of what pointers are released and what not and how to deal with for example a repeated free; that sort of functionality would be beyond what it is supposed to be doing... hence the undefined behaviour.

---

### Post by lurikeen on 2009-04-25
> **CptPicard said:**
> The combination of kernel and standard library to be exact, but yes, this is the point. It is not the job of the *C compiler* to produce code to keep track of what pointers are released and what not and how to deal with for example a repeated free; that sort of functionality would be beyond what it is supposed to be doing... hence the undefined behaviour.

Thanks. Got it now.

> Actually undefined can not only differ from compiler to compiler, but also theoretically differ each time you run the program. Again the beauty of undefined.

Much simpler in the long run to find the errors in your code and learn from them.

That is what I'd like to do, but at this stage, seg faults let me know there are errors :)

---

### Post by Zugzwang on 2009-04-26
> **lurikeen said:**
> That is what I'd like to do, but at this stage, seg faults let me know there are errors :)

Then debug your program using valgrind:
```

valgrind --tool=memcheck ./yourProgram

```
It will show you when you try to access memory not allocated/already freed/etc. in your program even if this does not cause seg-faults (but may do so sometimes on some machines). It's a very helpful tool!

---

### Post by monkeyking on 2009-04-26
The canononical is that
'undefined behavior will make daemons fly out of you nose'

[http://www.everything2.net/title/demons%2520fly%2520out%2520your%2520nose](http://www.everything2.net/title/demons%2520fly%2520out%2520your%2520nose)

---

