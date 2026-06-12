---
title: "Problems compiling Hello World program in D"
date: 2013-04-13
forum: Programming Talk
---

### Post by checoimg on 2013-04-13
```
import std.stdio;
main() {
    writeln("Hello, world!\n");
    exit (0);
}
```

This is the error I get :

```
clscr.d:3: function declaration without return type. (Note that constructors are always named 'this')
clscr.d:3: no identifier for declarator main()
```

Thank you in advance!

---

### Post by checoimg on 2013-04-13
I'm using GDC to compile. 
```
gdc -o hello hello.d
```
Let me say it worked before but now I'm getting this error.

---

### Post by checoimg on 2013-04-13
Attached the program I compiled before.

---

### Post by checoimg on 2013-04-13
A mystery why it compiled before but I corrected the problem by adding :
```
import std.c.stdlib;
```

---

### Post by checoimg on 2013-04-13
Now my complete code is :

```
import std.stdio;
import std.c.stdlib;
main() {
    writeln("Hello, world!\n");
    exit (0);
}


```

---

