---
title: "C++ exception handling not working properly"
date: 2008-01-18
forum: Programming Talk
---

### Post by me_himanshu on 2008-01-18
Hi,
      I have written a code in C++..I have used standard C++ exception handling in it (simple 'try' and 'catch')...But some errors like 

-segmentation fault 
-floating point exception etc.

are not caught but my application crashes instead.

while the only exception :

- bad alloc 

is being properly caught

I dont know whatz wrong. 



Thanks in advance
Himanshu

---

### Post by CptPicard on 2008-01-18
I have never heard that you could try catching segfaults in the first place, and floating-point issues are the same... when there is nothing thrown, you can't catch it.

---

### Post by wolfbone on 2008-01-18
[QUOTE="The C++ Annotations"]Four classes derived from std::exception are offered by the language:

    * std::bad_alloc: thrown when operator new fails;
    * std::bad_exception: thrown when a function tries to generate another type of exception than declared in its function throw list;
    * std::bad_cast: thrown in the context of polymorphism (see section 14.5.1);
    * std::bad_typeid: also thrown in the context of polymorphism (see section 14.5.2); 

[/QUOTE]

[http://www.icce.rug.nl/documents/cplusplus/cplusplus08.html](http://www.icce.rug.nl/documents/cplusplus/cplusplus08.html)

---

### Post by me_himanshu on 2008-01-18
so,
there no way in this world to catch segmentation faults and floating point exceptions in linux. Am i right sir?

---

### Post by wolfbone on 2008-01-18
> **me_himanshu said:**
> so,
there no way in this world to catch segmentation faults and floating point exceptions in linux. Am i right sir?

No - you can use signal handlers.

$ info libc signal

---

### Post by CptPicard on 2008-01-18
Although even that isn't really "catching" it in the sense of turning it into something handleable and recoverable... segfaults are OS-level situations where it just kills the process with the added option of graceful shutdown by signal handler, but it's definitely not comparable to exception handling. After all, if your code produces a segfault, it's got a major bug to start with, so it's probably not wise to just let it carry on...

---

### Post by wolfbone on 2008-01-18
Probably not wise, no. The only time I've ever done anything like that was in a CL program where division by zero in runtime generated code was normal and CL's condition system allows you to handle/ignore such things.

---

### Post by kevykev on 2008-01-18
> **me_himanshu said:**
> so,
there no way in this world to catch segmentation faults and floating point exceptions in linux. Am i right sir?

Well it's not just linux. You can't try/catch segfaults on any operating system just using standard c++

---

### Post by aks44 on 2008-01-18
> **kevykev said:**
> Well it's not just linux. You can't try/catch segfaults on any operating system just using standard c++

I agree on the *standard* part, where segfaults are part of the UB realm.


But in practice, MS Windows (and possibly other OSes, although I doubt it) has a mechanism called Structured Exception Handling to handle segfaults (aka. "access violations" in Microsoft jargon), FPU errors, privileged instruction errors etc (basically, most hardware-related errors).

SEH integrates so well with C++ exceptions (although originally they have little in common) that some Windows/C++ implementations even use it as the basis for their exception management, while some other implementations offer an almost transparent way to translate SEH exceptions to C++ exceptions. The final result being that on MS Windows you can actually catch hardware errors using the C++ exception mechanism.


So I can understand the OP's confusion: when I switched to Linux I too was *very* confused about signal handling even though I knew the principles beforehand.

If my opinion about that has any value (which I doubt ;)) I believe this is one of the very few technical details where MS OSes are superior to *nix OSes (in a C++ context, mind you): on Windows, a segfault is handled like any other C++ exception, with the benefit of easy recovery and/or clean shutdown.
Of course other languages (including C) may not really benefit from SEH (and it may even be a nuisance). So the opinion I stated really is biased. :)

---

### Post by vexorian on 2008-01-18
> If my opinion about that has any value (which I doubt ) I believe this is one of the very few technical details where MS OSes are superior to *nix OSes (in a C++ context, mind you): on Windows, a segfault is handled like any other C++ exception, with the benefit of easy recovery and/or clean shutdown. In my opinion It's one of those cases in which windows' solution is just lame and pointless adding more dependencies to your software and stuff. Most of the times this feature will just help you get a nice looking error message, cause one a program begins causing "access violation" it is already doomed anyways, can't think of a way to repair it with exception handling. 

To detect the cause of a segfault in Linux I use valgrind

```

sudo apt-get install valgrind

```

Then I run the program prefixing valgrind to its command. (In console)

It will show you the line and moment your program makes mistakes regarding memory, just fix them all (belonging to your program, ignore core lib stuff) and you are done.

---

### Post by aks44 on 2008-01-18
> **vexorian said:**
> In my opinion It's one of those cases in which windows' solution is just lame and pointless adding more dependencies to your software and stuff. Most of the times this feature will just help you get a nice looking error message, cause one a program begins causing "access violation" it is already doomed anyways, can't think of a way to repair it with exception handling.

IMHO there are two things you failed to take into account (as far as I can tell from your post):

(1) When it comes to segfaults, I guess I should have emphasized more on "clean shutdown". Proper C++ code relies on exception-safe idioms (using the RAII mechanism). In the event of a segfault on Windows, such exception-safe code can and will shutdown correctly, finalizing its resources during the stack unwinding. This is particularly useful when dealing with persistent resources (files) as this ensures that all error paths eventually behave correctly.
On Linux, in the event of a segfault you are limited to plain old C semantics for signal handling, which hardly mix with C++ code. Since you can't safely throw C++ exceptions from signal handlers, all the nifty exception-safe code you wrote that relies on RAII is just plain useless. If your program works with persistent resources, you have to write a whole bunch of code just to make sure that *if* there is an unexpected bug in your production code it doesn't end up corrupting your customer's precious data files. Talk about productivity and reliability...
Granted there are tools and methodologies to mitigate the risk of such critical bugs making it into release, but anyone claiming that this *can't* happen is just plain dishonest IMNSHO.


(2) To a lesser extent, many other hardware errors (eg. FPU errors) can be easily recovered from, if both the OS and language cooperate together to allow such recovery. Again, why should my server be killed in the event of (or why should I have to waste time writing and maintaining tons of code just to handle) bugs that may have slipped into production code?



Defensive (I should really say paranoid) programming has saved my *** uncountable times, but in spite of all the effort put into it, bugs can be and actually are released into production. As a matter of fact, SEH exceptions being translated to C++ exceptions guarantee in the end that such unexpected bugs have a very limited impact on the reliability of the software (in fact, no impact at all since all the code is exception-safe anyway).
Unfortunately *nix signals just don't provide this guarantee, in fact it is almost guaranteed that those deadly signals will irremediably screw up the most carefully crafted C++ code (in which case abruptly killing the application is the best solution, before things get even worse).

Again, keep in mind that my POV on that topic is strongly biased towards C++ programming. Other languages (such as C which doesn't have exceptions anyway) may cope better with signals, and may have quite a hard time dealing with SEH.

---

