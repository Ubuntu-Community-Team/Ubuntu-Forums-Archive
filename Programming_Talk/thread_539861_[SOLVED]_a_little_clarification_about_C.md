---
title: "[SOLVED] a little clarification about C"
date: 2007-08-31
forum: Programming Talk
---

### Post by eph1973 on 2007-08-31
A quick fairly basic question:

I thought when you used the library function free() with a structure, you had to free each member of the structure before freeing the structure itself.  Is this incorrect?

(this example is simplified to a great degree just to get my point across)

void freefunct(struct tnode *p){
free(p->foo);
free(p->bar);
free(p->left);
free(p->right);
free(p);
}
or is it ok just to free(p), and free() will free all the entirety of *p?

Thanks for your answers in advance.

---

### Post by slavik on 2007-08-31
```

struct _node {
  int number;
  int *more_numbers;
}

```

in example above, you must first free more_numbers, then the structure itself.

---

### Post by eph1973 on 2007-08-31
OK, thanks, that's what I thought, but I saw some code recently that didn't do that, and I just wanted to make sure I was doing things correctly.

---

### Post by bogolisk on 2007-08-31
> **eph1973 said:**
> OK, thanks, that's what I thought, but I saw some code recently that didn't do that, and I just wanted to make sure I was doing things correctly.

It's very simple: thou shall free what was malloced!:)

---

