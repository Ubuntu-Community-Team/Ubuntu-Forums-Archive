---
title: "Python problems.."
date: 2010-03-19
forum: Programming Talk
---

### Post by goseph on 2010-03-19
Hi everyone!

I'm attempting to make a program to draw some graphs for me but am having teething troubles.

Here is what happens when I run:

```

luke@brick:~/Documents/Auto-Grapher$ python graph.py
Traceback (most recent call last):
  File "graph.py", line 15, in <module>
    g.makegraph()
  File "graph.py", line 10, in makegraph
    Vg = d.data[1]
IndexError: index out of bounds

```


So it seems that the interpreter refuses to look at "data" because it was previously declared as being too small, but it is resized at run-time. Any bright ideas? (or simple ones)




here is my sauce:

graph.py:

```

import read
import plot

class Grapher:
    def makegraph(self):
        d = read.Datareader()
        data = d.readdata("/home/luke/Documents/Auto-Grapher/12 March/Device 1/Channel 1/Vg-Id 60V")
        Vg = d.data[1]
        Id = d.data[2]
        plotdata(Vg, Id)
        
g = Grapher()
g.makegraph()

```


```

import scipy

class Datareader:

    # Array containing array of column data read from datafile
    data = scipy.zeros((1,1))

    def readdata(self,path):
        # File containing Vg-Id data and related parameters
        datafile = open(path, 'r').readlines()
        numberofcolumns = 6
        # Row to start reading from
        rowstart = 1
        numberofrows = len(datafile)-rowstart
        
        data = scipy.zeros((numberofcolumns, numberofrows))

        # Read in a line of data at a time
        for rowindex in range(rowstart,numberofrows+1):
            # dataline is an array of the data on row $rowindex
            dataline = datafile[rowindex].split('\t')
            # print dataline
            # Read each datum into the array of data)
            for columnindex in range(0,numberofcolumns):
                data[columnindex][rowindex-rowstart] = dataline[columnindex]

```

---

### Post by soltanis on 2010-03-19
Wild guess because I don't know what's going on, but Python indexes from 0 (do you want data[0] and data[1]?) and you might want just data, instead of d.data (which is a property of d)?

---

### Post by goseph on 2010-03-19
I can assert that "data" is filled up with a 6 x 100 array of floats before

data[1] and data[2] should, in my book, reference the 2nd and 3rd columns in the 6x100 array.

I have had a thought that, it is possible that the problem is one of scope, I shall investigate and report back.

---

### Post by goseph on 2010-03-19
Yes!

It was simply an issue of range,

The problem was that inside the method where I read all the data into my array, i created a new variable called "data" instead of writing to the class variable.

This problem could be fixed therefore by explicitly putting "self.data" in the code above when it is ambiguous.

---

