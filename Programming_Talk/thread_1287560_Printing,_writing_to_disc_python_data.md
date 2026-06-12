---
title: "Printing, writing to disc python data"
date: 2009-10-10
forum: Programming Talk
---

### Post by jsschreck on 2009-10-10
Hi all,

I am running my code on a cluster at my school. In short, it diagonalizes matrices for different temperature values (the matrices are temperature dependent). So I partition up the temperature range and send off the partitions as jobs to nodes on the cluster. Fine. My problem arises when trying to collect all my data (the eigenvalues). One subtly here is that the cluster may not return the data files in chronological temperature order, which is important since ill be taking derivatives of the evalues. 

Previously I would write to file something like:
print >> outfile, T (the temperature value), logZ, logZ1, logZ2, ...                  (1) 

logZ's are the sums of the eigenvalues raised to some number. Bear in mind this print command is in a T loop which will spit out a data file with a few lines of (1) for different temps. Each node handles a job precisely as the one just stated, so I wind up with a bunch of .dat files that have N number of rows filled with the data as in (1).  From these, I can read line by line each of the data files and write everything into a master file. I can then use the following routine to sort the data based on the first element of each row (the temperature): 

data = sorted(data, lambda x, y: cmp(x[0], y[0]) ) ... where data is my master file.               (2)

This all works fine, but what I really want to store are the eigenvalues themselves (a list, or array), not sums of them (just numbers separated by commas). The eigvals() routine in numpy returns a numpy array of the eigenvalues. So I tried to print something like 

print >> outfile T, vals (an np.array).                  (3)

but I am having a really hard time reading this file back in later and retrieving the data (as well as looping through all the data files and creating one master file). I also cannot sort the master list based on the first element (the temp). I think what I want is something like the following

print >> outfile, T, vals[0], vals[1], ...             (4) 

Now the problem is how do I get the formerly array of eigenvalues down to just a simple listing of them followed by commas that can be written to my outfile? I have tried writing numpy arrays to file, but have been running into problems where the data just copies over itself in the outfile. I have also pickled the data, but cannot seem to get that to work as well. 

I present (4) as what I want mainly because the other small routines have been written already (reading everything into a master file and then the sort based on temp, the first element), and having my data stated above with the logZ's the whole program works. Can anyone give me some suggestions on how to remedy this? The science is all done, now its just data analysis! I can provide more specific details as well upon request.

---

### Post by unutbu on 2009-10-10
[PHP]In [1]: import numpy as np

In [2]: vals=np.array([1,2,3,4])

In [3]: print ', '.join([str(elt) for elt in vals])
1, 2, 3, 4

[/PHP]

---

### Post by jsschreck on 2009-10-10
This would work except that I need the actual numerical values to be floats, not strings. Is it possible to rewrite what you suggested except use float() instead of str()? Or alternatively, how I can convert the output of what you stated into four floats, separated by commas?

---

### Post by unutbu on 2009-10-10
Here is some example code for writing the floats as strings to a plain text file and
then reading them back and converting them to floats:

[PHP]#!/usr/bin/env python
import numpy as np

T=100
vals=np.array([1.5,2.1,3.1,4.4])
outfile=open('outfile','w')
print >> outfile, '%s, %s'%(T,', '.join(['%s'%elt for elt in vals]))
# 100, 1.5, 2.1, 3.1, 4.4

outfile.close()

infile=open('outfile','r')
for line in infile:
    line=line.strip()
    fields=line.split(',')
    T=float(fields[0])
    vals=np.array([float(elt) for elt in fields[1:]])
    print(T)
    # 100
    print(vals)
    # [ 1.5  2.1  3.1  4.4][/PHP]


As you mentioned in your first post, it is also possible to pickle the objects,
avoiding the need to do str() and float() conversion:

[PHP]#!/usr/bin/env python
import numpy as np
import cPickle

T=100
vals=np.array([1.5,2.1,3.1,4.4])

f=file('outfile', 'w')
cPickle.dump((T,vals), f)
f.close()

del T
del vals

f = file('outfile','r')
T,vals = cPickle.load(f)

print(T)
print(vals)[/PHP]


Or, perhaps even better, would be saving the values in a sqlite or mysql database.

---

### Post by Can+~ on 2009-10-10
There are multiple python libraries to achieve this:

[LIST]
[*]Marhsal
[*]Pickle and cPickle
[*]Shelve
[*]Struct
[/LIST]

I particularly like Shelve, as it behaves like a database with python types.

---

### Post by jsschreck on 2009-10-11
unutbu, your suggestions indeed have nearly solved my problems. I have one more small issue, if you could make a suggestion, I woud greatly appreciate it. Essentially what you suggested in your last post has been put into a loop. Recall I need the 'vals' for a bunch of different temperatures, in fact T is my loop iterator. So I have the following small example: 
[PHP]
data = [1,2]
for T in range(len(data)):

    A = numpy.array([[T,1],[1,T]])
    vals = eigvals(A)

    outfile = file("%s.dat" % (T), 'w')
    print >> outfile, '%s, %s'%(T,', '.join(['%s'%elt for elt in vals])) 
    outfile.close() 

bulke = open ( 'totL3.dat', 'w' )
for fileName in glob.glob ( '*.dat' ):                                                  
   file = open(fileName, 'r')
   for line in file:
      print >> bulke, line
bulke.close()

Tlen = range(len(data))
T_list = numpy.array([data])

list = []
infile=open('totL3.dat','r') 
for line in infile: 
    line=line.strip() 
    fields=line.split(',')  
    T=float(fields[0]) 
    vals=numpy.array([float(elt) for elt in fields[1:]]) 
    list.append([T, vals]) 
[/PHP]

The first two segments work just fine. The T loop creates two .dat files with my data: (T, vals). Then, the second loop reads all *.dat files and copies all lines from those files to the master file totL3.dat. This part also works fine for me. The last part, which is what you had suggested, gets hung up apparently on its second pass through with line. You can also see in the third section I am trying to make one array called list which will append all the data together. I get the following error: 

[PHP]
T=float(fields[0]) 
ValueError: empty string for float()
[/PHP]


If I print out fields each time, I get this: 
[PHP]
['0', ' 1.0', ' -1.0']
['']
[/PHP]
I am not so sure how to reconcile this problem, the complications seem to be coming from the fact that the master file is not just a single line. Any suggestions anyone?

---

### Post by unutbu on 2009-10-11
totL3.dat looks like this:
```

0, 1.0, -1.0

1, 2.0, 0.0
```

The extra blank lines are causing the problem.
You can solve the problem by changing
[PHP]
      print >> bulke, line[/PHP]

to
[PHP]
      print >> bulke, line,[/PHP]

The comma at the end of the print statement tells print to not add the extra \n.

Alternatively, you could modify the for-loop at the end:
[PHP]
for line in infile: 
    line=line.strip()
    if not line:
        continue
[/PHP]

---

### Post by jsschreck on 2009-10-12
unutbu, thank you very much, and also others who have looked at this post. Your suggestions have helped me get my code running very nicely now!

---

