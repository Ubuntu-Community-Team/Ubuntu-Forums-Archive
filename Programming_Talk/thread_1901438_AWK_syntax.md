---
title: "AWK syntax"
date: 2011-12-28
forum: Programming Talk
---

### Post by hailholyghost on 2011-12-28
Hello:guitar:,

just a very quick AWK question.  I can't find out how to do this online.  I've searched through many, many "AWK one-liner" pages!

I have a code that does

```
awk '{print $4/10}' getpdb | head -1
```

Now this works just fine, but I would like to know how to do this in one awk command.

something like ```
awk '{print $4/10}/&&/$NR==1/' getpdb
```

but this doesn't work.

I realize this might seem trivial, but I would like to know how to do it.  I don't like to use the pipes "|" unless I have to.

Thanks for your time!
Dave

---

### Post by Lars Noodén on 2011-12-28
I got help on this.  Would this do it?

```

awk '{print $4/10; exit}' getpdb

```

---

### Post by hailholyghost on 2011-12-28
Hi Lars Noodén,

thanks so much for your prompt reply; it worked!

I'm curious how it worked though.  What if it were necessary to print the 7th line of a 100 line file?

-Dave

---

### Post by Lars Noodén on 2011-12-28
Then it would have to do it differently.  This just takes one line and exits.

---

### Post by Lars Noodén on 2011-12-28
> **hailholyghost said:**
> 
I'm curious how it worked though.  What if it were necessary to print the 7th line of a 100 line file?

Something like this, I think:

```

awk 'NR==7 {print $4/10}' getpdb

```

---

### Post by Arndt on 2011-12-28
> **hailholyghost said:**
> Hello,

just a very quick AWK question.  I can't find out how to do this online.  I've searched through many, many "AWK one-liner" pages!


Rather than hunt for one-liners, if you want to use awk for everything, then the only way is to learn the whole language.

---

