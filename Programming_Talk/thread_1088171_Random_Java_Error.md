---
title: "Random Java Error"
date: 2009-03-05
forum: Programming Talk
---

### Post by vandorjw on 2009-03-05
```

-----

```

I have this strange Java Error.
does anyone know what causes it?

> 
****@***-laptop:~/2AA4-Sfwr_Design/Assignments/Assig4$ javac NodeT.javaNodeT.java:16: cannot find symbol
symbol  : constructor PointT()
location: class PointT
    {
    ^
1 error


---

### Post by C-- on 2009-03-05
It says the error is in your PointT class. Could you post it for us?

---

### Post by vandorjw on 2009-03-05
This is PointT. It compiles without problems or errors however. Maybe I don't quite understand how inheritance works.

```

 -- academic integrity --

```

A simple google search will turn up my code for other students to copy. That is why I removed it.

---

### Post by C-- on 2009-03-05
Change the NodeT constructor.

```
 EDIT: Code removed for cc7

```

Also get rid of the xc and yc variables in the NodeT class.

Try that and let me know if it works. I'll explain why this works if it does.

---

### Post by vandorjw on 2009-03-05
Thanks that works.:popcorn:
+1

explain please? :)

---

### Post by C-- on 2009-03-05
> **cc7gir said:**
> Thanks that works.:popcorn:
+1

explain please? :)

In Java, when you create an instance of an object, the class constructor of that object's class needs to call the constructor of it's superclass. This is required so that you cannot override a superclass constructor; doing so would destroy inheritance.

In your NodeT class, you did not call PointT's constructor. So, the compiler helped you out by inserting a call to the default constructor for you. The default constructor is always the constructor without arguments, in this case, PointT().

Normally the default constructor is also provided in a class by the compiler, unless you provide your own constructor. You wrote the PointT(double x, double y) constructor, so the compiler didn't create a default constructor for you. So when the compiler tried to call PointT() from from NodeT(double x, double y, nodeTypeT nt), it couldn't find it because it didn't exist. Hence, the error.

super(x,y) explicitly calls the superclass constructor that has those two arguments, so the compiler does not try and call the default constructor, which fixes the error.

Also, we got rid of the xc and yc variables in NodeT because it inherits those variables from PointT, and it can treat them as its own variables (without setters and getters) because you declared them as protected. Therefore it would be redundant to include another declaration in NodeT.

Hope that helps ;)

---

### Post by vandorjw on 2009-03-05
It does. Thank you for helping solve this so quick, and for the explanation. (the explanation being the more valuable of the two)

Cheers - CC7

---

