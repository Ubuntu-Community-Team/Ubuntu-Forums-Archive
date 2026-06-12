---
title: "java arraylist problem"
date: 2008-07-10
forum: Programming Talk
---

### Post by zizzdude on 2008-07-10
Hey, I try making an ArrayList for Integer objects, but it gives me a strange error, here's what I typed:

```

import java.util.*;
...
    private ArrayList<Integer> list = new ArrayList<Integer>();
    list.add(1);
...

```

error:
```

ArrayTest.java:6: <identifier> expected
    list = new ArrayList<Integer>();
        ^
ArrayTest.java:7: <identifier> expected
    list.add(1);
            ^
ArrayTest.java:7: illegal start of type
    list.add(1);
             ^
3 errors


```

I'm using java compiler version 1.6.0_06 if it helps.

---

### Post by Zugzwang on 2008-07-10
Works well here.

[PHP]
import java.util.*;

class Test {
    private ArrayList<Integer> list = new ArrayList<Integer>();
    
    public Test() {
        list.add(1);
    }
}
[/PHP]

Note that the second line you posted can't follow the first one since the first one is a declaration on class level (since you used the "private" keyword) whereas the second one is a command and has to stand inside of a function or method or so.

---

### Post by themusicwave on 2008-07-10
Also, 1 is not an Integer it is a primitive of type int.

You need to do the following:

list.add(new Integer(1)); 

Integer is an Object type, meaning it is a child of the Object class, just about everything in Java is an Object.

However, primitives are not Objects, for each primitive type there is a corresponding Object type so you can convert back and forth.

Float and float
Double and double
Integer and int
Byte and byte

The list continues.  Your ArrayList is of type Integer, not of type int.  Due to this you must send it an Integer.

I hope that helps,

Jon

---

### Post by themusicwave on 2008-07-10
Oops I completely misread the above...delete me

---

### Post by HotCupOfJava on 2008-07-10
Yes, the classes such as Integer, Double, Float, etc. are known as WRAPPER CLASSES because they "wrap" the primitive types to enable you to treat them like objects. You must handle them a little differently, though.

---

### Post by zizzdude on 2008-07-10
> **HotCupOfJava said:**
> Yes, the classes such as Integer, Double, Float, etc. are known as WRAPPER CLASSES because they "wrap" the primitive types to enable you to treat them like objects. You must handle them a little differently, though.

I did try doing the other way of adding an Integer object
```
list.add(new Integer(2));
```
but it still gives me that strange error.

---

### Post by themusicwave on 2008-07-10
Could you post some context?

It is hard to know what the problem is without the complete code or more of the code.

---

### Post by tinny on 2008-07-10
> **themusicwave said:**
> Also, 1 is not an Integer it is a primitive of type int.

You need to do the following:

list.add(new Integer(1)); 

Integer is an Object type, meaning it is a child of the Object class, just about everything in Java is an Object.

However, primitives are not Objects, for each primitive type there is a corresponding Object type so you can convert back and forth.

Float and float
Double and double
Integer and int
Byte and byte

The list continues.  Your ArrayList is of type Integer, not of type int.  Due to this you must send it an Integer.

I hope that helps,

Jon

You shouldnt have to worry about this.

Java provides [Autoboxing support]("http://jcp.org/aboutJava/communityprocess/jsr/tiger/autoboxing.html"). I think that this functionality was introduced as of JRE 5. The OP says they are using JDK 6, so they should be fine. (also I see that they are using Generics which is a Java 5 feature)

Are you using some sort of IDE? If so have you set-up your complier compliance level? In Eclipse this can be done by navigating to Project > Properties > Java Compiler

---

### Post by Zugzwang on 2008-07-11
> **zizzdude said:**
> I did try doing the other way of adding an Integer object
```
list.add(new Integer(2));
```
but it still gives me that strange error.

You did read my post, right? It should answer your question.

---

### Post by zizzdude on 2008-07-11
> **Zugzwang said:**
> You did read my post, right? It should answer your question.

yeah, I read it, thanks for the help. :)

---

