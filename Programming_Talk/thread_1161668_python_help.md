---
title: "python help"
date: 2009-05-16
forum: Programming Talk
---

### Post by flyingsliverfin on 2009-05-16
im a complete newbie at python (only been using it for about 2 months and am not very devoted to learning, im too busy, and i think im rushing through A Byte of Python (my turorial))

im my code I have tried to combine what I learned just then, but i get some error messageI can't figure out :(. can some1 tell me whats wrong with it? (I just need to know)


listnow = ['a','b']
listlater = ['(c','(d']

print 'my lists are',listnow,listlater,'\nnow my list is',listnow,'\nlater it is',listlater
print '\nin 10 minutes I will finish',listnow[0],'\n then I will have to',listlater[0]
del listnow[0]
listnow.append(listlater)
del listlater
print 'my lists are now',listnow,listlater

---

### Post by Xarver on 2009-05-17
Sorry, be we can't help you if you don't do these things:

1. Use **CODE** tags! We need readable code...
2. Paste the _**EXACT**_ error.

After you do these things than we'll happily help you.

---

### Post by Martin Witte on 2009-05-17
> **flyingsliverfin said:**
> i get some error messageI can't figure out :(. can some1 tell me whats wrong with it? (I just need to know)


I copied / pasted your code in a text file and let the Python interpreter run that, then I get:```

      1 #!/usr/bin/env python
      2 listnow = ['a','b']
      3 listlater = ['(c','(d']
      4 
      5 print 'my lists are',listnow,listlater,'\nnow my list is',listnow,'\nlater it is',listlater
      6 print '\nin 10 minutes I will finish',listnow[0],'\n then I will have to',listlater[0]
      7 del listnow[0]
      8 listnow.append(listlater)
      9 del listlater
     10 print 'my lists are now',listnow,listlater
~
``` (I turned line numbering on in vi)

The output I get:
```
my lists are ['a', 'b'] ['(c', '(d'] 
now my list is ['a', 'b'] 
later it is ['(c', '(d']

in 10 minutes I will finish a 
 then I will have to (c
my lists are now ['b', ['(c', '(d']]
Traceback (most recent call last):
  File "./test.py", line 10, in <module>
    print 'my lists are now',listnow,listlater
NameError: name 'listlater' is not defined

```
The error you get says 'listlater' is not defined in line 10, which makes sense, because in line 9 you deleted that object

---

### Post by StunnerAlpha on 2009-05-17
If you want to delete one element of listlater use:
```

del listlater[i]

```
Where "i" is an index value (like 0 or 1) that corresponds to a certain element in the list.

---

### Post by flyingsliverfin on 2009-05-20
ooook. thx all

---

