---
title: "Convert char* to char in C"
date: 2010-10-22
forum: Programming Talk
---

### Post by toanhoi on 2010-10-22
Hi Everybody,I have a question ,can you help me,please.I write a function to convert char* to char .Can you help me.Thanks you.This function converts char* to char and construct of convert(char xau[100],char* old)

---

### Post by Simian Man on 2010-10-22
Your question makes no sense to me.  char* is a pointer to a character and is often used for NULL terminated strings.  If all you want is the character pointed to, just dereference it:
```

char* x;
char a = *x;

```

If x points to a string, this will be the first character of that string.

---

### Post by TheBuzzSaw on 2010-10-22
Simian Man pretty much hit it right on the head. We need more details surrounding the context of your problem.

```

char a = yourCharPointer[0];

```

Something like that? It's basically the same thing as above.

---

