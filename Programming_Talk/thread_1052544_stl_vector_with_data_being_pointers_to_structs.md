---
title: "stl vector with data being pointers to structs"
date: 2009-01-27
forum: Programming Talk
---

### Post by monkeyking on 2009-01-27
Hey,
Is it possible to have a vector with pointers to structs like

[PHP]
struct datPoint{
int x;
int y;
int z;
int date;
double **data
}
[/PHP]
and then something like

[PHP]
vector<*datPoints> vv;
[/PHP]
but this gives me an error that looks like.


```
runRelate.cpp: In function ‘std::vector<iArray, std::allocator<iArray> > getTestIndividuals(const char*)’:
runRelate.cpp:325: error: no matching function for call to ‘std::vector<iArray, std::allocator<iArray> >::push_back(iArray*&)’
/usr/include/c++/4.2/bits/stl_vector.h:597: note: candidates are: void std::vector<_Tp, _Alloc>::push_back(const _Tp&) [with _Tp = iArray, _Alloc = std::allocator<iArray>]

```
thanks in advance

---

### Post by snova on 2009-01-27
It compiles fine for me:

[php]#include <vector>

struct datPoint
{
    int x;
    int y;
    int z;
    int date;
    double **data;
};

int main()
{
    std::vector<datPoint*> vv;
}[/php]

Perhaps the * was simply on the wrong side?

Unless you were asking something else...

---

### Post by TheBlackNoodle on 2009-01-27
It's been a while since I've worked in C++, but from what I remember, you'd want to change it to something like...

```

typedef struct _datPoint{
int x;
int y;
int z;
int date;
double **data
} datPoint;

```

```

vector<datPoint*> vv;  

```

I added the typedef because, iirc, if you don't do that then you'd need to fully qualify "struct datPoint" every time you referenced it.

I changed the location of * in the vector declaration because that's my understanding of how a pointer is declared, although there are a lot of weird options available...

---

### Post by snova on 2009-01-27
> **TheBlackNoodle said:**
> I added the typedef because, iirc, if you don't do that then you'd need to fully qualify "struct datPoint" every time you referenced it.

Only in C.

---

### Post by monkeyking on 2009-01-28
Thanks the * was simply on the wrong side.

Thanks again.

---

