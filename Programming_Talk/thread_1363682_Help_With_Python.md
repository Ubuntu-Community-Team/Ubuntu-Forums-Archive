---
title: "Help With Python"
date: 2009-12-24
forum: Programming Talk
---

### Post by HalfEmptyHero on 2009-12-24
I am learning python and am trying to write a script that will combine multiple plain text files into one. I have this so far:

```

#!/usr/bin/env python
# -*- coding: utf-8 -*-

import sys
inp = sys.argv[1]
outp = sys.argv[2]

def manComp(inFile, outFile):
  running = True
  inOp = open(inFile, 'r')
  outOp = open(outFile, 'w')
  while running:
    rl = inOp.readline()
    if len(rl) == 0:
      running = False
    outOp.write(rl)
  outOp.close()
  inOp.close()

manComp(inp, outp)    


```

This works so far with reading one file and writing to another, but how would I go about making it read from multiple files and write to the same file? In other words, with the script as I have it, i type in ```
python program.py input output
``` and what I want to be able to do is ```
python program.py input1 input2 input3 -o output
```

This is my first time using sys.argv so I don't know how to do that.

---

### Post by CptPicard on 2009-12-24
```

# -*- coding: utf-8 -*-
import sys
from itertools import chain

def pycat(infiles, out="default-out.txt"):
  outfile = open(out, "w")
  for line in chain(*[open(x,'r') for x in infiles]):
    outfile.write(line)
  outfile.close()


pycat(sys.argv[1:])
```

Then, read about OptionParser for the -o flag... :)

---

### Post by ghostdog74 on 2009-12-24
> **CptPicard said:**
> ```

....
  outfile = open(out, "w")

```

that should be "a" right?

---

### Post by ghostdog74 on 2009-12-24
```

import sys
o=open("out.txt","a")
for file in sys.argv[1:]:
    for line in open(file): 
         o.write(line)
o.close()

```

---

### Post by Can+~ on 2009-12-24
[PHP]#!/usr/bin/env python
#encoding: utf-8

from fileinput import FileInput

# All files to be read
readfiles = ["file00.txt", "file01.txt"]

# Open a file to output everything
outputfile = open("out.txt", "a")

# Put it on a stream
allfiles = FileInput(readfiles)

for line in allfiles:
	outputfile.write(line)[/PHP]

Using the fileinput module to put things on a stream. Similar to CptPicard's approach.

---

### Post by CptPicard on 2009-12-24
> **ghostdog74 said:**
> that should be "a" right?

Depends on the desired behaviour... perhaps. And yes, perhaps yours is clearer ;) Can't help my love for functional idioms... :p

> **Can+~ said:**
> 
Using the fileinput module to put things on a stream.

Wow, that was new to me. Neat.

---

### Post by ghostdog74 on 2009-12-24
good to know FileInput can be used, however, it runs slower than normal file iteration using for loop

---

### Post by HalfEmptyHero on 2009-12-27
Thanks for the suggestions guys, they've been very helpful. And I'll go ahead and read up on OptionParser

---

