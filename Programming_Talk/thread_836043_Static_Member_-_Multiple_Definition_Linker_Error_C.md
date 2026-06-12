---
title: "Static Member - Multiple Definition Linker Error C++"
date: 2008-06-21
forum: Programming Talk
---

### Post by SNYP40A1 on 2008-06-21
I have a class, call this class 'A', which is part of a C++ project that I am working on for a homework assignment.  Currently, my project compiles fine.  However, if I add one static variable to class A, even if it is not referenced anywhere else other than as a variable declaration in the class header file, I get several linking errors about the declaration being multiply defined.  In fact, I get errors stating that the variable was first defined in another class which inherits from a class included in the header file that class A includes.  Is there some kind of cyclic dependency going on?  I would post code, but I am not allowed to.

---

### Post by jim_24601 on 2008-06-23
Why can't you post code? It's a bit hard to figure out what's going wrong without it?

You didn't both define and declare the static member in the header file for the class, did you? Like:

file foo.h:
```

class Foo
{
  static int sInt;
}

static int Foo::sInt;
```

That would cause every source file that includes foo.h to try to allocate its own static member. Move the definition line to the cpp file instead.

The "variable first defined in other class" thing I'm not so sure about, but one error in a C or C++ program can often beget a huge family of spurious ones.

---

### Post by ranjeetsih on 2009-01-04
It worked for me. Thanks :)

---

### Post by kunigami on 2010-04-14
Solved my problem too. Thanks.

> **jim_24601 said:**
> Why can't you post code? It's a bit hard to figure out what's going wrong without it?

You didn't both define and declare the static member in the header file for the class, did you? Like:

file foo.h:
```

class Foo
{
  static int sInt;
}

static int Foo::sInt;
```That would cause every source file that includes foo.h to try to allocate its own static member. Move the definition line to the cpp file instead.

The "variable first defined in other class" thing I'm not so sure about, but one error in a C or C++ program can often beget a huge family of spurious ones.

---

