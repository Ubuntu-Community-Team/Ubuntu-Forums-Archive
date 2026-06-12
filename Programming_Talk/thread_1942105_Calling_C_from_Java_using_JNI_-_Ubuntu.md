---
title: "Calling C from Java using JNI - Ubuntu"
date: 2012-03-16
forum: Programming Talk
---

### Post by Ishayu on 2012-03-16
Hey there!

Can someone help me with some JNI fun?

I've tried to follow a few guides of how to use the Java Native Interface as I wish to make a wrapper for my algorithms written in C using Java.

I've done some research myself, but I need more help. Using Ubuntu 11.10 (in a VM, but whatever)

I started with the guide written by Sun themselves, but they are written for Solaris and Windows, which is a big problem.

Here's what I got so far:

I wish to just start out with a method that prints Hello World to the screen.

HelloWorld.java contains:
```
 class HelloWorld {
     private native void print();
     public static void main(String[] args) {
         new HelloWorld().print();
     }
     static {
         System.loadLibrary("HelloWorld");
     }
 }
```

I compile it with
```
javac HelloWorld.java
```

Then generate a header file
```
javah -jni HelloWorld
```

Then I write a C function.
```
 #include <jni.h>
 #include <stdio.h>
 #include "HelloWorld.h"
 
 JNIEXPORT void JNICALL 
 Java_HelloWorld_print(JNIEnv *env, jobject obj)
 {
     printf("Hello World!\n");
     return;
 }
```

And then I compile this C code with:
```
gcc -c -I/usr/lib/jvm/java-6-openjdk/include -I/usr/lib/jvm/java-6-openjdk/include/linux HelloWorld.c -o libHelloWorld.so
```

Then I rename HelloWorld.so to libHelloWorld.so because otherwise nothing works. I keep the old file as well just to make sure but I'm quite sure it's not used.

I then attempt to run HelloWorld, but that returns:
```
Exception in thread "main" java.lang.UnsatisfiedLinkError: /home/christian/workspace/testJNI/src/libHelloWorld.so: /home/christian/workspace/testJNI/src/libHelloWorld.so: invalid ELF header (Possible cause: endianness mismatch)
	at java.lang.ClassLoader$NativeLibrary.load(Native Method)
	at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1750)
	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1675)
	at java.lang.Runtime.loadLibrary0(Runtime.java:840)
	at java.lang.System.loadLibrary(System.java:1047)
	at HelloWorld.<clinit>(main.java:7)

```

This seems to suggest to me that I am running a 32-bit java but compiling 64-bit native C code, which obviously causes trouble.

I'm at a complete loss. I'm probably just stupid. Any help?

---

### Post by Ishayu on 2012-03-17
Bump

---

### Post by ziekfiguur on 2012-03-18
I've never done anything like this, but you could try compiling with -m32 to make a 32bits version of the library.

---

### Post by Ishayu on 2012-03-18
Works!

Isn't there a way to run Java as 64-bit instead?

---

### Post by dwhitney67 on 2012-03-18
> **Ishayu said:**
> 
And then I compile this C code with:
```
gcc -c -I/usr/lib/jvm/java-6-openjdk/include -I/usr/lib/jvm/java-6-openjdk/include/linux HelloWorld.c -o libHelloWorld.so
```


Change the statement above to the following to see if it makes a difference:
```

gcc -c **-fPIC** -I/usr/lib/jvm/java-6-openjdk/include -I/usr/lib/jvm/java-6-openjdk/include/linux HelloWorld.c

**gcc -shared -o libHelloWorld.so HelloWorld.o**

```
Then try running your program using a statement like this:
```

**LD_LIBRARY_PATH=./:${LD_LIBRARY_PATH}** java HelloWorld

```

---

### Post by Ishayu on 2012-03-18
> **dwhitney67 said:**
> Change the statement above to the following to see if it makes a difference:
```

gcc -c **-fPIC** -I/usr/lib/jvm/java-6-openjdk/include -I/usr/lib/jvm/java-6-openjdk/include/linux HelloWorld.c

**gcc -shared -o libHelloWorld.so HelloWorld.o**

```
Then try running your program using a statement like this:
```

**LD_LIBRARY_PATH=./:${LD_LIBRARY_PATH}** java HelloWorld

```

SHABAM.

That did it!

Now, why did this work? I'm a bit confused.

---

