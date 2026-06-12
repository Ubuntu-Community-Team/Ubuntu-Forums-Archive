---
title: "Can't get either gcj or Sun Java to work properly"
date: 2009-08-19
forum: Programming Talk
---

### Post by bbi5291 on 2009-08-19
I thought that all that was required to install GCJ was the packages gcj and libgcj-dev. So I installed them and then tried to compile the following file aplusb.java:
```

import java.util.Scanner;
public class aplusb
{
    public static void main()
    {
        Scanner sc = new Scanner(System.in);
        int a = sc.nextInt();
        int b = sc.nextInt();
        sc.close();
        System.out.println(a+b);
    }
}
```
Unfortunately I get the following error messages:
```

aplusb.java:1: error: The import java.util.Scanner cannot be resolved
        import java.util.Scanner;
               ^^^^^^^^^^^^^^^^^
aplusb.java:6: error: Scanner cannot be resolved to a type
        Scanner sc = new Scanner(System.in);
        ^^^^^^^
aplusb.java:6: error: Scanner cannot be resolved to a type
        Scanner sc = new Scanner(System.in);
                         ^^^^^^^
3 problems (3 errors)
```
So I tried the more basic 'Hello World!':
```

public class HelloWorld {
  public static void main(String args[]) {
     System.out.println("Hello World!");
  }
}
```
This at least compiles, but fails to link:
```

/usr/lib/gcc/i486-linux-gnu/4.3.3/../../../../lib/crt1.o: In function `_start':
/build/buildd/glibc-2.9/csu/../sysdeps/i386/elf/start.S:115: undefined reference to `main'
collect2: ld returned 1 exit status
```
Since gcc and g++ still work properly, I assume it is not a problem with the linker itself.

Frustrated, I tried Sun Java instead, and installed sun-java6-bin, sun-java6-jre, and sun-java6-jdk (actually the first two were installed already). Now I get:
```

root@pegjudge:~# java HelloWorld.class
Exception in thread "main" java.lang.NoClassDefFoundError: HelloWorld/class
Caused by: java.lang.ClassNotFoundException: HelloWorld.class
        at java.net.URLClassLoader$1.run(URLClassLoader.java:200)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:301)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:252)
        at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:320)
Could not find the main class: HelloWorld.class.  Program will exit.
```
*Sigh*... What am I doing wrong?
Also, which compiler is recommended if my programs are small ( < 1000 lines), I want the best execution speed, and I don't need huge collections of libraries? (It's for an online judge server.) Sun Java, or gcj, or another compiler altogether?

---

### Post by baizon on 2009-08-20
I'm only using Sun Java and everything is working fine.
Try this: [https://help.ubuntu.com/community/Java]("https://help.ubuntu.com/community/Java")
Then try again to _compile_ and _run_ the Program.

---

### Post by bbi5291 on 2009-08-20
OK, I tried that but I still get the same error as before.

---

### Post by Zugzwang on 2009-08-20
For your HelloWorld example, try the following commands:
```

javac HelloWorld.java
java HelloWorld

```
Note that for running programs, you must not give the ".class" extension of the class file.

Note: When posting errors, also include the commands you used for compiling/linking/executing.

---

### Post by baizon on 2009-08-20
```
root@pegjudge:~# java HelloWorld.class
```
This is wrong!
Usage (without .class), and it will work:
```
java HelloWorld
```

---

### Post by bbi5291 on 2009-08-20
Thanks guys... that was exactly the problem.
But does anyone know what I'm doing wrong with gcj?

---

### Post by jespdj on 2009-08-21
gcj probably only supports Java 1.4, and class java.util.Scanner is a newer class added in a newer version of Java.

I wouldn't use gcj; it's not that good and only supports and old version of Java.

---

