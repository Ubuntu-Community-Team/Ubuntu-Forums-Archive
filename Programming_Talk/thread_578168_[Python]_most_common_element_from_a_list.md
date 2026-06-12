---
title: "[Python] most common element from a list?"
date: 2007-10-17
forum: Programming Talk
---

### Post by syssyphus on 2007-10-17
basically I want to do a `uniq -c | sort -n | tail -n 1` in python....

I need to find the most common element in a large list (more than a million elements are in the list)


here is what I am using, (it is way too slow)

    nameDict = {}
    max = 0
    for uniqWord in uniqWordList:
        wordCount = wordList.count(uniqWord)
        nameDict[wordCount] = uniqWord
        if (wordCount > max):
            max = wordCount
            print "max: ", max
    print "common word found, returning"
    return max, nameDict[max]


basically I am taking a wordList, that contains many repeated elements. and I am copying it into a set and then back into uniqWordList, removing duplicate elements. I then iterate over this uniq word list and build a dictionary that includes the count of each uniq element, and the element it's self. I keep the largest known count (max) and return it along with the element it corresponds to when I am done. 

this is painfully slow, what am I doing wrong?

---

### Post by cwaldbieser on 2007-10-17
```

l = [1,3,2,2,1,1]
d = {}
for elm in l:
    d[elm] = d.get(elm, 0) + 1
counts = [(j,i) for i,j in d.items()]
count, max_elm = max(counts)

```
Build a dictionary of counts keyed by the elements.
The dictionary items(...) method is a list of tuples (element, count).
Reverse the order of the tuples to (count, element).
Let the max(...) function figure out the max count and element.

---

### Post by ghostdog74 on 2007-10-17
```

>>> d={}
>>> l = [1,3,2,2,1,1]
>>> for o  in l:
...  d.setdefault(o,0)
...  d[o]+=1
>>> d
{1: 3, 2: 2, 3: 1}

```

---

### Post by pmasiar on 2007-10-17
o and l are really the variable names I NEVER use :-(
Another naming convention I use is: don't have single letter variable names, use double-letter: ii, kk. Easier to find later :-) And collections end with letter s. :-)

Good names ARE important and add substantially to readability.

[php]
results = {}
items = [1,3,2,2,1,1]
for item in items: 
    results.setdefault(item, 0)
    results[item] += 1
[/php]

---

### Post by slavik on 2007-10-17
just to pimp Perl :)

[php]
$count{$_}++ for(LIST);
sort { $count{$b} <=> $count{$a} } keys %count; #<=> is for numbers, cmp is for strings
print @{%count}[0]
[/php]

---

### Post by dwblas on 2007-10-17
Your program takes a long time because this statement has to search the entire list for each word to get the count
wordCount = wordList.count(uniqWord)
So if you have 1 million entries, you have to search one million entries one million times which is somewhere around a trillion.  You at least eliminate looking up duplicate words again, but the best solution is already posted.  Go through the list once and increment a counter.

---

