---
title: "The import Java.io.console cannot be resolved..."
date: 2009-04-04
forum: Programming Talk
---

### Post by darkwing_duck on 2009-04-04
Hi, and thanks for visiting this thread....

I am new to Java in Ubuntu and I'm trying to compile a simple program to do some console input/output.

Here's my watered-down code...

```
import java.io.Console;

public class console_io 
{
  public static void main(String[] args)
  {
    Console console = System.console();

    if (console == null) 
    {
      System.err.println("No console.");
      System.exit(1);
    }
  }
}
```

Here's the compile-time error I get...

```
username@computer:~$ javac console_io.java
----------
1. ERROR in console_io.java (at line 1)
	import java.io.Console;
	       ^^^^^^^^^^^^^^^
The import java.io.Console cannot be resolved
----------
2. ERROR in console_io.java (at line 7)
	Console console = System.console();
	^^^^^^^
Console cannot be resolved to a type
----------
3. ERROR in console_io.java (at line 7)
	Console console = System.console();
	                         ^^^^^^^
The method console() is undefined for the type System
----------
3 problems (3 errors)username@computer:~$ 
```

I'm thinking this has to do with my Java install, but I'm not knowledgeable about that kind of stuff, any help resolving this would be much appreciated.

P.S. - I read the FAQ for this forum.

Thanks in advance.

---

### Post by darkwing_duck on 2009-04-04
oops....

```
username@computer:~$ java -version
java version "1.5.0"
gij (GNU libgcj) version 4.3.2
```

It looks like I'm using Java version 5, however, the "System.console()" function isn't implemented until Java version 6.  Looks like I just need to update to Java 6.  I'll try to figure out how to do that and if it works I'll repost solution in case anyone has the same problem in the future.

:lolflag:

---

### Post by darkwing_duck on 2009-04-04
Okay, now...

```
username@computer:~$ java -version
java version "1.6.0_10"
Java(TM) SE Runtime Environment (build 1.6.0_10-b33)
Java HotSpot(TM) Client VM (build 11.0-b15, mixed mode, sharing)
```

Now I just gotta figure out how to configure my Java to be the JDK instead of the JRE.

---

### Post by darkwing_duck on 2009-04-04
Eureka!

Here's what I did in case anyone has same problem...(assuming Java 6 JDK is installed, maybe via Synaptic Package Manager, sun-java6-jdk)

1) Configure Javac (duh, the compiler)
```
username@computer:~$ sudo update-alternatives --config javac

There are 4 alternatives which provide `javac'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/ecj
          2    /usr/bin/gcj-wrapper-4.3
*+        3    /usr/lib/jvm/java-gcj/bin/javac
          4    /usr/lib/jvm/java-6-sun/bin/javac

Press enter to keep the default[*], or type selection number: 4
Using '/usr/lib/jvm/java-6-sun/bin/javac' to provide 'javac'.

username@computer:~$ javac -version
javac 1.6.0_10
```

Now my simple Java Console Input/Output program compiles using the correct version of Java JDK (version 6 instead of version 5).

Thanks for anyone who read this,

:lolflag:

---

### Post by qwexer on 2009-04-12
Thank you, you saved me much headache.  Anyone reading this just make sure you choose the same option but not necessaryly the same number.

Michael

---

### Post by pempaganela on 2009-10-17
Thanks you! It worked =)

---

