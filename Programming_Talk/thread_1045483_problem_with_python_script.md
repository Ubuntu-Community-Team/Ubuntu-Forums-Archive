---
title: "problem with python script"
date: 2009-01-20
forum: Programming Talk
---

### Post by laplace/d on 2009-01-20
this is my first python script (and my first script) so forget about the style... i'm trying to read the locations of some songs on a m3u playlist file and after that copying the songs in a folder...

```
#!/usr/bin/python

import shutil

def extloc(flines):
    flines = flines[1:]   
    length = len(flines)
    cont = 0
    loc = []
    for i in range(1,length,2):
        loc.append(flines[i])
    return loc


f = open('/home/simon/Desktop/boogie.m3u')
flines = f.readlines()
loc = extloc(flines)
for i in range(len(loc)):
    aux = loc[i]
    aux = aux[:-1]
    shutil.copy(aux,'home/simon/Desktop/boogie')
```

everything seem to work fine (the interpreter displays no error) and still, when i run it, no file is copied to the folder.

---

### Post by Joeb454 on 2009-01-20
Moved to Programming Talk

---

### Post by snova on 2009-01-20
Perhaps a missing slash in the pathname where you move the files to?

'home/simon' -> '**/**home/simon'.

Also, is **aux[:-1]** used to remove the trailing newline? There's an easier way, **aux.strip()**.

Additionally, this is more complicated than necessary:

```
for i in range(len(loc)):
    aux = loc[i]
    aux = aux[:-1]
```

Instead, why not just iterate over the list itself?

```
for aux in loc:
    aux = aux.strip()
```

Note that I may not have actually fixed the bug, since I don't entirely understand your script...

---

### Post by ssam on 2009-01-20
a good way to debug something like this is to put in some out put.eg before you do
```
shutil.copy(aux,'home/simon/Desktop/boogie')
```
put a line
```
print "aux =",aux 
```
if the code is working correctly then this should print the original locations of of all the files. if prints nothing at all you might suspect that ```
loc
``` is empty, so print out ```
loc
```.

work back until you find where what the code is actually doing deviates from what you think/want it to do.

another shortcut for your code
instead of doing
```

for i in range(len(loc)):
    print loc[i]

```
use
```

for this_loc in loc:
    print this_loc

```

you can do the same to read the file a line at a time (to save you having to read a whole file into memory)

```

for line in open(filename):
    process(line)

```

---

### Post by laplace/d on 2009-01-21
thanx!, the problem was the location was wrong, i forgot the first '/' before 'home' (duh!)... 
regarding this piece of code piece of code:

```
for aux in loc:
    aux = aux.strip()
```

isn't the method 'strip' only for lists?... i tried what u suggested using strip and it doesn't work.

---

### Post by snova on 2009-01-21
> **laplace/d said:**
> thanx!, the problem was the location was wrong, i forgot the first '/' before 'home' (duh!)... 
regarding this piece of code piece of code:

```
for aux in loc:
    aux = aux.strip()
```

isn't the method 'strip' only for lists?... i tried what u suggested using strip and it doesn't work.

The opposite actually, it's only for strings.

---

### Post by laplace/d on 2009-01-22
cool man, thanx, i forgot something again, thats why it wasn't working. 
i forgot to write
```
for aux in loc:
```

---

