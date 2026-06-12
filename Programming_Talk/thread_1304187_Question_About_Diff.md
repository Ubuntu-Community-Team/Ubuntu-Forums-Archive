---
title: "Question About Diff"
date: 2009-10-29
forum: Programming Talk
---

### Post by StunnerAlpha on 2009-10-29
Ey guys, I am having trouble understanding how diff of directories works. I have a directory:
```

$ ls -aR
.				.FreezeFileSettings.txt		folder2
..				.FreezeFileSettings_fromBin.txt
.DS_Store			folder1

./folder1:
.	..	happy	subdir1

./folder1/subdir1:
.		..		hallel.txt

./folder2:
.	..	sad	subdir2

./folder2/subdir2:
.		..		bombakz		hallel.txt	subsub2

./folder2/subdir2/subsub2:
.	..	touched

```
Here are the contents of each file:
```

$ head -3 folder1/happy 
$ head -3 folder2/sad 
$ head -3 folder1/subdir1/hallel.txt 
jewish
$ head -3 folder2/subdir2/bombakz 
iiiiii
$ head -3 folder2/subdir2/hallel.txt 
wombatz
jewish
$ head -3 folder2/subdir2/subsub2/touched 
hummers

hithere


```

This is what I get when I diff from terminal:
```

diff folder1 folder2
Only in folder1: happy
Only in folder2: sad
Only in folder1: subdir1
Only in folder2: subdir2

```
...and when I do it from python:
```

>>> cmp = filecmp.dircmp(os.getcwd()+'/folder1',os.getcwd()+'/folder2/')
>>>
>>>
>>> cmp.report()
diff /.../testarea/folder2/
Only in /.../testarea/folder1 : ['happy', 'subdir1']
Only in /.../testarea/folder2/ : ['sad', 'subdir2']
>>>
>>>
>>>
>>> cmp.report_full_closure()
diff /.../testarea/folder2/
Only in /.../testarea/folder1 : ['happy', 'subdir1']
Only in /.../testarea/folder2/ : ['sad', 'subdir2']
>>>
>>>
>>> cmp.right_only
['sad', 'subdir2']
>>>
>>>
>>> cmp.left_only
['happy', 'subdir1']
>>>
>>>
>>> cmp.diff_files
[]

```
My question is, why isn't diff going all the way down the directories? Thanks.

Edit: Oh and what would you recommend to check to see if directories are identical? I want the function to recurse all the way down each directory in case there are some changes in the very last subdirectory. What is the most full-proof method for this? Thanks again.

---

### Post by Arndt on 2009-10-29
> **StunnerAlpha said:**
> 
My question is, why isn't diff going all the way down the directories? Thanks.



Does "diff -r" do what you want?

---

### Post by StunnerAlpha on 2009-10-29
> **Arndt said:**
> Does "diff -r" do what you want?

Nope, I just get this:
```

$ diff -r folder1 folder2
Only in folder1: happy
Only in folder2: sad
Only in folder1: subdir1
Only in folder2: subdir2

```

Thanks for the response.

---

### Post by Arndt on 2009-10-29
> **StunnerAlpha said:**
> Nope, I just get this:
```

$ diff -r folder1 folder2
Only in folder1: happy
Only in folder2: sad
Only in folder1: subdir1
Only in folder2: subdir2

```

Thanks for the response.

Do you want the comparison to go down and compare the contents of folder1/subdir1 and folder2/subdir2? If they were named folder1/subdir and folder2/subdir, they would. Now, their names are different, so the comparison stops there.

Do you know that each directory only contains at most one subdirectory? Then the operation is well defined, but I don't think 'diff' can do it.

---

### Post by StunnerAlpha on 2009-10-29
> **Arndt said:**
> Do you want the comparison to go down and compare the contents of folder1/subdir1 and folder2/subdir2? If they were named folder1/subdir and folder2/subdir, they would. Now, their names are different, so the comparison stops there.

Do you know that each directory only contains at most one subdirectory? Then the operation is well defined, but I don't think 'diff' can do it.

Ey man, to answer your question: no, I don't know that each directory will contain at most one subdir. I really need something that will recursively compare two directories as well as files within the directories(I want folder1/ compared with folder2/, then folder1/subdir1 compared with folder2/subdir2, and so on...). If diff cannot do it, is there any other utility that can help me out? Is there anything in the python libs that can help me here? Thanks.

---

### Post by Arndt on 2009-10-29
> **StunnerAlpha said:**
> Ey man, to answer your question: no, I don't know that each directory will contain at most one subdir. I really need something that will recursively compare two directories as well as files within the directories(I want folder1/ compared with folder2/, then folder1/subdir1 compared with folder2/subdir2, and so on...). If diff cannot do it, is there any other utility that can help me out? Is there anything in the python libs that can help me here? Thanks.

Then I think the task isn't well-defined yet. If you have these directories:

folder1/subdir1
folder1/subdir3
folder1/morefiles

folder2/subdir2
folder2/subdir3

then which directories do you want compared to which?

---

### Post by StunnerAlpha on 2009-10-29
> **Arndt said:**
> Then I think the task isn't well-defined yet. If you have these directories:

folder1/subdir1
folder1/subdir3
folder1/morefiles

folder2/subdir2
folder2/subdir3

then which directories do you want compared to which?

All I want is a boolean value based on if the two directories are identical or not. In the example you gave me folder1/subdir1 compared with both folder2/subdir2 and folder2/subdir3 to see if either of those folders are the same as folder1/subdir1, and then folder1/subdir3 compared with both subdirs of folder 2 again. But once the program comes to folder1/morefiles it should return False since "morefiles"(whether it be a dir or files) is not present in both directories in the same location. 

I don't want comparisons between the contents of files, I only want to compare the structure of the directories, meaning folders and contents of folders(filenames don't have to match, but there just needs to be the correct amount of files in one directory as in another).

Hmm... this is becoming a little too far-fetched eh? I had best make an algorithm to do this myself, right?

---

### Post by Arndt on 2009-10-29
> **StunnerAlpha said:**
> All I want is a boolean value based on if the two directories are identical or not. In the example you gave me folder1/subdir1 compared with both folder2/subdir2 and folder2/subdir3 to see if either of those folders are the same as folder1/subdir1, and then folder1/subdir3 compared with both subdirs of folder 2 again. But once the program comes to folder1/morefiles it should return False since "morefiles"(whether it be a dir or files) is not present in both directories in the same location. 

I don't want comparisons between the contents of files, I only want to compare the structure of the directories, meaning folders and contents of folders(filenames don't have to match, but there just needs to be the correct amount of files in one directory as in another).

Hmm... this is becoming a little too far-fetched eh? I had best make an algorithm to do this myself, right?

So the comparison of folder1 and folder2 should return False, since they have different numbers of subdirectories?

Then the task seems to be to check whether there exists some way of renaming all node names in one tree T1 so that it becomes identical to another tree T2. There may be code written for that already, in some tree and graph manipulation library. A naive implementation could become exponential. But maybe the problem is NP-complete, I don't know.

---

### Post by Arndt on 2009-10-29
> **Arndt said:**
> So the comparison of folder1 and folder2 should return False, since they have different numbers of subdirectories?

Then the task seems to be to check whether there exists some way of renaming all node names in one tree T1 so that it becomes identical to another tree T2. There may be code written for that already, in some tree and graph manipulation library. A naive implementation could become exponential. But maybe the problem is NP-complete, I don't know.

Interesting algorithm. The complexity is apparently n*log(n), so there is no need to worry. Google for "tree isomorphism" (assuming I haven't misunderstood your requirements).

---

### Post by StunnerAlpha on 2009-10-29
> **Arndt said:**
> So the comparison of folder1 and folder2 should return False, since they have different numbers of subdirectories?

Then the task seems to be to check whether there exists some way of renaming all node names in one tree T1 so that it becomes identical to another tree T2. There may be code written for that already, in some tree and graph manipulation library. A naive implementation could become exponential. But maybe the problem is NP-complete, I don't know.

What do you mean by "NP-complete"? Or the task could be to just check to see if an item is a file/directory and compare the amount of each to the other directory, rather than renaming and making a mess of things, because I want to preserve everything the way it is if possible. So if I renamed to do the comparison I would have to rename each file back to the name it initially had. Oh and thanks for checking the big-O for the algorithm, I am thinking of tackling this myself, if you think this is foolish let me know. I don't think it should be too hard.

---

### Post by Arndt on 2009-10-30
> **StunnerAlpha said:**
> What do you mean by "NP-complete"? Or the task could be to just check to see if an item is a file/directory and compare the amount of each to the other directory, rather than renaming and making a mess of things, because I want to preserve everything the way it is if possible. So if I renamed to do the comparison I would have to rename each file back to the name it initially had. Oh and thanks for checking the big-O for the algorithm, I am thinking of tackling this myself, if you think this is foolish let me know. I don't think it should be too hard.

Some problems are NP-complete, which usually means exponential in practice, for example the traveling salesman problem, or satisfying boolean formulas. But this was not one of them.

I think it seems doable.

One case where the general algorithm doesn't care, but you probably do: if you have folder1/subdir1, folder1/subdir2, folder2/subdir7 and folder2/subdir8, and these turn out all to have the same structure, do you identify subdir1 with subdir7 or subdir8?

---

### Post by StunnerAlpha on 2009-10-30
> **Arndt said:**
> Some problems are NP-complete, which usually means exponential in practice, for example the traveling salesman problem, or satisfying boolean formulas. But this was not one of them.

I think it seems doable.

One case where the general algorithm doesn't care, but you probably do: if you have folder1/subdir1, folder1/subdir2, folder2/subdir7 and folder2/subdir8, and these turn out all to have the same structure, do you identify subdir1 with subdir7 or subdir8?

Good question. I would have it check sub-directories in the other folder until it finds a match. So in this case folder1/subdir1 is first checked with folder2/subdir7 and is found to match, so the algorithm stops matching folder1/subdir1 and makes note that those two directory structures are the same(by dictionary or list or whatever). 

Then the algorithm goes to folder2/subdir2 and then attempts to match it with folder2/subdir7 but is not allowed to since that is already matched with folder1/subdir1, so it looks at folder2/subdir8 and finds they match, then does its storing.

Then it checks to make sure there are no other contents that aren't accounted for, and returns a boolean value based on if all contents of each folder are contained within the list or dictionary that stores equalities. In this case it would return True.

So to answer you question about if I care if it identifies subdir1 with subdir7 or 8: No, I don't. I don't care about names, just the structure of directories. If subdir1 were correlated with subdir8 instead, the algorithm would still return True and thats all I really care about.

I will take a shot at creating the algorithm and will post it up here. Let me know if you have any hints for me, and thanks for the responses. :)

---

### Post by StunnerAlpha on 2009-10-31
Alright, so I worked on it for a day and this is what I came up with. Let me know what you think and please point out if I happened to look over something. Thanks.

Anyways, here is my python code:
[php]
#!/usr/bin/env python

import sys, os

class G:
    folder1WalkContents = []
    folder2WalkContents = []
    
    folder1Ctrs = [0,0,0] #counter for r,d,f respectively
    folder2Ctrs = [0,0,0]
    
    folder1RDict = {}
    folder2RDict = {}
    
    folder1DDict = {}
    folder2DDict = {}
    
    folder1FDict = {}
    folder2FDict = {}

def retrieveR(splitR,o):
    try:
        if o == 1:
            return G.folder1RDict[splitR]
        elif o == 2:
            return G.folder2RDict[splitR]
    except:
        if o == 1:
            G.folder1Ctrs[0] += 1
            G.folder1RDict[splitR] = 'r_' + str(G.folder1Ctrs[0])
            return G.folder1RDict[splitR]
        elif o == 2:
            G.folder2Ctrs[0] += 1
            G.folder2RDict[splitR] = 'r_' + str(G.folder2Ctrs[0])
            return G.folder2RDict[splitR]
        
def retrieveD(d,o):
    try:
        if o == 1:
            return G.folder1DDict[d]
        elif o == 2:
            return G.folder2DDict[d]
    except:
        if o == 1:
            G.folder1Ctrs[1] += 1
            G.folder1DDict[d] = 'd_' + str(G.folder1Ctrs[1])
            return G.folder1DDict[d]
        elif o == 2:
            G.folder2Ctrs[1] += 1
            G.folder2DDict[d] = 'd_' + str(G.folder2Ctrs[1])
            return G.folder2DDict[d]

def retrieveF(f,o):
    try:
        if o == 1:
            return G.folder1FDict[f]
        elif o == 2:
            return G.folder2FDict[f]
    except:
        if o == 1:
            G.folder1Ctrs[2] += 1
            G.folder1FDict[f] = 'f_' + str(G.folder1Ctrs[2])
            return G.folder1FDict[f]
        elif o == 2:
            G.folder2Ctrs[2] += 1
            G.folder2FDict[f] = 'f_' + str(G.folder2Ctrs[2])
            return G.folder2FDict[f]

def eliminateBlanks(lst):
    removeCtr = 0
    for i in range(len(lst)):
        if lst[i] == '':
            removeCtr += 1
    for i in range(removeCtr):
        lst.remove('')
    return lst

def alterNames(r,d,f,o):
    newR = ''
    newD = []
    newF = []
    newRList = []
    newDList = []
    newFList = []
    splitR = r.split('/')
    splitR = eliminateBlanks(splitR)
    for i in range(len(splitR)):
        newRList.append(retrieveR(splitR[i],o))
    for i in range(len(d)):
        newDList.append(retrieveD(d[i],o))
    for i in range(len(f)):
        newFList.append(retrieveF(f[i],o))
    return (newRList,newDList,newFList)

def createWalkContents(r,d,f,o):
    (tempR,tempD,tempF) = alterNames(r,d,f,o)
    if o == 1:
        G.folder1WalkContents.append((tempR,tempD,tempF))
    elif o == 2:
        G.folder2WalkContents.append((tempR,tempD,tempF))

def findDifferences(argv):
    folder1 = argv[1]
    folder2 = argv[2]
    for r,d,f in os.walk(folder1):
        createWalkContents(r,d,f,1)
    for r,d,f in os.walk(folder2):
        createWalkContents(r,d,f,2)
    return G.folder1WalkContents == G.folder2WalkContents
   

def main(argv):
    if len(argv) < 3:
        print "Usage: python differences.py <folder 1> <folder 2>"
        exit()
    print findDifferences(argv)
    
if __name__ == '__main__':
    main(sys.argv)
    
[/php]

And here is my test directory with results:
```

$ ls -aR
.				.FreezeFileSettings_fromBin.txt	f1 copy
..				differences.py			f2
.DS_Store			f1				f3

./f1:
.	..	sub1

./f1/sub1:
.		..		touched1

./f1 copy:
.	..	sub1

./f1 copy/sub1:
.		..		touched1

./f2:
.	..	sub2	sub3

./f2/sub2:
.	..

./f2/sub3:
.	..

./f3:
.		..		template10	template5

./f3/template10:
.	..

./f3/template5:
.	..
$ python differences.py f1 f3
False
$ python differences.py f1 f2
False
$ python differences.py f3 f2
True
$ python differences.py f3 f1\ copy/
False
$ python differences.py f1 f1\ copy/
True
$ 

```

Thanks in advance for feedback. ;)

---

### Post by StunnerAlpha on 2009-10-31
Actually I found that the code I previously posted doesn't work with the following case where f2 and f3 should be reported as equal. Here is the directory layout:

```

$ ls -aR
.				.FreezeFileSettings_fromBin.txt	f1 copy
..				differences.py			f2
.DS_Store			f1				f3

./f1:
.	..	sub1

./f1/sub1:
.		..		touched1

./f1 copy:
.	..	sub1

./f1 copy/sub1:
.		..		touched1

./f2:
.	..	sub2	sub3

./f2/sub2:
.		..		something	somthing other

./f2/sub2/something:
.	..	hello

./f2/sub2/somthing other:
.	..	blank

./f2/sub2/somthing other/blank:
.	..

./f2/sub3:
.	..

./f3:
.		..		template10	template5

./f3/template10:
.			..			some other thing	somedir

./f3/template10/some other thing:
.	..	empty

./f3/template10/some other thing/empty:
.	..

./f3/template10/somedir:
.	..	hithere

./f3/template5:
.	..

```

So I fixed the script to work with it and tested it a little bit more and it ended up working:
```

$ mkdir f2/submarine
$ mkdir f2/submarine/subversion
$ mkdir f3/sub\ par
$ mkdir f3/sub\ par/birdie-not\ hole\ in\ one
$ python differences.py f2 f3
True
$ mkdir f3/sub\ par/birdie-not\ hole\ in\ one/tiger\ woods
$ python differences.py f2 f3
False
$ mkdir f2/submarine/subversion/sub-operative
$ python differences.py f2 f3
True
$ ls -aR
.				.FreezeFileSettings_fromBin.txt	f1 copy
..				differences.py			f2
.DS_Store			f1				f3

./f1:
.	..	sub1

./f1/sub1:
.		..		touched1

./f1 copy:
.	..	sub1

./f1 copy/sub1:
.		..		touched1

./f2:
.		..		sub2		sub3		submarine

./f2/sub2:
.		..		something	somthing other

./f2/sub2/something:
.	..	hello

./f2/sub2/somthing other:
.	..	blank

./f2/sub2/somthing other/blank:
.	..

./f2/sub3:
.	..

./f2/submarine:
.		..		subversion

./f2/submarine/subversion:
.		..		sub-operative

./f2/submarine/subversion/sub-operative:
.	..

./f3:
.		..		sub par		template10	template5

./f3/sub par:
.			..			birdie-not hole in one

./f3/sub par/birdie-not hole in one:
.		..		tiger woods

./f3/sub par/birdie-not hole in one/tiger woods:
.	..

./f3/template10:
.			..			some other thing	somedir

./f3/template10/some other thing:
.	..	empty

./f3/template10/some other thing/empty:
.	..

./f3/template10/somedir:
.	..	hithere

./f3/template5:
.	..


```
And here is the code that did it all:
[php]
#!/usr/bin/env python

import sys, os

class G:
    folder1WalkContents = []
    folder2WalkContents = []
    
    folder1Ctrs = [0,0,0] #counter for r,d,f respectively
    folder2Ctrs = [0,0,0]
    
    folder1RDict = {}
    folder2RDict = {}
    
    folder1DDict = {}
    folder2DDict = {}
    
    folder1FDict = {}
    folder2FDict = {}

def retrieveR(splitR,o):
    try:
        if o == 1:
            return G.folder1RDict[splitR]
        elif o == 2:
            return G.folder2RDict[splitR]
    except:
        if o == 1:
            G.folder1Ctrs[0] += 1
            G.folder1RDict[splitR] = 'r_' + str(G.folder1Ctrs[0])
            return G.folder1RDict[splitR]
        elif o == 2:
            G.folder2Ctrs[0] += 1
            G.folder2RDict[splitR] = 'r_' + str(G.folder2Ctrs[0])
            return G.folder2RDict[splitR]
        
def retrieveD(d,o):
    try:
        if o == 1:
            return G.folder1DDict[d]
        elif o == 2:
            return G.folder2DDict[d]
    except:
        if o == 1:
            G.folder1Ctrs[1] += 1
            G.folder1DDict[d] = 'd_' + str(G.folder1Ctrs[1])
            return G.folder1DDict[d]
        elif o == 2:
            G.folder2Ctrs[1] += 1
            G.folder2DDict[d] = 'd_' + str(G.folder2Ctrs[1])
            return G.folder2DDict[d]

def retrieveF(f,o):
    try:
        if o == 1:
            return G.folder1FDict[f]
        elif o == 2:
            return G.folder2FDict[f]
    except:
        if o == 1:
            G.folder1Ctrs[2] += 1
            G.folder1FDict[f] = 'f_' + str(G.folder1Ctrs[2])
            return G.folder1FDict[f]
        elif o == 2:
            G.folder2Ctrs[2] += 1
            G.folder2FDict[f] = 'f_' + str(G.folder2Ctrs[2])
            return G.folder2FDict[f]

def eliminateBlanks(lst):
    removeCtr = 0
    for i in range(len(lst)):
        if lst[i] == '':
            removeCtr += 1
    for i in range(removeCtr):
        lst.remove('')
    return lst

def alterNames(r,d,f,o):
    newR = ''
    newD = []
    newF = []
    newRList = []
    newDList = []
    newFList = []
    splitR = r.split('/')
    splitR = eliminateBlanks(splitR)
    for i in range(len(splitR)):
        newRList.append(retrieveR(splitR[i],o))
    for i in range(len(d)):
        newDList.append(retrieveD(d[i],o))
    for i in range(len(f)):
        newFList.append(retrieveF(f[i],o))
    return (newRList,newDList,newFList)

def createWalkContents(r,d,f,o):
    (tempR,tempD,tempF) = alterNames(r,d,f,o)
    if o == 1:
        G.folder1WalkContents.append((tempR,tempD,tempF))
    elif o == 2:
        G.folder2WalkContents.append((tempR,tempD,tempF))

def findDifferences(argv):
    folder1 = argv[1]
    folder2 = argv[2]
    for r,d,f in os.walk(folder1):
        createWalkContents(r,d,f,1)
    for r,d,f in os.walk(folder2):
        createWalkContents(r,d,f,2)
    return G.folder1WalkContents == G.folder2WalkContents

def findInList(item,lst):
    for itr in range(len(lst)):
        if lst[itr] == item:
            return True
    return False
   
def thoroughCompare():
    f1WCLen = []
    f2WCLen = []
    for i in range(len(G.folder1WalkContents)):
        f1WCLen.append([])
        for j in range(3):
            f1WCLen[i].append(len(G.folder1WalkContents[i][j]))
    #print f1WCLen
    for i in range(len(G.folder2WalkContents)):
        f2WCLen.append([])
        for j in range(3):
            f2WCLen[i].append(len(G.folder2WalkContents[i][j]))
    #print f2WCLen
    
    for i in range(len(f1WCLen)):
        bool = findInList(f1WCLen[i],f2WCLen)
        if not bool:
            return False
    return True
            

def main(argv):
    if len(argv) < 3:
        print "Usage: python differences.py <folder 1> <folder 2>"
        exit()
    if not findDifferences(argv):
        print thoroughCompare()
    else:
        print "True"
    #print 'f1:',G.folder1WalkContents
    #print 'f2:', G.folder2WalkContents
    
if __name__ == '__main__':
    main(sys.argv)
    
[/php]

---

