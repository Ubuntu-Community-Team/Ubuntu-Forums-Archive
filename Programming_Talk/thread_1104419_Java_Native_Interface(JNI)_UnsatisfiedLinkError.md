---
title: "Java Native Interface(JNI): UnsatisfiedLinkError"
date: 2009-03-23
forum: Programming Talk
---

### Post by C-- on 2009-03-23
I have created a Java file "Dock.java" which uses JNI to access a C function called "setStruts." The C function needs two header files, Xlib.h and Xatom.h.

Whenever I try to run Dock's main function, which just calls setStruts, I get the following error:

Exception in thread "main" java.lang.UnsatisfiedLinkError: Dock.setStruts(III)V
        at Dock.setStruts(Native Method)
        at Dock.main(Dock.java:12)

I am assuming this is because System.loadLibrary is not loading the right library. I know that loadLibrary's string parameter doesn't need to have the directory path or the ".so" extension, and I make sure to set LD_LIBRARY_PATH to point to the right directory. I believe it's because I am loading the wrong X11 shared library.

Note that when I compiled the C function I compiled with -fPIC and tried loading the resulting shared library.

---

### Post by C-- on 2009-03-23
Ok never mind I fixed the above problem; but now, I still cannot access X calls such as XOpenDisplay because the library isn't loading.

Exception in thread "main" java.lang.UnsatisfiedLinkError: /net/user3/manoyes/Desktop/jnitest/libsetstruts.so: /net/user3/manoyes/Desktop/jnitest/libsetstruts.so: undefined symbol: XOpenDisplay
        at java.lang.ClassLoader$NativeLibrary.load(Native Method)
        at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1751)
        at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1676)
        at java.lang.Runtime.loadLibrary0(Runtime.java:823)
        at java.lang.System.loadLibrary(System.java:1030)
        at Dock.<clinit>(Dock.java:7)

---

### Post by AkiraCrosshair on 2009-09-04
How did you solve the problem? I'm having a similar problem.

---

### Post by jespdj on 2009-09-04
> Exception in thread "main" java.lang.UnsatisfiedLinkError: /net/user3/manoyes/Desktop/jnitest/libsetstruts.so: /net/user3/manoyes/Desktop/jnitest/libsetstruts.so: undefined symbol: XOpenDisplay
This means you are trying to call a function that does not exist in the library libsetstruts.so.

@AkiraCrosshair: Another reason you might get an UnsatisfiedLinkError is because Java can't find the native library. Java uses the variable java.library.path to look for native libraries. You can specify it on the command line when you run your Java program like this:

```
java -Djava.library.path=/dir/that/contains/nativelib com.mypackage.MyProgram
```

---

### Post by AkiraCrosshair on 2009-09-04
What OS are you using and which development tool?

@jespdj:
I know about that problem and thats not my problem. My native library is located on the right path. If I remember correct that problem throws :

*lang*.*UnsatisfiedLinkError*: no library in *java*.library.path 

or something like that. Im relatively sure that my problem has something with how eclipse 3.5 creates the native library since the my library is loading or? Eclipse isnt made for dealing with JNI( according to me :/ ).

---

