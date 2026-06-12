---
title: "Python asin function"
date: 2007-05-10
forum: Programming Talk
---

### Post by forsaken_pariah on 2007-05-10
Hi all....

I've been trying to write a Python script to solve triangles given various types of information but I'm having a bit of trouble with math.asin()... The section that ails me at present looks like this:

```

. . .
        A = math.radians(A)
        sinB = (b*math.sin(A))/a
        B = math.asin(sinB)     #<---This is the part that screws me over.
        return B

```I can print B and it works just fine but the math.asin(sinB) part gives me a 'math domain error' and I have no idea why  and there is a surprisingly small amount of documentation on the internet for this function. This is the exact error I'm getting:

```

Traceback (most recent call last):
  File "./trisol.py", line 71, in <module>
    print parseArgs(sys.argv)
  File "./trisol.py", line 17, in parseArgs
    return ssa(argv)
  File "./trisol.py", line 60, in ssa
    B = math.asin(sinB)
ValueError: math domain error

```

Any help would be greatly appreciated.

---

### Post by Nikron on 2007-05-10
Well arcsin obviously needs the domain of -1 to 1 since it is .. arcsin..  So, what are the values of b and a?

---

### Post by forsaken_pariah on 2007-05-11
Never mind. It works now. I was drunk when I posted that last night. I didn't have any idea what I was doing.

---

### Post by WW on 2007-05-11
Heh, so you were **DWI** (*).

Next time, bring along a friend as a Designated Developer.





















* **D**eveloping **W**hile **I**ntoxicated

---

