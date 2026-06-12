---
title: "Is this a memory leak? C"
date: 2006-09-18
forum: Programming Talk
---

### Post by zootreeves on 2006-09-18
Hi,

I've never really consider memory usage before that much, but i'm writing a program now where it is important and i'm wondering is this a memory leak?

```

gchar * my_string;
my_string = g_strdup_printf("Pointer assigned once");
my_string = g_strdup_printf("Pointer assigned again");
g_free(my_string);

```

Thanks

---

### Post by angustia on 2006-09-19
yap, between second and third lines.

---

