---
title: "Please help me improve script performance"
date: 2010-12-10
forum: Programming Talk
---

### Post by Stunts on 2010-12-10
Hi everyone.
I'm posting here because I'm all out of ideas. I've made a ton of research in order to improve my script's performance and all I managed to squeeze out of it was an extra 15% speed and arguably compromised code readability. So I'm asking for your help. Allow me to explain the situation.
I am programming in python. I have built a script that takes two files. One is a (relatively) small list of potentially interesting information, with each line as an entry. The other is a very large list with a lot of uninteresting entries, and with relevant information about each entry that is not available in the first file; similarly, the second file also has one entry per line. (Just FYI the "small" file is 63Mb and the large file is 3.2Gb).
Here is what my script does:
It matches the entry names in the 1st file to the entry names in the second files, and when it finds a match, it checks the information about the entry in the second file, and if it is interesting, then it is sent into a shortlist, which is the output file.
Using "cProfile" I have found out that (not surprisingly) the operation that takes the longest is where I check if the lines from the first file exist on the second file.
For simplicity I will call the small file "list" and the large file "reference".
Originally I had something like:
```
def Indexer(reference, list):
    indeces = []
    for lines in list:
        if lines in reference:
            indeces.append(reference.index(call)) #I only need the index number, not the line itself.
    return indeces

```Which, after some research, I changed to a "map" version which granted me my 15% performance bonus, which looked like this:

```

def Indexer(reference, list):
    names = tuple(filter(lambda x: x in ref, list))
    indeces = tuple(map(ref.index,names))
    return indeces

```But this is still not nearly enough. My original program has been running for more than 48 hours now, and since I will have to run it very often and with (sigh!) even bigger files, I definitely need to improve it's performance.
The only idea I have left it to try and multi-thread the program, but I read that python was not very good at it, and that it would actually be kind of pointless ([here]("http://code.google.com/p/pyloadtools/wiki/CodeTutorialMultiThreading") and [here]("http://stackoverflow.com/questions/1222929/gil-in-python-3-1"), but there were more).

So what else can I do to *dramatically* improve the run times?
Have I reached python's limit, speedwise? I want to think I haven't. =-)

Notes: 
If the code looks weird, it's python3.
I am already using tuples instead of lists everywhere I possibly can think of. This did have a very positive effect on performance, but I didn't measure it at the time.
In order to test this I'm using clipped versions of my files ("list" is 250k and "reference" is 5.2Mb).

Any help is greatly appreciated.

---

### Post by DaithiF on 2010-12-11
with either method you're doing a linear search of the large chunk of data for every element of the smaller set of data.

you should be doing a dictionary look-up instead.

you could either:
(a) create a dictionary of the large dataset, then for each element of the smaller, do a lookup, or
(b) it may be quicker to do this in reverse, create a dictionary of the smaller data set, then iterate once over the larger one and do lookups for each item there (this is on the principle that you can't avoid iterating through the large data at least once, so may as well do the lookups on the smaller dataset for efficiency)

in pseudo code:

```
list_dict = dict( [ line, None) for line in list ] )
matches = [ item for item in reference if item.key in list_dict ]
```

---

### Post by ziekfiguur on 2010-12-11
> **DaithiF said:**
> 
```
list_dict = dict( [ line, None) for line in list ] )
matches = [ item for item in reference if item.key in list_dict ]
```

Shouldn't that be
```
list_dict = dict([(j, i) for i, j in enumerate(list)])
matches = [list_dict[item] for item in reference if item in list_dict]
```
this maps the lines of list to it's indices in list_dict and matches will be a list of indices (to items in list) for items from reference that also occur in list.

---

### Post by Stunts on 2010-12-11
Hi guys and thanks for your input.
Using DaithiF's idea, and modifying the suggestion made by ziekfiguur to this:
```
list_dict = dict([(j, i) for i, j in enumerate(list)])
matches = [reference.index(item) for item in reference if item in list_dict]
```I have managed to get a huge performance boost. We're talking about 10 or more times faster (with the small files I can't be that precise =-)).
Thanks for your input. You have been of great help.
I really tough that operation on tuples were much faster than operations on dictionaries, but I guess I was wrong!
Once I have applied it to the "real" files I will let you know the result.
Thanks again.

---

### Post by ziekfiguur on 2010-12-11
Sorry, i got you a list with the wrong indices.
Even better would be:
```
list_set = set(list)
matches = [i for i, j in enumerate(ref) if j in list_set]
```

---

### Post by Stunts on 2010-12-11
OWO!
Now that was absolutely amazing!
The whole thing ran in 6 minutes using the full dataset (and 5m50s are for loading the datafiles - I suppose I could also shave more time there if I needed). 
I didn't know of this "set" data structure. I'm seeing it but I still don't fully believe it!!
Thank you ziekfiguur! I am now marking this thread solved.

---

