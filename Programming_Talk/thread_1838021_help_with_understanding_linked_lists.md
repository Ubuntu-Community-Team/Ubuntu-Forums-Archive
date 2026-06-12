---
title: "help with understanding linked lists"
date: 2011-09-02
forum: Programming Talk
---

### Post by alegomaster on 2011-09-02
Hi, I am wondering if someone can tell me how the "->" operator works. A code sample demonstrating it in an simple manner would be helpful too. 

Thanks in ahead,
Alex

---

### Post by sisco311 on 2011-09-02
You forgot to specify the language. :)

---

### Post by alegomaster on 2011-09-02
> **sisco311 said:**
> You forgot to specify the language. :)


Wow i am so stupid](*,). I program in C, so C would be nice to see.

---

### Post by schauerlich on 2011-09-02
Do you know how structs work, and how to access fields? '->' is used to access fields on POINTERS to structs. If you have a struct named "foo" with a field "bar", you can access is like this:

```
struct foo_t foo;
foo.bar = 42;
```

Now, if we use a pointer:

```
struct foo_t *blah = &foo;
blah->bar = 256;
```

---

### Post by alegomaster on 2011-09-02
> **schauerlich said:**
> 

```
struct foo_t *blah = &foo;
blah->bar = 256;
```

Oh, now I get it. I was thinking of it wrongly. Blah is a pointer to foo, and you need the "->" operator to emulate the "." operator.

So "->" is used for pointer of structs, and "." is used for structs.

---

### Post by schauerlich on 2011-09-02
Yup. foo->bar is equivalent to (*foo).bar

---

