---
title: "Python Learning"
date: 2011-09-30
forum: Programming Talk
---

### Post by KeNtUrKeY on 2011-09-30
Hi everybody, 
Im pretty new (or u can say that completely new) to python and i try to learn from the very basic. I try to create grid data structure from array. Here i have some code, would you mind to look at it and give me an instruction:

```

import math
 
class Grid(object):
def __init__(self, width = 10, height = 10):
self.width = width
self.height = height
self.size = size
self.grid = []
cell_value = 0
 
.....

```
then i got stucked, i would like to print out this array and then save it into text file! i look some place and it gave me this 

```

import numpy as np
x = np.arange(20).reshape((4,5))
np.savetxt('test.txt', x)

```
but i dont know how to print it then save it into text file
if i have value with coordinate (x,y) later, can i change it in text file? and how?

thank you very much, it will be helpful

---

### Post by cgroza on 2011-09-30
By grid data structure I suppose you mean a 2 dimensional array.
So self.grid should be:
```

self.grid = [[]]

```
So to print it out you should do something like this:
```


for i in self.grid:
     for k in i:
           print k


```

Writing it to a file should be easy, the harder part will be to read it back.

---

