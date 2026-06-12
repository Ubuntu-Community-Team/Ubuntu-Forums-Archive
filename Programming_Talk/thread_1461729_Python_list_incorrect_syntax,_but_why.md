---
title: "Python list incorrect syntax, but why?"
date: 2010-04-24
forum: Programming Talk
---

### Post by myromance123 on 2010-04-24
Hello there, ok straight to the point.
 I'm using Python IDLE 3.1 in Ubuntu 10.04 Beta 2.

This is the part of the code that python complains about:
```
# add a score
elif choice == "2":
    score = int(input("What score did you get?: ")
    scores.append(score)
```

It says "scores.append(score)" is incorrect syntax. Why is this so?
I'm learning from a book titled 'Python Programming Third Edition for absolute beginners'. I initiated the scores list as follows:
```
scores[]
```

Thanks if anyone can assist me with this !

EDIT: I apologize, after going through it several times I realized it was missing an extra end brace for the input section.

---

