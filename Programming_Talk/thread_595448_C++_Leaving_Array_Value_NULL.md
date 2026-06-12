---
title: "C++ Leaving Array Value NULL"
date: 2007-10-28
forum: Programming Talk
---

### Post by TreeFinger on 2007-10-28
Is there a way to leave a value in an array NULL? I'd like to initialize values to index[0], index[1], index[3]. How can I do this?

My guess would be like this
```

int numbers[6] = {1, 2, , 4, , 5};

```

I don't think that is correct though.
Thanks in advance for the time.

---

### Post by hod139 on 2007-10-28
I don't quite understand your question, how about
```

int numbers[6] = {1, 2, NULL, 4, NULL, 5};

```

---

### Post by dwhitney67 on 2007-10-28
There's various ways, however using your way, I would recommend that you explicitly set the values to 0, since when dealing with integers, there is no "null" in the traditional sense.

Thus following might suffice for your needs:

```
int numbers[6] = {1, 2, 0, 4, 0, 5};
```

---

