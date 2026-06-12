---
title: "monodevelop: referencing extern alias"
date: 2011-02-06
forum: Programming Talk
---

### Post by Al4Oeboentoe on 2011-02-06
Hi guys,

Just started learning C# and use monodevelop 2.4 to test some exercises.
The problem is: How to tell the compiler what "extern alias Lib1;" refers to?

Got stuck with the "extern alias" example I saw in:
   [http://bartdesmet.net/blogs/bart/archive/2006/10/07/4502.aspx](http://bartdesmet.net/blogs/bart/archive/2006/10/07/4502.aspx)
This is about two libs defining a class with the same name. The
application containing "Main" references both libriaries
(in Solution-pad - MyApplication -> References).
If I don't use the conflicting class I can see that the compiler knows
how to find both libs (so that is defined correctly).
But if I use the conflicting class, and the "extern alias" specification, to avoid the
conflict I get the error:
   The extern alias "Lib1" was not specified in -reference option.

Don't know how to solve this (Help doesn't help: somewhere it says
I need a newer monodoc.)
I thought I had to use Right-click on Solution-pad -> MyApplication ->
References -> Lib1
but it only shows a greyed "Properties" item.

Can anyone tell me how to tell the compiler that "extern alias Lib1" refers
to the Lib1.dll ?

KR,
Albert

---

### Post by cariboo on 2011-02-07
A bump for the move.

---

### Post by wencha on 2011-09-29
I have the same problem! If someone knows howto please say!

---

