---
title: "Hmm, context free grammar"
date: 2008-10-14
forum: Programming Talk
---

### Post by akejuis on 2008-10-14
I'm trying to do some type of context free grammar problems.  The one I'm having trouble with is the unary addition where
1 + 1 = 11, and 1 + 11 = 111 and so on.

basically, the number of 1s have to be added up to the right side.

So here's what I done so far and I hope somebody can help me get through with this.
Well, the problem also states that consider there's at least two ones on the left side, meaning that the base case for this problem would at least have the form 1 + 1 = 11

I tried
S -> 1A + 11B = 11AB
A -> 1A
A -> 1
A -> lambda
B -> 1B
B -> 1
B -> lambda

and I see my mistake, and I tried many ways to fix it, I tried variations of this and it still doesn't work.  What am I doing wrong?

Thanks

---

### Post by theirishfozz on 2008-10-14
Im confused. Are you trying to solve for S, A or B? I hope you're not using hex code... Could you explain the problem and process a little more please?

---

### Post by Reiger on 2008-10-14
Well it looks so simple to me, I must be making a mistake:
```

add x y = read z :: Integer
          where
          z x y= (show x) ++ (show y)

```

That's: convert the numbers to strings (of 1's), concatenate these strings, and return the result of interpreting this as an Integer.

---

### Post by hod139 on 2008-10-14
This sounds suspiciously like homework, so I'll only give a hint. Try writing it as a tree:
```

    S
  / | \
 S  +  S
 |     |
 a     b

```where a and b are the terminals.  Hopefully this helps.

---

