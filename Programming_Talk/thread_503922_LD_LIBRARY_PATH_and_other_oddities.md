---
title: "LD_LIBRARY_PATH and other oddities"
date: 2007-07-18
forum: Programming Talk
---

### Post by d80tb7 on 2007-07-18
Hello all,

I'm trying to get something working with JNI and am having all sorts of problems.  The biggest of these is I can't get java to find my shared libraries.

Here's a (very simple) test program I knocked up:

```

public static void main(String args[]) {

	
	String javaLibraryPath = System.getProperty("java.library.path");
	
	System.out.println("java.library.path="+javaLibraryPath);
	System.loadLibrary("libjFFTW3");
}

```

The output of this is:
```

java.library.path=/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/jre/lib/amd64/server:/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/jre/lib/amd64:/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/jre/../lib/amd64:/usr/lib/firefox
Exception in thread "main" java.lang.UnsatisfiedLinkError: no libjFFTW3 in java.library.path

```

This would imply that  libjFFTW3 is not on the library path, however an ls on the first directory int he library path produces the following:

```

chris@lemming:/usr/lib/jvm/java-1.5.0-sun-1.5.0.11/jre/lib/amd64/server$ ls
libjFFTW3.so  libjsig.so  libjvm.so  Xusage.txt

```

More puzzelingly I found several references on the internet that say that the results of java  System.getProperty("java.library.path") should be the same as $LD_LIBRARY_PATH.  However my $LD_LIBRARY_PATH actually references something completely different (my shared library is also in the LD_LIBRARY_PATH directory)
```

echo $LD_LIBRARY_PATH
/usr/local/lib

```
 
My questions therefore are:

1.  Is there something wrong with the way I am calling System.loadLibrary()?
2.  How do I edit  the java.library.path if not by $LD_LIBRARY_PATH?
3.  Does the fact that I'm running 64 bit have anything to do with this?

thanks in advance

chris

---

### Post by oakz on 2007-07-18
try:

System.loadLibrary("jFFTW3");

---

### Post by d80tb7 on 2007-07-18
ah, that works!

thank you

Chris

---

