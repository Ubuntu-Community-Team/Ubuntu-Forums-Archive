---
title: "python question"
date: 2009-12-20
forum: Programming Talk
---

### Post by mo.reina on 2009-12-20
if i have the following function:

```
def draw(t, length, n):
  if n == 0:
    return
  angle = 50
  fd(t, length*n)
  lt(t, angle)
  draw(t, length, n-1)
  [B]rt(t, 2*angle)
  draw(t, length, n-1)
  lt(t, angle)
  bk(t, length*n)[/B]
```

how does execution of the code reach the lines in bold?  the function keeps calling itself and n decreases by 1, which will make the function exit once it reaches 0...

i know the whole function is executed because i've run it, i just don't understand how

---

### Post by -grubby on 2009-12-20
I don't see any bold.

---

### Post by kwyto on 2009-12-20
i don't see any bold either. now, the function doesn't exist when n = 0, you are using recursion; meaning that the function will call itself with different values of n until it reaches an "ending" statement, in this case when n = 0.

---

### Post by mo.reina on 2009-12-20
hmm... must be a rendering problem, my browser renders the bold lines.

anyway, the lines after the first recursion call are executed.  i don't understand how, since n is decremented by 1 by and the function is called again before the lines of code that are found after the recursion call can be executed.

```
def draw(t, length, n):
if n == 0:
    return
...
...
draw(t, length, n-1)
rt(t, 2*angle)
...
...

```

the code should stop at the function call, yet the code after that is still executed

---

### Post by Arndt on 2009-12-20
> **mo.reina said:**
> hmm... must be a rendering problem, my browser renders the bold lines.

anyway, the lines after the first recursion call are executed.  i don't understand how, since n is decremented by 1 by and the function is called again before the lines of code that are found after the recursion call can be executed.

```
def draw(t, length, n):
if n == 0:
    return
...
...
draw(t, length, n-1)
rt(t, 2*angle)
...
...

```

the code should stop at the function call, yet the code after that is still executed

I did see the bold in the original post, but maybe B tags inside CODE are not guaranteed to work. It's better this way.

Try to work out the execution by hand, using n = 2.

The execution comes back after the call if n = 1, right? So the whole function is executed if n = 1. That means that if n = 2, a call to 'draw' will also return. And so on. Recursion can be difficult to grasp at first.

---

### Post by mo.reina on 2009-12-20
i understand that, my question is since the function recurses *BEFORE* the other lines can be read (the function call is placed above the other lines), and the function will exit once n == 0, how come the other lines (below the function call) are executed?

in theory, the only lines of code that should be executed are the ones between the beginning of the function and the function call:

```
def draw(t, length, n):
if n == 0:
    return
...
...
draw(t, length, n-1)
```

but the lines after the first call are still executed:

```
 draw(t, length, n-1)
  rt(t, 2*angle)
  draw(t, length, n-1)
  lt(t, angle)
  bk(t, length*n)
```

---

### Post by unutbu on 2009-12-20
return is not the same as exit. Unlike exit, a bare return returns the value None, and proceeds to the next command after the function call. So the boldface lines do get executed.

---

### Post by BenAshton24 on 2009-12-20
```
def draw(t, length, n):
  if n == 0:
    return
  angle = 50
  fd(t, length*n)
  lt(t, angle)
  draw(t, length, n-1)
  [B]rt(t, 2*angle)
  draw(t, length, n-1)
  lt(t, angle)
  bk(t, length*n)[/B]
```

Ok, here's what happens...

function draw is called like this draw(1, 2, 3)
if n = 0 then the rest of the function is not called, and whatever code comes after the initial calling, is executed.

so, as "n" decreases from 3 in the recursion, when it finally equals 0, the function returns and your code in bold is executed.

draw(1,2,3)
-top part executed and draw called again
--draw(1,2,2)
---top part executed and draw called again
----draw(1,2,1)
-----top part executed and draw called again
------draw(1,2,0)
-------n=0 so the function returns
-----remaining bold code is executed

Hope this helps you.

Ben

---

### Post by mo.reina on 2009-12-20
> **unutbu said:**
> return is not the same as exit. Unlike exit, a bare return returns the value None, and proceeds to the next command after the function call. So the boldface lines do get executed.

> **BenAshton24 said:**
> Ok, here's what happens...

function draw is called like this draw(1, 2, 3)
if n = 0 then the rest of the function is not called, and whatever code comes after the initial calling, is executed.

so, as "n" decreases from 3 in the recursion, when it finally equals 0, the function returns and your code in bold is executed.

draw(1,2,3)
-top part executed and draw called again
--draw(1,2,2)
---top part executed and draw called again
----draw(1,2,1)
-----top part executed and draw called again
------draw(1,2,0)
-------n=0 so the function returns
-----remaining bold code is executed

Hope this helps you.

Ben

ok thanks.  i surmised that was what was happening but i wasn't quite sure... great info on return, thanks again

---

