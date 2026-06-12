---
title: "What's So Great about Ruby's Proc Objects?"
date: 2007-04-23
forum: Programming Talk
---

### Post by Ubuntist on 2007-04-23
Really, honestly, I don't want to start a religious war about the relative merits of Python and Ruby. I'm just a naive lost sole trying to understand the ins and outs of modern programming languages.

In Ruby, if I want to pass a function around I create a proc object, e.g.,
```
double = Proc.new {|x| 2 * x}
```To apply the proc object, I have to do something like
```
double.call(66)
```or
```
double[66]
```In Python, on the other hand, I can just create a regular function
```
def double(x):
  2 * x
```I can then pass this function as an argument and still use it in the intuitively obvious manner ```
f(66)
```So, my question is, what's the advantage of Ruby's approach?  The only advantage I can see is that in Ruby I can call a function of no arguments without a type a pair of parentheses after the function name, whereas in Python I'll have to type ```
f()
```But that seems like a pretty small advantage.

---

### Post by winch on 2007-04-23
In ruby a proc is a block with a set of local variables bound with it.

This is more inline with the python code.

```

def double(x)
    2 * x
end

f = self.method(:double)
f.call(66)

```

IMO the advantaged of rubys approach is it doesn't make a special case out of procs or methods. They are treated the same as other objects.

edit:

For instance if you where to now do this

```

def f(x)
    x * x
end

```

What would you expect to happen if you did this?

f(10)

---

### Post by Ubuntist on 2007-04-24
If I understand correctly, in Ruby we effectively have different namespaces for objects and methods.

---

### Post by winch on 2007-04-24
> **Ubuntist said:**
> If I understand correctly, in Ruby we effectively have different namespaces for objects and methods.

All methods are associated with a particular object.

So when you run irb and type in

```

def double(x)
    x * 2
end

```

Method double has to be associated with an object. It ends up as a private method of class Object.
Also ruby creates a top level object "main" which is an instance of Object. Ruby starts in the context of this object.

So you could call your double method in many ways

```

self.double(10)

#self is implied if no receiver object is specified
double(20)

Object.double(40)

a = Object.new
a.double(80)

```

This makes it possible to program in a procedural style even though ruby is OO.

---

