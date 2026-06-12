---
title: "c++ template question"
date: 2008-06-02
forum: Programming Talk
---

### Post by p_o_x on 2008-06-02
i want to initialize a pointer to a template, but as a java/c# programmer the syntax is throwing me off.  i want to be able to write the following in one line of code:

```
Key<int> k(&otherVariable);
Key<int>* j = &k;
//Key is my designed template
```

this works, but i'd like to avoid explicitly creating an object just to get a pointer to it.  looking for the c++ equivalent of java's:

```
Key<int>  k = new Key<int>(otherVariable);
//where the other variable is already a reference
//k will now point to a Key<int> object
```

thoughts?
ps, not a professional programmer, if i've missed something here, feel free to explain :)

---

### Post by slavik on 2008-06-02
a template is a template, you can't have a pointer to a template since it is not instantiated ...

what problems are you having with the second code snippet?

---

### Post by DavidBell on 2008-06-02
In second snippet

```

Key<int>  *k = new Key<int>(otherVariable);
//        ^ you forgot the star

// don't forget to delete later, no GC in C++

```

DB

---

### Post by uljanow on 2008-06-02
```
#include <cstdio>

template <typename T> class key {
public:
        key(T _n) { n = _n; }
        int n;
};

int main()
{
        key<int>* k = new key<int>(4455);
        printf("%d\n", k->n);

        return 0;
}
```
You need to provide a constructor which can cast the type of the other variable.

---

