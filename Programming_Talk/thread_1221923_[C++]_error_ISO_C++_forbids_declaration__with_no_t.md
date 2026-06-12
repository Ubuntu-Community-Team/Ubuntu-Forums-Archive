---
title: "[C++] error: ISO C++ forbids declaration  with no type"
date: 2009-07-24
forum: Programming Talk
---

### Post by wbest on 2009-07-24
I keep getting errors similar to:

error: ISO C++ forbids declaration of ‘XDBColumnImpl’ with no type

About the line:
```
  X_PRIVATE_PTR_MUTABLE(XDBColumnImpl, impl); 
```
See below for the full code.

But I feel like its declared here:

```
  friend class XDBColumnImpl;
```

From the code:
```

class DBCORE_API XDBColumn 
#ifdef USE_COMPAT 
    : public XCompatColumn 
#endif 
{ 
  friend class XDBColumnImpl; 
 
  X_PRIVATE_PTR_MUTABLE(XDBColumnImpl, impl); 
  DB_GET_IMPL(XDBColumnImpl, impl);
//Other "unimportant" lines
```


Note, though, that in X_PRIVATE_PTR_MUTABLE(foo, bar)
foo is being used as the type for bar.

So any ideas on what I'm doing wrong, or should change to fix this?
Isn't XDBColumnImpl a class?
I can post more code if you like, I just didn't want this post to get too long.

---

