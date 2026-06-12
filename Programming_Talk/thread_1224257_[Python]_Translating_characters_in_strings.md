---
title: "[Python] Translating characters in strings"
date: 2009-07-27
forum: Programming Talk
---

### Post by amiga_os on 2009-07-27
In Python is there a "correct" way to do this?  Rather than writing my own function?

```
def translate(string, from_list, to_list):
	for char in string:
		for index, value in enumerate(from_list):
			if value == char:
				char = to_list[index]
```

The string translate method wouldn't work for my purposes here.  It only translates from one char to one char... I want to translate all instances of, say, '\n' to r'\n'.

---

### Post by benj1 on 2009-07-27
what about replace()?

```
str = 'hello world'
str = str.replace('l','x')
```


for anything more advanced you would probably have to look at the re module.

---

### Post by amiga_os on 2009-07-27
That does one item at a time.

I want to replace a list of tokens with a corresponding list of tokens.

---

### Post by crownedzero on 2009-07-27
If your doing what it is I think you're trying to do can't use just set up and dictionary and use keys to change out values?

---

### Post by benj1 on 2009-07-27
```
for lines in text:
    lines.replace('foo','bar')
    lines.replace('hello','world')
    lines.replace('\n','\r\n')

```

and so on.

if you have to replace lots of things, a dictionary might work but not with new line characters etc.
maybe a list of lists or a dict of lists
```
listoflist = [['foo','bar'],['hello','world']]
for lines in text: 
    for entry in listoflist:
        lines = lines.replace(entry[0],entry[1])

```
is that what youre after?

---

### Post by unutbu on 2009-07-27
[PHP]#!/usr/bin/env python
import string
s='abracadabra'
from_list='abcdr'
to_list='?*!@|'
print s.translate(string.maketrans(from_list,to_list)), 
# ?*|?!?@?*|?
[/PHP]

---

