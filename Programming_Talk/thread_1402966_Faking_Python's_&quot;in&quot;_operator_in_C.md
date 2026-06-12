---
title: "Faking Python's &quot;in&quot; operator in C"
date: 2010-02-09
forum: Programming Talk
---

### Post by trilobite on 2010-02-09
Hi all -  

 After having used Python for a while, I've been getting into some C coding (and generally enjoying it). However, there is one thing that Python has (and C lacks, and I wish it had) - the "in" operator (when you want to easily check whether a value is one of a list of values).  

In Python, you just do - 
```
 
if val in [4, 27, 68, 152]: 
   print "ok" 

```  

That kind of thing.  So, how does one "fake this" in C, to get an "in" operator there?  
Many thanks in advance - 
- trilobite

---

### Post by SledgeHammer_999 on 2010-02-09
Maybe using a "switch"?

```

switch (val)
{
   case 4:
   case 27:
   case 68:
   case 152:
   printf("ok");
   break;

   default:
   break;
}
```

(I know, it's much bigger than python.)

---

### Post by trilobite on 2010-02-09
> **SledgeHammer_999 said:**
> Maybe using a "switch"?

```

switch (val)
{
   case 4:
   case 27:
   case 68:
   case 152:
   printf("ok");
   break;

   default:
   break;
}
```

(I know, it's much bigger than python.)

Hi Sledgehammer! 
 Thanks for that! I think you're right in that I'll have to use a switch/case, as you've shown. 
It's puzzling as to why such a useful thing as the "in" operator was left out of C. I guess they thought "ok, we've got switch - "in" isn't needed". Oh well.. maybe in C1x...  ;) 
- trilobite

---

### Post by wmcbrine on 2010-02-09
It's not puzzling. C is a much lower-level language than Python, and Python's "in" is a very high-level operation. Never mind the very thing you're using "in" on -- the list. Nothing in C is remotely comparable.

---

### Post by mdurham on 2010-02-09
C is also 'very' much older that Python.

---

### Post by Lux Perpetua on 2010-02-09
> **trilobite said:**
> It's puzzling as to why such a useful thing as the "in" operator was left out of C....because you don't have enough experience with C yet to understand it. The thing about C that is probably strange to you is that there is no magic behind the scenes. Once you come to terms with that, you will "get" C.

---

### Post by jpkotta on 2010-02-10
"in" is just syntactic sugar.  It's really just another way of doing collection.__contains__(obj), and in the case of lists __contains__() is not much more than a for loop.
```

static int
list_contains(PyListObject *a, PyObject *el)
{
        Py_ssize_t i;
        int cmp;

        for (i = 0, cmp = 0 ; cmp == 0 && i < Py_SIZE(a); ++i)
                cmp = PyObject_RichCompareBool(el, PyList_GET_ITEM(a, i),
                                                   Py_EQ);
        return cmp;
}

```

(BTW, that's C.)

---

### Post by MadCow108 on 2010-02-10
you could fake the in operator by defining iterators with a fixed interface to your containers just like C++ does it (which has an "in" operator for its generic containers, its called find)
Then you can write an "in" function with works on the generic iterators and does not care for the underlying container.
This will probably also be the way python does it under the hood.

but thats a lot of work in C and only useful if you have a ton of different containers for a big project and need a unified interface.

---

### Post by nrs on 2010-02-10
> **SledgeHammer_999 said:**
> Maybe using a "switch"?

```

switch (val)
{
   case 4:
   case 27:
   case 68:
   case 152:
   printf("ok");
   break;

   default:
   break;
}
```(I know, it's much bigger than python.)
It's not clear if the OP just wants to check the variable for a series of possible values, or if the OP wants to check an array / list for a value.
Former a simple switch would work, latter, no.

---

