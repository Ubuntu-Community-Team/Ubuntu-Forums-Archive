---
title: "Ctags Questions"
date: 2010-03-16
forum: Programming Talk
---

### Post by kogger on 2010-03-16
So I finally got OmniCppComplete working for Vim, but there are a couple things wrong with it that I would like to fix, and it's that ctags isn't getting all the data that I want. Using the ctags command suggested by OmniCppComplete works pretty well for the most part, but it fails to do two things:

1) It doesn't save namespace variables declared as extern
2) It doesn't let me access members of an object declared in another namespace

For example, for number one:

```

namespace A {
   extern const MyClass My_Object;
}

```

The variable A::My_Object is unrecognized, and :tselect My_Object says that the tag was not found. If I remove the extern keyword, it works, but I don't think I should do that in case it has unforeseen consequences on the rest of my program.

And then for number two:

```

Namespace C {
   MyClass *My_Object;
}

```

ctags will find the variable C::My_Object, but when using namespace C, My_Object->*complete* says that the pattern was not recognized. I can get around this problem by declaring the variable again in my main source file's header, but that seems unnecessary.

---

