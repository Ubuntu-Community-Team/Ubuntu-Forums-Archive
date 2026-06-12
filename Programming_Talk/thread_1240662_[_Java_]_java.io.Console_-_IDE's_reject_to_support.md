---
title: "[ Java ] java.io.Console - IDE's reject to support it .. why ?"
date: 2009-08-14
forum: Programming Talk
---

### Post by credobyte on 2009-08-14
Eclipse, NetBeans - both IDE's reject to support Console .. If I can compile it successfully via terminal ( javac <file>.java ), where's the problem ?
Is there any workarounds ?

```
java version "1.5.0"
gij (GNU libgcj) version 4.3.3

```

---

### Post by credobyte on 2009-08-15
Bump @ ^ ..

---

### Post by shadylookin on 2009-08-15
java.io.Console was added in java 1.6 not 1.5 

try getting the sun version of java look for sun-java6-jdk in synaptic package manager and make it the default version

---

### Post by credobyte on 2009-08-15
As I said, I can successfully compile my app in terminal, however, it's impossible in IDE's ( Console can't be resolved ). I already have Java6 JDK .. how do I make it Eclipse default ( looks like it's set to Java5 in-built compiler ) ?

---

### Post by shadylookin on 2009-08-15
I haven't used eclipse in a while, but this worked for me once upon a time

> 
go into eclipse.
click window in the toolbar
under window click preferences
open up the java tag
click on compiler
make sure your compiler compliance level is 1.6

next click on Installed JREs
you should have something like java-6-sun-1.6.0.10 with a location of
/usr/lib/jvm/java-6-sun-1.6.0.10

if not you need to make it so that it does

Give that a try and see what happens


---

