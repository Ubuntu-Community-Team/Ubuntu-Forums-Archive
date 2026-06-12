---
title: "Combinations routine: python -&gt; c++"
date: 2009-12-20
forum: Programming Talk
---

### Post by jsschreck on 2009-12-20
I can program in Python, but my knowledge of C++ is minimal. If someone can help me get started, I would really appreciate it. The following code, combo.py, does the following. Suppose you have N objects that can take on one of q colors. Then, if we want the state space of those N objects, we need to take all combinations of a list of lists, where the sublist are the number of colors (labeled by 0,1,2, etc). Example: we have 3 marbles and 3 possible colors, we need the combinations of this list: [[0,1,2],[0,1,2],[0,1,2]], which will yield [ [0,0,0], [0,0,1], ..., [2,2,2] ]. Follow me? One can see that the output has q^N # of sublists (so for my example 3^3). Here is the python routine that executes this:
[PHP]
def combinations( L ):
    N = len( L )
    if N == 0:
        return []
    elif N == 1:
        return [
        L[0][i:i+1]
        for i in xrange( 0, len( L[0] ) )
    ]
    else:
        return [
            L[0][i:i+1] + subcomb
            for i in xrange( 0, len( L[0] ) )
            for subcomb in combinations( L[1:] )
        ][/PHP]
Since python is great with strings, this code is easy. You can call the example I stated by
[PHP]
>> import combo
>> a = combo.combinations( [[0,1,2],[0,1,2],[0,1,2]])
>> print a [/PHP]
How do I implement something that is string heavy in c++ and save it to memory?

---

### Post by Can+~ on 2009-12-20
Combinatorics, also available in the [itertools module](http://docs.python.org/library/itertools.html#itertools.combinations).

> How do I implement something that is string heavy in c++ and save it to memory?

What do you mean "save it to memory"? Pretty much everything you do on Python or C/C++ exists in memory during execution. Do you want to share memory? I'm not quite sure if you could do that with to different levels of abstraction (Imagine trying to share complex python objects with C simple-minded structs). Maybe what you seek is Interprocess communication (or IPC) with messaging, like [MPI]("http://en.wikipedia.org/wiki/Message_Passing_Interface") modules.

If you wish to code C/C++ modules and integrate them in python, that is possible and not that hard, look at the [documentation about extending and embedding]("http://docs.python.org/extending/index.html").

---

### Post by jsschreck on 2009-12-20
Ideally I am trying to get off Python for the current project I am working on, which diagonalizes large, sparse matrices. Python seems to have served as a good proof-of-concept, up to a ~175,000 x 175,000 matrix, which it apparently is failing to give expected data. Python has easy-to-implement sparse matrix and sparse eigenvalue solver (based on ARPACK). This could be a whole other discussion; I really dont know why Python is giving bad data. All matrix elements are real and positive (non-symmetric). In order to fill out said matrices, I need to run tests over the combinations routine I described in my initial post. All suggestions from friends/colleagues are saying to migrate to c for numerical calculations. I never really learned c(++), but it seems that for the current project is necessary. 

So what I intend to do at this moment is have c++ use ARPACK and SparseLib++ to calculate eigenvalues and write them to disk. Then Python can take over for plots, etc. What I meant by saving the list combo to memory is that I need to enumerate the non-zero matrix elements over that list so I can fill it out numerically. So you can think of the result of combo.py as being placed along the top and left-side of a matrix, which has dimension q^N x q^N. Then each time you compare one element of the list of combos to another, you can determine the numerical value of a matrix element. But I dont need to build that combinations list each time I build the matrix (which can happen many times if its inside a loop), just once as it is being called in Python at the moment. What I would like to get out of my post would be for people to point me to good references, or help me get started with the code (the combo part). The packages I am using have good examples that I am dissecting at the moment. Or if you think what I am doing is totally backwards, any advice!

---

### Post by kwyto on 2009-12-20
i don't know about ARPACK or SparseLib++, but the problem "seems" fairly simple, maybe i'm not getting it. Let me see, you want a program in C/C++ that gives you all the possible combinations of a range of numbers. ex 0-4: 00000, 00001, 00002, ..., 44444, for a 5X5 matrix. if this the case then, i would suggest creating a dynamic matrix NXN and fill it out with all possible combinations. after that you can choose whether to store in a file, as strings, or keep on memory. maybe this can help

---

### Post by jsschreck on 2009-12-20
Yes, I would like to keep it in memory. If I write down the state of two neighboring sites where the state vector = [state of site i, state of site i+1], and each site can access states labeled [0,1,2], you can have can have state vector = { [0,0], [0,1], [0,2], [1,0], [1,1], [1,2], [2,0], [2,1] , [2,2] }.

---

### Post by kwyto on 2009-12-20
you explanation is not clear. i was thinking, and what you should do is a loop from 
0-NXN and get the iterator and convert it to binary that will give you the exact combination you are looking for, eg matrix 3x3 {000, 001, 010, 011, ... 111}. after this save the number in a array of strings. you can do it in python, probably be easier for you.

---

### Post by CptPicard on 2009-12-21
OP, you really should look at **itertools.product** -- it does what I believe you need (cartesian product of iterables)... your current own code looks potentially very slow...

---

