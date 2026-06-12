---
title: "c++ references and memory management"
date: 2011-08-22
forum: Programming Talk
---

### Post by tbastian on 2011-08-22
I just realized that my professors in university seemed to gloss over c++ references. I know what they are and how to declare them and some of the benefits, but I'm not sure what kind of memory management is or isn't required.

Is something like this acceptable?
```

SomeClass & var = * new SomeClass ();

```

or should I just use a pointer in that case? Also: if it IS acceptable, do I have to worry about freeing the memory after?

---

### Post by dwhitney67 on 2011-08-22
It is typically not done in that style, although I suppose syntactically it is legal.  Sometimes one allocates an object, and then passes it by reference to a function.  But be careful of handing off a reference to an object if later you plan to delete that object.

On the topic of deleting, yes, it is good practice to delete objects that you have allocated.

---

### Post by tbastian on 2011-08-22
Thanks!

---

### Post by karlson on 2011-08-22
> **tbastian said:**
> I just realized that my professors in university seemed to gloss over c++ references. I know what they are and how to declare them and some of the benefits, but I'm not sure what kind of memory management is or isn't required.

Is something like this acceptable?
```

SomeClass & var = * new SomeClass ();

```

or should I just use a pointer in that case? Also: if it IS acceptable, do I have to worry about freeing the memory after?

Doing something like this while probably legal is useless.  

As the name implies it is a reference or another name to an object already created.  If you are allocating an object within the code block I don't think you need to create a reference to it to access it.

Most commonly it is used when you want to pass an object to a function but you don't want to copy the object and if you will modify the parameter within the function the changes made to that parameter will be reflected in the original object for a lack of the better description.

As for you question on deallocation of memory if you allocate an object using new your will have to explicitly delete it.

---

