---
title: "[Python] Need help counting changes in program"
date: 2008-10-23
forum: Programming Talk
---

### Post by mhoy06 on 2008-10-23
I have the following program and it works, but I would like it to tell me how many times it replaced the text:
[PHP]
search = raw_input("Type what you want to search for: ")
replace = raw_input("Type what you want to replace it with: ")
inputFile = file('test.txt', 'r')
data = inputFile.read()
inputFile.close()
data = data.replace(search, replace)
outputFile = file('test.txt', 'w')
outputFile.write(data)
outputFile.close()
[/PHP]

Can somebody show me how to count the number of times (search) has been replaced?

---

### Post by nvteighen on 2008-10-23
Maybe, instead of immediately overwriting data by data.replace(), you could save it elsewhere, compare it to data and then overwrite.

Just my € 0.02

---

### Post by fiddler616 on 2008-10-23
I had to make a program to find and replace --and wasn't told about data.replace, so what I did was make a dictionary with the replacements as keys and the search terms as values, and then:
[PHP]
counter = 0
for i, j in the_dictionary.iteritems(): #Obviously replace the_dictionary with whatever you call it
    counter += 1
    output = output.replace(i, j)
[/PHP]

I'm sorta new to this--expect somebody to come down from the skies and say that's not Pythonic, but it's the best I can do for now...at least it works :)

---

### Post by nvteighen on 2008-10-23
> **fiddler616 said:**
> 
I'm sorta new to this--expect somebody to come down from the skies and say that's not Pythonic, but it's the best I can do for now...at least it works :)

It's very canonical Python code. Non-Pythonic would be looping using range() (loops à la C)

---

### Post by fiddler616 on 2008-10-23
> **nvteighen said:**
> It's very canonical Python code. Non-Pythonic would be looping using range() (loops à la C)
That just made my day
To the OP: [Here's]("http://python.tmac.andrewmin.com/raw/whirlpoolvone.txt") *my* program, that implements it in context--sometimes it's nice seeing something larger than snippets. Although you shouldn't need to :)...

---

### Post by damoxc on 2008-10-23
This should do it.
```

search = raw_input("Type what you want to search for: ")
replace = raw_input("Type what you want to replace it with: ")
inputFile = file('test.txt', 'r')
data = inputFile.read()
inputFile.close()
count = 0
while search in data
    data = data.replace(search, replace, 1)
    count += 1
outputFile = file('test.txt', 'w')
outputFile.write(data)
outputFile.close()

```

I'm fairly sure the previous example wasn't actually counting the number of times the search string was replaced, just counting the number of search and replaces occured.

---

### Post by mhoy06 on 2008-10-23
> **damoxc said:**
> This should do it.
```

search = raw_input("Type what you want to search for: ")
replace = raw_input("Type what you want to replace it with: ")
inputFile = file('test.txt', 'r')
data = inputFile.read()
inputFile.close()
count = 0
while search in data
    data = data.replace(search, replace, 1)
    count += 1
outputFile = file('test.txt', 'w')
outputFile.write(data)
outputFile.close()

```

I'm fairly sure the previous example wasn't actually counting the number of times the search string was replaced, just counting the number of search and replaces occured.

Thanks, this works. Only thing missing is the : in "while search in data" other than that it seems to work perfectly, thanks. And thanks for all the replies, this forum seems to be a good place to go for python help.

---

### Post by ghostdog74 on 2008-10-23
```

import re
search = raw_input("Type what you want to search for: ")
replace = raw_input("Type what you want to replace it with: ")
inputFile = file('file', 'r')
data = inputFile.read()
inputFile.close()
data,num=re.subn( search,replace,data)
print num
print data

```

---

### Post by damoxc on 2008-10-24
> **ghostdog74 said:**
> ```

import re
search = raw_input("Type what you want to search for: ")
replace = raw_input("Type what you want to replace it with: ")
inputFile = file('file', 'r')
data = inputFile.read()
inputFile.close()
data,num=re.subn( search,replace,data)
print num
print data

```

Probably want to add some regex escapes to the search string otherwise some funky things may happen.

---

### Post by ghostdog74 on 2008-10-24
> **damoxc said:**
> Probably want to add some regex escapes to the search string otherwise some funky things may happen.

i will leave that for the OP.

---

### Post by mhoy06 on 2008-10-24
> **ghostdog74 said:**
> ```

import re
search = raw_input("Type what you want to search for: ")
replace = raw_input("Type what you want to replace it with: ")
inputFile = file('file', 'r')
data = inputFile.read()
inputFile.close()
data,num=re.subn( search,replace,data)
print num
print data

```

Thanks Ghostdog. Your name seems familiar do you also post on python-forum.org?

---

### Post by ghostdog74 on 2008-10-24
> **mhoy06 said:**
> Thanks Ghostdog. Your name seems familiar do you also post on python-forum.org?

yes.

---

