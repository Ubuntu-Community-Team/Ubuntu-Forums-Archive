---
title: "why does a 1-element tuple in python require comma?"
date: 2014-07-05
forum: Programming Talk
---

### Post by IAMTubby on 2014-07-05
Hello,
Why is the comma in tup1 = (1**,**); required for a single element tuple in python?

```

#tup1 = (1);
tup1 = (1,);
print "tup1[0]: ", tup1[0]
```

Thanks.

---

### Post by CptPicard on 2014-07-05
Because otherwise it's ambiguous with the arithmetic expression (1), which is 1 with some extra parentheses.

---

### Post by IAMTubby on 2014-07-06
> **CptPicard said:**
> Because otherwise it's ambiguous with the arithmetic expression (1), which is 1 with some extra parentheses.
hmm...
CptPicard, Sorry I'm being a bit slow here. Say in a data structure like array in any programming language, you want to have only one value, you would just assign the value alone right ? Something like
```

#include <stdio.h>


int main(void)
{
 int a[] = {1};


 printf("%d",a[0]);


 return 0;
}

```
How is it different in tuples?

---

### Post by CptPicard on 2014-07-06
Go to the Python shell and type (1). What do you get? How could you tell the difference between the expression of a parenthesized 1 and a single-element tuple if the latter also looks like (1)? You couldn't, so you need to define the tuple as something else... for example (1,).

---

### Post by ofnuts on 2014-07-06
Corollary: to unpack your "unuple" you need the same kind of dangling comma:
```

>>> t = (1,)
>>> e, = t
>>> e
1

```
Otherwise:
```

>>> e = t
>>> e
(1,)

```

---

### Post by CptPicard on 2014-07-06
And an interesting feature of the tuple syntax I had not thought of before: The tuple actually seems to be just the comma-separated list of things, not the parenthesis around it. So the tuple (1,2) can be written as just "1,2".

---

### Post by ofnuts on 2014-07-06
> **CptPicard said:**
> And an interesting feature of the tuple syntax I had not thought of before: The tuple actually seems to be just the comma-separated list of things, not the parenthesis around it. So the tuple (1,2) can be written as just "1,2".

Never wrote a function that does "return x,y" before?

---

### Post by CptPicard on 2014-07-06
> **ofnuts said:**
> Never wrote a function that does "return x,y" before?

Good point. Then again it's been years since I last touched Python :)

---

### Post by IAMTubby on 2014-07-08
> **ofnuts said:**
> Corollary: to unpack your "unuple" you need the same kind of dangling comma:

> **CptPicard said:**
> Go to the Python shell and type (1). What do you get?
I did that, I got 
```

>>> a = (1)
>>> print a;
1
>>> b = (1,)
>>> print b
(1,)

```

> How could you tell the difference between the expression of a parenthesized 1 and a single-element tuple if the latter also looks like (1)? You couldn't, so you need to define the tuple as something else... for example (1,).
But isn't a "parenthesized 1" same as a single-element tuple. I'm assuming that a tuple is the same as an array in C except that "A tuple is an immutable list. A tuple can not be changed in any way once it is created.(from google)"

As per my understanding, since I think that a "parenthesized 1" is same as a single-element tuple, I still haven't got it completely.

---

### Post by spjackson on 2014-07-08
> **IAMTubby said:**
> 
But isn't a "parenthesized 1" same as a single-element tuple.

No.
```

>>> print 1 == (1)
True
>>> print 1 == (1,)
False
>>> print (1,) == (1,)
True
>>> print (1) == (1,)
False

```
> 
I'm assuming that a tuple is the same as an array in C except that "A tuple is an immutable list.

Using the C analogy, 1 is an int and an arrary of one int is not an int, it is an array.

---

### Post by ofnuts on 2014-07-08
> **IAMTubby said:**
> 

As per my understanding, since I think that a "parenthesized 1" is same as a single-element tuple, I still haven't got it completely.

You are confusing the concept and its notation... A tuple isn't a list of things inside parentheses, it is an immutable sequence of elements. It just happens that its notation uses parentheses, and that in some cases this can be ambiguous with the parentheses as used to group arithmetic expressions. 

The Python designers had to make choices, and decided that one single element surrounded by parentheses would fall in the arithmetic expression grouping realm. They could have chosen otherwise, because there isn't much use for a single operand between parentheses, but that would lead to ambiguous unpacking, because if "(1)" were a tuple, then by symmetry to unpack it you could write:
```
x = (1)
```and this would prevent the plain assigment of a tuple to a variable:
```
x = (1)
```So the unambiguous unpacking syntax is:
```
x, = (1)
```And by symmetry the one-element tuple is written (1,)

---

### Post by IAMTubby on 2014-07-08
> **spjackson said:**
> 
Using the C analogy, 1 is an int and an arrary of one int is not an int, it is an array.
Oh thanks a lot spjackson.
You mean to say 
[b]
a = (1) is same as doing int a = 1;
whereas a=(1,) is like int a[] = {1};[/b]

If my above understanding is correct, then it makes sense. I shall mark the thread as solved after I get confirmation on this.

Hopefully, I'm not dragging this thread too long. But couldn't this have been avoided if a=1;(in python) was enough for int a = 1,(in C) and 
a=(1) was an array(here tuple) ? 
But I know very little python, and I'm sure there must be some reasoning to it.

---

### Post by ofnuts on 2014-07-08
> **IAMTubby said:**
> But couldn't this have been avoided if a=1;(in python) was enough for int a = 1,(in C) and 
a=(1) was an array(here tuple) ? 

What makes the tuple is the comma, not the parentheses. Parentheses can be omitted in many cases
```

x = 1, # creates and assigns a tuple
x = 1 # assigns an integer

```

---

### Post by spjackson on 2014-07-08
> **IAMTubby said:**
> 
You mean to say 
[B]
a = (1) is same as doing int a = 1;
whereas a=(1,) is like int a[] = {1};[/B]

If my above understanding is correct, then it makes sense. I shall mark the thread as solved after I get confirmation on this.

Yes, that's about it.
> 
Hopefully, I'm not dragging this thread too long. But couldn't this have been avoided if a=1;(in python) was enough for int a = 1,(in C) and 
a=(1) was an array(here tuple) ? 
But I know very little python, and I'm sure there must be some reasoning to it.
Python, in common with many many languages (and math) allows parentheses to be placed around any expression. So we might write for example
```

>>> a = (((2) + (2)) * (6))
>>> print(a)
24

```
But a more natural way to write the same thing would be
```

>>> a = (2 + 2) * 6
>>> print(a)
24

```
We could simply that still further...
```

>>> a = (4) * 6
>>> print(a)
24

```
But by your suggestion, you don't want it to do that, because you want (4) to be a tuple, so you want it to be the same as
```

>>> a = (4,) * 6
>>> print(a)
(4, 4, 4, 4, 4, 4)

```
I suggest that would be somewhat confusing.

---

### Post by IAMTubby on 2014-07-09
> **ofnuts said:**
> 
The Python designers had to make choices, and decided that one single element surrounded by parentheses would fall in the arithmetic expression grouping realm. They could have chosen otherwise, because there isn't much use for a single operand between parentheses, but that would lead to ambiguous unpacking, because if "(1)" were a tuple, then by symmetry to unpack it you could write:
```
x = (1)
```and this would prevent the plain assigment of a tuple to a variable:
```
x = (1)
```So the unambiguous unpacking syntax is:
```
x, = (1)
```And by symmetry the one-element tuple is written (1,)

> **ofnuts said:**
> What makes the tuple is the comma, not the parentheses. Parentheses can be omitted in many cases
```

x = 1, # creates and assigns a tuple
x = 1 # assigns an integer

```
Thank you ofnuts, these two points clearly drive home the point.

> **spjackson said:**
> Yes, that's about it.
Thanks spjackson, comparing with C made understanding easier.

_Allow me to summarise : _
What really makes the tuple is the comma, not the parentheses. x = 1 cannot mean a tuple, so the python developers came up with the syntax of using x = 1, for tuple.
But Python allows parentheses to be placed around any expression rendering 1 and (1) to be the same thing. Applying this to above. x = (1) is an integer and x = (1,) is a tuple.

What we talked about so far was assigning or packing. Now looking at **unpacking** => x = (1) means x is a variable which has the value 1, whereas x, = (1) means x is a single-element tuple which has the value 1. Same would also be true for x = 1 and x, = 1

So x = (1) is an integer and not a tuple is the main take away.

Marking the thread as solved.

---

### Post by CptPicard on 2014-07-10
I feel a need to nitpick this a bit further... (1) is not an integer, it is an *arithmetic expression* that finally evaluates as an integer. This is not so much of a "python allows your to use parentheses" but an "arithmetic expressions are part of most programming languages and they let you use parentheses even in places where you don't strictly need to". See spjackson's example about expression evaluation, it was quite illuminating.

---

