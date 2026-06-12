---
title: "std::vector question"
date: 2011-04-17
forum: Programming Talk
---

### Post by t1497f35 on 2011-04-17
Hi,
Normally I do this:
std::vector<int> v1;
v1[0] = ...;

But how do I use the [] (square brackets) with a pointer to a vector?
std::vector<int> *pv1;
//?

Is it impossible to use brackets in this case?

---

### Post by NovaAesa on 2011-04-17
```

#include <vector>
int main()
{
    std::vector<int>* v = new std::vector<int>(10);
    
    //two ways to do it:
    v->operator[](0) = 42;
    (*v)[0] = 43;
}

```

---

### Post by t1497f35 on 2011-04-17
Thanks a lot!

---

### Post by schauerlich on 2011-04-17
std::vector allocates its own memory on the heap, so it's usually easier to just put the vector variable on the stack. If you need to pass it into a function, use a reference instead of a pointer.

---

### Post by NovaAesa on 2011-04-17
> **schauerlich said:**
> std::vector allocates its own memory on the heap, so it's usually easier to just put the vector variable on the stack. If you need to pass it into a function, use a reference instead of a pointer.

You're absolutely right. In C++, don't just use pointers for the sake of using pointers. Only use them when absolutely necessary!

---

### Post by cgroza on 2011-04-17
You can use:```


vector -> at(0);
```But that provides range checking too and brings a bit of overhead.

---

### Post by BkkBonanza on 2011-04-17
If you want to keep syntax simpler then you may also create a reference,

std::vector<int> *pv1;
std::vector<int>& v1 = *pv1;

v1[0] = ...etc.

---

