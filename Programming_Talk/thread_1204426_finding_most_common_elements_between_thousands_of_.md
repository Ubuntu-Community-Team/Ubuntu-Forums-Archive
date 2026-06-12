---
title: "finding most common elements between thousands of multiple arrays."
date: 2009-07-04
forum: Programming Talk
---

### Post by dracule on 2009-07-04
Currently I need to find the most common elements in thousands of 
arrays within one large array (arround 2 million instances with ~70k unique elements) 

so I set up a dictionary to handle the counting so when I am 
iterating  I up the count on the corrosponding dictionary element. I then iterate through the dictionary and find the 25 most common elements. the elements are initially held in a array within an array. so I am am just trying to find the most common elements between all the arrays contained in one large array. 
my current code looks something like this: 

d = {} 
for arr in my_array: 
-----for i in arr: 
#elements are numpy integers and thus are not accepted as dictionary keys 
-----------d[int(i)]=d.get(int(i),0)+1 




then I filter things down. but with my algorithm that only takes about1 sec so I dont need to show it here since that isnt the problem. 



But there has to be something better. I have to do this many many 
times and it seems silly to iterate through 2 million things just to get 25. The element IDs are integers and are currently being held in numpy arrays in a larger array. this ID is what makes up the key to the dictionary. 

It currently takes about 5 seconds to accomplish this with my current algorithm. 
So does anyone know the best solution or algorithm? I think the trick lies in matrix intersections but I do not know.


the common elements do not reside in ALL arrays.

I asked around on usenet and came up with this solution:

```
import numpy as np 
import heapq 
def frequency(arr): 
     '''Generate frequency-value pairs from a numpy array''' 
     clustered = arr.flatten() # copy (so can safely sort) 
     clustered.sort() # Bring identical values together 
     scanner = iter(clustered) 
     last = scanner.next() 
     count = 1 
     for el in scanner: 
         if el == last: 
             count += 1 
         else: 
             yield count, last 
             last = el 
             count = 1 
     yield count, last 
def most_frequent(arr, N): 
     '''Return the top N (freq, val) elements in arr''' 
     counted = frequency(arr) # get an iterator for freq-val pairs 
     heap = [] 
     # First, just fill up the array with the first N distinct 
     for i in range(N): 
         try: 
             heap.append(counted.next()) 
         except StopIteration: 
             break # If we run out here, no need for a heap 
     else: 
         # more to go, switch to a min-heap, and replace the least 
         # element every time we find something better 
         heapq.heapify(heap) 
         for pair in counted: 
             if pair > heap[0]: 
                 heapq.heapreplace(heap, pair) 
     return sorted(heap, reverse=True) # put most frequent first.

```

but that is still much too slow.I need to do this operation over 450,000 times and spending 5-15 seconds on each is simply not possible

Any help would be appreciated.

---

### Post by Tony Flury on 2009-07-04
to be honest - maybe you need to redesign your data (and maybe hold it in a fast relational database) in order to make this run quickly.

---

### Post by mdurham on 2009-07-04
Is it possible to sort it first so that common values are clumped together?

---

### Post by unutbu on 2009-07-04
Use numpy's bincount and argsort functions. 

Here is some demonstration code:

[PHP]
#!/usr/bin/env python
import numpy as np
import time

def print_timing(func):
    def wrapper(*arg):
        t1 = time.time()
        res = func(*arg)
        t2 = time.time()
        print '%s took %0.3fms.' % (func.func_name, (t2-t1)*1000.)
        return res
    return wrapper

@print_timing
def generate_array():
    array_length=2000
    num_arrays=1000
    max_value=100000
    arr=(max_value*np.random.random(
        array_length*num_arrays).reshape((num_arrays,array_length))).astype(int)
    print(arr)
    return arr

@print_timing
def dict_method(arr):
    d={}
    for row in arr:
        for i in row:
            d[int(i)]=d.get(int(i),0)+1
    e=d.items()
    e.sort(key=lambda x: x[1])
    print(e[-25:])

@print_timing
def bincount(arr):
    frequency=np.bincount(arr.ravel().tolist(),weights=None)
    most_common_elements=frequency.argsort()  
    print(zip(
            most_common_elements[-25:].tolist(),
            frequency[most_common_elements[-25:]].tolist()))

if __name__=='__main__':
    arr=generate_array()
    print
    dict_method(arr)
    print
    bincount(arr)
    
    
[/PHP]
Result:
```

[[93967 59863  7559 ..., 55995 34016 97269]
 [34103 78041 14693 ..., 19652 61467 29211]
 [26735 15113 29787 ..., 45879 39406  6614]
 ..., 
 [45908 86096 58951 ..., 16211 42942 43897]
 [50365 33661 84628 ..., 31385 97265 73772]
 [43027 16140 78073 ..., 49467  8217 86510]]
generate_array took 137.859ms.

[(69748, 37), (79487, 37), (98324, 37), (1421, 38), (10355, 38), (18942, 38), (31966, 38), (40648, 38), (43017, 38), (56999, 38), (64401, 38), (75608, 38), (97915, 38), (9445, 39), (23740, 39), (25807, 39), (42041, 39), (65916, 39), (68772, 39), (81486, 39), (36302, 40), (98705, 40), (72307, 42), (82403, 43), (85938, 43)]
dict_method took 3989.235ms.

[(15820, 37), (56906, 37), (3490, 37), (10355, 38), (40648, 38), (1421, 38), (64401, 38), (43017, 38), (75608, 38), (56999, 38), (18942, 38), (97915, 38), (31966, 38), (81486, 39), (65916, 39), (23740, 39), (42041, 39), (9445, 39), (25807, 39), (68772, 39), (98705, 40), (36302, 40), (72307, 42), (85938, 43), (82403, 43)]
bincount took 760.972ms.

```

---

