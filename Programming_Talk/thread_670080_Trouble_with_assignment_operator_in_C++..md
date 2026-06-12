---
title: "Trouble with assignment operator in C++."
date: 2008-01-17
forum: Programming Talk
---

### Post by MdaG on 2008-01-17
Hi!

I'm having trouble copying data from one object to the other.
The compiler says: *Can't convert from 'const A*' to 'A*'*
I'm sure there's an obvious mistake on my behalf here, but I can't see it... :confused:
Here's the setup:

```
void method(const A* a)
{
   A* tmpA = new A();
   tmpA = a;   // This line isn't accepted by the compiler!
   .
   .
   .
}

A& A::operator=(const A& a)
{
   // Copy members of a
   .
   .
   .
   return *this;
}
```

*EDIT*
Solved it. *tmpA = *A ... Doh!

---

### Post by dwhitney67 on 2008-01-17
Is the allocation of memory for tmpA necessary?

[PHP]   A* tmpA = new A();
   tmpA = a;   // This line isn't accepted by the compiler[/PHP]

Perhaps you wanted something like:

[PHP]A* tmpA = const_cast< A* >( a );   // establish a non-const reference to 'a'[/PHP]

or

[PHP]A tmpA = *a;   // make a copy of 'a'[/PHP]

---

### Post by aks44 on 2008-01-17
In this case you'd be better off using the *_copy constructor_* rather than  the assignment operator:
```
A* tmpA = new A(*a);
```

The final result is the same but it's way more efficient this way (there is only a construction, instead of a construction + an assignment).

---

### Post by dwhitney67 on 2008-01-17
> **aks44 said:**
> In this case you'd be better off using the *_copy constructor_* rather than  the assignment operator:
```
A* tmpA = new A(*a);
```

The final result is the same but it's way more efficient this way (there is only a construction, instead of a construction + an assignment).

Then you have to delete the tmpA when done.  With this added overhead, is it still "way more" efficient, or just perhaps "slightly" more efficient?

---

### Post by aks44 on 2008-01-17
> **dwhitney67 said:**
> Then you have to delete the tmpA when done.  With this added overhead, is it still "way more" efficient, or just perhaps "slightly" more efficient?

Hmm sorry I should have made it clear that this was intended to replace the OP's code, assuming (s)he *needs* both dynamic allocation *and* copy (rather than aliasing).

Of course the way *you* did it in your last example is the most efficient way to copy an object (stack allocation, a single copy constructor call, and you're done :)).


Since I didn't address that in my previous post, I'll also add that const_cast is Evil and should be avoided whenever possible... but I guess you already know that. ;)



_EDIT:_ re-reading your question I realize that I didn't understand it correctly the first time (thus I didn't answer properly).
The *_copy_* operation is "way more efficient" when using the copy constructor rather than default constructor + assignement, and this is independent of the way the object is allocated. Now, depending on the complexity of the class (which we have no clue about), the whole efficiency of object creation/destruction can indeed range from "slightly more efficient" (if the class is very simple, in which case the relative overhead of dynamic allocation is very important) to "amazingly more efficient" (if the class is very complex, contains sub-objects that need deep-copying, etc etc).

---

