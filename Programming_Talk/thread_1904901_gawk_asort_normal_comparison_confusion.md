---
title: "gawk asort normal comparison confusion"
date: 2012-01-05
forum: Programming Talk
---

### Post by gnometorule on 2012-01-05
I'm new to gawk. I read the asort function sorts by data element values; when no sort function is specified, in the default order (which I took as numerical sort or lexicographic sort respectively). I do not understand why the below is always the output...

Output:

```

index: 4 - value: 4
index: 1 - value: 1
index: 2 - value: 2
index: 3 - value: 3

```, independent on which single letter I choose for XXX, as long as the letter is distinct from the other array indices a, g, and m.

Command line entered:

```

$ gawk 'BEGIN{
>var["a"] = 1
>var["g"] = 2
>var["m"] = 3
>var["XXX"] = 4
>asort(var, test)
>for (i in test)
>print "index: " i, " - value:", test[i]
}'


```I didn't find a reference to the default comparison criterion on gawk's man page, but might have overlooked it. Googling for it produces examples in which lexicographic ordering works as expected, so I'm a bit at a loss.


Note:
- The problem is similar using asorti
- I'm working under Ubuntu 10.04.

---

### Post by Arndt on 2012-01-05
> **gnometorule said:**
> I'm new to gawk. I read the asort function sorts by data element values; when no sort function is specified, in the default order (which I took as numerical sort or lexicographic sort respectively). I do not understand why the below is always the output...

Output:

```

index: 4 - value: 4
index: 1 - value: 1
index: 2 - value: 2
index: 3 - value: 3

```, independent on which single letter I choose for XXX, as long as the letter is distinct from the other array indices a, g, and m.

Command line entered:

```

$ gawk 'BEGIN{
>var["a"] = 1
>var["g"] = 2
>var["m"] = 3
>var["XXX"] = 4
>asort(var, test)
>for (i in test)
>print "index: " i, " - value:", test[i]
}'


```I didn't find a reference to the default comparison criterion on gawk's man page, but might have overlooked it. Googling for it produces examples in which lexicographic ordering works as expected, so I'm a bit at a loss.


Note:
- The problem is similar using asorti
- I'm working under Ubuntu 10.04.

I don't use gawk much, but according to the documentation, the indices of the array are not used, only the set of values.

The next problem is that 'for (i in test)' also seemingly ignores the indices: it returns the values in random order.

This produces sorted output, at least:

```
gawk 'BEGIN{
var[1] = "1"
var[2] = "4"
var[3] = "3"
var[4] = "2"
asort(var, test)
for (i=1; i<=length(test); i++)
print "index: " i, " - value:", test[i]
}'

```

---

### Post by gnometorule on 2012-01-05
Thanks, Arndt. You're right, the issue was not failure to sort properly, but to use the right loop command. When I use the C-style loop on the original post, it prints out fine. So the other 'problem' was simply because gawk seems to be at liberty to print any hash array in any order it sees fit.

---

