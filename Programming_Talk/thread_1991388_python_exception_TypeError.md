---
title: "python exception TypeError"
date: 2012-05-30
forum: Programming Talk
---

### Post by fra11 on 2012-05-30
Dear experts,
I know this might not be the right forum to ask, but anyway, I'm quite new to python and while trying to run my script, I keep receiving the following error message that I don't understand.

Exception TypeError: "argument of type 'NoneType' is not iterable" in <function _remove at 0x2b4e26ab69b0> ignored

using python -v myscript.py the error seems to occur while cleaning os
# cleanup[2] os
Exception TypeError: "argument of type 'NoneType' is not iterable" in <function _remove at 0x2ba1aad019b0> ignored

does anyone know how to solve the issue?

While looking in the internet I came across the following thread but I don't really understand what it means and if it is pertinent to my case

[https://savannah.cern.ch/bugs/?46141](https://savannah.cern.ch/bugs/?46141) 

Thanks a lot

---

### Post by sffvba[e0rt on 2012-05-30
*Thread moved to **Programming Talk**.*


404

---

### Post by Bachstelze on 2012-05-30
Post your code.

---

### Post by trent.josephsen on 2012-05-30
We're not psychic, post your actual code and we might have something.

---

### Post by fra11 on 2012-05-30
Sorry is just that I thought it was a general problem. However here it is, even though it is not really easy to read...

```

import os
import numpy
from MDAnalysis import *
from MDAnalysis.analysis.distances import *
import subprocess
from goto import goto, comefrom, label

Trajectories= ['file.xtc']
Topology= 'file.gro'

u = Universe(Topology, Trajectories)
ref = Universe(Topology)

D=10 #number of clusterfiles
C=3 #num clusters
T=52 #num structures
array=numpy.zeros(T)
cluster=[]
lista = os.listdir('folder')
d = 0
numconst=numpy.zeros([D,1])
same=numpy.zeros([C,T+1,D])
for x in lista:
 array=numpy.loadtxt('./folder/%s' % x)
 array=array.reshape(1,52)
 bins=numpy.zeros([C,T+1])
 struct=[]
 for i in range(C):
  t=0
  clust=[]
  for s in range(T):
   if array[0,s] == i:
    bins[i,t] = s
    clust.append(s)
    same[i,t,d] = bins[i,t]
    t += 1
  struct.append(clust)
  bins[i,T]=t
  numconst[d,0] = t
  same[i,T,d] = t
 cluster.append(struct) 
# print bins
 d += 1
MAX=numpy.max(numconst)
c = 0
label .stepone
F=numpy.int(same[c,T,0])
insieme=[]
for t in range(F):
 step1 = numpy.int(same[c,t,0])
 s = 0
 insieme.append(step1)
 label .steptwo
 step2 = numpy.int(same[c,s,0])
 if step1==step2:
  s += 1
  goto .steptwo
 if step2==0:
  c += 1
  print insieme
  goto .stepone
 d = 0
 label .check
 for c1 in range(3):
  F1 = numpy.int(same[c1,T,d])
  for t1 in range(F1):
   if numpy.int(same[c1,t1,d]) == step1:
    for s1 in range(F1):
     print "prova"
     if numpy.int(same[c1,s1,d])==step2:
      d += 1
      if d < 10:
       goto .check
      elif d == 10:
       insieme.append(step2)
       s +=1
       goto .steptwo
      else:
       print "error!"

```

---

### Post by trent.josephsen on 2012-05-30
Ugh, mathematicians write such terrible code...

... wait, is that... goto? Never mind, you're on your own. Sorry to bother you. *runs*

---

### Post by fra11 on 2012-05-30
physicists too apparently :) 
but I really love goto

---

### Post by trent.josephsen on 2012-05-30
> **fra11 said:**
> physicists too apparently :) 
but I really love goto
Physicist, mathematician... it's all the same to me. I deal with things that do stuff. ;)

---

### Post by fra11 on 2012-05-30
and do you manage to make my program do stuff too?

---

### Post by PeterP24 on 2012-05-30
> **fra11 said:**
> physicists too apparently :) 
but I really love goto

You shouldn't. It makes your program harder to read. Plus it is also so unpythonic.

---

### Post by PeterP24 on 2012-05-30
> **fra11 said:**
> and do you manage to make my program do stuff too?

I'll try to reproduce your problem - as soon as I get that MDAnalysis stuff.

---

### Post by PeterP24 on 2012-05-30
Wow man, your trick really got me :D. I've dealt with the MDAnalysis module installation but in the end:

```
Traceback (most recent call last):
  File "/home/pts/pythw/crappy.py", line 6, in <module>
    from goto import goto, comefrom, label
ImportError: No module named goto
```

Turns out that:

> The "goto" module was an April Fool's joke, published on 1st April 2004. Yes, it works, but it's a joke nevertheless. Please don't use it in real code!

from here:

> [http://entrian.com/goto/](http://entrian.com/goto/)

No wonder the ubuntuforums gurus didn't wanted to be involved in this prank. Man - I suspected goto was a prank for python users - but I totally was fooled by it. LOOOOL :D.

---

### Post by PeterP24 on 2012-05-30
> **trent.josephsen said:**
> Ugh, mathematicians write such terrible code...

... wait, is that... goto? Never mind, you're on your own. Sorry to bother you. *runs*

It turns out he needs biopython and numpy which is a generic numerical python library. I've got MDAnalysis module in order to try to solve his problem, which pulled several more python modules (funny because I already have a lot of python scientific modules installed). I was "Aprilfooled" by the goto module prank although it is 30 May - go figure it out :D. He is not exactly a mathematician and it turns out I am "not exactly" a programmer :D!

---

### Post by fra11 on 2012-05-31
Yeah I had read it was an April's fool but I had used it before and it had worked...ok I'll try to rethink my algorithm without the goto...However, goto is so nice...why can't it be implemented in python for real? ok not really pythonish? numpy was built exactly to deal with matlabish nice  things and add them into python...

I <3 goto :P

---

### Post by PeterP24 on 2012-05-31
> **fra11 said:**
> Yeah I had read it was an April's fool but I had used it before and it had worked...ok I'll try to rethink my algorithm without the goto...However, goto is so nice...why can't it be implemented in python for real? ok not really pythonish? numpy was built exactly to deal with matlabish nice  things and add them into python...

I <3 goto :P

Ok. goto obviously works in python - I never thought that until I saw your post - and the April's fools joke. It is just that nobody (except you) thinks it is a good idea of using it in Python. You can make a position that in a lower level programming language like C, goto may by useful to break from inside a two nested loops. But in your case - jumping back and forth with goto in a language like python is purely ... um ... too much blasphemy. You need to use the language strengths - and goto not only it is not python, but it is a hack (and a bad joke) implemented in python. 

The fact that numpy fulfils a need for a matlab like functionality in Python, doesn't even compare with the fact that the goto module prank fulfils your need for goto (and label) statement in Python. Refactor the code without the goto - it would be easier to debug - basically you have a simple issue but I am not going to install the goto module to see in the current version of your program what is wrong.

---

### Post by Tony Flury on 2012-05-31
> **fra11 said:**
> Yeah I had read it was an April's fool but I had used it before and it had worked...ok I'll try to rethink my algorithm without the goto...However, goto is so nice...why can't it be implemented in python for real? ok not really pythonish? numpy was built exactly to deal with matlabish nice  things and add them into python...

I <3 goto :P

goto is a really bad idea in any programming language - as it leads to badly structured code.

It looks like you need loops - you are using for loops, why not using a while loop too, and maybe some functions.

As for your original error - I would imagine that somewhere you iterate on what you think is a list - but actually that list has never been initialised (hence the NoneType in the error message). Where exactly the error is I can't tell you because :
[LIST=1]
[*]Your code is so badly laid out (with no comments) it is almost impossible to read
[*]Your use of goto makes your code even more complex
[/LIST]

---

### Post by trent.josephsen on 2012-05-31
It would also be helpful to rename your variables more descriptively.

```
D=10 #number of clusterfiles
```
You wouldn't need that comment, and your code would be easier to read, if you just called the variable num_files or something similar.

---

