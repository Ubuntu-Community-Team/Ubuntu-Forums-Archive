---
title: "Is this expression tree correct??"
date: 2007-11-10
forum: Programming Talk
---

### Post by nite owl on 2007-11-10
Hi wasn't to sure where to post this question, but if anyone can just tell me whether I am right or wrong with this itd be great. Basically given and expression:

(A + B) * C - (B * D - E)

The expression tree I worked out is: 
```

                      -
                   /     \
                 x        -
               /  \      /  \
              C  +    E   x
                  / \        / \
                A   B      B  D

```
.......edit: sorry I just cant seem to get the branches etc... lined up right when I submit..

---

### Post by Compyx on 2007-11-11
You've got the operands of the expression B*D-E switched, B*D should be at the left branch of the '-' operator and E should be at the right branch. (That's the way the operands of the top '-' are organized, so you'd better keep that order consistent throughout the tree)

---

