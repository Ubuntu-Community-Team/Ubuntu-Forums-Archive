---
title: "A question about comma in Python"
date: 2007-07-13
forum: Programming Talk
---

### Post by mocqueanh on 2007-07-13
this is a Python source file:

```
print "Hi", age=int(raw_input("How old are you? "))
```

When i run it by Python IDLE, i receive: Syntax Error: Invalid Syntax

But if i put age with a new line, i can run it
```

print "Hi",
age=int(raw_input("How old are you?"))

```
Why ? I think a comma ( , ) is use to suppress new line in Python, so there is no diffrence between them above.

---

### Post by xtacocorex on 2007-07-13
You're trying to get user input while outputting (print statement) to the screen at the same time.  I belive that doesn't work.  I can't do that in FORTRAN or C++ because of how reads and writes are, Python should follow the same rule. 

I may be wrong here and welcome any Python expert to jump in and save me from imparting wrong wisdom.

---

### Post by bashologist on 2007-07-13
>>> age = raw_input("How old are you? ")
How old are you? 21
>>> print "Hi", age
Hi 21
>>> 

Hi 21?!

---

### Post by cwaldbieser on 2007-07-13
> **xtacocorex said:**
> You're trying to get user input while outputting (print statement) to the screen at the same time.  I belive that doesn't work.  I can't do that in FORTRAN or C++ because of how reads and writes are, Python should follow the same rule. 

I may be wrong here and welcome any Python expert to jump in and save me from imparting wrong wisdom.

This is not correct.
```

print "Hi", int(raw_input("How old are you? "))

```
The above will actually work just fine.

The problem with the original syntax is that assignment is a statement in Python.  It is not treated as an expression (like in C or Javascript, for example).  This is to thwart a common mistake in programming:
```

if(x = 7) //Oops!  Assignment.  This will always evaluate to a true value!
{
  alert("X is lucky seven!");
}

```

---

### Post by xtacocorex on 2007-07-13
Thanks cwaldbieser for the clarification.  I'm not a Python programmer and was going with my knowledge of other languages.

---

### Post by duff on 2007-07-13
> **mocqueanh said:**
> Why ? I think a comma ( , ) is use to suppress new line in Python, so there is no diffrence between them above.

Because Python uses a line break to separate statements.
```
print "Hi", age=int(raw_input("How old are you? "))
```
Is two distinct statements.  Either use a line-break (as you did), or insert a semicolon between the two
```
print "Hi",; age=int(raw_input("How old are you? "))
```

---

### Post by pmasiar on 2007-07-13
Comma is the tuple constructor operator, so you can ie. assign tuple to tuple:

a, b, c = 1, {'k': 'val'}, 'hi'

where value of b is dictionary, just to make it less boring

---

