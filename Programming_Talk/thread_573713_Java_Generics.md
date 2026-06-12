---
title: "Java Generics?"
date: 2007-10-11
forum: Programming Talk
---

### Post by keeler1 on 2007-10-11
I am writing a project for a class of mine and have run into a snag.

I have a parameterized class t

```
public class Polynomial<T extends Number>

```

Inside this class is a ```
Hashtable<Integer,T>
```

One method I have to make is one to take the derivative of the Polynomial, but not alter the original polynomial at all.

So I made a private constructor that takes a Hashtable

```
private Polynomial(Hashtable<Integer,T> newTable)
```

Inside my derivative method I create a new hashtable of the same type.  So now I need to initialize it and call the private constructor

The derivative function looks like this so far

```
      Hashtable<Integer,T> newTable = new Hashtable<Integer,T>();
      
      Set<Integer> keySet = ht.keySet();
      
      for(Integer key : keySet)
      {
         T newNum = ht.get(key);
         Integer newKey = key - 1;
         
         
         newTable.put(key -1, newNum.multiply(key));
      }
```

the last line is killing me. newNum.multiply(key) returns a new Number (which is the parameterization of the entier class) but the compiler complains.  

The error is

```
The method put(Integer, T) in the type Hashtable<Integer,T> is not applicable for the arguments (int, Number)	Proj1/src/proj1	Polynomial.java	line 53	
```

So basically it doesnt like the return type of the method eventhough the entire class is parameterized to be of type <T extends Number>

Is there any way around this or any way to put constraints on the parameterization of the Hashtable?

---

### Post by PaulFr on 2007-10-12
Should that be:

   1. public class Polynomial<T extends BigInteger> or
   2. public class Polynomial<T extends BigDecimal>

(multiply() function are defined for these classes, is it defined for Number class) ?

---

### Post by Quikee on 2007-10-12
newNum.multiply(key) returns Number not T (multiply is not a generic function)... 

a cast should solve this.
```
newTable.put(key -1, (T) newNum.multiply(key));
```


It might also be that boxing of "key -1" fails.

There might be other ways...

---

