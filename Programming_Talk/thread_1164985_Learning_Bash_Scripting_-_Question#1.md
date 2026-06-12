---
title: "Learning Bash Scripting - Question#1"
date: 2009-05-20
forum: Programming Talk
---

### Post by kpkeerthi on 2009-05-20
I'm working my way reading the book "Learning the Bash shell". I'm stuck with this:

What is the difference between this
```

if [ condition1 ] && [ condition2 ]; then
    ...statements...
fi

```
and this
```

if [ \( condition1 \) -a \( condition2 \) ]; then
    ...statements...
fi

```

---

### Post by geirha on 2009-05-20
It's just two ways of doing the same ...

---

### Post by kpkeerthi on 2009-05-20
Thanks. I thought so and discovered with a quite bit of experiment. The book sounded quite elusive to me on the topic.

---

