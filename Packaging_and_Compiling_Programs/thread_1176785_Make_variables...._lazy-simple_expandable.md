---
title: "Make variables.... lazy-simple expandable?"
date: 2009-06-02
forum: Packaging and Compiling Programs
---

### Post by dmitrijledkov on 2009-06-02
```
TEMP_DIR=$(shell mktemp -d)

```

I have get-orig-source target and I'm using a tmp dir to do all the repackaging. But I'm struggling with correct variable assignment.

If I do "=" assignment each time I try to do something in the $TEMP_DIR it creates a new one and ovverrides the value of the previous one.

If I do ":=" assignment a temp dir gets created on every invocation of any target (e.g. 10X ./debian/rules clean would result in 10 tmp dirs created)

If there a way to create a make variable which would be lazy evaluated only once?

---

