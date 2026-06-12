---
title: "Java and GCC"
date: 2008-09-08
forum: Programming Talk
---

### Post by elgoog on 2008-09-08
The command to execute a .jar file is 'gcj' right?
I have this simulator MarieSim.jar and I need to run this software. Using the above command I get this:

```


**_shabbirhussain@shabbirhussain:~/marie$_** gcj MarieSource.jar
/usr/lib/gcc/i486-linux-gnu/4.2.3/../../../../lib/crt1.o: In function `_start':
(.text+0x18): undefined reference to `main'
collect2: ld returned 1 exit status



```

---

### Post by Zugzwang on 2008-09-08
gcj is a Java compiler. 

See the stickies on how to install the Java Runtime Environment correctly and then run your program using "java -jar yourJav.jar". By the way, "MarieSource.jar" looks like you are trying to execute the wrong .jar. Any furthermore, why don't you just follow the instructions provided with the software?

---

