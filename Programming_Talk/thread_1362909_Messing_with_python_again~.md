---
title: "Messing with python again~"
date: 2009-12-23
forum: Programming Talk
---

### Post by Atzu on 2009-12-23
Hello everyone! 

Hmm what I want to do with python now is to load a text file (and write to it). Like... I want that my little program save a list to a text file like this:

This is the text file:

```

1,2,3,4,5,6,7,8,9,0

```

And also I want that my program is able to load the file and add it to the list named "numbers".

I don't know how I can search that on the web, so I'd appreciate your help. Thank you very much, again.

---

### Post by geirha on 2009-12-23
Assuming that is the only line of the file, then this should do it:
```

>>> l = [int(x) for x in open('file.txt').read().split(',')]
>>> print l
[1, 2, 3, 4, 5, 6, 7, 8, 9, 0]
>>> open('file.txt','w').write(','.join(str(x) for x in l))

```

---

### Post by Atzu on 2009-12-23
May you explain what that code do please? :p

Oh btw i think i didnt explain myself very well... Those are not only numbers... I want to add also words and stuff like that.

---

### Post by Can+~ on 2009-12-23
[PHP]>>> l = [int(x) for x in open('file.txt').read().split(',')][/PHP]

This line can be "decomposed" into:

[PHP]
alist = []
with open('file.txt') as infile:
    for line in infile:
        alist.append(int(line.split(",")))[/PHP]

Meaning that, it will break the file into commas, and convert it into integers, then store it in an list, all done in a single line.

[PHP]>>> open('file.txt','w').write(','.join(str(x) for x in l))[/PHP]

Also, decomposing:

[PHP]
alist = [1, 2, 3, 4, 5]
with open('file.txt', 'w') as outfile:
    for number in alist:
        outfile.write(str(number))[/PHP]

Open the file in write mode, write to it a string conformed by all the elements 'x' inside the list 'l'.

---

### Post by geirha on 2009-12-23
Best way to learn is to read the documentation of each class/function/method.
```

>>> help(int)
>>> help(str)
>>> help(str.split)
>>> help(str.join)
>>> help(open)
>>> help(file.read)
>>> help(file.write)

```

[something for x in list] is called list comprehension. Read about it in the tutorial: [http://docs.python.org/tutorial/datastructures.html#list-comprehensions](http://docs.python.org/tutorial/datastructures.html#list-comprehensions)

---

### Post by Atzu on 2009-12-23
Hmm ok... this is what i have... I have a file named: Date.txt which is:

```
1/1/1,2/2/2,3/3/3,4/4/4,5/5/5
```

and here is what i use to read it:

```

Date = []
k = open('Date.txt')
for x in k:
	y = x.split(',')
	Date.append(y)
print Date

```

and this is what i get:
[['1/1/1', '2/2/2', '3/3/3', '4/4/4', '5/5/5\n']]

Is there a way to delete or that it won't add the \n and the other []'s?? i want it to look like this: 

['1/1/1', '2/2/2', '3/3/3', '4/4/4', '5/5/5']

Thanks for helping btw~

EDIT: Ok i noticed that is really wrong because its adding all the thing on the files as a single thing in the list... I'm really lost here... :/

---

### Post by jpkotta on 2009-12-24
You want str.split().  [http://docs.python.org/library/stdtypes.html#string-methods](http://docs.python.org/library/stdtypes.html#string-methods)

EDIT: Yeah, I meant str.strip() in addition to str.split().

---

### Post by nvteighen on 2009-12-24
Let's divide the problem.

1) To destructure the data from the file What you need is **just** str.split()... nothing else. That will generate the list for you by using the given token as a delimiter.

```

>>> k = "1/1/1,2/2/2,3/3/3,4/4/4,5/5/5"
>>> k.split(",")
['1/1/1', '2/2/2', '3/3/3', '4/4/4', '5/5/5']
>>> 

```

You can do the same with the contents of a file by looping the file. Looping a file will give you the file's lines one by one, and those are strings.

2) To add that data to a preexistant list, don't use list.append(). That method will add whatever you hand to it to the list and do nothing else. Use list.extend() which "flatens" lists.

```

>>> z = [8, 9]
>>> z_copy = [8, 9] # Doing it this way for educational purposes
>>> d = [7, 99]
>>> z.append(d)
>>> z
[8, 9, [7, 99]]
>>> z_copy.extend(d)
>>> z_copy
[8, 9, 7, 99]
>>> 

```

3) The writing issue is actually the reading procedure done backwards. There's where str.join() comes in, which, essentially reverts stuff done by str.split(). Look at the documentation to see how it works. With str.join() you'll get a string you can write into the file.

That's all there is. It's actually much simpler than it might look at the beginning.

---

### Post by Can+~ on 2009-12-24
As a tip, try to learn your tools, throughtoutly (is this a word?).

Everything in python are objects, and each object has "methods" and "attributes" (Object Oriented), therefore, anything in python will have a set of methods like:

[PHP]>>> astr = "astr"
>>> dir(astr)[/PHP]

Will show you everything inside that object. Then, with this in mind, you can see that is not necessary to assign things to variables to actually use the methods/attributes:

[PHP]>>> "Hello,comma,separated,world".split(",")
['Hello', 'comma', 'separated', 'world'][/PHP]

Now, the big idea of this, is that you can put them one after the other, the case of split, converts a **string** into a **list**, so now, the result of the splitted string, you can apply list methods, as it's now a list.

[PHP]>>> "Hello,comma,separated,world".split(",").pop()
'world'[/PHP]

*pop removes the last element*

So, to solve your problem, applying everything above, you want to convert this:

```
input: "1/1/1,2/2/2,3/3/3,4/4/4,5/5/5\n"
expected result: ['1/1/1', '2/2/2', '3/3/3', '4/4/4', '5/5/5']
```

Split already converts from string to list, so a simple **split**, probably with a **strip** to eliminate any annoying trailing \n or whitespace.

[PHP]>>> "1/1/1,2/2/2,3/3/3,4/4/4,5/5/5\n".strip().split(",")
['1/1/1', '2/2/2', '3/3/3', '4/4/4', '5/5/5'][/PHP]

Seek the documentation when you have doubts about a particular method. Both lists and strings are a sequence of objects:

[Operations over mutable sequences]("http://docs.python.org/library/stdtypes.html#typesseq-mutable") (lists for example)
[Operation over sequences]("http://docs.python.org/library/stdtypes.html#sequence-types-str-unicode-list-tuple-buffer-xrange") (strings, tuples...)
[String methods]("http://docs.python.org/library/stdtypes.html#string-methods")

Notice that strings are non-mutable sequence types. So you can apply all the operations listed on sequences and string methods, but not of mutable operations. Lists can use all the mutable and non-mutable operations.

---

