---
title: "C++ STL vector: handling an ambiguity"
date: 2007-07-29
forum: Programming Talk
---

### Post by schultz on 2007-07-29
I just had a C++ doubt and found nowhere else to post. It is about the STL vector.

It is know this code is correct:

[B]int buff[100];
vector<int> A(10, 18 ) ;
vector<int> B(buff, buff+100);[/B]

This should leave A with 10 copies of 18 and B with the contents of buff.

The problem is, analysing the code of the vector data structure, I find something like:

[B]vector(size_t, const _Tp&);
...
template<typename _InputIterator> vector(_InputIterator, _InputIterator);[/B]

This, of course, if you ignore allocator issues. My doubt is why this code is not ambiguous, since if I call vector(10, 18 ), it fits in both prototypes? This is, since if _InputIterator = int and _Tp = int we should have two prototypes fitting vector(int, int), there should be an ambiguity.

Can some C++ guru help me with this?

---

### Post by thumper on 2007-07-29
When evaluating which function to call, a non-template matching function is chosen over any templated function.

---

### Post by schultz on 2007-07-29
Thanks for the hint, it helps a lot. Thanks indeed.

---

