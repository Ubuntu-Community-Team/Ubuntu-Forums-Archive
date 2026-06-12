---
title: "getClass() vs. Instanceof in equals()"
date: 2010-02-08
forum: Programming Talk
---

### Post by andrew222 on 2010-02-08
As we know there are differing opinions on what is better to use in overriding equals()...

 getClass() or instanceof for argument type checking.

I would like to know if there is anyone who is strongly in favor of using instanceof instead of getClass()?

---

### Post by Reiger on 2010-02-08
Instanceof. getClass().equals() does not work with supertypes (they have a different class from their derivative types); whereas the instanceof mechanism does work with super types, interfaces and the whole lot. This means that instanceof is correct (it honours the workings of the Java type system), whereas getClass().equals() is not.

---

### Post by andrew222 on 2010-02-08
What do you think about the possibility of instanceof breaking symmetry?

[http://www.javaworld.com/javaworld/jw-06-2004/jw-0614-equals.html?page=5](http://www.javaworld.com/javaworld/jw-06-2004/jw-0614-equals.html?page=5)

---

### Post by Axos on 2010-02-08
In my humble, non-academic opinion, having an instance of a superclass decide whether or not it is equal to an instance of a subclass is disgusting beyond belief. If you are going to do that kind of thing, the classes had better be intimately related (members of the same project at the very least). Doing that across a library boundary would be insanity.

Of course, I could be completely wrong. Maybe it's extremely elegant and I'm just too stupid to realize it. :D

---

### Post by NovaAesa on 2010-02-08
> **andrew222 said:**
> What do you think about the possibility of instanceof breaking symmetry?

[http://www.javaworld.com/javaworld/jw-06-2004/jw-0614-equals.html?page=5](http://www.javaworld.com/javaworld/jw-06-2004/jw-0614-equals.html?page=5)

As long as the contract of Object's equals(Object o) is held, it doesn't really matter.

---

### Post by Reiger on 2010-02-09
> **andrew222 said:**
> What do you think about the possibility of instanceof breaking symmetry?

[http://www.javaworld.com/javaworld/jw-06-2004/jw-0614-equals.html?page=5](http://www.javaworld.com/javaworld/jw-06-2004/jw-0614-equals.html?page=5)

Then you are doing it wrong. :P 

Seriously, though if you are going to override equals() you take this responsibility upon you. Symmetry can be ensured fairly trivially by comparing against a common interface. Symmetry can be ensured some more by not using instanceof() for direct comparison; rather by using it for type-safe casting and then checking with member methods as appropriate.

Note that the Object.equals() method does not work by comparing types. It works by comparing object locations in memory.

EDIT: Reading your link the problem exposed there is when people create fundamentally flawed inheritance trees: a point in 2D is not comparable with a point in 3D. Any equals scenario in 2D is going to be flawed because 2D is *not* the general case. The general case is the vectory of degree R. Therefore a multi-dimensional point comparison like this would involve something like the following:
```

interface MultiPoint<T> {
  /**
   * Get this point notated as vector (array) of coordinate values.
   * The index of a value 
   * corresponds to the degree of the coordinate. This means that a point with n dimensions 
   * returns the coordinate in the first dimension as the first element in the array, 
   * its coordinate in the second dimension as the second element, etecetera.
   * @return array with values of coordinates
   */
  T[] vector();
  /**
   * Get the degree of the Mathematical vector that describes this point in multidimensional space.
   */
  int degree();
  public static abstract class GenericMultiPoint<T> implements MultiPoint<T> {
    /**
     * Generic equals method suitable for any MultiPoint.
     * Returns true if and only if o is a MultiPoint, of same degree and coordinates
     * as this MultiPoint.
     * Thus, this method provides an equivalence relation in equals().
     */
    boolean equals(Object o) {
      if(!o instanceof MultiPoint) {
        return false;
      }
      int d=degree(),k=0;
      T[] myData=vector();
      Object[] data=((MultiPoint) o).vector();
      if(d != data.length) {
         return false;
      }
      boolean result=false;
      do {
        result = myData[k].equals(data[k]);
        ++k;
      }
      while(k<d && result);
      return result;
    }
  }
}

```

---

### Post by Some Penguin on 2010-02-09
> **andrew222 said:**
> What do you think about the possibility of instanceof breaking symmetry?

[http://www.javaworld.com/javaworld/jw-06-2004/jw-0614-equals.html?page=5](http://www.javaworld.com/javaworld/jw-06-2004/jw-0614-equals.html?page=5)

Don't do it.  equals() is a pretty fundamental method, and the last thing you need is for some Collection to behave unpredictably because you broke equals() and have a heterogeneous set.

---

### Post by Reiger on 2010-02-09
> **Some Penguin said:**
> Don't do it.  equals() is a pretty fundamental method, and the last thing you need is for some Collection to behave unpredictably because you broke equals() and have a heterogeneous set.

Do you mean instanceof in equals()? Because that is the only way _not_ to break Collections; if you use HashMap<K,V> such and put(Z,V) such that Z is a derivative type of K then any equals() method in K defined to depend on the outcome getClass().equals(K.class) will see you put things and never find them back again.

That is to say, the equivalence relation that equals() should be by contract is in practice less important to honour than an ill-defined equality relation this equals() supposedly is.

---

