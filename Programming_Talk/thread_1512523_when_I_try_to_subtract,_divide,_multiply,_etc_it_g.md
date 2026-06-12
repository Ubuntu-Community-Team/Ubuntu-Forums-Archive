---
title: "when I try to subtract, divide, multiply, etc it gives error"
date: 2010-06-18
forum: Programming Talk
---

### Post by makuab on 2010-06-18
```
lvlnn = 13,034,431

currentxp = input("current XP in skill? ")
xpph = input("XP per hour? ")
xpleft = lvlnn - currentxp
hoursleft = xpleft / xpph

print hoursleft
```


I get
```
TypeError: unsupported operation type(s) for -: 'tuple' and 'int'
```

---

### Post by lisati on 2010-06-18
Which language is this? And should the commas be there?

---

### Post by StephenF on 2010-06-18
> **makuab said:**
> ```
**lvlnn = 13,034,431**

currentxp = input("current XP in skill? ")
xpph = input("XP per hour? ")
xpleft = lvlnn - currentxp
hoursleft = xpleft / xpph

print hoursleft
```


I get
```
TypeError: unsupported operation type(s) for -: 'tuple' and 'int'
```
In bold there is your error. The commas denote a tuple which is a type of data container in this case with three elements, the integers 13, 34, and 431. In assignments the parentheses that surround tuples with one or more elements are unnecessary, so in summary those commas need to go.

@lisati, It's Python.

```

a = ()     # Empty tuple assigned to a.
a = (1, )  # Tuple with one element.
a = 1,     # Same as above but looks like a stray comma typo IMO.

```

---

### Post by simeon87 on 2010-06-18
To solve the problem, simply remove the commas. Python doesn't need help in understanding big numbers.

---

