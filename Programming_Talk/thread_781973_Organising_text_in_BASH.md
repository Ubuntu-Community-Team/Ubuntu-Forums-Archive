---
title: "Organising text in BASH"
date: 2008-05-04
forum: Programming Talk
---

### Post by ibuclaw on 2008-05-04
Hi all,

I was wondering how to organise text that is echo'd into the terminal into a proper format.

ie:
I have a BASH line like this:
[PHP]echo -e "$1\t$2\t$3\t$4"[/PHP]

Which gives me this output:
```

five.foo        /path/to/five.foo     2008-05-04      20:43:16
four.foo        /path/to/four.foo     2008-05-04      20:43:16
one.foo /path/to/one.foo      2008-05-04      20:43:16
three.foo       /path/to/three.foo    2008-05-04      20:43:16
two.foo /path/to/two.foo      2008-05-04      20:43:16

```

But I can't seem to get it looking **like this**:
```

five.foo        /path/to/five.foo     2008-05-04      20:43:16
four.foo        /path/to/four.foo     2008-05-04      20:43:16
one.foo         /path/to/one.foo      2008-05-04      20:43:16
three.foo       /path/to/three.foo    2008-05-04      20:43:16
two.foo         /path/to/two.foo      2008-05-04      20:43:16

```

Any help would be appreciated.

Regards
Iain

---

### Post by stroyan on 2008-05-04
You could use the printf builtin instead of the echo builtin. ```

printf "%-17s %-22s %-15s %-17s\n" "$1" "$2" "$3" "$4"

```
That will expand to spaces between fields instead of tabs between fields.
It also allows you to set different fields to different widths.

As an alternative you could use ```

echo -e "$1\t$2\t$3\t$4" | expand -19

```
But that would have uniform field widths, wasting columns.

---

### Post by ibuclaw on 2008-05-04
> **stroyan said:**
> You could use the printf builtin instead of the echo builtin. ```

printf "%-17s %-22s %-15s %-17s\n" "$1" "$2" "$3" "$4"

```
That will expand to spaces between fields instead of tabs between fields.
It also allows you to set different fields to different widths.

As an alternative you could use ```

echo -e "$1\t$2\t$3\t$4" | expand -19

```
But that would have uniform field widths, wasting columns.

Thanks, printf works like a charm.

**expand** on the otherhand is a little harder to control (still get wonky field separators).

But thanks again for you help.

Regards
Iain

---

