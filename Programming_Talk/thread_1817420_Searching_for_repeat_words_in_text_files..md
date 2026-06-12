---
title: "Searching for repeat words in text files."
date: 2011-08-03
forum: Programming Talk
---

### Post by moadeep on 2011-08-03
Hi All,

For a while I have been considering writing a simple programme to search for repeat words such as and and in documents I produce in latex. I always seem to miss one when proof reading my work. Unfortunately, I have no idea where to start and which language would be best.

Any ideas or do similar algorithms already exist?

Moa

---

### Post by cgroza on 2011-08-03
So you basically want to find cases similar to this:

```

There was a rabbit and and a fox fox ...

```?

Perl is pretty good for this kind of task.

---

### Post by moadeep on 2011-08-03
> **cgroza said:**
> So you basically want to find cases similar to this:

```

There was a rabbit and and a fox fox ...

```?

Perl is pretty good for this kind of task.

Exactly. I have been considering learning Perl, maybe this problem will encourage me.

---

### Post by cgroza on 2011-08-03
> **moadeep said:**
> Exactly. I have been considering learning Perl, maybe this problem will encourage me.
If you want to just look for the lines where these words occur, you can use grep -E:
It uses a regexp to find those words.

I put together this Perl regular expression that apparently works:
```

m/(\w+)\s+\1+\b/ig

```Note, I am not sure it works with grep, I tested it using Perl.

---

### Post by moadeep on 2011-08-03
> **cgroza said:**
> If you want to just look for the lines where these words occur, you can use grep -E:
It uses a regexp to find those words.

I put together this Perl regular expression that apparently works:
```

m/(\w+)\s+\1+\b/ig

```Note, I am not sure it works with grep, I tested it using Perl.


Thanks for your help. Unfortunately I have zero knowledge of Perl (at the moment) and have no idea how to execute the command. I love the simplicity in the expression and will definitely be investigating the language when I have some free time next week.

Moa

---

### Post by cgroza on 2011-08-03
> **moadeep said:**
> Thanks for your help. Unfortunately I have zero knowledge of Perl (at the moment) and have no idea how to execute the command. I love the simplicity in the expression and will definitely be investigating the language when I have some free time next week.

Moa
It should easily be converted to shell regular expression syntax.
EDIT: Here is the grep command:
```
grep -E "(\w+)\s+\1+\b" yourfile.txt
```

---

