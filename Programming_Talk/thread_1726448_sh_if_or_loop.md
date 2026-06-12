---
title: "sh if or loop"
date: 2011-04-11
forum: Programming Talk
---

### Post by jdb91 on 2011-04-11
This should be easy but I've forgotten how to do it and it's driving me crazy.

All I want to do is this:

```

#!/bin/sh

if [ $FOO != "A" || "B" || "C" ]; then
    exit 1
fi

```

But it's saying the syntax is wrong, so I tried

```

if [ $FOO != "A" ] || [ $FOO != "B" ]; then
    exit 1
fi

```

But that exits if FOO = A because when it hits the B check, they don't match.

I'm sure this is simple, but I can't remember how to do it.

Cheers.

---

### Post by Some Penguin on 2011-04-11
(x != A) && (x != B) <=> !((x == A) || (x == B))

What you're doing there, '(x != A) || (x != B)' will always be true if A != B because one of the two clauses must be true.

---

### Post by jdb91 on 2011-04-11
> **Some Penguin said:**
> (x != A) && (x != B) <=> !((x == A) || (x == B))

What you're doing there, '(x != A) || (x != B)' will always be true if A != B because one of the two clauses must be true.

Ah of course, stupid me, I've done that before!

Many thanks.

---

### Post by geirha on 2011-04-11
On a side note, use lowercase variable names, and quote parameter expansions; "$foo", not $foo.

I'd use case for that particular case

```

case "$foo" in
  A|B|C) echo "Great!";;
  *) echo "Not great"; exit 1;;
esac

```

---

### Post by bashologist on 2011-04-12
As Some Penguin said case probably is best for that situation, but to correct your if syntax you didn't quote the $FOO which might lead to the syntax error in practice. You don't need quotes if you used double [[.

So rather than this.
```

if [ $FOO != "A" ] || [ $FOO != "B" ]; then
    exit 1
fi

```

You maybe could've done this.
```

if [[ $FOO != "A" || $FOO != "B" ]]; then
    exit 1
fi

```

I may be wrong but I'm just pointing that out.

---

### Post by geirha on 2011-04-14
@bashologist That's good bash syntax, yes, but the OP is writing an sh script, not bash. Also, the logic is still wrong...

[http://en.wikipedia.org/wiki/De_Morgan%27s_laws](http://en.wikipedia.org/wiki/De_Morgan%27s_laws)

---

