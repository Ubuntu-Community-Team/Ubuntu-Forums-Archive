---
title: "[SOLVED] Pyhotn forward declaration?"
date: 2007-07-20
forum: Programming Talk
---

### Post by olejorgen on 2007-07-20
Is this really the correct way of doing forward declaration in python?
```

# ugly forward declaration :-/
class Bar:
 def __init__(self):
  pass

class Foo:
 def __init__(self):
  pass
 def bars(self):
  return [Bar(), Bar()]
class Bar:
 def __init__(self):
  pass
 def foos(self):
  return [Foo(), Foo()]

```

PS: How do I change the post title?

---

### Post by Paul Miller on 2007-07-21
Yes, this is the best way to do this sort of thing.  However, you can reduce the initial definion of Bar to
```

class Bar:
    pass

```

There's no reason to define __init__ in the dummy class definition.

---

### Post by olejorgen on 2007-07-21
It's not? I assumed all methods that was used inside  Foo had to be dummy declared.
```

class Bar:
 pass

class Foo:
 def __init__(self):
  pass
 def bars(self):
  return [Bar(1), Bar(1)]
class Bar:
 def __init__(self, d):
  self.d = d
 def foos(self):
  return [Foo(), Foo()]

```
*testing*
But it doesn't.

Thanks.

This isn't that strange, when I think a little, since python is dynamically bound

---

### Post by cwaldbieser on 2007-07-21
> **olejorgen said:**
> It's not? I assumed all methods that was used inside  Foo had to be dummy declared.
```

class Bar:
 pass

class Foo:
 def __init__(self):
  pass
 def bars(self):
  return [Bar(1), Bar(1)]
class Bar:
 def __init__(self, d):
  self.d = d
 def foos(self):
  return [Foo(), Foo()]

```
*testing*
But it doesn't.

Thanks.

This isn't that strange, when I think a little, since python is dynamically bound
In your simple example, the is no reason to forward declare Bar.
```

class Foo:
 def __init__(self):
  pass
 def bars(self):
  return [Bar(1), Bar(1)]
class Bar:
 def __init__(self, d):
  self.d = d
 def foos(self):
  return [Foo(), Foo()]

foo = Foo()
foo.bars()
print "OK"

```
The above works fine with no forward declaration.

In your example, this is what is happening:
The interpreter is making a single pass through your source code, from top to bottom, executing code as it goes.  The first statement it executes is "class Bar", which assigns the name "Bar" to some class object.
Next, if sees the statement "class Foo", which assigns the name Foo to some class object.  Then is sees the statement "class Bar" again, so it rebinds the name Bar to some entirely different class object.  At no point has it actually tried to execute the methods in any of these classes yet, so there is no problem that the name Bar was originally assigned to a class object with no members.  As illustrated in my example, it makes no difference whether the name Bar was bound to any object at all at that point!

In my script, when the line "foo.bars()" is executed, the name Bar must have been bound, or else an error would have resulted when the Foo object attempted to create some Bar objects.

---

### Post by olejorgen on 2007-07-21
Ah, then it was bacause I had a static member of the same type
```

class Bar:
 b = Bar()

```

---

