---
title: "python help"
date: 2009-07-05
forum: Programming Talk
---

### Post by c0mput3r_n3rD on 2009-07-05
Hey all! 
I'm just learning python on ubuntu, which is v2.5 (already installed), but I can't find a tutorial for v2.5, only v2.6.2.  Can any one help me out with either upgrading and/or a tutorial on v2.5, which I should do

thanks a lot

---

### Post by Can+~ on 2009-07-05
You're on Intrepid? I don't know if there's an available version of python 2.6 from the repository for that version. Try to check on synaptic.

If not, well, there's not much difference between 2.5.2 to 2.6, so I guess you could still learn from the documentation. Or install python3.

btw: In case you're wondering, there's no problem on installing two different versions of python at the same time; I've got python2.6 and 3 installed at the same time.

---

### Post by c0mput3r_n3rD on 2009-07-05
Yeah I just checked synaptic, and their are a million versions haha, so that didn't really help to much.  And I thought their wouldn't be a huge difference b/t 2.5 and 2.6 either, how ever as the programs will run, the results are not correct, even when the syntax is. hmmmmm. :-\

---

### Post by Can+~ on 2009-07-05
> **c0mput3r_n3rD said:**
> Yeah I just checked synaptic, and their are a million versions haha, so that didn't really help to much.  And I thought their wouldn't be a huge difference b/t 2.5 and 2.6 either, how ever as the programs will run, the results are not correct, even when the syntax is. hmmmmm. :-\

What problems do you experience? Try to show some code and I may point you what's wrong.

---

### Post by c0mput3r_n3rD on 2009-07-05
#! /usr/bin/env python
for n in range(2, 10):
    for x in range(2, n):
        if n % x == 0:
            print n, 'equal', x, '*', n/x
            break
        else:
            #loop feel throughw with out finding a factor
            print n, 'is a prime number'
--------------------------------------------------------------------------------------
Output:

3 is a prime number
4 equal 2 * 2
5 is a prime number
5 is a prime number
5 is a prime number
6 equal 2 * 3
7 is a prime number
7 is a prime number
7 is a prime number
7 is a prime number
7 is a prime number
8 equal 2 * 4
9 is a prime number
9 equal 3 * 3


So the code should only print out each number once, and I've double checked my code with the example in the tutorial.

---

### Post by Can+~ on 2009-07-05
> **c0mput3r_n3rD said:**
> #! /usr/bin/env python
for n in range(2, 10):
    for x in range(2, n):
        if n % x == 0:
            print n, 'equal', x, '*', n/x
            break
        else:
            #loop feel throughw with out finding a factor
            print n, 'is a prime number'


Actually, you have a little typo, the "else" statement can also be used paired with the [FONT="Courier New"]for _ in ____[/FONT]. For's else is called when the for statement ends, for example:

[PHP]>>> for i in xrange(0, 10):
...     print i
... else:
...     print "END!"
... 
0
1
2
3
4
5
6
7
8
9
END![/PHP]

So, to fix your code, remove some indentation the else block, like this:

[PHP]#!/usr/bin/env python
for n in range(2, 10):
    for x in range(2, n):
        if n % x == 0:
            print n, 'equal', x, '*', n/x
            break
    else:
        #loop feel throughw with out finding a factor
        print n, 'is a prime number'[/PHP]

Which outputs

```
2 is a prime number
3 is a prime number
4 equal 2 * 2
5 is a prime number
6 equal 2 * 3
7 is a prime number
8 equal 2 * 4
9 equal 3 * 3
```

---

### Post by c0mput3r_n3rD on 2009-07-05
Oh yeah you're right!  So you're saying I should be alright (at least for a little bit) learning v.2.6 and v2.5 compiler?

---

### Post by c0mput3r_n3rD on 2009-07-05
And is that else for the loop???

---

### Post by Can+~ on 2009-07-05
> **c0mput3r_n3rD said:**
> Oh yeah you're right!  So you're saying I should be alright (at least for a little bit) learning v.2.6 and v2.5 compiler?

You'll notice the difference when you need newer libraries, but as for learning the base language, 2.5 does the job.

> And is that else for the loop??? 

Yup. In the [doc you can read more about it]("http://docs.python.org/reference/compound_stmts.html#for").

---

### Post by c0mput3r_n3rD on 2009-07-05
Sweet deal man thanks for the help!

---

### Post by Empire537 on 2009-07-06
For the record 2.6 has no major changes over 2.5. Mainly bug fixes. You can run 2.6 commands in 2.5 python no problem.

---

