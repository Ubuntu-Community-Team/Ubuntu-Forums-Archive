---
title: "JAVA and ASSEMBLY united!"
date: 2009-01-28
forum: Programming Talk
---

### Post by Kilon on 2009-01-28
I just found two very interesting articles that open new frontiers for both JAVA and ASSEMBLY developers. It is the way to unite the two quite different languages.  Enjoy!!!

From Assembly to Java

[http://blogs.sun.com/CoreJavaTechTips/entry/launch_java_applications_from_assembly](http://blogs.sun.com/CoreJavaTechTips/entry/launch_java_applications_from_assembly)

From Java to Assembly 

[http://today.java.net/pub/a/today/2006/10/19/invoking-assembly-language-from-java.html](http://today.java.net/pub/a/today/2006/10/19/invoking-assembly-language-from-java.html)

---

### Post by Kilon on 2009-01-28
So from the lack of replies I must assume that people are not that interested or keen on  in mixing Assembly with Java.

---

### Post by NathanB on 2009-01-28
> **Kilon said:**
> So from the lack of replies I must assume that people are not that interested or keen on  in mixing Assembly with Java.

It is a very niche thing.  When you consider the overhead of loading-in the Java VM environment, you tend to look for better solutions to the problem.

---

### Post by wmcbrine on 2009-01-28
> **Kilon said:**
> So from the lack of replies I must assume that people are not that interested or keen on  in mixing Assembly with Java.I saw the thread title and just thought, "madness".

---

### Post by Branimir on 2009-01-28
ROFL

Greets, Branimir.

---

### Post by kavon89 on 2009-01-28
unpossible

---

### Post by Reiger on 2009-01-29
Why? Java already *has* means of loading system libraries (.so/.dll files). 

But if it is intended to be anything 'maintstream; I think ASM + Java is a typical case to go and read Aisopos' fable about the father who had two daughters... :p They are two different ends of a spectrum, the JVM is as far as Java concerned a very real *machine* but as far as ASM is concerned a fictious construct made to do improbable statements.

---

### Post by Kilon on 2009-01-29
> **Reiger said:**
> Why? Java already *has* means of loading system libraries (.so/.dll files). 

But if it is intended to be anything 'maintstream; I think ASM + Java is a typical case to go and read Aisopos' fable about the father who had two daughters... :p They are two different ends of a spectrum, the JVM is as far as Java concerned a very real *machine* but as far as ASM is concerned a fictious construct made to do improbable statements.


I do not see any reason why the one cannot benefit from the other. Maybe you should read the two link more carefully. It explains why Assembly can be very useful for JAVA and JAVA for Assembly.

---

### Post by Reiger on 2009-01-29
"Why?" was meant to refer to the post before mine.

But I do maintain that ASM does not work well if you want as much portability as you can get in Java.

---

### Post by Kilon on 2009-01-29
> **Reiger said:**
> "Why?" was meant to refer to the post before mine.

But I do maintain that ASM does not work well if you want as much portability as you can get in Java.


why will I want as much portability as java , if I am using Assembly from inside Java ? The whole purpose of Assembly is to bring custom made machine code to java . if it was the same as java why even bother ?

---

### Post by cabalas on 2009-01-29
> **Kilon said:**
> why will I want as much portability as java , if I am using Assembly from inside Java ? The whole purpose of Assembly is to bring custom made machine code to java . if it was the same as java why even bother ?

I think that his point (please correct me if I'm wrong Reiger) was that java was designed to be portable and assembly in java seems like a contradiction, due to java's touted 'write once, run everywhere' ideology (yes I know in reality it doesn't work out like that).

Personally I don't see the point of assembly in java where there are languages better suited to the task (such as C).  It seems like a mistake to try and mess around in the low level stuff when you are using a high level language as it makes all the abstractions essentially pointless.

---

### Post by NathanB on 2009-01-29
> **Kilon said:**
>  From Assembly to Java

[http://blogs.sun.com/CoreJavaTechTips/entry/launch_java_applications_from_assembly](http://blogs.sun.com/CoreJavaTechTips/entry/launch_java_applications_from_assembly)



In the article he says "The original application was written in assembly language." which means he probably had few options to consider.  Re-writing the entire app in Java would be expensive.

Only a rare few would find themselves in a similar situation.

---

