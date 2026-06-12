---
title: "Help to make my Python script run faster!"
date: 2010-08-09
forum: Programming Talk
---

### Post by melissawong on 2010-08-09
Hi, I wrote a Python script that works on small data but not large file(9 million lines). Appreciate anybody's help to fix it. 

I have two tab delimited input files: f1 and f2. f1 contains lines of interest (max 20,000 lines) while f2 is the complete data. I wanna look for those lines in f2. For every line of interest, I check for lines in the range of 100 in f2. Then, I look for patterns in column 3 and report it in output. I made a dictionary for all the patterns. 

Here's the improved script. Takes 34 sec to process every 120 lines in my smallest f1. 
```

for line in f1:
    l = line.strip()
    tags = l.split()
    tagset.add(tags[0])
    columns = tags[:2]
    position = int(tags[1])
    slist = "\t".join(columns)
    allSets[slist] = set()
    allSets[slist] = allSets[slist].union(range(position-50, position+50))
f1.close()
for r in f2:
    s = r.split()
    tag = s[0]
    if tag in tagset:
        rlist.append(s)
f2.close()
klist = allSets.keys()
for key in klist:
    length = 0
    blist = []
    key1 = key.split()[0]
    for r in rlist:
        if r[0] == key1 and int(r[1]) in allSets[key]:
            length += 1 #find number of lines matching the condition
            blist.append(r[2]) #add column 3 of these lines to a list
    all = "".join(blist) #convert list to string
    a = len(dict['p1'].findall(all)) #find pattern
    b = len(dict['p2'].findall(all))
    c = len(dict['p3'].findall(all))
    d = len(dict['p4'].findall(all))
    e = len(dict['p5'].findall(all))
    f = a-(2 * b)
    out.write("%s\t%d\t%d\t%d\t%d\t%d\t%d"%(key,length,f,b,c,d,e)+ "\n")

```Example:
f1 contains 
name position
C1    172
A2    120
A2 5000
*f1 might contain lines with same name but different position. 

f2 contains 
name position alphabet
C1    171    A
C1    172    C
C1    173    A
.....

My job is to search for lines with same name in f2. There might be 1000 matches but I'm only interested in lines with position in range of 100 (50 upstream and 49 downstream) from my line of interest. 
Say, C1\t172 in f1. I only want lines with C1\t122 until C1\t221 in f2. Then I get a list of the alphabets and count how many different patterns of alphabets in the list. I use regular expression to find patterns and I put them in a dictionary.

---

### Post by Bachstelze on 2010-08-09
I suspect it's because since you do f2.readlines(), f2 gets antirely loaded in memory.  Since it's large, that's a performance killer.  Use readline() instead to read one line at a time.

---

### Post by ssam on 2010-08-09
instead of:
```
#add lines in f2 in rlist
reads = f2.readlines()
for r in reads:
    s = r.split()
    rlist.append(s)

```
do:
```

#add lines in f2 in rlist
for r in f2:
    s = r.split()
    rlist.append(s)

```

also if you are only interesting in a few lines, then it is probably best only put those ones into rlist.

---

### Post by melissawong on 2010-08-09
> **ssam said:**
> instead of:
```
#add lines in f2 in rlist
reads = f2.readlines()
for r in reads:
    s = r.split()
    rlist.append(s)

```do:
```

#add lines in f2 in rlist
for r in f2:
    s = r.split()
    rlist.append(s)

```also if you are only interesting in a few lines, then it is probably best only put those ones into rlist.

Thanks. I only append certain lines in rlist. I see some improvement. 120 lines is processed every 3 minutes. Means I need to wait 8 hours for my biggest file. *faint

---

### Post by StephenF on 2010-08-09
Python is not optimised for global variable access so it will run faster just from throwing all that code into a function. It's not clear from the code you posted that any functions have been used.

---

### Post by Queue29 on 2010-08-09
> **stephenf said:**
> python is not optimized.

ftfy

---

### Post by StephenF on 2010-08-09
I think it's clear to all readers that this is the wrong tool for this job.

---

### Post by ssam on 2010-08-09
> **StephenF said:**
> I think it's clear to all readers that this is the wrong tool for this job.

unless the pattern bit is very CPU intensive this looks like it will probably be IO bound, so python would be fine. it just needs to be used right. the best C will probably always beat python. but the python you could write in a few hours may beat the C you could write in the same time.

here are some more ideas.

is the data file all numbers? if so read it all into a numpy array. these are far faster and more memory efficient than lists. but they are more limited, all the entries must be of the same type.

make it so that you dont have nested loops looking for the bit of data you are interested in. so first read f1 and figure out which lines you need. you can use something like
```

for n, line in enumerate(f2):
    if n in lines_of_interest:
         #do something

```
also you might want to store lines_of_interest in a set instead of a list, as it much faster to check if contains a value.
```

sam@oberon:~$ /usr/lib/python2.6/timeit.py "a = list(xrange(0,1000,2))" "[x in a for x in xrange(1000)]"
100 loops, best of 3: 10.2 msec per loop
sam@oberon:~$ /usr/lib/python2.6/timeit.py "a = set(xrange(0,1000,2))" "[x in a for x in xrange(1000)]"
10000 loops, best of 3: 180 usec per loop

```

---

### Post by Some Penguin on 2010-08-09
Bad algorithm.  You're doing a full linear scan over the full set for every query.

Two alternate approaches that come to mind:

1) Put the full data in a relational database.  Use a hash index on the first column and a b-tree index on the second column, because you're doing an exact match on one and a range query on the other.  This should cut down the IO by a lot.

2) Since you're willing to load the full set into RAM, at least use an associative array / hash table so the exact-match query is quick.    Map from first column -> list sorted by second columns, and do two binary searches.   Basically the same as above except you need to do the data structures but not mess with SQL.

---

### Post by ghostdog74 on 2010-08-09
use grep and awk, grep because its algorithm is optimized to search through files efficiently and awk to do further programming on your column 3.
```

grep -f f1.txt f2.txt  | awk '{ print "do something to $3" }' 

```

---

### Post by melissawong on 2010-08-09
Hi, thanks for all your suggestions. Some Pengiun hits the nail on the head. My problem is finding exact  match on one and a range query in another. I'm still a beginner in  Python but I will give these suggestions a try. Will post again soon. 

P.S. I have updated my initial post to provide a clearer idea.

---

### Post by teryret on 2010-08-10
I'm not 100% sure what you're asking for, but the following code should quickly find every matching name that is within 100 of a position of interest.

```

allSets = {}

for line in f1:
    line = line.strip()
    tags = line.split('\t')
    if tags[0] not in allSets:
        allSets[tags[0]] = set()
    position = int(tags[1])
    allSets[tags[0]] = allSets[tags[0]].union(range(position-50, position+50))
    
for line in f2:
    tags = line.split('\t')
    if tags[0] in allSets and int(tags[1]) in allSets[tags[0]]:
        print line

```

Does that help?  If not could you please clarify what you need?  For example if f1 had one line "C1\t150" and f2 contained three lines:
A1\t5\tA
C1\t150\tQ
D73\t007\tG

What would you expect the output to be?

---

### Post by melissawong on 2010-08-10
> **teryret said:**
> I'm not 100% sure what you're asking for, but the following code should quickly find every matching name that is within 100 of a position of interest.

```

allSets = {}

for line in f1:
    line = line.strip()
    tags = line.split('\t')
    if tags[0] not in allSets:
        allSets[tags[0]] = set()
    position = int(tags[1])
    allSets[tags[0]] = allSets[tags[0]].union(range(position-50, position+50))
    
for line in f2:
    tags = line.split('\t')
    if tags[0] in allSets and int(tags[1]) in allSets[tags[0]]:
        print line

```Does that help?

Thanks a lot! That's a brilliant idea to put the names and range of position in a dictionary! I will never think of it. I have to use name\tposition as key because f1 might contains lines with same name and different position. Now I can see 120 lines being processed every 1 min rather than 3 min.

---

### Post by teryret on 2010-08-10
That's the thing, you don't have to keep the key together and it will be faster and more space efficient if you don't.  If you use my code in interactive python mode print the contents off allSets in between the two for loops to convince yourself.

Any chance you could link to your f1 and f2 so I could do some performance tests?

Edit, also, would you mind posting the current iteration of your code?

---

### Post by juancarlospaco on 2010-08-10
**psyco**

---

### Post by schauerlich on 2010-08-10
> **juancarlospaco said:**
> **psyco**

Psyco can't fix a bad algorithm.

---

### Post by melissawong on 2010-08-12
Code updated!

---

### Post by teryret on 2010-08-13
Several things:

1)  I promise, you really don't need to keep the keys together and it will be much faster if you don't.  This is because nesting for loops always slow things down and should be avoided if at all humanly possible.

2)  Once you've gotten rid of the nested looping you'll find that taking the if out of my first loop will cause a bug.

3)  Consider, in my second loop, putting the characters onto the ends of strings that are in a dictionary indexed by the same keys as my allSets dictionary, then at the end you can simply loop a third time through each built up string and match each against the combined regex.

---

### Post by juancarlospaco on 2010-08-13
> **schauerlich said:**
> Psyco can't fix a bad algorithm.

The title says *"(...) run faster!"*
Not run faster and properly coded.
:)

---

