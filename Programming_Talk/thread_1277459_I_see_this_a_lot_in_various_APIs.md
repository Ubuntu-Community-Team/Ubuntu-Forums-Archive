---
title: "I see this a lot in various APIs"
date: 2009-09-28
forum: Programming Talk
---

### Post by TheBuzzSaw on 2009-09-28
This is what I always use:
```
struct x
{
    int a;
    int b;
};
```

This is what I always see when browsing the insides of certain APIs:
```
typedef struct { int a; int b; } x;
```

Why do they do that? What benefits are there? How are they fundamentally different?

---

### Post by Simian Man on 2009-09-28
In ANSI C, you can not use structs by name without without the struct keyword:
```

struct x
{
    int a;
    int b;
};

x x1;         /* will NOT work */
struct x x1;  /* will work */

```

You can get around this using a typedef:
```

struct tagx
{
    int a;
    int b;
};

typedef struct tagx x;

x x1;  /* will now work */

```

This can be merged into the following:
```

typedef struct
{
    int a;
    int b;
} x;

x x1;  /* will now work */

```

Basically it's just a trick to make straight C compilers happy.

---

### Post by TheBuzzSaw on 2009-09-28
Ahhh... that makes sense. Thanx!

---

