---
title: "Python Permutation Generating"
date: 2008-05-14
forum: Programming Talk
---

### Post by Mr.Macdonald on 2008-05-14
I want to build a python function that generates all the possible permutations of the elements in an array

ex. (i call it lexo)

>>> lexo([1,2,3])
[123,132,213,231,312,321]

see my attached file i think that the pseudocode should work once constructed but i am in question??

please help me learn by teaching me my errors

please no randomly permutation generating because i made one do that yesterday and it hasn't finished (the progress is logarithmic)

Thank you

---

### Post by CptPicard on 2008-05-14
I was messing with something similar some time ago.

[http://ubuntuforums.org/showthread.php?t=649295](http://ubuntuforums.org/showthread.php?t=649295)

It's not quite the same thing, but the idea should generalize easily (and is left as homework for the reader :)

---

### Post by Mr.Macdonald on 2008-05-14
I have found that it works to a point but then i get a nice list of 

  File "<stdin>", line 10, in lexo
  File "<stdin>", line 10, in lexo
  File "<stdin>", line 10, in lexo
  File "<stdin>", line 10, in lexo
  File "<stdin>", line 10, in lexo
  File "<stdin>", line 10, in lexo
  File "<stdin>", line 10, in lexo
  File "<stdin>", line 10, in lexo
  File "<stdin>", line 10, in lexo
  File "<stdin>", line 10, in lexo
  File "<stdin>", line 10, in lexo
  File "<stdin>", line 10, in lexo
  File "<stdin>", line 10, in lexo
  File "<stdin>", line 10, in lexo
  File "<stdin>", line 10, in lexo
  File "<stdin>", line 10, in lexo
  File "<stdin>", line 10, in lexo
  File "<stdin>", line 10, in lexo
  File "<stdin>", line 10, in lexo
  File "<stdin>", line 14, in lexo
RuntimeError: maximum recursion depth exceeded in cmp


Looks fun doesn't it !!!


I don't see why i should worry about infinite recursion because i have designed it to stop it's self after enough recursions by deleting elements of a list that it is reading off of.

I actually have functioning code now !!!

Edit:

The wierd thing is that its blowing up and the

if i2 in perms:

which doesn't make sense unless when a sub function (the main one called itself) adds something to perm then it adds it the the perm fro the above function, and why would it do that.

---

### Post by Mr.Macdonald on 2008-05-14
Please is there some way to enable infinite recursion without recompiling python (my dad told me thats how you do it)

EDIT:

Never mind, i found this


```
def all_perms(str):
    [INDENT]if len(str) <=1:
        [INDENT]yield str[/INDENT]
    else:
        [INDENT]for perm in all_perms(str[1:]):
            [INDENT]for i in range(len(perm)+1):
                [INDENT]yield perm[:i] + str[0:1] + perm[i:][/INDENT][/INDENT][/INDENT][/INDENT]
```
I AM SO MAD, I SPENT ALL THAT TIME AND THIS IS ENOUGH CODE TO SOLVE THAT!?!?!?!??!?!?!?!

Please explain it, i don;t know what yield does

---

### Post by Can+~ on 2008-05-15
You just started with python and rushed into doing a permutation?

Recompile python? Python is interpreted, you don't compile it (well, it actually compiles but.. ), and a recursion is done with:

[PHP]def myFunction():
	doSomething()
	myFunction()[/PHP]

And yield is to produce a generator object, which is iterable, but that's a bit advanced. Here's an example anyway, a generator that returns odd numbers:

[PHP]def oddNumbers(max):
	i = -1
	while(i+2 < max):
		i += 2
		yield i

for odds in oddNumbers(10):
	print odds[/PHP]

(Example is a bit dumb, you could do it with [FONT="Courier New"]for i in xrange(1,10,2)[/FONT])

And please, try to put your code inside PHP tags or CODE at least.

Edit: I knew I saw this question before:
[http://ubuntuforums.org/showthread.php?t=720650&highlight=Permutation](http://ubuntuforums.org/showthread.php?t=720650&highlight=Permutation)

---

### Post by CptPicard on 2008-05-15
> **Mr.Macdonald said:**
> Please is there some way to enable infinite recursion without recompiling python

If you're able to actually enable *infinite recursion* and do something useful with it by just recompiling Python, please share -- it would have tremendous theoretical implications ;)

Seriously speaking, recursions must have their end-conditions... something that runs forever or runs out of stack is not of much use :)

EDIT: Oh well, stackless Python and some kind of tailcall optimization is probably what you mean. Tail recursion can be converted to loop, as you may know... it's still not what you need though. ;)

---

### Post by Mr.Macdonald on 2008-05-15
maybe i didn't clarify

i meant to recompile and change the whole interpreter ( i know this sounds stupid but i was desperate )

and i don't know if this is true, it just what i heard to solve the max recursion error. and not have it run infinitly just until i run out of memory and the system crashes. i do think its called stackless?

i did find that you don't have to "recompile the python interpreter" just do >>> sys.setrecursionlimits(2000000) of something like that

but with my code that i made i am done, because it didn't work.


Ok,

I am beginning to see the brilliance of that code.

let me explain what i am thinking

the premutations function starts out and test for anything in the list and if not then it returns and empty list

then it goes to a for loop that scrolls through the indexes to the list (ie 1 2 3 4 5 ...). then the next for loop scrolls through the elements of the recursivly called permutations of the list excluding the element (list[i]) that the first for loop is currently on. then the function yeilds list[i] + the sub-permutations

and yield just waits until someone asks for a value and then generates it.

But why doesn't this give the recursion limit exceeded error.
and would it if i gave a big enough list ( 0 1 2 3 4 ... 99999 )??

---

### Post by dov.grobgeld on 2008-05-15
Hello all.

I just played around with creating permutations in python and found the following very compact way by using a recursive yield. I thought that this forum would be a good place to show it off. Enjoy!

```

def permute(a):
     if len(a)==1:
         yield a
    else:
        for p in permute(a[1:]):
             for i in xrange(len(a)):
                 yield p[0:i]+[a[0]]+p[i:]

for p in permute([1,2,3]):
     print p
```

---

### Post by Lux Perpetua on 2008-05-15
Not bad. That's definitely one of the more elegant solutions I've seen. I think this is a good illustration of the usefulness of the generator paradigm. 

In contrast, my nonrecursive x86 assembly implementation which I wrote about a year ago for fun seems to be about 75 times faster when permuting 10 items (0.839 seconds vs. 62.982 seconds), but at the expense of 86 lines of ugly assembly code, vs. 7 lines of beautiful python.

---

### Post by Can+~ on 2008-05-15
> **Lux Perpetua said:**
>  (0.839 seconds vs. 62.982 seconds)

Don't be fooled, there's a serious lag with printing:

[PHP]import time

def exectime(target):
	def wrapper(*args, **kwargs):
		tini = time.time()
		target(*args, **kwargs)
		tend = time.time()
		print "Completed: it took %f seconds." % (tend-tini)
	
	return wrapper
	
def permute(a):
	if len(a)==1:
		yield a
	else:
		for p in permute(a[1:]):
			for i in xrange(len(a)):
				yield p[0:i]+[a[0]]+p[i:]

@exectime
def permuteFunc():
	for p in permute([1,2,3,4,5,6,7,8,9,10]):
		pass #print p

permuteFunc()
[/PHP]

with print it takes:
[FONT="Courier New"]Completed: it took 151.066708 seconds.[/FONT]

without printing:
[FONT="Courier New"]Completed: it took 6.468537 seconds.[/FONT]

I noticed this when working on a different project, also with a truckload of numbers, it ran normally, then I added a print line and the whole thing took 100 times to do it.

---

### Post by Lux Perpetua on 2008-05-16
Good point. Printing is also the main bottleneck in my assembly program, apparently even more so than in the python program: without printing, the assembly program runs in 0.109 seconds vs. 17.230 for the python. 

I think there are two main contributors to my program's speed. Firstly, it only permutes characters in strings, which translates easily into simple and fast machine code. The python version permutes any list. Thus, you could say the comparison is a bit unfair. 

Secondly, my program permutes in place by swapping elements, as opposed to creating new lists. I think an in-place python implementation would see a significant speed boost.

---

