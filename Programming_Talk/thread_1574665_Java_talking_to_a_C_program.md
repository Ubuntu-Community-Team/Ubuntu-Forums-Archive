---
title: "Java talking to a C program"
date: 2010-09-14
forum: Programming Talk
---

### Post by Finalfantasykid on 2010-09-14
I have a Java game which is currently doing image scaling in java, and the scaling is taking up most of the cpu.  I imagine that if I were to use a faster language such as c to do the image scaling, that the performance of the game would be faster and more stable.  I am unsure as to how to have Java send the c program an int[] and then have the c program scale that to a larger int[] and then pass it back to the java program.  I could probably do this with pipes, but I want the game to be able to run on all platforms, and I do not think that Windows uses pipes, at least not in the same way.

So any advice on how I would accomplish this?

---

### Post by r-senior on 2010-09-14
Is C significantly faster than JIT compiled Java?

[http://www.idiom.com/~zilla/Computer/javaCbenchmark.html]("http://www.idiom.com/~zilla/Computer/javaCbenchmark.html")
[http://www.stefankrause.net/wp/?p=4]("http://www.stefankrause.net/wp/?p=4")

Before embarking on the fusing of the two, I think it would certainly be worth verifying that a standalone C program can deliver the performance you need?

---

### Post by jpaugh64 on 2010-09-14
Well, first off, are you sure you need to switch languages? Is there perhaps a faster way to do this in Java? Higher level languages are really good at making optimizations non-intuitive, from my perspective at least.

If an extension (of Java) is the only option, then I think the best way to do that (or the only?) is to create a Java class that has some of its methods implemented in another language. The Java keyword for this is "native". You could find a lot of tutorials on the topic by searching for "Java, native".

---

### Post by Finalfantasykid on 2010-09-14
The portion of code that I would need to port is quite small(probably less than 100 lines of code), but extremely time expensive.  

ie. one function I have is called about 62,208,000 times per second.

So it's not like I need to redo thousands of lines of code.  It would probably take me a few hours or so to code this up in c, so really it is no time wasted, and it could potentially save me several frames per second.

I'll look into JNI, that seems to be pretty much exactly what I wanted, Thanks!

---

### Post by endotherm on 2010-09-14
if you don't need to pass data between the two, you could just compile your c into an executable and shell it independently from your java code. file and database intermediaries are common, as are sockets for passing data between processes

---

### Post by jbrown96 on 2010-09-14
IPC overhead is likely to consume any benefits you would get from moving to C.

Java is only about 50% slower than C for most operations. You should profile your code and see how much of a bottleneck it is.

---

