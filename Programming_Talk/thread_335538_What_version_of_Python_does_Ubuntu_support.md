---
title: "What version of Python does Ubuntu support?"
date: 2007-01-10
forum: Programming Talk
---

### Post by thenetduck on 2007-01-10
Hi, 
  I was reading about Python on Wikipedia and noticed that there are many different variations of Python. For instance there is CPython or Jython among others. I was wondering what Ubuntu prefered so to speak or what they support as Python goes. I know their main choice in language was Python, but I wasn't sure on whave version of python it was. 
   Also is Python a multi platformed language like Java? and what I mean is will the code transfer without editing it to a different os and run the same? Thanks, 

 The Net Duck

---

### Post by tzulberti on 2007-01-10
Python is multiplataform, because it is intepretated...

---

### Post by pmasiar on 2007-01-10
> **thenetduck said:**
>  there are many different variations of Python. For instance there is CPython or Jython among others. I was wondering what Ubuntu prefered 

Ubuntu uses Python == CPython.

CPython is same thing as Python - C means build on top of GNU's C libraries. MS sponsored development Python for .NET - IronPython BTW open-sourced!. Presumably very fast (IIRC uses JIT compiling to CIL), faster than CPython. Jython languishes - MS hired Jython developer to make IronPython. I bet one of reasons was to deny Java convenient scripting language - and gave it it C# instead. :twisted:

>    Also is Python a multi platformed language like Java? and what I mean is will the code transfer without editing it to a different os and run the same?

No, python is *much* better than java! ;-)

CPython can also run also on mac and Windows with some limitations. If code carefully, you can run code on all platforms, but it is not painless or careless. You have to think about it -- not all the time, but in some situation (when talking to OS, files, GUI etc). so: you have almost perfect platform independence with some care. How hard is it? It depends. :-)

On Windows you can run also ironPython - but not on linux. 

Jython was able to inherit from Java (and IIRC be superclass for java classes). It is still being developed, but not actively :-( Lack of resources. Sun selected competitor, Ruby, for JRuby. Another bad choice :twisted:

> **tzulberti said:**
> Python is multiplataform, because it is intepretated...
multiplatfor and interpreted are independent. VBasic is interpreted but not multiplatform. Just for intepreters it is easier to make port to other system, so you can get confused these two concepts.

---

### Post by thenetduck on 2007-01-10
Hey thanks for the comments. That makes me excited to start using Python more. I have done a lot of Java and C++ programming and am ready to "take it to the next level" well so to speak. I haven't really used c++ or java for anything other than making a plugin for Azues :) so have gotten kind of board with them. I wanna help program in the community so was looking at Python. Would this be the best language to learn if I wanna help you guy's out? Thanks, 

 The Net Duck

---

### Post by pmasiar on 2007-01-10
yes, Python is prefered language for ubuntu (and for mark the sabdfl)

---

