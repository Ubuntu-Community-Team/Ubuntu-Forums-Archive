---
title: "ArrayList - symbol not found Java"
date: 2009-03-21
forum: Programming Talk
---

### Post by TeeRev on 2009-03-21
I'm not sure what the problem here is exactly...

This is for an assignment, and the basis is switching everything that was an Array to ArrayList.  I have java.util.ArrayList imported at the top, and I have the class extending ArrayList, but when I try using certain features such as ArrayList.clear() or ArrayList.toArray() it says it cannot find the symbol.  I checked my version and I have java 1.6.0_10 installed.  Pretty stumped as to what's going on..

Here's an example of one of the errors I am getting:

ToDoList.java:292: cannot find symbol
symbol  : method clear(java.util.ArrayList<java.lang.String>)
location: class java.util.ArrayList
	  ArrayList.clear(this.activity);
	           ^
I'm not sure if I still have the proper syntax as I have been messing around with some things that I have found in other forums, but the main problem is that it is not finding the clear() method.

---

### Post by simeon87 on 2009-03-21
I can't really tell but are you using the clear method like a static method? I.e., like this: ArrayList.clear(this.activity)? The clear method does exist but it's not a static method, so you can use it like this:

```

ArrayList example = new ArrayList();
example.add(new Object());
example.clear();

```

Edit: Why are you extending ArrayList? This is not needed for normal use..

---

### Post by TeeRev on 2009-03-21
Thanks for the quick response!  I guess I had it kind of backwards, I don't quite understand the ArrayList stuff fully yet, but I switched it to 

this.activity.clear();

and the error is gone.  Still a few things I need to get going before I can fully test the file, but that one is off the error list anyways so it seems like that did it, thanks!

---

