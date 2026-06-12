---
title: "Search a list in Python"
date: 2007-07-11
forum: Programming Talk
---

### Post by Siph0n on 2007-07-11
Hey. I am creating a Soduko solver in python, and when I try and remove certain possibilites from a list, i want it to check to see if the number being removed is still in the list (cause it could be removed from checking other rows and columns and areas). Right now I have the idea of using a for loop to check each element in a list, but i was curious if there was an easier way.... like a built in attribute or sometin. Here is an idea of my for loop:

remove = 0
for x in SudokuPossibility[(i*9) + ii]:
    if x == NumToRemove:
        remove = 1
    SudokuPossibility[(i*9) + ii][xxx].remove(x)


This code isn't my complete code of course (I'm at work and dont have my code here), but I was curious if there was something like,  if NumToRemove is in SudokuPossibility?

---

### Post by Smygis on 2007-07-11
```

if value in sequence: # ;)

```

```
 >>> 5 in range(10)
True

```

---

### Post by Siph0n on 2007-07-11
hehe awesome thanx!!! I was pretty close!!! ;)

---

### Post by 24*7 on 2009-04-19
tnx a lot. that was such a simple solution :)

---

