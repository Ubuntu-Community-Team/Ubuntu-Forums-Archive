---
title: "Creating and linking shared libraries"
date: 2015-05-08
forum: Programming Talk
---

### Post by Ashley_Hemingway on 2015-05-08
I've been trying to create and link and shared library for use with the Java Native Interface (JNI) for ages with no success.

Basically I've got a C file which calls methods which are in various custom libraries. These libraries I've placed in the /lib/i386-linux-gnu directory and installed using ldconfig. Once I've refreshed the cache, I can see these libraries when listing with 'ldconfig -p'.

When I run:
```

$ gcc -shared -fpic -o libWrapper.so -I/usr/lib/jvm/java-7-openjdk-i386/include -I/usr/lib/jvm/java-7-openjdk-i386/include/linux -I/home/test/packets/include Wrapper.c

```
I get a shared library but when I check it with 'nm libWrapper.so' it shows that I have unreferenced links to methods in those libraries which I installed myself, which is further proven when I run the Java program get errors relating to the same issue.

I'm confused how to reference my installed libraries or what step I'm missing out. I've tried using the GNU ld, gcc and libtool with no success.

Any advice would be appreciated.

---

