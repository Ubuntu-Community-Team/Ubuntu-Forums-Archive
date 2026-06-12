---
title: "concatenate output of two commands"
date: 2008-05-22
forum: Programming Talk
---

### Post by asubedi on 2008-05-22
How do I concatenate output of two commands? For example, if I do

$ echo "foo" && echo "bar" > tmp

Then foo will be printed in stdout and bar in tmp. I guess I could do

$ echo "foo" > tmp && echo "bar" >> tmp

But what if I want to print to lp? 

$ echo "foo" && echo "bar" | lp 

will print only bar.

---

### Post by geirha on 2008-05-22
```
{ echo "foo" && echo "bar"; } | lp
```

The semicolon at the end of the group must be there, and there must be whitespace after the { and before the }.

---

### Post by asubedi on 2008-05-22
> **geirha said:**
> ```
{ echo "foo" && echo "bar"; } | lp
```


Thanks!

---

### Post by ghostdog74 on 2008-05-23
> **asubedi said:**
> Thanks!

```

printf "foo\nbar" | lp

```

---

