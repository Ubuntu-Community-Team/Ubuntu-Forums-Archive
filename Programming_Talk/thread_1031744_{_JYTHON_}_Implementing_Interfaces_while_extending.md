---
title: "{ JYTHON } Implementing Interfaces while extending classes"
date: 2009-01-05
forum: Programming Talk
---

### Post by Kilon on 2009-01-05
From this article ( [http://www.weiqigao.com/articles/Scripting.html](http://www.weiqigao.com/articles/Scripting.html))  and an 160 page Jython tutorial I have just read I know that implementing is done the same way as extending in JYTHON. But what happens when I want to do both? Create a class that extends another JAVA class and implements a JAVA interface. I ask this because from one hand I assume that I will just need to add it in the definition but on the other hand  I have read  that using JYTHON's multi-inheritance is a bad idea since this is not supported in JAVA. Will adding two things inside the parentheses create any problems ?


for example

```
class MyJythonClass (JavaExtendedClass, JavaImplementedInterface)
```

---

### Post by txcrackers on 2009-01-06
You're a bit mistaken about what "multi-inheritance" is: that's a convention that allows a single Object to extend the functionality of 1..N other Objects. Interfaces are not "objects" in this sense - they are essentially *definitions* of behavior and not *implementations* of behavior.

So, in Java terms, a class can only extend one other class, but can implement many interfaces. The "prohibition" against using Jython to extend two different classes (which is allowed in Python) is to keep to the strict Java convention. (After living with it for a while, you'll see why this is generally a good idea.)

---

### Post by Kilon on 2009-01-06
Thank you for your reply. 

I knew how JAVA was treating interfaces but I just did not know if Jython treaded them the same way. By the way Unless I am mistaken JYTHON also allows multi-inheritance but only for JYTHON classes not JAVA classes. I am new to JYTHON but already like what I am seeing here.

---

