---
title: "First project with Vala"
date: 2010-08-15
forum: Programming Talk
---

### Post by kahumba on 2010-08-15
Hi,
I read the official Vala tutorial, compiled and ran the examples, anything was good.
Now I decided to create my own little project and I realized I don't know how to manage it.
All examples from the tutorial were 1 file, but how do I go about multiple files?
Example:
Main.vala:
```

static int main(string[] args) {
    new Helper().sayHello();
    return 0;
}

```Helper.vala:
```

public class Helper {
    public void sayHello() {
        stdout.printf("hello!\n");
    }
}

```Is the only way to compile this by feeding _all_ files to the compiler at once?:
valac Main.vala Helper.vala
As the project becomes like 50-100 files I really need to split the compilation process (not having to recompile all files every time).
I used "makefiles" for C++ projects but I can't figure out how to apply them to Vala since it's a different beast from C/C++ despite producing C source code.

---

### Post by Queue29 on 2010-08-15
Set CC to "vala" instead of "gcc", replace every ".c" with ".vala", etc. 

There isn't much else to say, because until you have an understanding of how make works, you're just going to have to continue copying sample makefiles off the internet.

---

### Post by kahumba on 2010-08-15
Thanks I actually found this and it works:
[http://westhoffswelt.de/blog/0043_build_vala_projects_with_cmake_macros.html](http://westhoffswelt.de/blog/0043_build_vala_projects_with_cmake_macros.html)

---

