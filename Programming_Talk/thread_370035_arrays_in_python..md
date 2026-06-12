---
title: "arrays in python."
date: 2007-02-25
forum: Programming Talk
---

### Post by Choad on 2007-02-25
lol i typed "pythons in arrays" as the thread title. 

neway... i have googled this subject for ages, and i *still* dont really understand

python seems to have about half a dozen different array-like structures all offering slightly different things

could someone PLEASE kindly explain them to me. i am used to c-like languages. and to be entirely honest, its the one negative thing i have to say about python. also seems really messy with the use of ( and { and [ all over the place. i really want to say

ClassType myClassArray[10][10] = new ClassType(whatever)

how would i do that in python?

how would i then say

myClassArray[x][y].attribute = 5

??

thanks

---

### Post by ssam on 2007-02-25
lists store a list of things,you create them with [], you can access members with []
(these examples are made with a python console, open a terminal and type python)
```

>>> a_list = [2,4,6,8,10]
>>> a_list[2]
6
>>> a_list[2] = 7
>>> a_list[2]
7

```
tuples are just immutable lists

dictionaries store a mapping, create with {}, access with []
```

>>> a_dict = {0:2, 1:4, 2:6, 3:8, 4:10}
>>> a_dict[2]
6
>>> a_dict[2] = 7
>>> a_dict[2]
7
```

with a list you cannot add new members with []
```

>>> a_list = [2,4,6,8,10]
>>> a_list[5] = 12
Traceback (most recent call last):
  File "<stdin>", line 1, in ?
IndexError: list assignment index out of range

```
you must use
```
a_list.append(12)
```

dicts do not have this restriction.

you can make 2d lists or dicts
```
>>> a_list = [[1,2],[3,4],[5,6]]
>>> a_list[1]
[3, 4]
>>> a_list[1][0]
3
>>> a_dict ={0:{0:2,1:4},1:{0:3,1:5},2:{0:4,1:6}}
>>> a_dict[1][0]
3

```

all the above examples where with ints, but any other type will work. (except the indexes of lists must be ints).

using nested dicts to store strings your code might look like

```
>>> a_dict = {}
>>> a_dict[1] = {}
>>> a_dict[1][2] = "Ssam"
>>> a_dict[1][2].lower()
'ssam'
```

so there is the extra hassle of adding the inner dicts compared to c. the advantages are that you grow the dict to any size and mix types.

to use a list to do a similar thing you could initialise it with a loop

```

a_list = []
for x in xrange(10):
  a_list.append([])
  for y in xrange(10):
    a_list[x].append(0)
print a_list

```

if you are dealing with numbers the are libraries for making and using multidimentional arrays. see  [http://www.scipy.org/](http://www.scipy.org/)

---

### Post by Mirrorball on 2007-02-25
A list is like a C array.
```

li = [1, 2, 3] # create a list ([] for an empty one)
li[0] # output: 1
li[1] # output: 2
li[2] # output: 3
li[0] = 4

```
A tuple is like a list, but you can't change it after you create it.
```

tu = (1, 2, 3) # create a tuple
tu[0] # output: 1
tu[1] # output: 2
tu[2] # output: 3
tu[0] = 4 # won't work, will raise an exception

```
A dictionary is like a C++ std::map. It's an associative array.
```

d1 = {} # create an empty dictionary
d1['string'] = 1 # you can use any **immutable** object as an index
d1[tu] = 2 # such as a tuple
d1[0] = 3 # or a number
d1[li] # but not a list, this will raise an exception
d2 = {'Ubuntu': 'Linux', 'Python': 'Programming Language'}
d2['Ubuntu'] # output 'Linux'

```

---

### Post by Choad on 2007-02-25
ok cool, so how would i declare a 2d list of classes, 10x10, without writing 100 class names?

classArray = [[class, class, class, class, class, etc.][class, class, class, class, class, etc.] etc]

thats the bit i cant figure out :(

---

### Post by Mirrorball on 2007-02-25
```

li = [[class()] * 10] * 10

```

---

### Post by Choad on 2007-02-25
you have no idea how hard it has been to find that 1 line of code :)

thanks!

oh one more thing. 

li = [[class()] * 5] * 10

would li[5][10] be the last one, or would li[10][5] be the last one

wondering to get it in the correct x, y order. should it be *width, *height or *height, *width

---

### Post by Mirrorball on 2007-02-25
None, it would be li[9][4]. But li[-1][-1] would be even simpler.

---

### Post by Choad on 2007-02-25
ok, cool

now one more question, is there a way to iterate through the contents of a 2d list

for item in 2dlist:

that makes item in to a list containing all the rows, and it iterates through the columns. do i have to nest it

```

for list in 2dlist:
    for item in list:

```
or is there a better way?

---

### Post by ghostdog74 on 2007-02-25
take note that by creating 2d arrays like this
```

>>> alist = [[1]*2]*2
>>> alist
[[1, 1], [1, 1]]
>>> alist[1][1]=3 #only want to change one element
>>> alist
[[1, 3], [1, 3]] # not the desired result. 
>>>    

```

in this case , its better to create 2d arrays using for loop

---

### Post by Choad on 2007-02-25
:o

that sucks!

so how do i make a *usable* 2d array?

---

### Post by Mirrorball on 2007-02-25
OK, then.
```

li = [[None] * cols for i in range(rows)]
```

---

### Post by pmasiar on 2007-02-25
2d array is just an array which items are arays. Nothing more and nothing less. Not sure what you mean to be "usable". If you want, you may use list comprehension for create one or two dimensions of it, or loops, as you wish.

---

### Post by Requiem on 2007-02-26
lists multiplication produces copies of list contents but lists don't really store objects only references, so you are in fact multiplicating references, you can see this directly by checking their id like this:

>>> mylist = [object()] * 2
>>> id(mylist[0])
-1210272688
>>> id(mylist[1])
-1210272688

what you want is to make multiple calls the object's constructor (in this case the root object 'object' but any class name will do)

>>> mylist = [object() for x in range (2)]
>>> id(mylist[0])
-1210272688
>>> id(mylist[1])
-1210272680

do that multiple times to get multiple results like this:

>>> mylist = [
                      [object()
                        for x in range(50)
                      ] for x in range(100)
                     ]
>>> id(mylist[30][27])
-1210710920
>>> id(mylist[15][48])
-1210716816

you can of course wrap this in a function like this:

>>> Array2D = lambda the_class,width,depth: [[the_class() for x in range(depth)] for x in range(width)]
>>> mylist = Array2D(object,4,5)
>>> mylist[3][4] == mylist[-1][-1]
True

---

### Post by Choad on 2007-02-26
ok that makes a bit of sense. 

...still dont see why python doesnt do "normal" arrays. what could be simpler than a c-type array? they are damned usefult too.

anyhow, thanks for the help guys im sure i can sort it now

---

### Post by cwaldbieser on 2007-02-26
> **Choad said:**
> ok that makes a bit of sense. 

...still dont see why python doesnt do "normal" arrays. what could be simpler than a c-type array? they are damned usefult too.

anyhow, thanks for the help guys im sure i can sort it now

This library provides optimized arrays: [http://numpy.scipy.org/]("http://numpy.scipy.org/")

Another way you could do what you want is to specify the coordinates in a tuple and use a dictionary:

```

d = dict()
d[(1,7)] = 255
d[(3,5)] = 500

for x in range(10):
  for y in range(10):
    print d.get((x,y), 0)

```

There are advantages and disadvantages.  You don't have to initialize the dtata structure before inserting/updating the values.  However, you won't get an index error if you insert an index outside the bounds you want.  You can get a KeyError if you try to look up a coordinate that was not entered, but using dict.get() or dict.setdefault() can make that problem simpler to deal with.

If you are doing some serious number crunching, though, NumPy is recommended.

---

### Post by pmasiar on 2007-02-26
> **Choad said:**
> ...still dont see why python doesnt do "normal" arrays. what could be simpler than a c-type array? they are damned usefult too

Choad, you are learning new language, you need to learn idiomatic ways to do things in new language. It does not make sense to write C code in python syntax.

2d array is just a syntax sugar, which Python designers decided not to replicate. Also, C-way 2d array is easier to do if dimensions are fixed - not the case for Python. Your thinking in Python is still restricted by what is available in C, you are not using Python yet. many things are dynamic and you will learn how to use it to simplify your code.

Ie. in C when you handle dictionaries (associative arrays) you are tempted to check for existing key, to avoid exceptions. In python exceptions are given, so using it proactively makes your code faster:

```

try:   # using exceptions is faster
   dic[key] += value
except:
   dic[key] = value

if key in dic:  # checking for key is slower, because...
    dic[key] += value # it will check for exception (missing key) anyway
else:
    dic[key] = value

```

It might be not intuitive for C coder, but for Python is perfectly intuitive and proper way to code. Especially when you realize that in most cases, the if way will find the key (so exception will not fire) and only dic[key] += value will get executed.

So my advice is: embrace new language and new possibilities it allows you, don't limit your coding to what is possible in your old language. Pythol lists/arrays do not have to be homogenous, different object can be mixed with no problems if you need it.

If you need homogenous arrays and speed improvement which migt come with it, use numpy/numeric modules. And then you start asking - why o why C-style arryas are so inflexible?... and start coding in real Python :-)

---

