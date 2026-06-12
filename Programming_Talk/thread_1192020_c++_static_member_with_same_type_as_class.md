---
title: "c++ static member with same type as class"
date: 2009-06-19
forum: Programming Talk
---

### Post by Victor Liu on 2009-06-19
In C++ is it possible to declare a static member variable of a class that is the same type as the class? As in, I want to be able to write

```

class NumberType{
    int val;
public:
    NumberType(int i):val(i){}
    static const NumberType ZERO;
};

```

When I try to do something like this, the initializer in the implementation file is

```

const NumberType NumberType::ZERO(0);

```

which gives compiler errors
```

error: expected unqualified-id before '(' token
error: abstract declarator `const NumberType' used as declaration

```

Is there something I'm doing wrong?

**Solved:** Nevermind; my member was named NAN, and that is apparently declared in a header file already. I just need to use a different name.

---

### Post by Mirge on 2009-06-19
Not to hi-jack your thread, but could you explain what:

**NumberType(int i):val(i){}**

does please? :val(i) ?

---

### Post by Victor Liu on 2009-06-19
That's an initializer list. See here:
[http://www.parashift.com/c++-faq-lite/ctors.html#faq-10.6](http://www.parashift.com/c++-faq-lite/ctors.html#faq-10.6)

---

### Post by Mirge on 2009-06-19
Thanks ;)

---

### Post by dwhitney67 on 2009-06-19
> **Victor Liu said:**
> ...

**Solved:** Nevermind; my member was named NAN, and that is apparently declared in a header file already. I just need to use a different name.

I'm not sure what you solved.  The code you posted in your OP compiles just fine, even if I change the variable name ZERO to NAN.

---

