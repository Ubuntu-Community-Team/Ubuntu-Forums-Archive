---
title: "Question about  C"
date: 2011-06-18
forum: Programming Talk
---

### Post by stamatiou on 2011-06-18
Hey guys,
in a piece of code, I have seen the main function divided by two, something like that:

```

main()
{
blablablabla;
}
/* a comment */
{
blablabla;
}
```

---

### Post by BkkBonanza on 2011-06-18
Were you intending to ask a question? 
Or just let us know you saw something strange...

---

### Post by simeon87 on 2011-06-18
It seems unlikely that that's what you've seen. Did it compile correctly?

---

### Post by dwhitney67 on 2011-06-18
> **simeon87 said:**
> It seems unlikely that that's what you've seen. Did it compile correctly?

I concur.

What the OP probably saw was something like:
```

int main()
{
   *some declarations*;

   *some statements*;

   {
      *some declarations*;

      *some statements*;
   }

   *more statements*;
}

```

---

