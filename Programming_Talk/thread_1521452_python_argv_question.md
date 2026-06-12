---
title: "python argv question"
date: 2010-06-30
forum: Programming Talk
---

### Post by tdrusk on 2010-06-30
i am new to using commandline arguments in python. i am a bit confused as to why my code doesn't work when i pass commandline arguments, but does work when i just create a list in program. for example

```

import sys
i = [4,2,5,3,-22,33]
for p in range(1,len(i)):
        print "pass "+str(p)
        for c in range(p,0,-1):
                print '\t'+str(i[c-1])+' checked with '+str(i[c])
                if(i[c]<i[c-1]):
                        print '\tswapped '+str(i[c])+' with '+str(i[c-1])
                        t=i[c-1]
                        i[c-1]=i[c]
                        i[c]=t
                print '\t'+str(i)
print "done: " +str(i)                  

```gives me the output 
```
pass 1
        4 checked with 2
        swapped 2 with 4
        [2, 4, 5, 3, -22, 33]
pass 2
        4 checked with 5
        [2, 4, 5, 3, -22, 33]
        2 checked with 4
        [2, 4, 5, 3, -22, 33]
pass 3
        5 checked with 3
        swapped 3 with 5
        [2, 4, 3, 5, -22, 33]
        4 checked with 3
        swapped 3 with 4
        [2, 3, 4, 5, -22, 33]
        2 checked with 3
        [2, 3, 4, 5, -22, 33]
pass 4
        5 checked with -22
        swapped -22 with 5
        [2, 3, 4, -22, 5, 33]
        4 checked with -22
        swapped -22 with 4
        [2, 3, -22, 4, 5, 33]
        3 checked with -22
        swapped -22 with 3
        [2, -22, 3, 4, 5, 33]
        2 checked with -22
        swapped -22 with 2
        [-22, 2, 3, 4, 5, 33]
pass 5
        5 checked with 33
        [-22, 2, 3, 4, 5, 33]
        4 checked with 5
        [-22, 2, 3, 4, 5, 33]
        3 checked with 4
        [-22, 2, 3, 4, 5, 33]
        2 checked with 3
        [-22, 2, 3, 4, 5, 33]
        -22 checked with 2
        [-22, 2, 3, 4, 5, 33]
done: [-22, 2, 3, 4, 5, 33]

```which is perfectly correct
but when i use commandline arguments i get a different(wrong) answer
```
import sys
i=sys.argv[1:]
for p in range(1,len(i)):
        print "pass "+str(p)
        for c in range(p,0,-1):
                print '\t'+str(i[c-1])+' checked with '+str(i[c])
                if(i[c]<i[c-1]):
                        print '\tswapped '+str(i[c])+' with '+str(i[c-1])
                        t=i[c-1]
                        i[c-1]=i[c]
                        i[c]=t
                print '\t'+str(i)
print "done: " +str(i)        
``````

python insertionsort.py 4 2 5 3 -22 33
pass 1
        4 checked with 2
        swapped 2 with 4
        ['2', '4', '5', '3', '-22', '33']
pass 2
        4 checked with 5
        ['2', '4', '5', '3', '-22', '33']
        2 checked with 4
        ['2', '4', '5', '3', '-22', '33']
pass 3
        5 checked with 3
        swapped 3 with 5
        ['2', '4', '3', '5', '-22', '33']
        4 checked with 3
        swapped 3 with 4
        ['2', '3', '4', '5', '-22', '33']
        2 checked with 3
        ['2', '3', '4', '5', '-22', '33']
pass 4
        5 checked with -22
        swapped -22 with 5
        ['2', '3', '4', '-22', '5', '33']
        4 checked with -22
        swapped -22 with 4
        ['2', '3', '-22', '4', '5', '33']
        3 checked with -22
        swapped -22 with 3
        ['2', '-22', '3', '4', '5', '33']
        2 checked with -22
        swapped -22 with 2
        ['-22', '2', '3', '4', '5', '33']
pass 5
        5 checked with 33
        swapped 33 with 5
        ['-22', '2', '3', '4', '33', '5']
        4 checked with 33
        swapped 33 with 4
        ['-22', '2', '3', '33', '4', '5']
        3 checked with 33
        ['-22', '2', '3', '33', '4', '5']
        2 checked with 3
        ['-22', '2', '3', '33', '4', '5']
        -22 checked with 2
        ['-22', '2', '3', '33', '4', '5']
done: ['-22', '2', '3', '33', '4', '5']


```i have a feeling i am just overlooking something stupid, but any advice as to why this is happing would be much appreciated.:guitar:

---

### Post by schauerlich on 2010-06-30
When you make the list yourself, you're making a list of integers. When you're getting it from the command line, you're getting a list of strings. You have to convert the arguments to integers.

```
numbers = sys.argv[:]
for number in numbers:
    try:
        number = int(number)
    except:
        print "Input must be integers"

```

---

### Post by tdrusk on 2010-06-30
> **schauerlich said:**
> When you make the list yourself, you're making a list of integers. When you're getting it from the command line, you're getting a list of strings. You have to convert the arguments to integers.

```
numbers = sys.argv[:]
for number in numbers:
    try:
        number = int(number)
    except:
        print "Input must be integers"

```
your tip got me in the right direction. thanks!

```

import sys
i=sys.argv[1:]
for j in range(len(i)):
        try:
                i[j]=int(i[j])
        except:
                print "input must be int"
for p in range(1,len(i)):
        print "pass "+str(p)
        for c in range(p,0,-1):
                print '\t'+str(i[c-1])+' checked with '+str(i[c])
                if(i[c]<i[c-1]):
                        print '\tswapped '+str(i[c])+' with '+str(i[c-1])
                        t=i[c-1]
                        i[c-1]=i[c]
                        i[c]=t
                print '\t'+str(i)
print "done: " +str(i)


```gives me
```

pass 1
        4 checked with 2
        swapped 2 with 4
        [2, 4, 5, 3, -22, 33]
pass 2
        4 checked with 5
        [2, 4, 5, 3, -22, 33]
        2 checked with 4
        [2, 4, 5, 3, -22, 33]
pass 3
        5 checked with 3
        swapped 3 with 5
        [2, 4, 3, 5, -22, 33]
        4 checked with 3
        swapped 3 with 4
        [2, 3, 4, 5, -22, 33]
        2 checked with 3
        [2, 3, 4, 5, -22, 33]
pass 4
        5 checked with -22
        swapped -22 with 5
        [2, 3, 4, -22, 5, 33]
        4 checked with -22
        swapped -22 with 4
        [2, 3, -22, 4, 5, 33]
        3 checked with -22
        swapped -22 with 3
        [2, -22, 3, 4, 5, 33]
        2 checked with -22
        swapped -22 with 2
        [-22, 2, 3, 4, 5, 33]
pass 5
        5 checked with 33
        [-22, 2, 3, 4, 5, 33]
        4 checked with 5
        [-22, 2, 3, 4, 5, 33]
        3 checked with 4
        [-22, 2, 3, 4, 5, 33]
        2 checked with 3
        [-22, 2, 3, 4, 5, 33]
        -22 checked with 2
        [-22, 2, 3, 4, 5, 33]
done: [-22, 2, 3, 4, 5, 33]


```

---

### Post by nvteighen on 2010-07-01
> **schauerlich said:**
> When you make the list yourself, you're making a list of integers. When you're getting it from the command line, you're getting a list of strings. You have to convert the arguments to integers.

```
numbers = sys.argv[:]
for number in numbers:
    try:
        number = int(number)
    except:
        print "Input must be integers"

```

A bit smaller and in functional programming fashion:
```

import sys

args = None # It's always good to initialize stuff... see below.
try:
    args = map(int, sys.argv[1:])) # argv[0] is always a string, so skip it!
except ValueError:
    print("All arguments required to be integers")
    # args will be None here. This allows you to check later in code whether
    # args is valid or not where needed instead of immediately quitting the
    # application by default.

```

---

