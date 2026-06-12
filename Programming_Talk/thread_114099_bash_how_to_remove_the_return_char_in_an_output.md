---
title: "bash: how to remove the return char in an output"
date: 2006-01-07
forum: Programming Talk
---

### Post by Cyrus on 2006-01-07
Hi,

when I am using a shell program it returns its output always with a carriage return. I want to remove this, because I am piping everything into a textfile, where no return should be. A simple example:

```
echo hallo >> test
echo hallo >> test
```

The file test looks now like this:

> hallo
hallo

I need:

> hallohallo

Maybe cut helps?

```
echo hallo | cut ... >> test
```

---

### Post by cylon359 on 2006-01-07
echo -n hallo >> test

---

### Post by Cyrus on 2006-01-10
Works just great, thanks alot!

---

