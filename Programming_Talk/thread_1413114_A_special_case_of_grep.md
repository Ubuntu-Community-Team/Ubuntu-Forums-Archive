---
title: "A special case of grep"
date: 2010-02-22
forum: Programming Talk
---

### Post by borncrusader on 2010-02-22
Hi,

I need to grep a program's output and want to find the lines encompassing my request string. Supposing my string occurs on the line 100, I would need grep's output to print from say 95 to 105, considering my range to be 10. How can I use grep here? Is there any option I could use. The manual couldn't help me with what I want.

I could redirect the output to a file, then do the check to find the line number and then find the encompassing lines. But that's a lot of steps.. :)

Thanks & Regards,
Srinath

---

### Post by Bachstelze on 2010-02-22
You didn't read the manual well enough. ;) The [font=monospace]-C[/font] flag is what you want.

---

### Post by borncrusader on 2010-02-22
I think -c only counts the number of lines having the search string. But I need to get the n lines before and after the string occurrence.

If this is my program output,

> i like
ubuntu and
programming is fun
using gcc, gdb
and vim.

Suppose my grep string is "fun" and I need lines before and after the occurrence, i.e, my intended output if i invoke

```
./a.out | grep <some_switch_here> 1 "fun"
```

will be

> ubuntu and
programming is **fun**
using gcc, gdb

I hope I'm clear here.. :)

---

### Post by gmargo on 2010-02-22
> **borncrusader said:**
> I think -c only counts the number of lines having the search string. 

It's a capital 'C'.

```

# two lines of context before, two after:
grep -C 2     
grep -2
grep --context=2

# two lines of context before, three after:
grep -B 2 -A 3
grep --before-context=2 --after-context=3

```

---

### Post by borncrusader on 2010-02-22
Thanks.. :)

---

