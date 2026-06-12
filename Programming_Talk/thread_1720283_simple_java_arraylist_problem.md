---
title: "simple java arraylist problem"
date: 2011-04-03
forum: Programming Talk
---

### Post by slwx on 2011-04-03
Hi,
Suppose I have an arraylist:
ArrayList<Type> a = new ArrayList<Type>();

I would like to know the type, but 

a.getClass()

returns java.util.ArrayList
 
any ideas how i can get the type? the arraylist is initialy empty..

Thx,
Mathias

---

### Post by Joeb454 on 2011-04-03
<type> should have been specified when you created the ArrayList, so you should already know what it is. That's how I've always used it, at least.

---

### Post by simeon87 on 2011-04-03
You should be able to get that information using reflection. The type of a generic ArrayList is available at compile time but not at runtime so I don't think you can call a method to get the type. But with reflection you may be able to obtain it. You could also store the type separately in a variable (Type.class).

---

### Post by Some Penguin on 2011-04-03
See [http://i-proving.ca/space/BC+Holmes/blog/2008-11-18_2]("http://i-proving.ca/space/BC+Holmes/blog/2008-11-18_2").

---

### Post by dazman19 on 2011-04-04
wrap it in a class and use your class. Then you can add all sorts of stuff to it. 

But that is the type, what its returning its the name of the type.

---

