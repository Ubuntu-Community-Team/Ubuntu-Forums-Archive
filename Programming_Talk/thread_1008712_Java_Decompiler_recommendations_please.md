---
title: "Java Decompiler recommendations please"
date: 2008-12-11
forum: Programming Talk
---

### Post by tinny on 2008-12-11
Hello

I have had very little experience with Java decompilers.

I would really appreciate any recommendations or feedback on experiences people have had with Java decompilers.

E.g What decompilers you have used, how good a Job they did etc.

Thanks :-)

---

### Post by tinny on 2008-12-11
I have had Jad recommended to me, anyone used this before?

[http://www.kpdus.com/jad.html](http://www.kpdus.com/jad.html)

---

### Post by myrtle1908 on 2008-12-11
> **tinny said:**
> I have had Jad recommended to me, anyone used this before?

[http://www.kpdus.com/jad.html](http://www.kpdus.com/jad.html)

I lost source code to a project back in 2005 and used JAD to decompile the class files.  From memory it did its job well.  I recall that it changes some variable names to things like s1, s2, ... for Strings etc.  Also re-arranges your code to a certain degree but all in all quite readable.

---

### Post by jespdj on 2008-12-12
Note that it's not possible to fully reconstruct the source code from a Java class file. You can use it for research purposes or to rescue part of your project if you lost the source, but don't expect to get fully working and easy to read source code back.

I've also used JAD, works OK for what it can do. Note that the JDK contains the tool **javap** with which you can disassemble class files, see [the documentation](http://java.sun.com/javase/6/docs/technotes/tools/windows/javap.html).

Do you need a decompiler for a specific purpose?

---

### Post by howlingmadhowie on 2008-12-12
> **tinny said:**
> I have had Jad recommended to me, anyone used this before?


in case you didn't know, jad is not free software.

---

### Post by tinny on 2008-12-14
Thanks for the replies.

Its a long story but basically a developer as stolen and locked up some code that belongs to a client of mine.

So now I need to rewrite this software (I understand the decompiler doesnt create maintainable code).

I basically need to extract some SQL queries and XML parsing code (and anything else that might help :-) ).

---

### Post by pmasiar on 2008-12-14
> **tinny said:**
> Its a long story but basically a developer as stolen and locked up some code that belongs to a client of mine.

Client shold complain to company where developer worked. Sue them. Badmouth them in Better Busines Bureau or Chamber of Commerce. Raise stink: that is not how repeat customer business is made.

---

### Post by tinny on 2008-12-14
> **pmasiar said:**
> Client shold complain to company where developer worked. Sue them. Badmouth them in Better Busines Bureau or Chamber of Commerce. Raise stink: that is not how repeat customer business is made.

The developer was an independent contractor that worked for this client of mine.

They have only become a client of mine since the code was stolen. I am the one that is meant to get them out of the XYZ.

Legal proceedings are underway but these things take time.

---

### Post by reality1011 on 2008-12-15
sending you a link for the one that I use...  its a download link, enjoy :)

---

### Post by tinny on 2008-12-15
> **reality1011 said:**
> sending you a link for the one that I use...  its a download link, enjoy :)

Thanks

---

### Post by tinny on 2008-12-15
Jad and Jadclipse has been working well for me over the last day.
[http://www.kpdus.com/jad.html](http://www.kpdus.com/jad.html)
[http://jadclipse.sourceforge.net/wik....php/Main_Page](http://jadclipse.sourceforge.net/wik....php/Main_Page)

---

### Post by ian dobson on 2008-12-15
Hi,

I was in the same boat as you (Developer ran off with source code leaving us with the byte code). I ended up using "Cavaj Java Decompiler" to decompile the code.

Regards
Ian Dobson

---

### Post by jespdj on 2008-12-16
[Cavaj](http://www.bysoft.se/sureshot/cavaj/) uses Jad for decompiling, so the results would most likely be the same.

---

