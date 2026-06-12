---
title: "C++11 and global const variable thread safety"
date: 2014-03-14
forum: Programming Talk
---

### Post by kangaba on 2014-03-14
Hi,
Is "static const Pair kAnimation = {..}" created thread safely upon first usage in c++11 in the following code?
```

namespace ods    { // ods::

enum class Id : quint8
{
    Animation = 1
};

struct Pair
{
    const ods::Id    id;
    const QString  uri;
};

static const Pair kAnimation = {
    Id::Animation,
    QStringLiteral("some string")
};
} // ods::

```

I know that in c++11 static vars inside a function are thread safe, but not sure about this one where the variable (kAnimation) is const and global.

---

