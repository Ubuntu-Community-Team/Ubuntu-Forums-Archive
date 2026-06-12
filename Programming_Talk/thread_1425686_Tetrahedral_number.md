---
title: "Tetrahedral number"
date: 2010-03-09
forum: Programming Talk
---

### Post by blackevil on 2010-03-09
[SIZE=2]
[/SIZE][SIZE=2]I have been given a task of writing a program in Python for Tetrahedral number in recursive function form  ie :


code:

def tet(n):
               if n<=*: 
              return *
                else: 
              return * + tet(**)
 


numbers are:

1                   1
2                   4
3                  10
4                  20
5       35

[/SIZE][SIZE=2]


What is the nth term?



[/SIZE]

---

### Post by kernco on 2010-03-09
Hmm...

1 1 = 1^2
2 4 = 2^2
3 10 = 3^2 + 1
4 20 = 4^2 + 4
5 35 = 5^2 + 10

Looks like f(n) = n^2 + f(n-2)?

---

### Post by blackevil on 2010-03-09
> **kernco said:**
> Hmm...

1 1 = 1^2
2 4 = 2^2
3 10 = 3^2 + 1
4 20 = 4^2 + 4
5 35 = 5^2 + 10

Looks like f(n) = n^2 + f(n-2)?




it works for 1,2,3

but didnt work for the rest?

---

### Post by kernco on 2010-03-09
> **blackevil said:**
> it works for 1,2,3

but didnt work for the rest?

Well the equation I posted definitely works for 4 and 5, you can do the math to confirm it.  So it must be that your code isn't correctly representing the equation.  Here's how I'd fill in the blanks in the code you posted.

def tet(n):
if n<=2: 
return n**2
else: 
return n**2 + tet(n-2)

---

### Post by Can+~ on 2010-03-09
So we're answering homeworks now?

---

### Post by kernco on 2010-03-09
> **Can+~ said:**
> So we're answering homeworks now?

I need something to pass the time at work.

---

### Post by MadCow108 on 2010-03-09
the next numbers are: 56, 84, 120, 165, 220, 286, 364, 455, 560, 680, 816, 969,.. 

to find the formula think about what a tetraeder is
(or use the obvious lazy route I choose ;) )

---

### Post by kernco on 2010-03-09
Uh oh! Guess my equation fails for n>5

---

### Post by LKjell on 2010-03-09
Go to wikipedia you get a formula there.

---

### Post by wmcbrine on 2010-03-09
Please use code tags, especially around Python code, where indentation is significant. In this case it's possible to infer the intended indent, but it isn't always.

And yeah, stop posting homework.

---

