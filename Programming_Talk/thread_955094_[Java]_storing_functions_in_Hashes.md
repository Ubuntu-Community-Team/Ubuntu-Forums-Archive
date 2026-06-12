---
title: "[Java] storing functions in Hashes?"
date: 2008-10-21
forum: Programming Talk
---

### Post by meanburrito920 on 2008-10-21
Is there a way to accomplish this, such as in python, where one can store a function into a dictionary and call it through the dictionary? Is there even a way to return functions? All I can think of is storing a function wrapped into its own class in a HashMap and then returning the class and calling a act() function off of it. However, I think creating a wrapper for every function is a bit of overkill. Any ideas?

Edit: maybe I could use an enum and map the functions using a switch?

---

### Post by tinny on 2008-10-22
> **meanburrito920 said:**
> Is there a way to accomplish this, such as in python, where one can store a function into a dictionary and call it through the dictionary? Is there even a way to return functions? All I can think of is storing a function wrapped into its own class in a HashMap and then returning the class and calling a act() function off of it. However, I think creating a wrapper for every function is a bit of overkill. Any ideas?

Edit: maybe I could use an enum and map the functions using a switch?

Anonymous inner classes in Java are often used instead of closures. So you could just define a anonymous inner class and pass that to the collection. The anonymous inner class could implement a "Closure" interface that defines 1 method (".exe()")

---

### Post by joe_bruin on 2008-10-22
Yes, you can do this without creating a wrapper for every function.  Look at java.lang.reflect.Method.  This gives you an object that contains reference to a function.  You can then create a hash of Method objects and call their contained functions.

---

