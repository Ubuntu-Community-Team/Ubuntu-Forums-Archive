---
title: "C++ EndOfStreamException"
date: 2010-02-21
forum: Programming Talk
---

### Post by Clivest on 2010-02-21
Hi

I am writing a program in c++ to read in characters individually. The characters are generated in another program which throws an EndOfStreamException when there are no more characters.

What do I need to #include or #using at the start of the program to use the  EndOfStreamException?

I've found this website, 
[http://www.gnu.org/projects/dotgnu/pnetlib-doc/System/IO/EndOfStreamException.html](http://www.gnu.org/projects/dotgnu/pnetlib-doc/System/IO/EndOfStreamException.html)
but I'm still not sure what to do. I'm using g++ to compile.

Thanks

Clive

---

### Post by dwhitney67 on 2010-02-21
HA!  You got me there... I just examined the link you posted.  That is for a JAVA, or possibly C#, exception class; it has nothing to do with C++.

-------------------------------

If you have one program (application) throwing an exception, and your hoping to have another program catch it, then good luck with that, because AFAIK, it's not possible.

Could you please explain the issue you are having a little more clearly, maybe even show some code.  I am not at all familiar with this EndOfStreamException.  Is is "home-made"?

---

### Post by Clivest on 2010-02-27
Thanks for the reply.

I had a bit more look into it, but still couldn't find anything, so I ended up doing it a different way instead that avoided using the Exception. Not as neat, but it works now :).

Clive

---

