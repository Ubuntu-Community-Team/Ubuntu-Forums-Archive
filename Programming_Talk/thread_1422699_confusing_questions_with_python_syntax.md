---
title: "confusing questions with python syntax"
date: 2010-03-05
forum: Programming Talk
---

### Post by XXMy_Little_ShinigamiXX on 2010-03-05
hi, i was wondering abotu some of the formats being used in the python tutorial, i have figured out some of what the code is trying to say, but not all of it as it still throws me off. 
```

>>> table = {'Sjoerd': 4127, 'Jack': 4098, 'Dcab': 8637678}
>>> print ('Jack: {0[Jack]:d}; Sjoerd: {0[Sjoerd]:d}; '
...        'Dcab: {0[Dcab]:d}'.format(table))
Jack: 4098; Sjoerd: 4127; Dcab: 8637678

```

in this format there is the letter D after the : sign. and why is the 
zeros there this is such a confusing format. lol

```

>>> table = {'Sjoerd': 4127, 'Jack': 4098, 'Dcab': 8637678}
>>> print 'Jack: {Jack:d}; Sjoerd: {Sjoerd:d}; Dcab: {Dcab:d}'.format(**table)
Jack: 4098; Sjoerd: 4127; Dcab: 8637678

```

this is supposed to have been the same thing but with the 2 ** signs 
instead. 


```

>>> table = {'Sjoerd': 4127, 'Jack': 4098, 'Dcab': 7678}
>>> for name, phone in table.items():
...     print '{0:10} ==> {1:10d}'.format(name, phone)
...
Jack       ==>       4098
Dcab       ==>       7678
Sjoerd     ==>       4127

```

this source code is an interesting one as well because when i use the D
here it doesnt work lol. i have to type;

print '{0:10}  ==>  {1:10}'.format(name, phone)

what are the 10s being used for in that format? i think the 0, 1 are 
being used to the name, phone format am i right? but im lost as to what 
the 10s are and why on earth they have a D after the 10, {1:10d}

thank you :popcorn:

---

### Post by Bachstelze on 2010-03-05
[http://docs.python.org/3.1/library/string.html#formatstrings](http://docs.python.org/3.1/library/string.html#formatstrings)

> **XXMy_Little_ShinigamiXX said:**
> hi, i was wondering abotu some of the formats being used in the python tutorial, i have figured out some of what the code is trying to say, but not all of it as it still throws me off. 
```

>>> table = {'Sjoerd': 4127, 'Jack': 4098, 'Dcab': 8637678}
>>> print ('Jack: {0[Jack]:d}; Sjoerd: {0[Sjoerd]:d}; '
...        'Dcab: {0[Dcab]:d}'.format(table))
Jack: 4098; Sjoerd: 4127; Dcab: 8637678

```

in this format there is the letter D after the : sign. and why is the 
zeros there this is such a confusing format. lol

0 means the first parameter passed to the format method. d means to display the number as a decimall integer.

> **XXMy_Little_ShinigamiXX said:**
> what are the 10s being used for in that format? i think the 0, 1 are 
being used to the name, phone format am i right? but im lost as to what 
the 10s are and why on earth they have a D after the 10, {1:10d}

10 is the length of the field. If you do

```
>>> print('"{0:10}"'.format(50))
"        50"
```

You see that the space between the two double-quotes is 10 characters.

---

