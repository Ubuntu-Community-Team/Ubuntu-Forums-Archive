---
title: "a Java question"
date: 2006-12-15
forum: Programming Talk
---

### Post by slavik on 2006-12-15
in Java, what happens in the following code?

```
String s1 = "Hello World";
String s2 = s1;
```

---

### Post by amo-ej1 on 2006-12-15
Quoting your best friend, the java api documentation at  [http://java.sun.com/j2se/1.5.0/docs/api/java/lang/String.html](http://java.sun.com/j2se/1.5.0/docs/api/java/lang/String.html)

> 
String(String original)
          Initializes a newly created String object so that it represents the same sequence of characters as the argument; in other words, the newly created string is a copy of the argument string.


---

### Post by slavik on 2006-12-15
> **amo-ej1 said:**
> Quoting your best friend, the java api documentation at  [http://java.sun.com/j2se/1.5.0/docs/api/java/lang/String.html](http://java.sun.com/j2se/1.5.0/docs/api/java/lang/String.html)

this is part of the problem ... what if I want s1 and s2 to represent the same string?

ie: change s2 and s1 changes. think C pointers.

---

### Post by samjh on 2006-12-15
> **slavik said:**
> this is part of the problem ... what if I want s1 and s2 to represent the same string?

ie: change s2 and s1 changes. think C pointers.You can't.

Instead, you do something like this:```
class experiment {
        public static void main(String[] args) {
                String s1 = "Hi";
                String s2 = s1;
                System.out.println("s1: " + s1);
                System.out.println("s2: " + s2);
                s2 = "Lo";
                s1 = s2;
                System.out.println("s1: " + s1);
                System.out.println("s2: " + s2);
        }
}
```

There is no pointer arithmetic in Java.  You cannot make s2 point to s1 in the same way that C or C++ points allow you to.

---

### Post by jan247 on 2006-12-15
Consider using StringBuffer instead of the String class.

---

### Post by firebadger on 2006-12-15
I don't think any of the replies so far have answered your question.

In Java, if you do this...

```
Object obj1 = new Object();
Object obj2 = obj1;
```

Then obj2 is "pointing" or referring to the same object as obj1.  There is only one object.  You can obviously reassign the variable to point elswhere, but if you don't they will continue to point at the same object.

By talking about Strings you chose a confusing example as this...
```
String s = "something";
```
is not the same as 
```
String s = new String("something");
```

You might like to read this for further info...
[http://mindprod.com/jgloss/interned.html](http://mindprod.com/jgloss/interned.html)

However, to return to your original question then both s1 and s2 refer to the same internalized String object and both == and .equals() will return true.
And to answer your next question, declare your first String explictly as a new object and it should behave as you want.  If I understand you correctly that is.

---

