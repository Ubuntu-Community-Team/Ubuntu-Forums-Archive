---
title: "Iterating using a for loop"
date: 2009-09-04
forum: Programming Talk
---

### Post by 7raTEYdCql on 2009-09-04
I want to iterate over a list three at a time.

something like this
[a,2,3,4,5,6,7]
and it should iterate a,4,7.

Is there a inbuilt function or do we have to enumerate the list and then increment the iterator??

---

### Post by yabbadabbadont on 2009-09-04
You'll have to tell us which language you are using before anyone will be able to give you a correct answer.  :)

---

### Post by Finalfantasykid on 2009-09-04
Ya I'm not sure if you can do this in all languages, although I am pretty sure this would be pretty universal.

```
for(int i = 0; i < size; i+=3){
   // Your code
}
```

I'm pretty sure that should work at least :P

---

### Post by Bodsda on 2009-09-04
Python solution

```

list = ["a", 2, 3, 4, 5, 6, 7]
string = ""
count = 0
for i in range((len(list) / 3) + 1):
    string += str(list[count])
    count +=3
print string

```

---

### Post by ghostdog74 on 2009-09-04
> **Bodsda said:**
> Python solution

```

list = ["a", 2, 3, 4, 5, 6, 7]
string = ""
count = 0
for i in range((len(list) / 3) + 1):
    string += str(list[count])
    count +=3
print string

```
```

>>> alist=['a', 2, 3, 4, 5, 6, 7]
>>> ''.join(map(str,alist[::3]))
'a47'


```

---

### Post by Bodsda on 2009-09-04
> **ghostdog74 said:**
> ```

>>> alist=['a', 2, 3, 4, 5, 6, 7]
>>> ''.join(map(str,alist[::3]))
'a47'


```

Dear python god,

I bow before as I promise to do some research on how that works.
I ask of you lord only that you point me in the correct direction

Amen

---

### Post by ghostdog74 on 2009-09-04
> **Bodsda said:**
> Dear python god,

I bow before as I promise to do some research on how that works.
I ask of you lord only that you point me in the correct direction

Amen
if you buy a gadget and don't know how to use, you read the manual. same in programming, see [this]("http://docs.python.org/reference/datamodel.html") under sequences

---

### Post by Reiger on 2009-09-04
Oh it's fairly trivial: he uses the fact that a String is commonly treated as a List/Array of characters.

That explains: '.'join() (join() being a concatenation function), as well as the str (to string conversion, presumably.)

Python also has something for selecting specific ranges/indices in lists: that is the [::3] bit (alist is the name of the list). Now the map thing is an implicit for-each loop: only implemented recursively, from the functional programming world and called map and applied to lists...

Map does the following: it breaks down an input list item by item and feeds each item to a function supplied (e.g.: str) and then builds a corresponding output list. So you get e.g.: map str [1,2,3] => ["1","2","3"]

...
Which brings me to a function language called Haskell. In there the solution is somewhat different:
```

-- function to take all items exactly q positions apart in the list
iTake q list = func 0 list
    where
	  func _ [] = []
	  func 0 (x:xs) = x: func q xs
	  func r (x:xs)	= func (r-1) xs
```

As you will notice it is merely an additional variable declaration in the signature of iTake (the q) instead of a hardcoded value in func 0 (x:xs) (I use q instead of a hardcoded 2).

And more skilled Haskell'ers will probably find this too imperative. There's probably a funky fold-based definition out there. :P

---

### Post by DaithiF on 2009-09-04
in python:
```
alist= ['a',2,3,4,5,6,7]
[ x for ( i, x) in enumerate(alist) if i % 3 == 0]

```
gives
['a',4,7]

---

### Post by ad_267 on 2009-09-04
> **DaithiF said:**
> in python:
```
alist= ['a',2,3,4,5,6,7]
[ x for ( i, x) in enumerate(alist) if i % 3 == 0]

```
gives
['a',4,7]

So does "alist[::3]"

---

### Post by yabbadabbadont on 2009-09-04
Why do I feel like we've just done someone's homework for them?  :D

---

### Post by Can+~ on 2009-09-04
> **ad_267 said:**
> So does "alist[::3]"

Yup. Funny that no one else noticed that.

Also, you can invert a list with [::-1].

---

### Post by ad_267 on 2009-09-04
> **Can+~ said:**
> Yup. Funny that no one else noticed that.

Also, you can invert a list with [::-1].

ghostdog74 did, and included the rest of the solution to convert it to a string. :)

---

### Post by 7raTEYdCql on 2009-09-05
This wasn't a homework of any sort. I anyway did use slicing with alist[::3] just that i didn't update this page before i got it, am sorry guys, but thanks for the help. Your spontaneous reponse keeps calling me here for my programming needs. :) Awesome place.

---

