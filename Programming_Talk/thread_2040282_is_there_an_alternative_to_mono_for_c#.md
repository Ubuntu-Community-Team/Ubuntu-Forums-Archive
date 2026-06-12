---
title: "is there an alternative to mono for c#?"
date: 2012-08-10
forum: Programming Talk
---

### Post by tommycake50 on 2012-08-10
Well I'm not sure if this is in the right section or not :confused:.

But coming from a windows environment(and i have to say Ubuntu is 100% better) i cant help noticing that in monodevelop you cant use timers, web browsers,sockets,processes or any other useful component for that matter is there a workaround for this or is there an alternative IDE and DLL's to make that IDE work with mono?
I tried dotGNU but i couldn't find an IDE for that and VS or SharpDevelop wont install/run under WINE so I'm all out of idea's now :(.
+I don't want to use Windows again and i cant get a VM to work:(.
~tommy

---

### Post by nidzo732 on 2012-08-10
Mono is currently the best c# implementation for Linux, there isn't anything better. If you are willing to learn you could try c++ and Qt, Qt is extremely powerful and capable of networking and web browsing, you could also try Java which is almost identical to C# and you wont have to do much learning (some people claim that MS copied Java and made C#) it also has a huge library.

---

### Post by tommycake50 on 2012-08-10
> **nidzo732 said:**
> Mono is currently the best c# implementation for Linux, there isn't anything better. If you are willing to learn you could try c++ and Qt, Qt is extremely powerful and capable of networking and web browsing, you could also try Java which is almost identical to C# and you wont have to do much learning (some people claim that MS copied Java and made C#) it also has a huge library.

Sorry for being controversial but i tried java and to me it nothing like c# and hard to learn + I'm learning c++ anyway and c# is a big part of the programming i do but thanks anyway.

i might try qt :D.

---

### Post by nidzo732 on 2012-08-10
If you're used to Visual Studio (or Mono) and it's GUI editor, you should try Qt Creator. It's very easy to use.

---

### Post by muteXe on 2012-08-10
> **tommycake50 said:**
> Sorry for being controversial but i tried java and to me it nothing like c# and hard to learn + I'm learning c++ anyway and c# is a big part of the programming i do but thanks anyway.



You're not being controversial, just wrong (in my opinion). I've only been doing java for about a year but I find the syntax very similar to C#.

---

### Post by durdenstationer on 2012-08-10
> **muteXe said:**
> You're not being controversial, just wrong (in my opinion). I've only been doing java for about a year but I find the syntax very similar to C#.

Comparing how similar two languages are purely based on syntax is silly.  I can write C++ that looks almost exactly like C.  Doesn't mean C++ is an identical language to C.  There are far more to languages than their syntax.  There are major differences in the low-level design details between the two and between their standard libraries.  If they are so identical, please explain to me how I can do operator overloading in Java like I can in C#.  Or how I can do pointer arithmetic in Java like I can in C#.  Or how I can get the generics implementation in Java to stop doing useless boxing and unboxing that doesn't happen when using them in C#.  Please tell me how to use optional arguments and extension methods in Java.  Also do we also ignore that all methods are virtual in Java but not in C#?  I could go on and on about real differences between the languages that get glossed over by superficial syntax comparisons.

---

### Post by xb12x on 2012-08-10
> **muteXe said:**
> You're not being controversial, just wrong (in my opinion). I've only been doing java for about a year but I find the syntax very similar to C#.

Java was developed by Sun. Microsoft saw it as a threat to Windows. Sun claimed that Microsoft was purposely hindering Java development under Windows and brought legal action.

As a result of losing a lawsuit to Sun concerning Java, Microsoft developed C# as its own solution, a solution it could control.

---

### Post by trent.josephsen on 2012-08-10
May I observe that if you write C++ that looks exactly like C, you are, in fact, writing C?

The similarities between Java and C# are extensive, self-evident, and go far beyond syntax.

---

### Post by muteXe on 2012-08-11
Ffs, where exactly did I use the word 'identical'?

---

### Post by StinkySQL on 2012-09-21
> **muteXe said:**
> You're not being controversial, just wrong (in my opinion). I've only been doing java for about a year but I find the syntax very similar to C#.


I was doing Java when they came out with C# and always felt it a copy, although they stripped out all the historical baggage that Java had at the time. Now, sure, - it i harder to see the similarity. But it was pretty clear back in the day.

---

### Post by directhex on 2012-09-23
> **tommycake50 said:**
> Well I'm not sure if this is in the right section or not :confused:.

But coming from a windows environment(and i have to say Ubuntu is 100% better) i cant help noticing that in monodevelop you cant use timers, web browsers,sockets,processes or any other useful component for that matter is there a workaround for this or is there an alternative IDE and DLL's to make that IDE work with mono?
I tried dotGNU but i couldn't find an IDE for that and VS or SharpDevelop wont install/run under WINE so I'm all out of idea's now :(.
+I don't want to use Windows again and i cant get a VM to work:(.
~tommy

I'm not sure I understand some of the issues you're having. Sockets don't work? Wat?

---

