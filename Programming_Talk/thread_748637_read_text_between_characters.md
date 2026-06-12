---
title: "read text between characters"
date: 2008-04-07
forum: Programming Talk
---

### Post by cmat on 2008-04-07
What is a good way to split a string between two characters in Python?

For instance I have text in between two brackets and I would like make the text a variable in my program. Sometimes it may be multi-lined like this:

```
ID (
stuff
stuff
stuff
)
```

What would be the best way to do this without using regular expressions?

---

### Post by tseliot on 2008-04-07
You could read() the text into a string and use find(), however I would use "re" and readlines().

EDIT: but of course it also depends on the text you're dealing with.

---

### Post by Can+~ on 2008-04-07
well, if it's multilined, you could start off with a splitlines (which is a glorified split(" ")).

I notice most people is fan on splitting, then slicing the array on sections when needed.

[PHP]a = \
"""
1 (
widget
widgetx
widget
)

2 (
stuff 
stuff
stuffx
)"""

b = a.splitlines()
print b[/PHP]

Produces this:
```
['1 (', 'widget', 'widgetx', 'widget', ')', '', '2 (', 'stuff ', 'stuff', 'stuffx']
```

The thing is the way the data is distributed on the file. If it's a kind of storage system you're building there, then you should be consistent, and for instance, notice I added an empty line between 1 and 2, therefore, you could use as a split point. Then split and slice as needed with an iteration.

Another part of my mind is shouting "USE REGULAR EXPRESSIONS!, they work in any case!" but you don't want them :(.

---

### Post by cmat on 2008-04-07
I'm still trying to grasp the concept behind "re". But here is the actual file I'm trying to parse. It's sort of like a database I'm building for a program. 

```
%[1] {
	var1="hello",
	var2="good bye" }

%[2] {
	var1="hi",
	var2="bye" }

```

The file is going to be pretty big so recursion would be in order. The last ting I would want to do is write the subroutine in C. Then I would have to cross-compile everything since I'm using this app on Windows too.

---

### Post by Can+~ on 2008-04-07
Wouldn't be easier to use a database for that, like, sqlite3 that uses a file as a "database" and let's you use sql syntax to add and retrieve data?

Anyway, I'll post a solution with regexps later, I usually like to test them a lot before posting.

*edit: finished*
```

import re

a = \
"""
%[1] {
	var1="hello",
	var2="good bye" }

%[2] {
	var1="hi",
	var2="bye" }

%[3] {
	var1="lala",
	var2="word word"
	var3="look ma I'm a variable"}
"""

regexp = r"(\d)=\"([\w,.'_ ]+?)\"|\d"

pattern = re.compile(regexp, re.I)

result = pattern.finditer(a)

if result:
	for i in result:
		print i.group()
else:
	print "No matches found"
```

Output:
```
1
1="hello"
2="good bye"
2
1="hi"
2="bye"
3
1="lala"
2="word word"
3="look ma I'm a variable"
>>> Exit Code: 0
```

Now, I'm guessing, even with regular expressions returning iterators, using sqlite3 is far faster.

---

### Post by cmat on 2008-04-07
Thanks for that. I may have to go the SQLite route but I will need this for future reference for other programs. Greatly appreciated.

---

### Post by pmasiar on 2008-04-07
cmat, if you can modify your file a little, it looks very close to syntactically correct dictionary:

```

%[1] {
	var1="hello",
	var2="good bye" }

#can be changed to 
d = []

d[1] = dict(
	var1="hello",
	var2="good bye" )
# etc.

```

Then, all you need is eval() the text, list of dictionaries will be created for you. To access valeus, you use d[1]['var1'] # has value "hello". No databases needed. Will it work?

---

### Post by ghostdog74 on 2008-04-07
> **cmat said:**
> What is a good way to split a string between two characters in Python?

For instance I have text in between two brackets and I would like make the text a variable in my program. Sometimes it may be multi-lined like this:

```
ID (
stuff
stuff
stuff
)
```

What would be the best way to do this without using regular expressions?

the algorithm is to set flags...something like this. of course you also can use splits like others have mentioned.
```

f=0
for lines in open("file"):
    if lines.startswith(")"): f=0
    if "ID (" in lines:        
        f=1
        continue
    if f: print lines.strip()
    

```
output:
```

 # ./test.py
stuff
stuff
stuff


```

if you are more familiar with regexp next time, 
```

import re
pat=re.compile("ID \((.*?)\)",re.M|re.DOTALL)
data=open("file").read()
print pat.findall(data)

```
output:
```

# ./test.py
['\nstuff\nstuff\nstuff\n']

```

---

