---
title: "[C++] warning: NULL used in arithmetic"
date: 2008-08-29
forum: Programming Talk
---

### Post by NovaAesa on 2008-08-29
Okay, say I have a function foo that returns a pointer to an object of type dataType. This function will either return NULL or a pointer to an object.
```

dataType* foo();

```

I want to test if the return value is NULL or not. I use code something like this:
```

if (foo() == NULL) {
  //do something
}

```

Now, the code in question does what I want it to, I'm just getting this pesky warning:
```
warning: NULL used in arithmetic
```

What's this all about? I want to fix whatever it's warning me about, but I don't see what's wrong with it.


EDIT: I can post actual code if that will help, this is just mockup of what the situation is.

---

### Post by mike_g on 2008-08-29
Looks ok to me. Are you sure its not something else thats causing the problem? Many you could post the code it came from.

On a side note i prefer using:
```
if(! foo())
{
  //do something
}
```
But then I'm lazy :)

---

### Post by NovaAesa on 2008-08-29
Wow, silly me. I just realised that my fuction 'foo' actually returns a boolean. I can see why I got the error now. I was comparing a boolean with a zero constant (NULL).

---

### Post by Rany Albeg on 2008-08-29
Same thing happened to me:)

---

### Post by Paul Miller on 2008-08-29
Isn't NULL defined as ((void*)0)?  If that's the case, I don't exactly see why checking 0 == NULL triggers such a warning.

---

### Post by dribeas on 2008-08-29
> **NovaAesa said:**
> ```

if (foo() == NULL) {
  //do something
}

```

Standard recommendation is using 0 instead of NULL. I know that you've already solved it, but nonetheless...

---

### Post by nvteighen on 2008-08-29
> **Paul Miller said:**
> Isn't NULL defined as ((void*)0)?  If that's the case, I don't exactly see why checking 0 == NULL triggers such a warning.
Because they're of different types. 0 is int, (void *)0 is a pointer.

---

