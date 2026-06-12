---
title: "installing libraries in linux?"
date: 2009-05-12
forum: Programming Talk
---

### Post by aNxello on 2009-05-12
Hi =)
well, i have this little problem....
i'm learning c++ and the book i'm reading uses a librarie called EzWindows,
i found it on the internet and the website said that inside there's a readme file, but i dont see any readme file just the folders.

in the librarie folder there are 3 other folders
one is called include, the other one lib and the last one src

the incldue fodler contain .h files
the lib folder has an .a file
and the src folder has .cc files

can someone tell me how to isntall this library please? =)

thank you =)

---

### Post by slavik on 2009-05-12
looks like you found the code for the library, the .a files is what you would statically link against. -L will allow you to specify a directory to look into when looking for libraries when you invoke gcc.

---

### Post by aNxello on 2009-05-13
mmmm... i really didnt understand what to do =/

---

### Post by dwhitney67 on 2009-05-13
To re-iterate what Slavik was stating, you already have the library in a directory.  If this directory is not suitable for you, then feel free to install the library and its associated header files elsewhere, but just note that this is not required.

You indicated earlier that you have a directory, and for lack of a better name, let's just call it "foo".  Within foo, you have an "include" directory (with header files), a "lib" directory (with a libfoo.a), and a "src" directory (with source code).

When you build your application, that depends in the foo library, you need to compile/link it using a statement similar to the following:
```

gcc -I/path/to/foo/include MyApp.c -L/path/to/foo/lib -lfoo -o MyApp

```
Of course, the "/path/to/foo" should be replaced with the actual path of where the library exists.  Also, if you are developing in C++, then use g++ in lieu of gcc.

---

