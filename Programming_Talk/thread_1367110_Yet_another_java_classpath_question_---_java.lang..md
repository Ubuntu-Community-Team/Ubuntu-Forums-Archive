---
title: "Yet another java classpath question --- java.lang.NoClassDefFoundError Jama"
date: 2009-12-29
forum: Programming Talk
---

### Post by raequin on 2009-12-29
Hi, all.  I have been searching the webs for instructions on how to get my java code to run, but I still get the following error:

Exception in thread "main" java.lang.NoClassDefFoundError: Jama/Matrix

The code compiles fine, but the preceeding error is thrown when I go to run it.  Here are the details:

I have downloaded Jama-1.0.2.jar to my desktop (/home/matt/Desktop/).  My source and class files are in another directory.  I'll paste the source code below, since it's very small; just a simple application to try and get this issue ironed out.

CPTesting.java:

```
import java.io.*;

public class CPTesting {
    public static void main(String[] args) {
	NGN testNew = new NGN(4, 5);
    }
}
```

NGN.java:

```
import java.io.*;
import Jama.Matrix;

class NGN {
    Matrix f_k, f_k1, deltaF;
    Matrix theta_k, theta_k1, hTheta;
    Matrix t_k, t_k1, hT;
    Matrix hTilde;
    Matrix JTilde_k, JTilde_k1;
    Matrix fHat_t_k, fHat_t_k1;
    Matrix JHat_k, JHat_k1;

    public NGN(int fs, int dof) {
	//	JHat_k1 = new Matrix(dof, fs);
	JHat_k1 = new Matrix(5, 6);
	//	JHat_k1 = JHat_k1.identity(dof, fs);
	JHat_k1.print(1, 1);
    }
}
```

I compile with the following commands:

```
javac CPTesting.java
```

and

```
javac NGN.java -cp /home/matt/Desktop/Jama\-1\.0\.2.jar
```

No errors, as I said.  Then:

```
java CPTesting 
Exception in thread "main" java.lang.NoClassDefFoundError: Jama/Matrix
	at NGN.<init>(NGN.java:14)
	at CPTesting.main(CPTesting.java:3)
Caused by: java.lang.ClassNotFoundException: Jama.Matrix
	at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:319)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:264)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:332)
	... 2 more
```

and

```
java CPTesting -cp /home/matt/Desktop/Jama\-1\.0\.2.jar
Exception in thread "main" java.lang.NoClassDefFoundError: Jama/Matrix
	at NGN.<init>(NGN.java:14)
	at CPTesting.main(CPTesting.java:3)
Caused by: java.lang.ClassNotFoundException: Jama.Matrix
	at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:319)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:264)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:332)
	... 2 more
```

So ... I'm stumped.  Please elucidate this for me.

Thanks!

---

### Post by matsuzine on 2009-12-29
I think the problem you're seeing here is because you don't have the current directory in your classpath.  It is finding your jama classes okay, b/c you specified that path, but it then goes to load NGN and it doesn't know where the classes are. 

Simple fix, change your classpath to this and I think it will work...

```

java -cp /home/matt/Desktop/Jama\-1\.0\.2.jar:. CPTesting

```

I hope it helps!

---

### Post by raequin on 2009-12-29
Sweet!  Man, that did it.  Thanks a lot!

I guess I had to add the current directory because I had manually specified a path, otherwise it would have just looked in the current directory only?

---

### Post by matsuzine on 2009-12-29
That's right.  The current directory isn't included by default.  It has caught me a couple of times.  Glad it worked!

---

