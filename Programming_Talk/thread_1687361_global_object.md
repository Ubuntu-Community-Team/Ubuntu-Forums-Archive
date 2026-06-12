---
title: "global object?"
date: 2011-02-13
forum: Programming Talk
---

### Post by gufide on 2011-02-13
I there, no one know how to make an object accessible by all my files or functions in c++? thank you

---

### Post by MadCow108 on 2011-02-13
simply don't create it static or in an anonymous (unnamed) namespace
this is default.

```

MyClass myobj; // global to all
static MyClass myobj2; // only global to this file
namespace {
  MyClass myobj3;// only global to this file
}

```
access it in other files with the extern keyword
```

extern MyClass myobj; // from other file

```

but you should avoid this design when possible. It usually makes more problems than it solves.
If you really need it look up the singleton pattern, its still bad pattern but its better than plain global objects.

---

