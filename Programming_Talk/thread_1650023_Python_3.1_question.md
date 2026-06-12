---
title: "Python 3.1 question"
date: 2010-12-20
forum: Programming Talk
---

### Post by yeklef on 2010-12-20
I am sure that this is a very easy question, but I just can't get it to work.  I am doing simple program that will sum multiples of 3 and 5, up until a certain point.   For some reason I just can't get return to work.  

Here is my current batch of code.  I have tried numerous things.  One example is to have the returned value be in parentheses "return(total)"

[PHP]import math

def multiples_3_n_5(n):
    test = fives(n, 0, 0)
    test2 = threes(n, 0, 0)
    final = test + test2
    print(final)
    
def fives(n, f, total): # this section adds all multiples of 5 less than 'n' (1000 in this case)
    if f < n:
        total = f + total
        fives(n, f+5, total)
    else:
        print("fives done")
        print(total)
        int(total)
        return total

def threes(n, t, total): # this section adds in multiples of 3 less than 'n' (1000 in this case) 
    if t < n:
        if t%5 == 0:
            threes(n, t+3, total)  # this line keeps multiples of 5 from being added twice
        else:
            total = t + total
            threes(n, t+3, total)
    else:
        print("threes done")
        print(total)
        int(total)
        return total

multiples_3_n_5(1000) 

[/PHP]



Here is the current output message when I call it in a terminal.  The first four lines are just calls to print() that I put in to help me debug.  Thanks for any help



fives done
99500
threes done
133668
Traceback (most recent call last):
  File "project1.py", line 32, in <module>
    multiples_3_n_5(1000)
  File "project1.py", line 6, in multiples_3_n_5
    final = test + test2
TypeError: unsupported operand type(s) for +: 'NoneType' and 'NoneType'

---

### Post by Arndt on 2010-12-21
> **yeklef said:**
> I am sure that this is a very easy question, but I just can't get it to work.  I am doing simple program that will sum multiples of 3 and 5, up until a certain point.   For some reason I just can't get return to work.  

Here is my current batch of code.  I have tried numerous things.  One example is to have the returned value be in parentheses "return(total)"

[PHP]import math

def multiples_3_n_5(n):
    test = fives(n, 0, 0)
    test2 = threes(n, 0, 0)
    final = test + test2
    print(final)
    
def fives(n, f, total): # this section adds all multiples of 5 less than 'n' (1000 in this case)
    if f < n:
        total = f + total
        fives(n, f+5, total)
    else:
        print("fives done")
        print(total)
        int(total)
        return total

def threes(n, t, total): # this section adds in multiples of 3 less than 'n' (1000 in this case) 
    if t < n:
        if t%5 == 0:
            threes(n, t+3, total)  # this line keeps multiples of 5 from being added twice
        else:
            total = t + total
            threes(n, t+3, total)
    else:
        print("threes done")
        print(total)
        int(total)
        return total

multiples_3_n_5(1000) 

[/PHP]



Here is the current output message when I call it in a terminal.  The first four lines are just calls to print() that I put in to help me debug.  Thanks for any help



fives done
99500
threes done
133668
Traceback (most recent call last):
  File "project1.py", line 32, in <module>
    multiples_3_n_5(1000)
  File "project1.py", line 6, in multiples_3_n_5
    final = test + test2
TypeError: unsupported operand type(s) for +: 'NoneType' and 'NoneType'

You need 'return' at every point where you want to return a value, like here:

```
def fives(n, f, total): # this section adds all multiples of 5 less than 'n' (1000 in this case)
    if f < n:
        total = f + total
        return fives(n, f+5, total)

```

---

### Post by Tony Flury on 2010-12-21
This is Euler Project 1 - isn't it.

that is a pretty complex way of doing it to be honest.

---

### Post by wmcbrine on 2010-12-21
[Never mind]

---

### Post by yeklef on 2010-12-21
Arndt, thanks, that did it.  Worst part is, as soon as you said it, I remembered reading somewhere at one point too.  


> **Tony Flury said:**
> This is Euler Project 1 - isn't it.

that is a pretty complex way of doing it to be honest.


Yeah, it is project 1.  And I know there are more efficient ways of doing it, but I wasn't worried about efficiency the first time I did it, I just wanted to get it done.  For being hideously out of practice at programming, and not really knowing python yet, I went for fairly straight forward code, even if the computer has to work a little extra.

---

### Post by Tony Flury on 2010-12-21
well - doing it via recursion is a pretty complicated way of doing it - i wouldn't call your solution straightforward at all :-)

In python - without using any special constructs you can do it in only a few lines 

```

total = 0 
for n in range(1,1000):
    if (n%3 == 0 or n%5 ==0) and not (n%15== 0):
        total = total + n
print( total )

```
That should work :-)

the % operator (modulus) is standard in most languages - and the range function is pretty simple - just replicates the 
```

for i = a to b

```
type construct found in most languages.

---

### Post by yeklef on 2010-12-21
Yeah, I have since slimmed it down to something closer to that, not that short yet, but getting close.  But I wanted to figure out what I was doing wrong with 'return' so I posted that first set of code that I had.  

So another question.  Wouldn't 'for' also be recursive?  My way with 'if' would be more explicitly recursive, but 'for' strikes me as being recursive as well.  Maybe more subtle, but still recursive?  Like I said before, out of practice with programming, and terms were never my strong point either.

---

### Post by Vaphell on 2010-12-22
for is iterative not recursive, it's a simple flat loop with counter.
recursion is when a function is embedded in itself

---

### Post by Arndt on 2010-12-22
> **Vaphell said:**
> for is iterative not recursive, it's a simple flat loop with counter.
recursion is when a function is embedded in itself

"Embedded" seems the wrong word to use, but you probably know what you mean. I would say it's when a function calls itself, directly or indirectly. The important point is whether an indeterminate number of intermediate states need to be saved, in order to continue the execution after the call. For a 'for' loop, only the loop variable needs to be kept (and a piece of code implementing the stop criterion).

Iterative constructs are often expressed in a recursive way when reasoning about them abstractly, but the distinction is often quite clear when we look at the implementation. Some languages don't mind recursion at all, and some don't even have any other means of looping.

---

### Post by yeklef on 2010-12-22
So to see if I understand you correctly, the loops in my original code (which are recursive) would be a memory hog, because it is basically saving all the variables each time it calls itself, but the way that Tony Flurry showed (which is iterative) only has to save the value of the range, and then each variable once, and then each time through the "loop" just changes that variable, instead of saving another instance of it. (edit: After reading your explanation again, it seems like there is more too it than this though.)

If I understand it correctly then, what advantages are there to using recursion as opposed to iteration?  The only thing that I can think of would be maybe recursion could be made to use fewer cpu cycles in some instances?  Or maybe if you have different functions that are mutually recursive?

Thanks for all the information/help so far

---

### Post by Vaphell on 2010-12-22
while in most languages recursion is not the king of performance, it is useful because it allows for cleaner, shorter, more elegant, easier to maintain, bug free code.
Some classes of problems naturally subscribe to recursion. Let's say you have a tree and you need to perform some operation on every node. With recursion all you need to do is to call
some_function(node)
{
do_stuff;
some_function(left);
some_function(right);
}
some_function(root);

Imagine all the hassle required to track the current state of iteration and to assure that every node has been visited. It is certainly doable, but you would spend a lot of time debugging and if there is no high performance/low memory requirement, why would you want to choose the hard way?

---

### Post by trent.josephsen on 2010-12-22
Recursion often makes it easier to write an algorithm because you only have to think about one piece at a time.

In some cases, like when you're traversing a directory tree, the iterative solution is much more complicated than the recursive one, and requires little or no more memory or CPU time.  In other cases, like traversing a simple linked list, the overhead of calling a new function for every node may be absurd.

Fundamentally, though, programmers write recursive algorithms because they make it easier for programmers, not for computers.

---

### Post by yeklef on 2010-12-22
Thanks for all the answers.  This is a way better way to learn than in the classroom :D

---

