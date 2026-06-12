---
title: "sed and awk in a python script??"
date: 2010-11-04
forum: Programming Talk
---

### Post by rajan on 2010-11-04
I am having problems putting either a sed or an awk command in my python script. 

Using this script: 

```
import sys
import os

def splitter(y):
    fop = open(y,'w')
    fop.write('hello world\n')
    return fop

filehandl = splitter(sys.argv[1])

filehandl.write('now got here\n')

string1 = 'awk \'{ sub(/got here/,\"hot gere\"); print }\' '+filehandl.name+' > '+filehandl.name+'_2'

os.system(string1)

print string1

os.system('cat '+filehandl.name+'_2')
```

```
user@mirror15 [~/ClassicalMech/SphereSim] % python este.py atre
awk '{ sub(/got here/,"hot gere"); print }' atre > atre_2
```

This clearly isn't the way things should work. Instead of replacing the regexp in the file "atre" and putting the output into "atre_2", "atre_2" is simply an empty file. I will also note that this same thing happens with an equivalent implementation of sed.

The really confusing part is that when I print the command that python feeds the command line in the line:
```
os.system(string1)
```
and then I copy that printed string1 directly into my terminal, it does things as expected. 

The gist of this problem is that the same command does different things on the command line versus in the context of a python script. Even when I enter the python interpreter, I can do everything normally and everything works. The python script just doesn't want to work. Any ideas?

---

### Post by DaithiF on 2010-11-04
it does work, in the sense that the awk command is executed just fine.  the problem though is that the content you have written to your file is being buffered, so at the time you call out to os.system you have a 0-byte file being operated on.

either add a filehandl1.flush() or filehandl.close() (the latter if you're done writing to it), before you execute your system commands.

I suppose you know that you can probably do whatever you need to do within python rather than calling out to awk or sed?

---

### Post by rajan on 2010-11-04
> **DaithiF said:**
> 
either add a filehandl1.flush() or filehandl.close() (the latter if you're done writing to it), before you execute your system commands.


i read a bit about the buffer problem with sed/awk when they're not interactive, but i didn't know/understand anything about that. i was able to research a bit about it and now my script is working. much appreciated! 

> **DaithiF said:**
> 
I suppose you know that you can probably do whatever you need to do within python rather than calling out to awk or sed?

while researching the above, i saw some people saying the same thing -- that python can do sed/awk tasks. i didn't, however, see any examples of the search/replace function in python ("sub" in awk). do you know if such a thing exists? i would happily use python over sed/awk, if for no other reason than that it would eliminate an interface between programs.

---

### Post by DaithiF on 2010-11-05
> **rajan said:**
> 
while researching the above, i saw some people saying the same thing --  that python can do sed/awk tasks. i didn't, however, see any examples of  the search/replace function in python ("sub" in awk). do you know if  such a thing exists? i would happily use python over sed/awk, if for no  other reason than that it would eliminate an interface between  programs.
for simple string replacement:
```
x = 'got here'
y = x.replace('got', 'hot')
```

for regular expression-based replacement (for more complex cases) [B]re.sub
[/B]```
import re
x = 'got get git gun'
re.sub(r'g(.t)', r'h\1', x)
hot het hit gun'
```

---

### Post by rajan on 2010-11-05
> **DaithiF said:**
> for simple string replacement:
```
x = 'got here'
y = x.replace('got', 'hot')

import re
x = 'got get git gun'
re.sub(r'g(.t)', r'h\1', x)
hot het hit gun'
```

DaithiF, thanks for the reply. The functions you provided are very helpful.

---

