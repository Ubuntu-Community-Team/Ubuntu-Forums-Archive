---
title: "globals"
date: 2010-08-07
forum: Programming Talk
---

### Post by noobermin on 2010-08-07
This is probably a noob question, but oh well.

I've read somewhere that globals are best defined on the stack. That's nice and all, but how about when you have large resources (image files, etc.) that you'd rather be global to all parts of the program and can't simply be defined on the stack? I can define the pointer on the stack in one file then have others have an extern in    the other files, but yes, the actual data is on the heap.

How is that a problem? Unless you just are sloppy?

Now I know you could send the address of said resources to each and every function in other files that uses them, and then you are conscious about what you're sending to who, but then that makes things more cumbersome, having to make long arrays of pointers to the resources, for example, when simply defining them global, and being careful, will do.

Thanks.

---

### Post by schauerlich on 2010-08-07
> **noobermin said:**
> That's nice and all, but how about when you have large resources (image files, etc.) that you'd rather be global to all parts of the program and can't simply be defined on the stack? I can define the pointer on the stack in one file then have others have an extern in    the other files, but yes, the actual data is on the heap.

You're given a relatively small amount of memory on the stack to work with, whereas the amount of heap space you're allowed to request scales with the amount of available memory. Thus, big things go on the heap, and small local things go on the stack.

> How is that a problem? Unless you just are sloppy?

You run the risk of corrupting the stack. Taking a random global that you may or may not know the size of and manipulating it is asking for a buffer overflow. It's not as big of a deal on small projects where one person is doing all of the coding, and would already know the details of the implementation.

---

### Post by nvteighen on 2010-08-07
> **noobermin said:**
> This is probably a noob question, but oh well.

I've read somewhere that globals are best defined on the stack. That's nice and all, but how about when you have large resources (image files, etc.) that you'd rather be global to all parts of the program and can't simply be defined on the stack? I can define the pointer on the stack in one file then have others have an extern in    the other files, but yes, the actual data is on the heap.

How is that a problem? Unless you just are sloppy?

Now I know you could send the address of said resources to each and every function in other files that uses them, and then you are conscious about what you're sending to who, but then that makes things more cumbersome, having to make long arrays of pointers to the resources, for example, when simply defining them global, and being careful, will do.

Thanks.

The issue with that IMO is that it makes things less abstracted and less mantainable. Probably, a struct/class may help you there to avoid "large arrays of pointers" by packing the stuff into a single "opaque" unit. That way, passing the struct to the functions that need it won't be that cumbersome...

Now, the reason why globals are considered "evil" is because in large projects they can make things terribly difficult to debug: imagine having a global variable affecting several modules in 100 modules-large project... Where do you start your search? Who's the faulty function that's setting the global incorrectly? 

Ok, sometimes you might see globals in "professional" code, but you'll soon notice the "allowed" globals tend to be 1) static (i.e. access restricted to the file) and 2) usually very general stuff that doesn't affect the program's behaivor save for very very specific stuff usually related to error diagnoses or well... not rather what the program's supposed to do but just to check the program's execution status... I'm not sure if you get what I mean... Take for example errno.h in C: that one thing that header makes available is a global variable called errno which functions can use to set an error code when they also have to return something else in case of failure.

That's the "best" usage of globals... Of course, other situations may arise where a global may be of use.

BTW, noob questions are always welcome when honest: we all were noobs at some point and we all have the right to learn :) Keep learning and asking!

---

