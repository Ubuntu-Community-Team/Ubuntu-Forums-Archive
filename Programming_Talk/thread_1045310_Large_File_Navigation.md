---
title: "Large File Navigation"
date: 2009-01-20
forum: Programming Talk
---

### Post by twade on 2009-01-20
I use kate for editing code, which is typically tens of thousands of lines long in one file (someone else's design, not mine).  Just wondering what tools exist to help you navigate and let you know where your are in the code.  I know about code folding, but I'm thinking something along these lines:

I you have a file that looks something like this (but image it a thousand times longer):
```

for i10 = 1:10
   if bob = joe
      blah blah blah
   endif
   abc = 3.14
   for i20 = 3:30
      if jim = john
         currently editing here
      endif
   endif
end

```
It would be nice to know where you are via a panel that highlights the structure and hides the details, something like:
```

for i10 = 1:10
   for i20 = 3:30
      if jim = john

```
(i.e. one line for each level of depth)
Any ideas?

---

### Post by Sprut1 on 2009-01-20
You mean to strip down to show only certain blocks?

---

