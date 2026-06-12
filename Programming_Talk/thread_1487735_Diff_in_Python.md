---
title: "Diff in Python"
date: 2010-05-19
forum: Programming Talk
---

### Post by dragos2 on 2010-05-19
How can I do a diff in Python on 2 lists. Each of them contains a list of folders and files.

Except calling diff externally, is there other way ?

I want to do a simple diff: diff list1 list2 and put the output in a third one.

---

### Post by rrashkin on 2010-05-19
I find that the best way is to make each of the lists into a **set** and then use the **difference** method on sets.

```
set1=set(list1)
set2=set(list2)
list3=list(set1.difference(set2))
```

---

### Post by Tony Flury on 2010-05-19
@dragos2 - do you want to see the difference between the two lists - i.e. which file names are in list1 and not in list2, or do you want to actually see the differenece in the content of the files named in list1 and list2 ?

rrashkin's solution will give you the first problem - a list of filenames that exist in one list and not the other. 

For the 2nd problem if you want the complete set of differences i can see no way of doing it other than calling diff externally.
If all you want to know is which files are different from their counterpart, you could shorten the problem and looking at file sizes (if the file sizes are different the content definitely is and you can add something to your 3rd list without calling diff on the two files). There are also options you can use on diff so that it stops as soon as it finds a difference - if that is all you want to do, or you could write a very simple function that opens both files and steps through them one line at a time (byte at a time if they are binary files), and stops when it finds lines that are different - it is possible to write a loop in python that advances two iterators at the same time ("zip" springs to mind).

---

### Post by Tony Flury on 2010-05-19
```

def compare(filea, fileb):
    fa, fb = open(filea,"r"), open(fileb,"r")
    for (la,lb) in zip(fa,fb):
        if la <> lb:
           return False
    return True

```

The above function takes two parameters which are full file names of two text files you want to compare.

If the two files are line for line the same - it will return True, if the files are not the same it will return False 

Edit - the original snippet as above only works if the two files are exactly the same length - will work on a correction.

---

### Post by Tony Flury on 2010-05-19
Corrected - minimal testing but it seems to work

```

def cmp(filea, fileb):
    fa, fb = open(filea,"r"), open(fileb,"r")
    diff = False
    while not diff:
        la,lb = fa.readline(),fb.readline()
        if (la <> lb):
            diff = True 
        if (la == "" or lb == ""):
            break
    return not diff

```

---

### Post by jpkotta on 2010-05-20
[http://docs.python.org/library/difflib.html](http://docs.python.org/library/difflib.html)
[http://docs.python.org/library/filecmp.html](http://docs.python.org/library/filecmp.html)

Depending on what you're doing, just calling diff will probably be easier.

---

