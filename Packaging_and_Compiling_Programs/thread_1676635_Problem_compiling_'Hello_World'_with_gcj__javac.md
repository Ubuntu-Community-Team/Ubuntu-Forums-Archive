---
title: "Problem compiling 'Hello World' with gcj / javac"
date: 2011-01-27
forum: Packaging and Compiling Programs
---

### Post by rezsbc on 2011-01-27
Hey,

I'm having trouble  compiling a simple 'Hello World' program using gcj or the gcj version of 'javac' under Ubuntu 10.10 (amd64).  I've installed GCJ from the Ubuntu repositories using apt.

This is my HelloWorld.java file:

```

cathal@officepc:~/java$ cat HelloWorld.java 

public class HelloWorld {
  
  public static void main (String[] args) { 

    System.out.println(“Hello World!”);

  }
}



```

And this is what happens when I try to compile (same things happens with GCJ):

```

cathal@officepc:~/java$ javac HelloWorld.java 
HelloWorld.java:6: error: Syntax error, insert "AssignmentOperator Expression" to complete Assignment
	System.out.println(“Hello World!”);
	           ^^^^^^^
HelloWorld.java:6: error: Syntax error, insert ";" to complete BlockStatements
	System.out.println(“Hello World!”);
	           ^^^^^^^
2 problems (2 errors)


```


My system is using the following:

```

cathal@officepc:~/java$ uname -a
Linux officepc 2.6.35-24-generic #42-Ubuntu SMP Thu Dec 2 02:41:37 UTC 2010 x86_64 GNU/Linux

```

```
 
cathal@officepc:~/java$ javac --version
gcj-4.4: no input files

```

```
 
cathal@officepc:~/java$ gcj --version
gcj (Ubuntu 4.4.4-14ubuntu2) 4.4.5
Copyright (C) 2010 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

```


Anyone got any ideas?  I do not have a CLASSPATH environment variable set however I would assume if that was the problem I'd see a 'class not found' error or similar?

I could try another java version however I'm interested in using GCJ to produce native code.

---

### Post by SevenMachines on 2011-01-27
Watch when cut & pasting programs from documents, this tends to crop up quite a bit, the quotes are specially formatted quotes and not 'normal' ones, you need to replace them. Note the difference below.

Broken due to special formatted quotes
```
System.out.println(&#8220;Hello World!&#8221;);
```
Proper Quotes, notice the difference
```
System.out.println("Hello World!");
```

---

### Post by rezsbc on 2011-01-29
Feel like a total idiot! Thanks for pointing out the error of my ways... stared and stared at it and couldn't see the thing with the quotes.

Cheers.

---

### Post by SevenMachines on 2011-01-29
Exactly as i have and thousands before us! Depending on the font it can actually be almost impossible to tell the difference, you don't suspect it until its happened to you once. The hours of staring are necessary to make sure you always know to look for it in the future :)

---

