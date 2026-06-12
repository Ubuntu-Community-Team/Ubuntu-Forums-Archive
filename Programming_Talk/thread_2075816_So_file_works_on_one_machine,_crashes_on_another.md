---
title: "So file works on one machine, crashes on another"
date: 2012-10-24
forum: Programming Talk
---

### Post by nasdaqtr on 2012-10-24
I have created a so file to be used in an app using netbeans 7.1 C++. I designed an exe to check the output. The file works fine without crashing. When I hand off the file to be run on another machine, the file breaks giving a message vector is out of range. 
 
The implementation of the code is the same, I have checked through everything but I cant seem to find any reason why this would be happening.
 
I have also ran this on another machine where it worked fine.
 
Can someone give any pointers please.

---

### Post by dwhitney67 on 2012-10-24
> **nasdaqtr said:**
> 
Can someone give any pointers please.

Debug the application on the system where it is crashing; or just use valgrind to determine where it is crashing.

---

### Post by nasdaqtr on 2012-10-24
> **dwhitney67 said:**
> Debug the application on the system where it is crashing; or just use valgrind to determine where it is crashing.
I debugged and  terminate is called after throwing an instance of 'std::out_of_range'
what(): vector::_M_range_check

[FONT=arial]When i check call stack it is crashed at a ollowing function
[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]CalculateResults(.....).[/FONT]
[FONT=arial] [/FONT]
[FONT=arial]The strange thing is that I have checked the implementation on another machine and I have checked through all possibilities that might cause the vector to break and those are taken care of and I am not able to reproduce the error on other machines. [/FONT]

---

### Post by dwhitney67 on 2012-10-24
> **nasdaqtr said:**
> ... I am not able to reproduce the error on other machines. [/FONT]

I can assist helping you, however you will need to post your code.  My crystal ball is still in the shop being fixed.

---

### Post by nasdaqtr on 2012-10-25
Thanks for the offer to help. Really appreciate it. We found something that perhaps you could shed some light on. It seems that our .so file works fine on the machines it is compiled on but not on other machines. Any thoughts what could be causing this. The code is quite extensive, if this does not resolve it, I will curtail the implementation and post it here.
Thanks for any advice you could provide.

---

### Post by dwhitney67 on 2012-10-25
> **nasdaqtr said:**
> Thanks for the offer to help. Really appreciate it. We found something that perhaps you could shed some light on. It seems that our .so file works fine on the machines it is compiled on but not on other machines. Any thoughts what could be causing this. The code is quite extensive, if this does not resolve it, I will curtail the implementation and post it here.
Thanks for any advice you could provide.

Do you know where in your code that it is crashing?  If so, can you snip part out so as to implement it in a smaller application?

I suspect you have a bug in your application.  The range-check error implies that you are exceeding the bounds of the vector.

I've developed software for Solaris, VxWorks, and Linux in C++, and never "spontaneously" had the error you described. That is why I suspect your code has a bug.

P.S.  If you know where in the code the exception is being thrown, then perhaps you can analyze the index that is being used to access the vector.  Or if you are using an iterator, make sure that you are not exceeding the bounds of the vector.

---

### Post by nasdaqtr on 2012-10-29
I noticed another thing, when I compile on the machine I was supposed to run the .so file. The file works. Its just that I am not able to just copy the file to a new machine and start using as a library. But if I were to go and compile on the same machine, it would work fine. I have no idea...I checked through the points you pointed out, but I feel those are fine.

---

### Post by dwhitney67 on 2012-10-29
> **nasdaqtr said:**
> I noticed another thing, when I compile on the machine I was supposed to run the .so file. The file works. Its just that I am not able to just copy the file to a new machine and start using as a library. But if I were to go and compile on the same machine, it would work fine. I have no idea...I checked through the points you pointed out, but I feel those are fine.

Do both systems share the same type of architecture?  Or is one a 32-bit system and the other a 64-bit system?

Have you determined where in the code is the application crashing?  Is there nothing in that area that points to the problem?  Is it perhaps that you are performing some pointer arithmetic?  Or perhaps trampling over the vector with a previous operation that moved/copied data around?

---

### Post by nasdaqtr on 2012-10-29
Yes friend, both systems share the same type of architecture, 64 bit. In fact, we have tried on more than two machines but this seems to be consistent behavior all across but when we compile on that machine, the so. file works with our exe. 
 
Yes, we have determined where the app is crashing and I dont find that there is there was anything wrong. Also, if the code was the problem, why would the code work after compilation on that machine. Is that a problem/ issue you see could still be connected with how the code is written.

---

