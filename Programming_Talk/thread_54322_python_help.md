---
title: "python help"
date: 2005-08-04
forum: Programming Talk
---

### Post by fng on 2005-08-04
Is there a nice way for auto-generating the following array/list?

```

dealOrder = [1,1,1,1,2,2,2,2,3,3,3,3,4,4,4,4,1,1,1,1,2,2,2,2,3,3,3,3,4,4,4,4,1,1,1,1,1,2,2,2,2,2,3,3,3,3,3,4,4,4,4,4]

```

---

### Post by SGC on 2005-08-04
I'm sure there are  better ways than the following: 
```

dealorder = [1, 2, 3 , 4]
newdealorder = []
i = 2

def repeat(item, times):
 global newdealorder
 s = 0
 while s < times:
  newdealorder.append(item)
  s = s + 1

while i > 0:
 for h in dealorder:
  repeat(h, 4)
 i = i -1

for h in dealorder:
 repeat(h, 5)
  
print newdealorder


```

If you don't want to use a function:
```

dealorder = [1, 2, 3 ,4]
newdealorder = []
i = 2

while i > 0:
  for j in dealorder:
      newdealorder.append(j)
      newdealorder.append(j)
      newdealorder.append(j)
      newdealorder.append(j)
  i = i -1

for h in dealorder:
  newdealorder.append(h)
  newdealorder.append(h)
  newdealorder.append(h)
  newdealorder.append(h)  
  newdealorder.append(h)
  
print newdealorder

```

---

### Post by fng on 2005-08-04
thnx for the solutions

i came up with another one:
```

        dealOrder = []
        n = 1
        l = 4
        
        for i in range(12):
            for j in range(4):
                dealOrder.append(n)
           
            if i == 7:
                l = l + 1
        
            if n == 4:
                n = 1
            else:
                n = n + 1

```
pretty ugly he :)

---

### Post by bittner on 2005-08-04
The simplest way I can think of is:

```
([1] * 4 + [2] * 4 + [3] * 4 + [4] * 4) * 2
```
This way you avoid much code you then need to maintain.
Dunno if this meets your requirements though.

Peter

---

### Post by thumper on 2005-08-05
You could use a generator (if using python 2.4):
```
def deal():
    seat = [1,2,3,4]
    for count in xrange(2):
        for s in seat:
            for count in xrange(4):
                yield s
    for s in seat:
        for count in xrange(5):
            yield s
```

I put that in gentest.py, and then fired up the interpreter

```
>>> import gentest
>>> list(gentest.deal())
[1, 1, 1, 1, 2, 2, 2, 2, 3, 3, 3, 3, 4, 4, 4, 4, 1, 1, 1, 1, 2, 2, 2, 2, 3, 3, 3, 3, 4, 4, 4, 4, 1, 1, 1, 1, 1, 2, 2, 2, 2, 2, 3, 3, 3, 3, 3, 4, 4, 4, 4, 4]
>>> 
```

---

### Post by jerome bettis on 2005-08-05
^ well done i like it

but i have no idea how it works :-P.  could you explain it a little?  yield .. is that yield in the sense of threads or something else?

---

### Post by LordHunter317 on 2005-08-05
[http://www.python.org/peps/pep-0255.html](http://www.python.org/peps/pep-0255.html) is the technical explanation of yield.

Basically, yield causes an early return from a function.  The calling function is given the yielded value, and does whatever it wants with it.  When it calls the yielding function again, the yielding function resumes right where it left off.

This is a way to support some commonly desired iteration techniques without needing to keep extra state, as the language does it for you.  Otherwise, the deal() function above would have to remember where it was on every call.  IOW, it'd have to have an explict variable/counter to remember where it was in the list it is returning.  With yield, it's handled by the language.

This is a high-level view and I'm not much of a Python programmer, so I'm probably missing more than a few details about how generators work in python and how they can be used for other clever things.

---

### Post by thumper on 2005-08-07
[QUOTE=LordHunter317]Basically, yield causes an early return from a function.  The calling function is given the yielded value, and does whatever it wants with it.  When it calls the yielding function again, the yielding function resumes right where it left off.
<snip>
This is a high-level view and I'm not much of a Python programmer, so I'm probably missing more than a few details about how generators work in python and how they can be used for other clever things.[/QUOTE]
For someone who is not much of a Python programmer you did a pretty good job of explaining it.

The mention of yield and threads does bring some interesting parallels.  When calling yield for threads means "I'm done for now, let someone else have a go", and the yield function in python has similar semantics, "I'm done for now, here's a value, but start again from here next time".

---

### Post by byronsalty on 2005-08-13
Here's how to do it in one line and I think it's still easy to understand:

```

l = range(1,5)*4; l.sort(); l*=3
print l
[1, 1, 1, 1, 2, 2, 2, 2, 3, 3, 3, 3, 4, 4, 4, 4, 1, 1, 1, 1, 2, 2, 2, 2, 3, 3, 3, 3, 4, 4, 4, 4, 1, 1, 1, 1, 2, 2, 2, 2, 3, 3, 3, 3, 4, 4, 4, 4]

```


Did you really want the last set to have 5 elements instead of 4? It looked like you're code didn't do that so I wasn't sure.

If so you could use the same technique:

```

l = range(1,5)*4; l.sort(); l*=2
l2 = range(1,5)*5; l2.sort(); l += l2
print l
[1, 1, 1, 1, 2, 2, 2, 2, 3, 3, 3, 3, 4, 4, 4, 4, 1, 1, 1, 1, 2, 2, 2, 2, 3, 3, 3, 3, 4, 4, 4, 4, 1, 1, 1, 1, 1, 2, 2, 2, 2, 2, 3, 3, 3, 3, 3, 4, 4, 4, 4, 4]

```

---

### Post by Soulfly on 2005-08-13
I would recommend the fast python list operationsover the more complex sort function. Those are pretty straight forward.e.g:

>>> dealorder=[ 1 , 2 , 3 , 4 ]
>>> repetitions=4
>>> sequences=2
>>> reduce( list.__add__ , [ [x]*repetitions for x in dealorder ] )*sequences
[1, 1, 1, 1, 2, 2, 2, 2, 3, 3, 3, 3, 4, 4, 4, 4, 1, 1, 1, 1, 2, 2, 2, 2, 3, 3, 3, 3, 4, 4, 4, 4, 1, 1, 1, 1, 2, 2, 2, 2, 3, 3, 3, 3, 4, 4, 4, 4]

In python2.4 you can do this using generator expressions if you dont want to create all intermediate lists

---

### Post by cwaldbieser on 2005-08-13
[QUOTE=thumper]
The mention of yield and threads does bring some interesting parallels.  When calling yield for threads means "I'm done for now, let someone else have a go", and the yield function in python has similar semantics, "I'm done for now, here's a value, but start again from here next time".[/QUOTE]

There is an interesting MSDN article that touches on this very topic: [http://msdn.microsoft.com/msdnmag/issues/03/09/CoroutinesinNET/default.aspx](http://msdn.microsoft.com/msdnmag/issues/03/09/CoroutinesinNET/default.aspx) 

They talk about how to use Win32 fibers to implement coroutines.

---

### Post by fng on 2005-08-23
[QUOTE=byronsalty]
Did you really want the last set to have 5 elements instead of 4? It looked like you're code didn't do that so I wasn't sure.
[/QUOTE]

Yes, the last set of elements needs to be 5

I'm new to pyhton and just goofing around.
To get the hang of it, i'm trying to simulate a game of belgian whist
The dealorder is 4 4 5 cards for each person.

---

### Post by Mike Buksas on 2005-08-24
[QUOTE=LordHunter317][http://www.python.org/peps/pep-0255.html](http://www.python.org/peps/pep-0255.html) is the technical explanation of yield.

Basically, yield causes an early return from a function.  The calling function is given the yielded value, and does whatever it wants with it.  When it calls the yielding function again, the yielding function resumes right where it left off.

This is a way to support some commonly desired iteration techniques without needing to keep extra state, as the language does it for you.  Otherwise, the deal() function above would have to remember where it was on every call.  IOW, it'd have to have an explict variable/counter to remember where it was in the list it is returning.  With yield, it's handled by the language.

This is a high-level view and I'm not much of a Python programmer, so I'm probably missing more than a few details about how generators work in python and how they can be used for other clever things.[/QUOTE]


A minor clairification: You only call the function once, instead of getting a value, you get a iterator object. When you call the next() method of the iterator object, you get the first value, and subsequent values when you call next again. For example:

```

it = testgen.deal()
it.next()
1
it.next()
1
it.next()
1
it.next()
1
it.next()
2

```

Or you can stick it in a for loop:
```

for card in testgen.deal()
   print card

```

Your example with list() constructs a list from the iterator object. A very nice shortcut. Generators are especially useful when you don't want to store long lists of values in memory, but can write a generator function to produce the values on demand. 

Mike

---

