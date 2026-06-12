---
title: "Basic Python Programming Question"
date: 2010-01-30
forum: Programming Talk
---

### Post by Cunnilingus on 2010-01-30
Why does the program
```
length = 5
width = 2
 
area = length * width
print('Area is', area)
print('Perimeter is', 2 * (length + width))
```

give an output of
```
('Area is', 10)
('Perimeter is', 14)
```

---

### Post by Zugzwang on 2010-01-30
Because you are printing tuples. The print command can be used without parentheses.

---

### Post by CptPicard on 2010-01-30
That is, print is a statement, not a function. This will change in Python 3 though.

---

### Post by Cunnilingus on 2010-01-30
Got it. Thanks!

---

### Post by nvteighen on 2010-01-30
You can use it with parentheses, but instead of commas, you have to use + and be sure everything is a string... or convert it to string using str()

```

print("A" + str(4) + "b")

```

Anyway, it's nicer to use printf-like control strings or the new format() method (only since Python 2.6):
```

print "A%d %s" % (4, "b")
# or Python 2.6+
print "A{0} {1}".format(4, "b")

```

---

