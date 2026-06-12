---
title: "Calling a C function in Java: JNI gcc flags"
date: 2008-11-27
forum: Packaging and Compiling Programs
---

### Post by Xlksjdsa on 2008-11-27
I included the header file created by javah -jni and the final step before running it is building the native library. I'm following a Sun tutorial which uses Solaris (eh...) which compiles the program using 
```

cc -G -I/java/include -I/java/include/solaris
    HelloWorld.c -o libHelloWorld.so

```
I'm not sure what paths to use for linux.

---

### Post by ko_aung on 2009-06-28
hi, i'm also studying JNI and followed the tutorial book from Sun.

i found it one web site showing a simple JNI example for Ubuntu.
[http://www.scribd.com/doc/6049142/JNIJava-Native-Interface-Execute-Native-Code-In-Java]("http://www.scribd.com/doc/6049142/JNIJava-Native-Interface-Execute-Native-Code-In-Java")

cc -o libHelloWorld.so -shared -I/<path_to_JDK_install_directory>/include -I/<path_to_JDK_install_directory>/include/linux HelloWorld.c

good luck and pls let me know if you can finish the tutorial.

---

