---
title: "Python operator overloading using C"
date: 2010-06-02
forum: Programming Talk
---

### Post by zarqoon on 2010-06-02
I have created two new python types Foo and Bar using the c api. Foo's PyMethodDef contains the function __lshift__. This function accepts a Bar object.
If i now call 
```
foo.__lshift__(bar)
```
with foo beeing an instance of Foo and bar of Bar everything works perfectly.
But if i call
```
foo << bar
```
ipython reports
```
<type 'exceptions.TypeError'>: unsupported operand type(s) for <<: 'Foo' and 'Bar'
```

I can not figure out why this is. To my knowledge foo << bar should cause foo.__lshift__(bar) to be called but somehow it doesn't.
The only reason i can think of is that setting an operator method using the tp_methods field of a type somehow does not work.
I use the most basic baseclass. I checked if i do not declare __lshift__ my type does not have that method. I therefore suspect that i've to declare it somewhere else or set some flag somewhere but i can not figure out where.

I get the same error if i call
```
operator.__lshift__(foo,bar)
```
And as a second note i am using << as if it where a stream operator. Not to bitshift anything, but since the function doing the work does not even get called this can not be the problem, can it?

---

### Post by tookyourtime on 2010-06-02
Is your function definition of the style:

```
Foo.__lshift__(self, other)
```

and not just ```
__lshift__(other)
```

Can you post the actual code?

---

### Post by matja on 2010-06-02
Hi zarqoon,

I think your suspicion is correct, [PyTypeObject]("http://docs.python.org/c-api/typeobj.html#type-objects") has a [tp_as_number]("http://docs.python.org/c-api/typeobj.html#tp_as_number") field that can point to a [PyNumberMethods]("http://docs.python.org/c-api/typeobj.html#number-structs") struct. That in turn has a *nb_lshift* field that you can set to point to a binary function that implements a left shift or in your case a stream operation.

I used the PyNumberMethods struct to get (inplace) addition to work for a C extension type of my own, this should be no different. I don't think you need to set a flag to tell Python that the tp_as_number field is available, but a look through the documentation probably won't hurt. I noticed some advice regarding type checking, for instance.

Hope this helps!

Regards, Mattias

---

### Post by zarqoon on 2010-06-04
@ tookyourtime
neither. I have a ```
PyObject* Foo_lshift(PyObject* self,PyObject*args)
``` function that is set in a PyMethodDef struct with function name __lshift__

@ matja 
On a first look your suggestion looks very promising. I'll check into that. I'll actually need to implement an addition operator next. The behavior of my object makes sense now that i've seen this.

---

### Post by zarqoon on 2010-06-07
I've implemented matja's suggestion an it kind of works. thx for that.
But there is one problem i do not know how to get rid of.
I implemented the field nb_lshift in the Type Foo
If i use ```
foo << foo
``` the function gets called, but ```
foo << bar
``` does not call the function and outputs the same TypeError as above.

Solved that one myself.
The Py_TPFLAGS_CHECKTYPES flag has to be set to in the Type object to turn typechecking for number functions of.

---

