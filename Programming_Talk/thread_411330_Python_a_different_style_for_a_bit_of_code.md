---
title: "Python: a different style for a bit of code"
date: 2007-04-16
forum: Programming Talk
---

### Post by MadeR on 2007-04-16
I'm here again to bother pythoners. I am a newcomer to python, and I desire to improve my knowledge about it.

At workplace we have a bunch of files that are more or less (overlapping) fragments of a database dump, backupped on different dates.
Each row of the file represents one column of the table. Rows are written in the format "TAG: DATA\n".
Each file contains at least one record of the database.

I have two different folders containing these files. Due to various errors, often the same key can be found into different files (and that should never happen).
So my task is finding these repeated keys and calculating the intersection and differencen between the key sets in the two folders.

I wrote the following code.

```

#!/usr/bin/python

import os

TAG = 'NCTN: '
PATH = '/home/mader/Desktop/schede'

filegroup = [ f for f in os.walk(PATH) if len(f[2]) ]

nctn = {}
for filenames in filegroup:
    for filename in filenames[2]:
        f = os.path.join( filenames[0], filename ) 
        for line in file(f):
            if line[:len(TAG)] == TAG:
                index = line[len(TAG):].strip()
                if index in nctn:
                    nctn[index].append(f)
                else:
                    nctn[index] = [f]

print nctn

```

My goal is to create one dictionary for each folder:
{ keyValue:[file1,file2], .... }
where the files are the files in which the key is found.

Having dictionaries allows me to use the methods listed in "dir(set)".

I'm really unsatisfied with the code I wrote for two reasons:
 - it seems to me not very pythonesque (in my opinion there are to few comprehension lists and to many traditional for(each) cycles)
 - it is really slow

what are your critics, hints and so on? :popcorn:

(yes, I can start "compile"-ing index and filegroup)

---

### Post by pmasiar on 2007-04-16
1) you are saving file object - saving just filename instead of reference of complex object could save a lot of RAM

2) Python adds checks for exceptions anyway, so gurus suggest using try explicitly is faster:

```

try:
    nctn[index].append(filename)
except KeyError:
    nctn[index] = [filename]

```

Good style is *not* about using list comprehension a lot, but writing readable code. Your code is reading a lot of files and creating huge dict, so it might take a while to finish. Just for fun, you may add after-run statistics: files parsed, keys created, to get idea how much work was done.

---

### Post by dwblas on 2007-04-17
> calculating the intersection and difference between the key sets in the two folders.I don't know if it would be faster, but using 2 lists, one for each directory containing the keys, converting to sets and using set intersection would give you the duplicate keys which you could then extract from the file into your dictionary without having to deal with the unique entries, could speed things up.  The down side would be parsing the dir listing twice.```
color_list1 = ['red','green','blue','black','orange','white']
color_list2 = ['black','maroon','grey','blue']
# # change to sets
color_set1 = set(color_list1)
color_set2 = set(color_list2 )
print "\nIntersection", color_set1.intersection(color_set2)
print "difference", color_set1.difference(color_set2)
```

---

### Post by ghostdog74 on 2007-04-17
> **dwblas said:**
> I don't know if it would be faster, but using 2 lists, one for each directory containing the keys, converting to sets and using set intersection would give you the duplicate keys which you could then extract from the file into your dictionary without having to deal with the unique entries, could speed things up.  The down side would be parsing the dir listing twice.```
color_list1 = ['red','green','blue','black','orange','white']
color_list2 = ['black','maroon','grey','blue']
# # change to sets
color_set1 = set(color_list1)
color_set2 = set(color_list2 )
print "\nIntersection", color_set1.intersection(color_set2)
print "difference", color_set1.difference(color_set2)
```
from my encounters, set operations for getting unique items using intersections/difference are a bit slower than dictionary operations using del etc,especially if the lists of files are huge.

---

### Post by pmasiar on 2007-04-17
> **ghostdog74 said:**
> from my encounters, set operations for getting unique items using intersections/difference are a bit slower than dictionary operations using del etc,especially if the lists of files are huge.

I agree, we had this discussion couple months ago in this forum, and we found out that most straightforward and obvious way (using "keyvar in dictvar", not set intersections) was also the fastest - as the Python mantra goes **there should be one obvious way to do it right** :-)

---

### Post by cwaldbieser on 2007-04-17
> **MadeR said:**
> 
```


                if index in nctn:
                    nctn[index].append(f)
                else:
                    nctn[index] = [f]

```

This bit could be written as:
```

nctn.setdefault(index, []).append(f)

```

---

### Post by MadeR on 2007-04-17
> **pmasiar said:**
> I agree, we had this discussion couple months ago in this forum, and we found out that most straightforward and obvious way (using "keyvar in dictvar", not set intersections) was also the fastest - as the Python mantra goes **there should be one obvious way to do it right** :-)

My task is to find the list of all NCTN's that are in any file in both folders, not to test if a NCTN is in a folder or not.

---

### Post by MadeR on 2007-04-17
> **cwaldbieser said:**
> This bit could be written as:
```

nctn.setdefault(index, []).append(f)

```

nice trick :)

---

### Post by Mirrorball on 2007-04-17
I think your code is excellent. I could read it and understand immediately what it does. I was just going to suggest setdefault, but cwaldbieser has already done it. And I just wanted to know why the data are not in a database anymore.

---

### Post by dwblas on 2007-04-17
Just to exhaust the possibilities, using two lists, sorting and stepping through/comparing each in turn would take more time than a dictionary as well, when the lists are large.  There might be some time increase if you divided the keys into several sections, and just added the keys for each section into the two dictionaries, creating smaller dictionaries.  But again, you would have to process the file as many times as you have sections, and it probably wouldn't be worth it.

---

### Post by pmasiar on 2007-04-17
> **MadeR said:**
> My task is to find the list of all NCTN's that are in any file in both folders, not to test if a NCTN is in a folder or not.

... and I explained you that sets are slower than straightforward dictionaries. folder != dictionary in Python :-)

---

### Post by MadeR on 2007-04-17
> **Mirrorball said:**
> And I just wanted to know why the data are not in a database anymore.
I'll try to explain but, not being English my native language, it is not so easy for me.

I am working to a national project whose goal is to create a digital version of all documents about (ancient) art object.
In the last year a team of "experts" created the rules to for the database structure and table field names, but in some offices throught Italy local groups had already started to create digital archives on their own or the same office decided to change the fileds in the digital version from time to time (upgrade).
So different tables, structures and field lists existed in similar formats (think about a national language and dialects):
similar, because they all followed the field list of the paper files (they had standard, established fields) but also different because each team added new structures, field or just... ideas.

But the key field(s), NCTN (Numero CaTalogazione Nazionale = National CaTalogue Numeber) is the same everywhere.

I'm trying to discover if groups of files created by the same teams in different times contain duplicated documents...

I hope my written text to be understandable :)

---

### Post by Mirrorball on 2007-04-17
English is not my first language either and I could understand your post. Your project sounds interesting but what a mess! Good luck to you.

---

### Post by MadeR on 2007-04-19
Today I needed two functions:

one should extract from a dictionary all the elements (as a dictionay) that have certain keys or property
the other should extract all the elements (as a dictionary) corresponding that have certain values or property

I ended up in using:
dict( filter( lambda x: x[1] % 2, d.iteritems() ) )   or   
dict( [x for x in d.iteritems() if x[1] % 2 ] )

dict( filter( lambda x: x[0] in f, d.iteritems() ) )   or   
dict( [x for x in d.iteritems() if x[0] in f ] )


I am very unsatisfied with these solutions, because I convert a {} to [] and then back from [] to {}

I think this should be methods of the dict class, but they are not.
Do similar functions exist and I do not know them?

also an overloading of some operators would be useful:
keys = [ 1, 3, 4, 6 ]
d = { 1:'a', 2:'b', 3:'c', 4:'d', 5:'e'}
subset = ks % d
or d.per_keys(ks)
resulting in subset = { 1:'a', 3:'c', 4:'d' }
I'm in doubt whether to raise or not an exception for key 6 not being contained in the dictionary.

and operator & (intersection) also working with tuples/lists

other useful extensions: 
dictionary in dictionary
set/enum/tuple/list in dictionary as (keys|values)
set/enum/tuple/list in tuple/list
Result: (True if left operand wholly contained in right operand else False)

I wish python HTML documentation were like PHP one...

---

