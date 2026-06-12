---
title: "Python: How to input multiple variables in a single line?"
date: 2010-10-22
forum: Programming Talk
---

### Post by unmole on 2010-10-22
Could anyone please point me to the Python equivalent of C's
```
scanf("%d%d%d", &a, &b, &c);
```

Much obliged.

---

### Post by unmole on 2010-10-22
Not really an equivalent but I'm using this hack for now
```
line=raw_input()
x = line.split(' ')
a=x[0]
b=x[1]
c=x[2]
```

---

### Post by Miyavix3 on 2010-10-22
Scanf just lets someone input on 3 different lines, correct? 
```

a, b, c = raw_input(), raw_input(), raw_input()

```

Change the raw_input() to input() or int(raw_input()) if you need.

You can assign many things on the same line. Though, it can be sloppy.

---

### Post by StephenF on 2010-10-22
[http://docs.python.org/library/re.html#simulating-scanf](http://docs.python.org/library/re.html#simulating-scanf)

---

