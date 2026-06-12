---
title: "Java - generic Array"
date: 2010-01-03
forum: Programming Talk
---

### Post by LKjell on 2010-01-03
Since I cannot create generic array because of some type safety how can I then create an array for example in toArray() method?

---

### Post by PaulM1985 on 2010-01-03
Creating a generic array?  Do you mean you want to create an array of a specific type, or do you want to create an array of all types?  So for example do you want an array of Cat objects or an array of any type of Object.

There are generic arrays that can be used for creating an array of a type.  Look up ArrayList on the Java API.

If you want an array to store Object 's of various types...  why would you want to do this?

Paul

---

### Post by NovaAesa on 2010-01-03
I think LKjell means that you cannot create an array of say List<MyObj>. (which of course you can't - obvious type safety issues there). I'm not really sure what JKjell's actual question is though!

---

### Post by Reiger on 2010-01-03
Uhm?

```

public Type[] fromCollection(Collection<Type> collected) {
  /* see the docs at: http://java.sun.com/j2se/1.5.0/docs/api/java/util/Collection.html */
  return collected.toArray(new Type[] {});
}

```

---

### Post by LKjell on 2010-01-03
Say I have

```
public class list<E extends Comparable<E>> implements mylist<E> {

...

public E[] toArray(E[] a) {
            E b[] = new E[size]; //Error: generic array
         ...
     }
}
```

---

### Post by Reiger on 2010-01-03
Since your E is-a Comparable:

```

public E[] toArray(E[] a) {
  Comparable [] my_array = new Comparable[size]; // use supertype
  /* code */
  return (E[]) my_array; // cast to return type.
}

```

---

### Post by LKjell on 2010-01-04
Thanks Reiger I was pulling my hair when I was one error reading "Found E required E".

---

