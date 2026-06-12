---
title: "ktechlab compile issue"
date: 2009-04-22
forum: Packaging and Compiling Programs
---

### Post by tom66 on 2009-04-22
I get this, when I try to make. I have g++-4.3, I think it might require g++-4.2 or less, but how can I fix this? 

```

/usr/include/c++/4.3/bits/stl_vector.h:932: error: no matching function for call to 'std::vector<std::vector<unsigned int, std::allocator<unsigned int> >, std::allocator<std::vector<unsigned int, std::allocator<unsigned int> > > >::_M_fill_initialize(size_t, unsigned int&)'
/usr/include/c++/4.3/bits/stl_vector.h:974: note: candidates are: void std::vector<_Tp, _Alloc>::_M_fill_initialize(size_t, const _Tp&) [with _Tp = std::vector<unsigned int, std::allocator<unsigned int> >, _Alloc = std::allocator<std::vector<unsigned int, std::allocator<unsigned int> > >]
make[4]: *** [matrix.lo] Error 1
make[4]: Leaving directory `/home/thomas/ktechlab-0.3/src/electronics/simulation'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/thomas/ktechlab-0.3/src/electronics'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/thomas/ktechlab-0.3/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/thomas/ktechlab-0.3'
make: *** [all] Error 2

```

Any help appreciated.

---

### Post by BackwardsDown on 2009-05-24
I'm running into the same problem.

---

