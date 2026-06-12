---
title: "Filtering by grep or sed in python"
date: 2009-09-22
forum: Programming Talk
---

### Post by ohssss on 2009-09-22
Is there a simple way to do filtering and replacing lines in a input file in python like those in grep or sed?

I have met this problem few times and it usually need few ten lines of python code. However, some combinations of grep/sed/awk can do the job quickly. I want to know is there some similar and simple way to do that in python. I am a bit new to python.

As an example, in the file 'test.txt':
"""
marker
start Hello-world-1
some_other_text
start Hello-world-2
marker
start Hello-world-3
marker
"""

The output should be a list of words after the marker line with duplicated middle part:
Hello-world--world-1
Hello-world--world-3

This can be done by the command:
cat 'test.txt' | grep -A1 marker | grep start | sed 's/^B\s*//g' | sed 's/-.*-/&&/g'

---

### Post by Bachstelze on 2009-09-22
> **ohssss said:**
> I want to know is there some similar and simple way to do that in python.

Not that I know of. That's why we have sed and awk. ;)

---

### Post by unutbu on 2009-09-22
[PHP]#!/usr/bin/env python
import os
import re
filename='test.txt'
fh1=open(filename)
fh2=open(filename)
fh2.next()
for line1,line2 in zip(fh1,fh2):
    if line1.find('marker')>-1 and line2.find('start')>-1:
           astr=re.sub('-(.*)-',r'-\1--\1-',line2)
           print astr,
[/PHP]
yields
```

start Hello-world--world-1
start Hello-world--world-3
```

fh1 and fh2 are two filehandles to the same file.
fh2.next() reads (and discards) one line of the file. So when you
go through the for-loop, 
```

for line1,line2 in zip(fh1,fh2):
```

line1 gets a line of the file and line2 gets the succeeding line.

---

### Post by DaithiF on 2009-09-22
definitely easier in sed :)
```
sed -n '/^marker/{n;s/^start //;s/-.*-/&&/g;p}' testfile
```

---

### Post by ohssss on 2009-09-22
> **Bachstelze said:**
> Not that I know of. That's why we have sed and awk. ;)

I also prefer to use sed and awk style, so I expect that python should have some modules accepting these inputs. :)
In this case, are you suggesting me to use the system call in python and parse the outputs?


> **unutbu said:**
> fh1 and fh2 are two filehandles to the same file.

Opening file twice seems a bit strange to me. Also, shifting the lines in this way is not very fixable for similar problem. Anyway, I get a better idea of using regex in python. Your code is simpler than what I have thought before. Thanks.


> **DaithiF said:**
> definitely easier in sed :)


Yup, it works, but assigning different filter to different parts is much clearer for me. Also, your output has one more line at the end ;)

---

### Post by ghostdog74 on 2009-09-22
> **unutbu said:**
> [PHP]#!/usr/bin/env python
import os
import re
filename='test.txt'
fh1=open(filename)
fh2=open(filename)
fh2.next()
for line1,line2 in zip(fh1,fh2):
    if line1.find('marker')>-1 and line2.find('start')>-1:
           astr=re.sub('-(.*)-',r'-\1--\1-',line2)
           print astr,
[/PHP]
yields
```

start Hello-world--world-1
start Hello-world--world-3
```

fh1 and fh2 are two filehandles to the same file.
fh2.next() reads (and discards) one line of the file. So when you
go through the for-loop, 
```

for line1,line2 in zip(fh1,fh2):
```

line1 gets a line of the file and line2 gets the succeeding line.

no need to open 2 file handles and the regex should be compiled for efficiency
```

import re
pat=re.compile('-(.*)-')
f=0
for line in open("file"):
    line =line.strip()
    if "marker" in line: f=1;next
    if f and "start" in line:
        print pat.sub(r'-\1--\1-',line)
        f=0

```

---

### Post by unutbu on 2009-09-22
> **ghostdog74 said:**
> no need to open 2 file handles and the regex should be compiled for efficiency
```

import re
pat=re.compile('-(.*)-')
f=0
for line in open("file"):
    line =line.strip()
    if "marker" in line: f=1;next
    if f and "start" in line:
        print pat.sub(r'-\1--\1-',line)
        f=0

```
I agree that opening 2 file handles is not necessary. 

Not sure if this is important to the OP, but that solution will match
the first line that contains "start" and which comes after a line containing the word "marker", whereas grep -A1 would only match lines that contain "start" which follow immediately after a line containing "marker".

Yet a third alternative is to use a ring buffer:
[PHP]
#!/usr/bin/env python
import re
filename='test.txt'

class RingBuffer(list):
    def __init__(self,length,*args):
        super(RingBuffer,self).__init__(args[:length])
        self.length=length
    def append(self,x):
        if self.length>0:
            if len(self)>=self.length:
                self.pop(0)
            list.append(self,x)

ring=RingBuffer(2)
pat=re.compile('-(.*)-')
for line in open(filename):
    ring.append(line)
    if len(ring)>1 and "marker" in ring[0] and "start" in ring[1]:
        print pat.sub(r'-\1--\1-',ring[1]),[/PHP]
Using a ring buffer would make it easy to generalize to situations where you want something like grep -A n for any n.

---

### Post by ghostdog74 on 2009-09-23
> **unutbu said:**
> 
 but that solution will match
the first line that contains "start" and which comes after a line containing the word "marker".

well, its certainly easy to change it to check whether "start" is the first word by using startswith().

---

### Post by unutbu on 2009-09-23
No, what I meant was if test.txt looked like this:
```

marker
some_other_text
start Hello-world-1
start Hello-world-2
marker
start Hello-world-3
marker

```
Then 
```

grep -A1 marker test.txt | grep start | sed 's/-.*-/&&/g'
```

returns
```

start Hello-world--world-3
```

while your program returns
```

start Hello-world--world-1
start Hello-world--world-3
```

---

### Post by ghostdog74 on 2009-09-23
> **unutbu said:**
> No, what I meant was if test.txt looked like this:
```

marker
some_other_text
start Hello-world-1
start Hello-world-2
marker
start Hello-world-3
marker

```
well, of course if it looks like this, things will be different. but i guess only OP knows how his file format will be like.

[quote]
```

grep -A1 marker test.txt | grep start | sed 's/-.*-/&&/g'
```

i won't even bother using grep + sed... its ugly and too much pipes. i will use awk instead, as always. :)

---

