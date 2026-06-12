---
title: "[SOLVED] How can I make a script that does..."
date: 2008-12-19
forum: Programming Talk
---

### Post by dwally89 on 2008-12-19
Hi,

Please could someone tell me how to make a script (in Python) that does:

1. Load each line of file X into an array
2. Load each line of file Y into an array
3. For each line in arrayX, go through arrayY, and if it is found, add this line to arrayZ.
4. Write out arrayZ to a new file.

Thanks

---

### Post by Tony Flury on 2008-12-19
If lines are duplicated (either in X or Y) what do you want it to do then ?

if you don't care about duplication - then look at sets. Sets have a nice operator, called intersect, which will produce a new set which contain all the entries that are two sets the you apply the operation too.

If you do care about duplication, then you will need to use a list (the nearest that Python has to an array. Reading files into a list is trivial in python.

Take a look at [http://docs.python.org/index.html](http://docs.python.org/index.html) - loads of information in there about sets, lists and reading files.

---

### Post by rzrgenesys187 on 2008-12-19
Not sure if this is the best code (I just started with python yesterday) but here is what I came up with.  It's pretty easy to understand but post any questions and I'll try to answer them

EDIT: I thought you wanted someone to write a script that would do this for you.  I left the code up anyways since I don't really know how to tell you how to do it.  IMO I'd say it's probably best to study the code

```

#!/usr/bin/python

infile1 = file ('infile1.txt', 'r')
infile2 = file ('infile2.txt', 'r')
outfile = file ('new_file.txt', 'w')

arrayX = []
arrayY = []
arrayZ = []

for line in infile1:
    arrayX.append(line)
    
for line in infile2:
    arrayY.append(line)

infile1.close()
infile2.close()

print arrayX
print arrayY

for line in arrayX:
    if (line in arrayY):
        arrayZ.append(line)

for i in range(len(arrayZ)):
    outfile.write(arrayZ[i])
    
outfile.close()

```

---

### Post by mssever on 2008-12-19
> **rzrgenesys187 said:**
> Not sure if this is the best code (I just started with python yesterday) but here is what I came up with.
@OP:

Go ahead and read the docs. This implementation might get the job done, but if you read the docs, you'll find a better way to approach the task.

---

### Post by dwally89 on 2008-12-19
Thanks

---

