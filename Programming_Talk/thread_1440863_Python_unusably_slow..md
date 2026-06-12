---
title: "Python unusably slow."
date: 2010-03-28
forum: Programming Talk
---

### Post by weezerBo on 2010-03-28
_***Disclaimer:***_ I realize expecting Python to be as fast as C/C++ is unrealistic. I also realize this is an inherently slow operation.

It takes over 5 minutes to complete this function! The image is 640x480 and contains ~33 blobs. My C++ variant is using an image that is 12000x2000 long and contains infinitely more blobs and is able to complete in under 30 seconds. 


```

 58                   for anchor in image.blobs:
 59                        for compare in image.blobs:
 60                            neighbor = []
 61                            if compare.id == anchor.id:
 62                                continue
 63                            for a in xrange(len(anchor.points)):
 64                                for b in xrange(len(compare.points)):
 65                                    distance = float(sqrt(pow(anchor.points[a][0] - compare.points[b][0], 2) \
 66                                                      + pow(anchor.points[a][1] - compare.points[b][1], 2)))
 67                                    if distance <= 1.5:
 68                                        neighbor.append((anchor.points[a][0], anchor.points[a][1]))
```

.points is a list of 2D points (x,y) that represents a silhouette of each blob. This type of loop is the only way I can think of to compare every point in every blob to each other. I need this to create lists of border line segments which I use for drawing purposes. (attached image below).

Any ideas on how to speed this up in Python? Are there better loop methods?

---

### Post by TheStatsMan on 2010-03-28
Python isn't very fast when it comes to looping (so loops within loops can be a problem). You should write this function in a faster language and just call it from Python. You may have to rethink your algorithm a little, but it should not be hard for a problem like this. One option is to use weave which enables you to use inline C. Another approach could be to use fortran and compile with f2py. You can also use f2py with C it simply requires you to write a Fortran signature file. There are numerous solutions, however those two are the easiest which I have tried.

---

### Post by wmcbrine on 2010-03-28
I think the standard solution for this sort of thing is to use the NumPy or SciPy package, but I never have, so I can't comment further on them.

Python isn't a fast language, period, but I don't think it's correct to say that it has any particular slowness with looping. A loop is just more likely to expose the general slowness, since it's dealing with a lot of repeated operations.

Personally I'd rewrite this snippet in what I think is a slightly more Pythonic way, that I suspect will be faster (not tested, since I don't have the rest of your code):

```
for anchor in image.blobs:
    for compare in image.blobs:
        neighbor = []
        if compare.id == anchor.id:
             continue
        for x1, y1 in anchor.points:
            for x2, y2 in compare.points:
                dx = x1 - x2
                dy = y1 - y2
                if (dx * dx) + (dy * dy) <= 2.25:
                    neighbor.append((x1, y1))
```

---

### Post by lavinog on 2010-03-28
I have noticed that list comprehensions can make a huge difference:
```

datalist = [[ fun(x) for x in data if x==something ]]

```
They are supposed to run at c speed.

---

### Post by weezerBo on 2010-03-28
> **wmcbrine said:**
> I think the standard solution for this sort of thing is to use the NumPy or SciPy package, but I never have, so I can't comment further on them.

Python isn't a fast language, period, but I don't think it's correct to say that it has any particular slowness with looping. A loop is just more likely to expose the general slowness, since it's dealing with a lot of repeated operations.

Personally I'd rewrite this snippet in what I think is a slightly more Pythonic way, that I suspect will be faster (not tested, since I don't have the rest of your code):

```
for anchor in image.blobs:
    for compare in image.blobs:
        neighbor = []
        if compare.id == anchor.id:
             continue
        for x1, y1 in anchor.points:
            for x2, y2 in compare.points:
                dx = x1 - x2
                dy = y1 - y2
                if (dx * dx) + (dy * dy) <= 2.25:
                    neighbor.append((x1, y1))
```
You just got down to 1m40s. :) I think this is about as close as it's going to get using pure python. Also, points is actually an ndarray, I got that wrong earlier. 

I don't know the correct terminology (if someone could point it out that'd be great)  so I'll use VM terms, but I'm wondering when mixing C/C++ with Python if it's better to host in C/C++ (I'm assuming that's possible) and guest in Python or vice versa? I guess whichever you're using most of is the best to host?

by host I mean initial entry point, core, etc.

---

### Post by weezerBo on 2010-03-28
> **lavinog said:**
> I have noticed that list comprehensions can make a huge difference:
```

datalist = [[ fun(x) for x in data if x==something ]]

```They are supposed to run at c speed.
That's something I looked at, but they seem strange and foreign. I can't imagine how they'd work in this instance because of scope issues and it only looks like you call stuff from them, you can't preform multistage operations.

Am I wrong?

---

### Post by lavinog on 2010-03-28
I have been playing around with a couple of things:
```

calculating fun1 : original function
fun1 completed 8.11848306656 secs.
-=-=-=-=-=-
calculating fun2 : removed sqrt
fun2 completed 7.41183280945 secs.
-=-=-=-=-=-
calculating fun3 : removed use of xrange and indexes
fun3 completed 5.88201379776 secs.
-=-=-=-=-=-
calculating fun4 : removed float cast
fun4 completed 4.97397899628 secs.
-=-=-=-=-=-
calculating fun5 : convert pow into ** 
fun5 completed 3.27229404449 secs.
-=-=-=-=-=-
calculating fun6 : use distance function 
fun6 completed 4.23879504204 secs.
-=-=-=-=-=-
calculating fun7 : ignore points already in list 
fun7 completed 4.23956108093 secs.
-=-=-=-=-=-
calculating fun8 : use list comprehension 
fun8 completed 4.35823392868 secs.

```
I haven't validated the data returned but so far fun5 is the best way to go:
```

def fun5(anchor,compare):
    '''convert pow into ** '''
    neighbor = []
    for apoint in anchor.points:
        for cpoint in compare.points:
            sq_distance = ( (apoint[0] - cpoint[0]) ** 2 \
                               + (apoint[1] - cpoint[1]) ** 2 )
            if sq_distance <= 2.25:
                neighbor.append(apoint)
    return neighbor

```

I'll post all of the test code in a little bit.

---

### Post by lavinog on 2010-03-28
another shortcut:
```

calculating fun9 : check axial distance first
132
fun9 completed 2.06948494911 secs.
-=-=-=-=-=-
calculating fun5 : convert pow into ** 
132
fun5 completed 3.27488589287 secs.


```
```

def fun9(anchor,compare):
    '''check axial distance first'''
    neighbor = []
    for apoint in anchor.points:
        for cpoint in compare.points:
            xdelta = apoint[0] - cpoint[0]
            if xdelta > 2 : continue

            ydelta = apoint[1] - cpoint[1]
            if ydelta > 2 : continue
            
            sq_d = ( xdelta ** 2 + ydelta ** 2 )

            if sq_d <= 2.25:
                neighbor.append(apoint)
    return neighbor 

```

---

### Post by weezerBo on 2010-03-28
> **lavinog said:**
> another shortcut:
```

calculating fun9 : check axial distance first
132
fun9 completed 2.06948494911 secs.
-=-=-=-=-=-
calculating fun5 : convert pow into ** 
132
fun5 completed 3.27488589287 secs.


``````

def fun9(anchor,compare):
    '''check axial distance first'''
    neighbor = []
    for apoint in anchor.points:
        for cpoint in compare.points:
            xdelta = apoint[0] - cpoint[0]
            if xdelta > 2 : continue

            ydelta = apoint[1] - cpoint[1]
            if ydelta > 2 : continue
            
            sq_d = ( xdelta ** 2 + ydelta ** 2 )

            if sq_d <= 2.25:
                neighbor.append(apoint)
    return neighbor 

```
45s. :)

---

### Post by weezerBo on 2010-03-28
I can't believe how much of an effect these relatively minor alterations produced. Thanks to all, especially lavinog who has gone above and beyond.

---

### Post by Letrazzrot on 2010-03-28
If you are really going for optimization, you may try to alter the algorithm first before just moving to a different language.  The best way to speed up loops, any loop in any language, is to loop less times (or do less for each loop).  Do you really need to compare *every* coordinate in each list?  lavindog seems to be already on the right track, by eliminating unnecessary operations inside the loop. 

For example, could you divide the blobs into different lists depending on which section of the image they fall in, or pre-process the whole thing into a BSP or other tree-like data structure?   Then you only compare the coordinates that are relatively closer together, eliminating unnecessary comparisons.  Optimizations like these often depend on specifics of the problem, but can speed these things up dramatically.

Of course, you will have to determine what is fast enough and weigh it against effort/complexity.  This sounds suspiciously similar to the age-old collision detection problem in games, where many of these types of comparisons happen in a fraction of each frame.  There are many documented algorithms and approaches.

Sorry if all of this has already occurred to you, I'm just spouting off what my first steps would be if faced with this problem, and hopefully giving you some search terms in case you were interested.  ;)

---

### Post by lavinog on 2010-03-28
I think this might be the best I could do:
```

-=-=-=-=-=-
calculating fun10 : use sort to eliminate xaxis distances
98
fun10 completed 0.690037965775 secs.
-=-=-=-=-=-
calculating fun1 : original function
98
fun1 completed 8.52043914795 secs.

```

```

def fun10(anchor,compare):
    '''use sort to eliminate xaxis distances'''
    # sort points first
    cpoints_sorted = sorted(compare.points)
    
    # make list of sorted x values
    cpoints_x = [ c[0] for c in cpoints_sorted ]
    
    neighbor = []
    for apoint in anchor.points:
        
        # find index range where x values are close
        minx = apoint[0]-2
        maxx = apoint[0]+2
        starti=0  
         
        while starti < len(cpoints_sorted):
            if cpoints_x[starti]>=minx: break
            starti+=1
        
        endi=starti+1 # find index
        while endi < len(cpoints_sorted):
            if cpoints_x[endi]>maxx: break
            endi+=1
        
        for cpoint in cpoints_sorted[starti:endi+1]:
            ydelta = apoint[1] - cpoint[1]
            if ydelta > 2: continue
            
            xdelta = apoint[0] - cpoint[0]
            
            sq_d = ( xdelta ** 2 + ydelta ** 2 )

            if sq_d <= 2.25:
                neighbor.append(apoint)
    return neighbor 

```

The sort function actually does the sort at c speed, so by sorting the list, we can ignore values above and below the index range.

EDIT: I attached the test script I used.

---

