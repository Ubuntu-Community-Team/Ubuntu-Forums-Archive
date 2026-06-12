---
title: "tool to subsitute foo by bar in multiple files"
date: 2007-03-16
forum: Programming Talk
---

### Post by mezhaka on 2007-03-16
hello, ubuntu users!

i have a bunch of python files and i'd like to change the name of a particular variable throughout many files in a particular directory, but i has to be a command line tool. can anyone suggest one? i could have written a perl oneliner for that. but i guess it's a solved problem, i'm just not aware of the solution.

---

### Post by 23meg on 2007-03-16
Check out *sed*.

---

### Post by dwblas on 2007-03-16
> (I) have a bunch of python filesIt can also be done pretty easily using Python.  There are threads in this forum about doing similar things using SED, per the above post, if that is your script of choice.

---

### Post by johnnymac on 2007-03-16
sed is your friend.....

cat *.py |sed 's/foo/bar/g'

---

### Post by ghostdog74 on 2007-03-17
> **mezhaka said:**
> hello, ubuntu users!

i have a bunch of python files and i'd like to change the name of a particular variable throughout many files in a particular directory, but i has to be a command line tool. can anyone suggest one? i could have written a perl oneliner for that. but i guess it's a solved problem, i'm just not aware of the solution.

i assume you know Python
```

import glob,os
yourdir = os.path.join("/","test")
os.chdir(yourdir)
for fi in glob.glob("*foo*.py"):
    newfile = fi.replace("foo","bar")
    os.rename(fi,newfile)

```

---

### Post by smartbei on 2007-03-17
A decently powerful tool I use when I feel like a gui and more features (like undoing changes - I think...) is KFileReplace, available through synaptic.

EDIT - sorry missed that it has to be command line.

---

### Post by tomchuk on 2007-03-17
```
sed -i -e 's/foo/bar/g' *.py
```

---

### Post by amanda on 2007-12-04
tomchuk,

I'm embarrassed by how long I've been trying to sort that out. 

Thank you.

---

