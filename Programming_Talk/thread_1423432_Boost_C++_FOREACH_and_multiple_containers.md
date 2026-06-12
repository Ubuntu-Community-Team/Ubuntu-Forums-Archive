---
title: "Boost C++ FOREACH and multiple containers"
date: 2010-03-06
forum: Programming Talk
---

### Post by WebDrake on 2010-03-06
Hello,

I've recently discovered the Boost FOREACH macro:
[http://www.boost.org/doc/libs/1_42_0/doc/html/foreach.html](http://www.boost.org/doc/libs/1_42_0/doc/html/foreach.html)

Is there something comparable out there which permits simultaneous iteration across multiple containers?  I'm thinking e.g. of the usecase when by default you have to do,

```

for(unsigned int i=0;i<vec1.size();++i) {
    vec1.at(i) = vec2.at(i);
}
```

Yes, I know that's a stupid example, because in reality there are more efficient vector-copying methods.  Actually, the real situation I would like to 'solve' is more like,

```

for(unsigned int i=0;i<vec1.size();++i) {
    vec1.at(i)->some_func(vec2.at(i));
}
```
... where vec1 is a vector of pointers to different instances of a class, and vec2 is a vector of input values for some_func.

Anyway, the point is, is there some equivalent or extension to BOOST_FOREACH to let me do something like (pseudo-code),
```

FOREACH(my_class *v1, vec1; double v2, vec2) {
    v1->some_func(v2);
}
```

.... ?

---

