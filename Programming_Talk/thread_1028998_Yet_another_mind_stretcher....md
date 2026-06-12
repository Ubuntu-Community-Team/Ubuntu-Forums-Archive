---
title: "Yet another mind stretcher..."
date: 2009-01-02
forum: Programming Talk
---

### Post by dwhitney67 on 2009-01-02
Find the values a, b, and c that satisfy the following formula:

      abca = a^b * c^a

Hint: a, b, and c represent values that are less than 10.

---

### Post by chrisamiller on 2009-01-03
Pretty trivial to code up a solution.  

Actually, there are several solutions:  (and even more if you allow any of the variables to be equal to one another)

2,3,6,8
2,4,3,6
3,1,2,4
4,1,2,8
6,2,1,3
8,2,1,4

---

### Post by pp. on 2009-01-03
> **chrisamiller said:**
> Actually, there are several solutions:  (and even more if you allow any of the variables to be equal to one another)

2,3,6,8
2,4,3,6
3,1,2,4
4,1,2,8
6,2,1,3
8,2,1,4

What are these the solutions of? The OP states a problem in three variables, your list appears to show solutions consisting of four discrete values.

---

### Post by Reiger on 2009-01-03
@chrisamiller... your solutions don't work out. There's a catch:
a*b*c***a** ;)

Anywho using the hint we obtain this in Haskell (or any other equivalent code):
```

main = putStrLn $ show $ [ (a,b,c) | a<-[1..10] , b<-[1..10], c<-[1..10], (a^b) * (c^a) == (a*b*c*a) ]

```

---

### Post by Reiger on 2009-01-03
> **dwhitney67 said:**
> Hint: a, b, and c represent values that are less than 10.

Unless both a and b are 1 in which case any (1,1,c<-R) is a solution. (c = c)

---

### Post by .Maleficus. on 2009-01-03
dwhitney67 - Including zeros?  You just say less than 10...  Anyways, very clever problem.  Another good Python one-liner.  Here's the code:
[php]    print [(a,b,c) for a in xrange(10) for b in xrange(10) for c in xrange(10) if (a**b * c**a) == a*b*c*a][/php]
Not as elegant as Reiger's Haskell version, but works just the same (though I am including zero).

---

### Post by dwhitney67 on 2009-01-03
More hints:

'a', 'b', and 'c' are base-10 numbers.
'abca' represents a 4-digit, base-10, number.

A little reminder... the '^' symbol denotes that a value is to be raised by some power.  For example, 4^3 = 4*4*4 = 64

Also remember, the problem asks for three values:  a, b, and c.  If you wish to provide the value(s) 'abca', then that is ok too.

---

### Post by dwhitney67 on 2009-01-03
> **.Maleficus. said:**
> dwhitney67 - Including zeros?  You just say less than 10...  Anyways, very clever problem.  Another good Python one-liner.  Here's the code:
[php]    print [(a,b,c) for a in xrange(10) for b in xrange(10) for c in xrange(10) if (a**b * c**a) == a*b*c*a][/php]
Not as elegant as Reiger's Haskell version, but works just the same (though I am including zero).
See my last post which provides more hints/clarifications.  'abca' is a discrete value, not to be confused with a*b*c*a.

---

### Post by dwhitney67 on 2009-01-03
> **.Maleficus. said:**
> dwhitney67 - Including zeros?  You just say less than 10...  Anyways, very clever problem.  Another good Python one-liner.  Here's the code:
[php]    print [(a,b,c) for a in xrange(10) for b in xrange(10) for c in xrange(10) if (a**b * c**a) == a*b*c*a][/php]
Not as elegant as Reiger's Haskell version, but works just the same (though I am including zero).
See my last post which provides more hints/clarifications.  'abca' is a 4-digit number, which is not a*b*c*a.

---

### Post by Reiger on 2009-01-03
Oh well,

```

main = putStrLn $ show $ [ (a,b,c) | a<-[0..9], b<-[0..9], c<-[0..9], (show $ (a^b) * (c^a)) == (concat $ map show [a,b,c,a]) ]

```

Produces:
[(2,5,9)]

A slightly less verbose (removed redundant parentheses) version with improved semantics (using the function-composition rather than function-application operator where possible):
```

main = putStrLn . show $ [ (a,b,c) | a<-[0..9], b<-[0..9], c<-[0..9], (show $ a^b * c^a) == (concat $ map show [a,b,c,a]) ]

```

---

### Post by dwhitney67 on 2009-01-03
> **Reiger said:**
> Oh well,

```

main = putStrLn $ show $ [ (a,b,c) | a<-[0..9], b<-[0..9], c<-[0..9], (show $ (a^b) * (c^a)) == (concat $ map show [a,b,c,a]) ]

```

Produces:
[(2,5,9)]

A slightly less verbose (removed redundant parentheses) version with improved semantics (using the function-composition rather than function-application operator where possible):
```

putStrLn . show $ [ (a,b,c) | a<-[0..9], b<-[0..9], c<-[0..9], (show $ a^b * c^a) == (concat $ map show [a,b,c,a]) ]

```

Bingo!  You got the correct answer.

Now, see if you can optimize your code to trim down the number of iterations spent in the "for-loops".  Think of the possible values for 'a', 'b', and 'c', and try to discount/eliminate from the range of values those which could never satisfy the requirements of the problem.

---

