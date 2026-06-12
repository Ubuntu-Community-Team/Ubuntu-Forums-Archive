---
title: "sed non-sequential line numbers"
date: 2013-01-06
forum: Programming Talk
---

### Post by maclenin on 2013-01-06
I am not quite sure how to **sed** this:

**Substitue "A" for "B" in lines 5 and 11 and 34 and 92 and 108 within test_file.**

I am able to substitue "A" for "B" in a range of lines within test_file:
```
sed -r '5,108 s/B/A/' -i test_file
```

I am also able to subsitute "A" for "B" in a single line within test_file:
```
sed -r '34 s/B/A/' -i test_file
```

Thanks for any guidance!

---

### Post by ibuclaw on 2013-01-06
> **maclenin said:**
> I am not quite sure how to **sed** this:

**Substitue "A" for "B" in lines 5 and 11 and 34 and 92 and 108 within test_file.**

I am able to substitue "A" for "B" in a range of lines within test_file:
```
sed -r '5,108 s/B/A/' -i test_file
```

I am also able to subsitute "A" for "B" in a single line within test_file:
```
sed -r '34 s/B/A/' -i test_file
```

Thanks for any guidance!

Don't think it can be done without using -e for each regexp.

```
-e '5 s/B/A' -e '11 s/B/A' -etc...
```

---

### Post by Vaphell on 2013-01-06
if you want to keep it short and not duplicate the expression you could do something like this:
```
$ s='s/A/A*/'
$ for i in {1..10}; do echo A; done | sed "5$s; 7$s; 9$s"
A
A
A
A
A*
A
A*
A
A*
A
```

---

