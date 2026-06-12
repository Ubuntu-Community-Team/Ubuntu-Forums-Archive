---
title: "Python Incrementing issue."
date: 2008-02-21
forum: Programming Talk
---

### Post by sp0nge on 2008-02-21
I am trying to manipulate items of a list as follows:

```

list = [100, 100, 100, 100]
for letter in t:
	list.append(ord(letter))
list2 = []
for i in range(len(list)+1)[1:]:
	list2.append(list[i-1]+i)

```

when list2 returns 
```
101, 102, 103, 104
```

I realize that I'm missing some detail. I want the outcome to be:
```
100, 101, 102, 103 
```

I know I'm going to kick myself, but I just can't seem to get it!

---

### Post by raja on 2008-02-21
Manipulate what ?

---

### Post by sp0nge on 2008-02-21
Sorry, I sneezed and apparently hit the enter button which posted prematurly!

---

### Post by raja on 2008-02-21
Maybe its just that I am dense - but I dont get exactly what you want.

What is t and what exactly do you want to do?

---

### Post by sp0nge on 2008-02-21
I want to take the values in list and modify them. 

Item one is unchanged, Item 2 gets 1 added, item 3 gets 2 added and so on.

---

### Post by amingv on 2008-02-21
If it's not too much of an intrusion, what do you wish to achieve?

To get the effect you want change this line:
[PHP]for i in range(len(list)+1)[1:]:[/PHP]
to this:
[PHP]for i in range(len(list)+1):[/PHP]

You can also change
[PHP]for i in range(len(list)+1)[1:]:
	list2.append(list[i-1]+i)[/PHP]
for
[PHP]for i in range(len(list)):]:
	list2.append(list[i]+i)[/PHP]

And make it less redundant.

---

### Post by raja on 2008-02-21
What you want maybe is

```
testlist = [100,100,100,100]

for i in range(len(testlist)):
	testlist[i]+=i 

print testlist

```
or

```

testlist = [100,100,100,100]
print [x+testlist[x] for x in range(len(testlist))]
```

---

### Post by sp0nge on 2008-02-21
amingv: Thanks for the code, I know I'm sloppy as I'm still very new to programming. The problem with your suggestion is that in this code:

```
for i in range(len(list)+1):  
```

It returns one additional item at the end if the list:

```

list = [100, 100, 100, 100, 100]
for i in range(len(list)+1):  
    list2.append(list[i-1]+i)

```

will return:
```
100, 101, 102, 103,104, 105
```

I need to get rid of the added item (105).

---

### Post by ghostdog74 on 2008-02-21
```

>>> import operator
>>> l=[100, 100, 100, 100]
>>> map(operator.add, range(len(l)) ,l )
[100, 101, 102, 103]


```

---

### Post by amingv on 2008-02-21
Well, I must say I hadn't seen such a method before, but if you want an extra item then I guess it works fine. Just notice that the 0th element in list2 will be the last (ie the -1st) element in list, which may or may not be what you want, depending on your purpose.

Also, no need to excuse yourself, I am a green programmer too and I can prove as sloppy as you (or maybe more).

---

### Post by sp0nge on 2008-02-21
ghostdog74, this code works, but I need the values to be made available either in the original list or in a new one. 

```

>>> list = [100, 100, 100, 100]
>>> map(operator.add, range(len(list)) ,list )
[100, 101, 102, 103]

>>> list # The value(s) of the list items are still the same.
[100, 100, 100, 100]

```

---

### Post by pmasiar on 2008-02-21
list is name of built-in function, you should not name variable like that.

---

### Post by Quikee on 2008-02-21
[PHP]numbers = [100, 100, 100, 100]

numbers  = [x+i for i,x in enumerate(list)][/PHP]

---

### Post by sp0nge on 2008-02-21
> list is name of built-in function, you should not name variable like that.

I'm aware, thank you. I suppose I need to start mentioning when I use pseudocode.. 

Quickee, thanks for the input. This didn't seem to work though: 

```
>>> numbers = [100, 100, 100, 100]
>>> numbers = [x+1 for i, x in enumerate(list)]
>>> numbers
[98, 98, 98, 98]
```

As you see, this increments all items the same.

---

### Post by ghostdog74 on 2008-02-21
You seems to just run code blindly without understanding how they work. I would suggest you read up on how enumerate works,[ here]("http://docs.python.org/tut/node7.html"). Look under 5.6.  After that, you will know why x+1 is wrong.

---

### Post by sp0nge on 2008-02-21
It is blind to some degree because I am quite new to programming. Though I did try to solve this problem on my own before going to the forums for exactly this reason- people in the forums have a tendancy to flame users who are simply having difficulty. 

I was simply commenting that the code suggested was not working, when the code I have been playing with is more accurate to my purpose. 

In any event, I've solved this problem:

```

>>> myList = [100, 100, 100, 100, 100]
>>> myOtherList = [list[i-1]+i for i in range(len(list))]
>>> myOtherList
[97, 98, 99, 100, 101]

```

I will follow your suggestion, ghostdog74, to understand the enumerate function a little better. I'll be interested to see if I can find an alternative method to accomplish this goal using it.

---

### Post by pmasiar on 2008-02-21
It is of course nitpicking but Python code standards suggest using lowercase with underscore for variables: my_list, my_other_list etc. CamelCase is for classnames. Just FYI, so you don't have to unlearn bad habits, if you decide later to go with standards.

---

### Post by sp0nge on 2008-02-24
I appreciate the input, I am new to the language and still working on the grammar.

---

