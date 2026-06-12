---
title: "using sed del first few char"
date: 2009-11-21
forum: Programming Talk
---

### Post by aliahsan81 on 2009-11-21
Hi ALL

Hope you all are fine.

I am facing little problem in sed.

I have this string

```

xxxx-h.new.like.com.

xxxxxxx-h.new.like.com.


```

Now i want to del characters up to -h.

Like 

-h.new.like.com.

So how it be possible.

---

### Post by Arndt on 2009-11-21
> **aliahsan81 said:**
> Hi ALL

Hope you all are fine.

I am facing little problem in sed.

I have this string

```

xxxx-h.new.like.com.

xxxxxxx-h.new.like.com.


```

Now i want to del characters up to -h.

Like 

-h.new.like.com.

So how it be possible.

Did you look at the manual page for 'sed'? It can be intimidating, but what you want to do is among the simplest 'sed' tasks. Use the s command.

---

### Post by aliahsan81 on 2009-11-21
yes i have tried with this.But didnt work out.

sed 's/^.\{4\}//g

---

### Post by sisco311 on 2009-11-21
```
sed 's/.*\(-h.*$\)/\1/'
```

---

### Post by diesch on 2009-11-21
If you want to delete any number of leading *x*:

```
sed 's/^x*//'
```

---

### Post by Arndt on 2009-11-21
> **aliahsan81 said:**
> yes i have tried with this.But didnt work out.

sed 's/^.\{4\}//g

It works for your first example, but that's of course because there are exactly four x before the -h.

---

### Post by aliahsan81 on 2009-11-21
Yes thanks.All. My script is completed now.
Special thanks to sisco311

---

### Post by sisco311 on 2009-11-21
> **aliahsan81 said:**
> Yes thanks.All. My script is completed now.
Special thanks to sisco311

Cool!!!

Please mark your thread as [SOLVED] by selecting **Mark this thread as solved** from the [color="Red"]Thread tools[/color].

EDIT: Thanks!

---

### Post by ghostdog74 on 2009-11-21
no need to use external tools. if "-h" is always before the first "dot"

```

$ a=xxxx-h.new.like.com
$ IFS="." ;set -- $a
$ echo $1
xxxx-h
$ unset IFS

```

---

### Post by diesch on 2009-11-22
With shell variables I'd use
```
echo "-h${a##*-h}"
```

---

