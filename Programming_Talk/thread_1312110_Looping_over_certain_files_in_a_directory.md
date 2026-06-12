---
title: "Looping over certain files in a directory"
date: 2009-11-02
forum: Programming Talk
---

### Post by jsschreck on 2009-11-02
Ive got a bunch of data files that pertain to different cases, say we have L number of cases. What I need to do for each case is to read the lines from 4 data files that I titled 0totL3, 1totL3, 2totL3, 3totL3 for each instance of L (so the next data set I have is 0totL5, 1totL5, 2totL5, 3totL5. I have the code written already to read the the 4 files in, what I want to do is loop over the cases opening the files that pertain to that case. So far I tried to pass an iterator like in the following: 
[PHP]
L_set = [5, 7]

for i in L_set:
    q = 3
    L = i

    infile0=open("0totL%.dat",'r') % (i) 
    infile1=...
    .
    .

[/PHP]

This doesnt work. I think you can probably catch my drift with what I want to do, any suggestions?

---

### Post by amingv on 2009-11-02
I'm not sure I understand the problem, do you just want to pass a formated string to the function?
If so, try this:

[PHP]infile0=open("0totL%d.dat" % i,'r')[/PHP]

Is that about what you want? If not, please elaborate on it.

---

### Post by jsschreck on 2009-11-03
Yes, this worked! Thanks a lot, I am still new to Python, just had the % in the wrong place then.

---

