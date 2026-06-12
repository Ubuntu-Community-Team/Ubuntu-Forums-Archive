---
title: "Please help analyze..."
date: 2010-08-26
forum: Programming Talk
---

### Post by Shippou on 2010-08-26
Hello guys.

Can anyone please explain to me or point to me where my analysis went wrong with this code?

```

     a[i++] = a[++i] = a[i++] = (i++ + ++i);

```

Yes, this is BAD programming practice. This is actually a question I want to ask in our "mini-quiz bee".

In my analysis, this should be assigning 2 to a[2] and a[4]. But upon running, it assigns 4 to a[2].

Any thoughts?

---

### Post by Bachstelze on 2010-08-26
The result is undefined. Different compilers may give different results. Don't ask a question about this.

---

### Post by Shippou on 2010-08-26
> **Bachstelze said:**
> The result is undefined. Different compilers may give different results. Don't ask a question about this.

Thanks for the reply.

I tried researching also about this, and yes it is undefined. I am currently reading this article: [http://www.eskimo.com/~scs/cclass/notes/sx7c.html](http://www.eskimo.com/~scs/cclass/notes/sx7c.html)

Now I know what the right answer is. Thank you very much.

---

