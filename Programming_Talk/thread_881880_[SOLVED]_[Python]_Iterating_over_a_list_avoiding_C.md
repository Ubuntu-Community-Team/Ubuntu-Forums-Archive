---
title: "[SOLVED] [Python] Iterating over a list avoiding C-like code"
date: 2008-08-06
forum: Programming Talk
---

### Post by nvteighen on 2008-08-06
Hi,
Travelling on Python from my C experience (I just like to do things in the reversed order), I have noticed the huge difference there is in Python's for-loops compared to C's.

But, for some reason, the loops in this code seem too C-ish to me: I'm still iterating from outside the object. So, is there a more Python-ish way to write the __parse_file() function?

[PHP]
class matrix:
    def __parse_file(self):
        data = self.__filebuf.read().splitlines()
        raw_nodes = []
        for i in range(data.__len__()):
            buf = data[i].split(",")
            for j in range(buf.__len__()):
                buf[j] = int(buf[j])
            raw_nodes += buf
        return set(raw_nodes)
        
    def __matrix_gen(self):
        pass # forget this for a while.

    def __init__(self, filename):
        try:
            self.__filebuf = open(filename, "r")
            self.nodes = self.__parse_file()
            self.adjmatrix = self.__matrix_gen()
            self.__filebuf.close()
        except IOError:
            print "Error while reading file"
[/PHP]

As you see, I'm trying to use Python thinking in Python and not just translating C, which would be really silly. The class is not finished, it's purpose is to organize data into a tree structure, like I did in [this thread]("http://ubuntuforums.org/showthread.php?p=5469976#post5469976") (in C).

Thanks!

---

### Post by unoodles on 2008-08-06
Instead of data.__len__(), use len(data). len is a built-in function.
Also, what is 'i'?
You use data[i], but I don't see 'i' defined anywhere.

---

### Post by nvteighen on 2008-08-06
> **unoodles said:**
> Instead of data.__len__(), use len(data). len is a built-in function.
Also, what is 'i'?
You use data[i], but I don't see 'i' defined anywhere.

'i' was left because of a typo. See the post again; I've fixed it.

EDIT: The idea is that the class opens a file like this:
```

3,5
1,2
2,3
1,5

```
And separates the values, generating a set of unique values.

---

### Post by Wybiral on 2008-08-06
> **nvteighen said:**
> 'i' was left because of a typo. See the post again; I've fixed it.

EDIT: The idea is that the class opens a file like this:
```

3,5
1,2
2,3
1,5

```
And separates the values, generating a set of unique values.

You need a set of unique values from the entire file?

```

values = set()
for line in open("file.txt"):
    for x in line.split(','):
        values.add(int(x))
print values

```

---

### Post by nvteighen on 2008-08-06
> **Wybiral said:**
> You need a set of unique values from the entire file?

```

values = set()
for line in open("file.txt"):
    for x in line.split(','):
        values.add(int(x))
print values

```

Thank you, but now why? Doesn't open() return a file object, so how can line turn into a string? Or the **in open("file.txt")** is hiding a **open("file.txt").next()** method (which does return a string)?

---

### Post by Wybiral on 2008-08-06
> **nvteighen said:**
> Thank you, but now why? Doesn't open() return a file object, so how can line turn into a string? Or the **in open("file.txt")** is hiding a **open("file.txt").next()** method (which does return a string)?

It's the __iter__ method for open. Try this:
```

print list(open("file.txt"))

```
(since any iterable can be passed to list, this works)

It's just a nice abstraction to make it so you don't have to do so much splitting/reading on your own.

You also could use map for the lines:
```

nodes = set()
for line in open("file.txt"):
    nodes.update(map(int, line.split(',')))
print nodes

```

EDIT:

It also is neat because you can do something like index a file by line number...

```

from itertools import count, izip

print dict(izip(count(), open("file.txt")))

```

---

### Post by nvteighen on 2008-08-06
> **Wybiral said:**
> 
It's just a nice abstraction to make it so you don't have to do so much splitting/reading on your own.

You're talking to a guy used to have almost no abstractions available :) Interesting, of course...

Now the issue is generating the adjacency matrix, but I'll try this on my own. Thanks for your help!

---

### Post by pmasiar on 2008-08-06
> **nvteighen said:**
> I'm trying to use Python thinking in Python and not just translating C, 

it is very un-pythonic code. :-)

Use lists and iterators. As Wyb said:

for line in open('file'):

would open file and iterate over lines. List will shrink or expand as needed - thats whole point of using Python: Python will handle for you many details you are used to handle by yourself in C: Not to have to have to worry about all that crap is whole point of using Python!

---

### Post by mssever on 2008-08-06
> **Wybiral said:**
> ```
for line in open("file.txt"):
```
Does this leave the file open (until the program terminated or until it's garbage-collected)? I thought the only way in Python to make files close themselves was to use the with statement.

(I'm used to the Ruby way where if you give a block to File.open, the file is automatically closed when the block returns.)

---

### Post by Wybiral on 2008-08-06
> **mssever said:**
> Does this leave the file open (until the program terminated or until it's garbage-collected)? I thought the only way in Python to make files close themselves was to use the with statement.

(I'm used to the Ruby way where if you give a block to File.open, the file is automatically closed when the block returns.)

You're right, it is better practice to close them, but for simply reading the files it's OK (CPython frees them almost immediately because it uses a pretty straight-forward reference counting for simple objects like that. This wouldn't hold true for something like Jython or any other future platforms... So I should probably get in the habit of closing them myself) Writing them is pretty much a must to close though.

---

### Post by imdano on 2008-08-06
> **Wybiral said:**
> You're right, it is better practice to close them, but for simply reading the files it's OK (CPython frees them almost immediately because it uses a pretty straight-forward reference counting for simple objects like that. This wouldn't hold true for something like Jython or any other future platforms... So I should probably get in the habit of closing them myself) Writing them is pretty much a must to close though.The "with" statement getting added in Python 2.6 (you can use it in 2.5 if you import it from __future__) handles this pretty well.
```
from __future__ import with_statement
with open('some_file', 'r') as f:
    for line in f:
        # do stuff
```The file descriptor gets closed automatically when the code block finishes.  There's more details on advanced usage [here](http://docs.python.org/whatsnew/pep-343.html).

---

### Post by dwhitney67 on 2008-08-06
> **nvteighen said:**
> Hi,
Travelling on Python from my C experience (I just like to do things in the reversed order), I have noticed the huge difference there is in Python's for-loops compared to C's.

But, for some reason, the loops in this code seem too C-ish to me: I'm still iterating from outside the object. So, is there a more Python-ish way to write the __parse_file() function?

[PHP]
class matrix:
    def __parse_file(self):
        data = self.__filebuf.read().splitlines()
        raw_nodes = []
        for i in range(data.__len__()):
            buf = data[i].split(",")
            for j in range(buf.__len__()):
                buf[j] = int(buf[j])
            raw_nodes += buf
        return set(raw_nodes)
        
    def __matrix_gen(self):
        pass # forget this for a while.

    def __init__(self, filename):
        try:
            self.__filebuf = open(filename, "r")
            self.nodes = self.__parse_file()
            self.adjmatrix = self.__matrix_gen()
            self.__filebuf.close()
        except IOError:
            print "Error while reading file"
[/PHP]

As you see, I'm trying to use Python thinking in Python and not just translating C, which would be really silly. The class is not finished, it's purpose is to organize data into a tree structure, like I did in [this thread]("http://ubuntuforums.org/showthread.php?p=5469976#post5469976") (in C).

Thanks!
Thank you for the hint that the code you have provided in in Python.  It would be more helpful if you were to comment your code rather than expect someone to take their precious time to figure out what the he** you are doing.

P.S.  He** = heck

---

### Post by nvteighen on 2008-08-07
> **dwhitney67 said:**
> Thank you for the hint that the code you have provided in in Python.  It would be more helpful if you were to comment your code rather than expect someone to take their precious time to figure out what the he** you are doing.

Quite strange from me; I usually tend to overcomment my code.

And also strange me posting in Python instead of C, isn't it? (considering that we both and Lster are the C-regulars here).

---

### Post by Wybiral on 2008-08-07
> **nvteighen said:**
> And also strange me posting in Python instead of C, isn't it? (considering that we both and Lster are the C-regulars here).

I used to be a C regular here ...

But the kool-aid is good... Very good.

---

### Post by nvteighen on 2008-08-07
> **Wybiral said:**
> I used to be a C regular here ...

But the kool-aid is good... Very good.
Kool-aid? (I googled it and see it's an American soft-drink... but what's the context with this?)

It's pretty nice to be in the C side. You're safe from the usual programming languages' flamewars, which usually involve Python, Perl, Java and C++ with occasional outbreaks because of C#. Something similar occurs with Lisp-hackers.

Well, the Python code was useless :) I mean, my data structure idea was plain wrong. Luckily, I found an article that helped me see the right track (a dictionary to emulate an adjacency list and keep the edges of my graph).

---

### Post by Wybiral on 2008-08-07
> **nvteighen said:**
> Kool-aid? (I googled it and see it's an American soft-drink... but what's the context with this?)

It's a cult reference.

[quote=wikipedia]Having "drunk the Kool-Aid" also refers to being a strong or fervent believer in a particular philosophy or mission — wholeheartedly or blindly believing in its virtues.[/quote]

---

### Post by nvteighen on 2008-08-07
Well, it works now.

I learned a lot of things: for example, how to use an adjacency list for storing a graph, instead of an adjacency matrix (which I used in my C version) And I hope it's Pythonic enough...

If you want to try it, a complying test data file would be (just save it as a text file):
```

1,2
2,3
3,4
1,10
9,10
15,19
3,15

```

Thanks to all!

[PHP]
#!/usr/bin/env python

# tree.py - Displays a tree from data in a file
# Copyright (C) 2008 Eugenio M. Vigo (aka "nvteighen")
#
# This program is free software: you can redistribute it and/or modify it under 
# the terms of the GNU General Public License as published by the Free Software 
# Foundation, either version 3 of the License, or (at your option) any later 
# version.
#
# This program is distributed in the hope that it will be useful, but WITHOUT 
# ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS 
# FOR A PARTICULAR PURPOSE. See the GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License along with 
# this program. If not, see <http://www.gnu.org/licenses/>.

import sys

class graph:
    """ This class represents a graph read from a file in CSV format, where 
    (x, y) means that there's an edge between nodes x, y. Currently, it only
    supports numerical nodes. The graph is abstracted in an adjacency list, 
    saved in the 'adjlist' attribute as a dictionary, with each node as key for
    a list containing all adjacent nodes. The 'queue' attribute can be used to
    keep track of what nodes haven't been visited yet; useful for traversal 
    control. """

    def __init__(self, filename):
        """ The constructor method. It initializes the private file buffer 
        ('__filebuf'). The adjacency list ('adjlist'; actually, a dictionary) is 
        set from reading the file, so it's ready for use in code. The 'queue' is
        also initialized.
        
        ARGS: The data filename as an argument.
        RET: (None). """
        
        try:
            self.__filebuf = open(filename, "r")
            self.adjlist = self.__parse_file()
            self.queue = self.set_queue()
            self.__filebuf.close()
        except IOError:
            print "Error while reading file"

    def __parse_file(self):
        """ This private method reads the file buffer and generates the 
        adjacency list.
        
        ARGS: (None).
        RET: A dictionary containing the adjacency list. """
        
        final = {}
        
        for line in self.__filebuf: 
            # Each line in the file is split and the integers stored in a list.
            buf = list(map(int, line.split(",")))
            
            for i in range(len(buf)):
                # We first check the first value in 'buf'; if there's a key for
                # that node in 'final', we append the *other* value in 'buf' to
                # the value list the key points in 'final'.
                try:
                    final[buf[i]].append(buf[1 - i])
                except KeyError:
                    # If the exception is thrown, we have to create the list
                    # for the key.
                    final[buf[i]] = [buf[1 - i]]
            
        return final
    
    def set_queue(self):
        """ It just fills the queue with a set containing all nodes in the 
        graph. 
        
        ARGS: (None)
        RET: The queue. """
        
        return set(self.adjlist.keys())

# Here begins the test program. The output function is independent of the class
# in purpose to give the client code freedom to choose any way to print the 
# graph.

def output(graph, node, offset = 0):
    """ This prints the graph to screen using one more tab for each children 
    level. 
    
    ARGS: The graph, the current node and (optional), a starting amount of tabs 
    for the first node. """
    
    if node in graph.queue:
        # Only traverse nodes which haven't been visited (i.e. those which 
        # haven't been removed from the queue yet.
        
        print "\t" * offset, node
        graph.queue.remove(node)
        for i in range(len(graph.adjlist[node])):
            # Execute the function recursively for all nodes adjacent to the
            # last printed, increasing offset by one.
            output(graph, graph.adjlist[node][i], offset + 1)

def main():
    """ Main function of the test suit. """
    
    if sys.argv.__len__() != 2:
        print "Usage: tree.py FILE"
        quit()

    mytree = graph(sys.argv[1])
    
    # Arbitrarily, we define the smallest node as root. We can use either 
    # 'min(mytree.queue)' or 'min(mytree.adjlist)' interchangeably.
    root = min(mytree.queue)
    
    for x in range(len(mytree.queue)):
        output(mytree, root)

if __name__ == "__main__": # This prevents execution when importing in console.
    main()
[/PHP]

---

### Post by pmasiar on 2008-08-09
> **nvteighen said:**
> Kool-aid? (I googled it and see it's an American soft-drink... but what's the context with this?)

Don't google: wikipedia is better strat point to a research:

[http://en.wikipedia.org/wiki/Kool_aid#.22Drinking_the_Kool-Aid.22](http://en.wikipedia.org/wiki/Kool_aid#.22Drinking_the_Kool-Aid.22)

"The term is derived from the 1978 cult suicide in Jonestown, Guyana. Jim Jones, the leader of the Peoples Temple, persuaded his followers to move to Jonestown. Late in the year he ordered his followers to commit suicide by drinking grape-flavored Flavor Aid laced with potassium cyanide. "

It's of course a joke - Python in fact IS the best language :-)

---

### Post by LaRoza on 2008-08-09
> **pmasiar said:**
> Don't google: wikipedia is better strat point to a research:

[http://en.wikipedia.org/wiki/Kool_aid#.22Drinking_the_Kool-Aid.22](http://en.wikipedia.org/wiki/Kool_aid#.22Drinking_the_Kool-Aid.22)


Just googled it, wikipedia is first link.

Sometimes I just use google knowing I will be getting wikipedia.

I also found another use for wikipedia, the Hindi version does automatic transliteration in the search and I can type and read Hindi without any special effort.

---

### Post by nvteighen on 2008-08-10
> **pmasiar said:**
> Don't google: wikipedia is better strat point to a research:

[http://en.wikipedia.org/wiki/Kool_aid#.22Drinking_the_Kool-Aid.22](http://en.wikipedia.org/wiki/Kool_aid#.22Drinking_the_Kool-Aid.22)

"The term is derived from the 1978 cult suicide in Jonestown, Guyana. Jim Jones, the leader of the Peoples Temple, persuaded his followers to move to Jonestown. Late in the year he ordered his followers to commit suicide by drinking grape-flavored Flavor Aid laced with potassium cyanide. "

Yes, I've heard about that... though I didn't know how they suicided. A horrible story, of course.

> It's of course a joke - Python in fact IS the best language :-)

My little experience on Python doesn't allow me to have a solid opinion on this.

---

### Post by LaRoza on 2008-08-10
> **nvteighen said:**
> 
My little experience on Python doesn't allow me to have a solid opinion on this.

If only people in general were able to recognize things like this.

---

