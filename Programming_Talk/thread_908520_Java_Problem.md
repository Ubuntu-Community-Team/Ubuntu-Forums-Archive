---
title: "Java Problem"
date: 2008-09-02
forum: Programming Talk
---

### Post by DBQ on 2008-09-02
Hi everybody.  I have a strange problem in Java.  I have two classes A and B.  Class A uses class B inside of it (ie makes instances of it). Both classes belong to the same package (same package declaration on top).  When I compile it, class A does not see class B.  Says undefined symbol.

This whole thing worked fine in eclipse.  Now it does not work when I try to compile it using the command line (javac).  Any clues?

---

### Post by Ruhe on 2008-09-02
Can you post contents of your classes, and how you compile and run them?

Easy examaple how it should work:

[PHP]
package com.ruhe.evil;

public class A {

    public A() {
        B b = new B();
        b.someMethod();
    }

    public static void main(String[] args) {
        new A();
    }

}[/PHP]

[PHP]package com.ruhe.evil;

public class B {

    public void someMethod() {
        System.out.println("yaha");
    }

}
[/PHP]

And compile and run commands:
```

javac com/ruhe/evil/A.java
java com.ruhe.evil.A

```

---

### Post by DBQ on 2008-09-02
I cannot post the content of the classes.  But I compile them simply like this: javac package_path_from_root A.java.

---

### Post by DBQ on 2008-09-02
I have realized that my path was too deep.  However, now when I compile it I get all the instances of Arrays.copyOf flagged. And I get this error:

A/A.java:123: cannot find symbol
symbol  : method copyOf(java.lang.String[],int)
location: class java.util.Arrays
					String[] c = Arrays.copyOf(n, e.size() + n.length);
                                                             ^
Note: A/A.java uses unchecked or unsafe operations.

---

### Post by DBQ on 2008-09-02
I solved it - need Java 1.6.  Thank you for all the advice!

---

