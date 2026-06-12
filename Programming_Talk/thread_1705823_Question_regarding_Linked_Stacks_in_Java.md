---
title: "Question regarding Linked Stacks in Java"
date: 2011-03-12
forum: Programming Talk
---

### Post by Quake on 2011-03-12
I'm currently studying Linked Stacks in Java.

One the things that caught my eyes is pop(), this is my prof's code:

```
public E pop() {
        E savedInfo = top.info;

        Elem<E> oldTop = top;
        Elem<E> newTop = top.next;

        top = newTop;

        oldTop.info = null; // scrubbing the memory
        oldTop.next = null; // scrubbing the memory

        return savedInfo;
    }
```

The way I understand it,  "oldTop.info = null" and  "oldTop.next = null" are unnecessary because the reference of top is being replaced by another reference in by top.next.

Correct me if I'm wrong.

Thanks.

---

### Post by NovaAesa on 2011-03-12
As far as I can tell, you are correct. The reference variable oldTop will go out of scope when pop() returns, and the Elem object it pointed to will have no references and will eventually be garbage collected.

Although, you will be helping out the garbage collector by nulling out the references. Think about what the garbage collector will do when you pop the stack again. Drawing a diagram will help.

---

### Post by Some Penguin on 2011-03-13
It depends on whether you ever export a reference to the Elem, such as through an already-created iterator.

---

### Post by Reiger on 2011-03-13
The whole use of oldTop is redundant. Iterators don't come into it, nothing is exported here (and this method is local to the class). Simpler version:
```

public E pop() {
   E savedInfo = top.info;
   top = top.next;
   return savedInfo;
}

```

The scrubbing the memory bit is redundant. Why?

Top is a reference to an object, not the object itself. Therefore the garbage collector will not collect top if a reference is held outside of the data structure, and setting bits to null locally doesn't affect bits outside the data structure.

---

### Post by Reiger on 2011-03-13
> **NovaAesa said:**
> Although, you will be helping out the garbage collector by nulling out the references.
Not really, these are local variables and they have a short life span (meaning that the GC will strongly favour reclaiming them anyway). It is quite possible that they are already collected as part of cleanup once the method exits (apart from the periodic sweeps, the VM might allocate the objects on the stack with corresponding clean up as a result).

---

### Post by Quake on 2011-03-13
> **Reiger said:**
> The whole use of oldTop is redundant. Iterators don't come into it, nothing is exported here (and this method is local to the class). Simpler version:
```

public E pop() {
   E savedInfo = top.info;
   top = top.next;
   return savedInfo;
}

```

The scrubbing the memory bit is redundant. Why?

Top is a reference to an object, not the object itself. Therefore the garbage collector will not collect top if a reference is held outside of the data structure, and setting bits to null locally doesn't affect bits outside the data structure.

This is exactly what I thought but I had doubts because as you know, this is the prof's code.

---

