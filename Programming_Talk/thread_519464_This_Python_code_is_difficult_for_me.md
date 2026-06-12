---
title: "This Python code is difficult for me"
date: 2007-08-07
forum: Programming Talk
---

### Post by mocqueanh on 2007-08-07
```

girls = ['alice', 'bernice', 'clarice']
boys = ['chris', 'arnold', 'bob']
letterGirls = {}
for girl in girls:
    letterGirls.setdefault(girl[0], []).append(girl)
print [b+'+'+g for b in boys for g in letterGirls[b[0]]]

```

letterGirls is a dictionary, and i think diction doesnt have append method
And i dont know what is **letterGirls[b[0]]**

*P/S: I feel since i was member here, i ask too much, this code comes from my book: Beginning Python, the author of book is good coder, but his skill of teaching is not good, many example coding in book that i have read (i've read the chapter: Conditional, this code  in that), he put some functions, statements that he hasnt teach me yet. I am reading book to learn without teacher, so sorry if  you think i ask you too much :popcorn:*

---

### Post by ghostdog74 on 2007-08-07
if you don't understand certain statements in Python, you can print them out
```

girls = ['alice', 'bernice', 'clarice']
boys = ['chris', 'arnold', 'bob']
letterGirls = {}
for girl in girls:
    print "girl is: ",girl
    letterGirls.setdefault(girl[0], []).append(girl)
    for key,value in letterGirls.iteritems():
        print "key: ",key
        print "value: ", value
    raw_input("Press key: ")
print [b+'+'+g for b in boys for g in letterGirls[b[0]]]

```

---

### Post by strider1551 on 2007-08-07
Wow.  Well I think I know what's going on, so let's give this a shot.  There are two lines which are complicated, so let's look at each one individually.

```
letterGirls.setdefault(girl[0], []).append(girl)
```
What you need to understand here is setdefault().  You can read the standard library documentation for its explanation but here's mine:  if girl[0] exists, then work with that.  If it doesn't exist, make it an empty dictionary.  So it could be seen as an abbreviated form of:
```

if girl[0] in letterGirls:
    letterGirls[girl[0]].append(girl)
else:
    letterGirls[girl[0]] = []
    letterGirls[girl[0]].append(girl)

```
girl[0] is the first character in the string girl.  So if girl is "alice", letterGirls[girl[0]] is no different from letterGirls["a"]

The second difficult line is
```
print [b+'+'+g for b in boys for g in letterGirls[b[0]]]
```
This is called a list comprehension.  A google search should get some good tutorials. Basically it is a compression of:
```

tmp = []
for b in boys:
    for g in letterGirls[b[0]]:
        tmp.append(b+'+'+g)
print tmp

```

---

### Post by pmasiar on 2007-08-07
> **mocqueanh said:**
> 

letterGirls is a dictionary, and i think diction doesnt have append method

this code comes from my book: Beginning Python, the author of book is good coder, but his skill of teaching is not good, many example coding in book that i have read (i've read the chapter: Conditional, this code  in that), he put some functions, statements that he hasnt teach me yet. I am reading book to learn without teacher,

learning without a teacher to show you simple tricks is hard.

Before writing code in file, you can (and should) try little snippets in python shell. Python shell is one of the best features, use it to the full!

ie how to find if a dictionary has "append" method: enter in the shell, like in IDLE:
```


dd = {} # create a dictionary
dir(dd) # check all the method of object dd (no append available)
help(dd.setdefault) # get help (docstring) for dictionary's method setdefault


```

HTH, with these little tricks learning Python is a snap: just create an object you need, check it's methods, read docs, and try them - all interactively from commandline.

Also, bookmark this: [http://docs.python.org/lib/lib.html](http://docs.python.org/lib/lib.html)

---

### Post by gtcoffee on 2007-08-07
```
for girl in girls:
    letterGirls.setdefault(girl[0], []).append(girl)
```

why don't just put girl into second argument of setdefault, same result tho:
```
for girl in girls:
    letterGirls.setdefault(girl[0], girl) 
```

and i c the trick for append() here...
yeah dictionary doesn't has append(), but here append is for the second argument of setdefault(first, second),
you may append more value to the key, so append is there u go..
```
 letterGirls.setdefault('a', []).append('test1')
output:  {'a': ['test1'] }

letterGirls.setdefault('a',[]).append('test2')
output: {'a': ['test1', 'test2'] }

#nothing change
letterGirls.setdefault('a','test3')
output: {'a': ['test1', 'test2'] }'
```

---

### Post by pmasiar on 2007-08-07
> **strider1551 said:**
> 
```
letterGirls.setdefault(girl[0], []).append(girl)
```
... if girl[0] exists, then work with that.  If it doesn't exist, make it an empty dictionary. 

Correct. Of course you intended to write "empty list". [] is a list, {} is dictionary.

setdefault(key, []).append() is very idiomatic use of Python: create a dictionary with given key (first character of girl's name) and value is a *reference to a list* (of names in our case).

When key does not exists, setdefault returns empty list, to which name is appended. So append() is a method of the list (value from dictionary), not the dictionary itself.

Another often-used idiom is in the play: method chaining. It means results of a method is not assigned to a variable, but immediately used with another method (of the result), like:

```

# replace , with + and uppercase: uppercase a string, then split it on commas (to a list), and join back using '+' sign, 
text = '+'.join('a,b,c,d'.upper().split(','))

```

---

### Post by pmasiar on 2007-08-07
> **gtcoffee said:**
> 
why don't just put girl into second argument of setdefault, same result tho:


Not so. Original value is reference to a list (of all names). Your variant will replace name every time, result will be last name encountered.

---

