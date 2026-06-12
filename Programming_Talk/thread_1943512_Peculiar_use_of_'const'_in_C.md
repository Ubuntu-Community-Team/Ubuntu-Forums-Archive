---
title: "Peculiar use of 'const' in C"
date: 2012-03-19
forum: Programming Talk
---

### Post by cguy on 2012-03-19
I've seen this type of code:

In the .c file:
```

int my_function(const char *const param1, const int param2)
{
...
}

```

In the header:
```

int my_function(const char *param1, int param2);

```

Why is the "const" removed in the header?
It doesn't seem to be a mistake because there are lots of functions declared like this.

---

### Post by GeneralZod on 2012-03-19
The const modifier in "const int param2" is ignored completely when the compiler constructs the function signature (it's 8.3.5.3 in the C++ spec; not sure where in the C one) so that

```

int my_function(const char *param1, int param2);

```

and

```

int my_function(const char *param1, const int param2);

```

are identical from the compiler's point of view.  As to why the const isn't used in the header file: the fact that param2 can't be modified inside the body of my_function is an implementation detail only (which may end up changing) and should be of absolutely no interest to callers of my_function, so it's probably best not to mention it in the header.

Edit:

Note that e.g.

```

int my_function2(const char *param1);

```

and

```

int my_function2(char *param1);

```

are *not* the same, however.

---

