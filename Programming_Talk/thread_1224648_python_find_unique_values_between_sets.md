---
title: "python find unique values between sets"
date: 2009-07-27
forum: Programming Talk
---

### Post by lavinog on 2009-07-27
I am working on a python project that involves finding numbers in sets that don't exist in any other set.

The code I have looks like it works, but it seems like there should be an easier way to do this:
(make_unique is the function in question)
```


def make_unique(setdata):
    '''Remove values in each set that exist in another set'''
    keys=setdata.keys()
    
    keys_checked=list() # list of keys that have been checked
    
    notunique=set() # set of values that exist in more than one set
    
    for key1 in keys:
        keys_checked.append(key1)  
        
        for key2 in keys:
            if key2 in keys_checked : continue # skip already iterated key
            
            for n in setdata[key1] : 
                
                if n in notunique : continue # already know it isn't unique
                
                if n in setdata[key2] :
                    notunique.add(n) # n not unique
                    continue
                    
    for key in keys:
        # remove non-unique numbers 
        setdata[ key ] = setdata[ key ] - notunique 
        



def makedata():
    '''Create dictionary of sets for testing'''
    import random
    setdata=dict()
    
    for key in 'abcdef':
        count=random.randrange(1000,10000)
        nlist=set()
        for n in range(count):
            nlist.add(random.randrange(10000) )
        
        setdata[key]=nlist
        
    return setdata



        
def printset(setdata):
    for key in setdata.keys():
        print( key,len( setdata[ key ] ) )          
            
    
setdata=makedata()
printset(setdata)

make_unique(setdata)
print('-'*30)
printset(setdata)

```

---

### Post by Can+~ on 2009-07-27
> **lavinog said:**
> I am working on a python project that involves finding numbers in sets that don't exist in any other set.

A intersect B = Things that are on A and in B.

A intersect B^c = Things that are on A but not on B. Set theory says that this is equal to difference.

[PHP]a = set((1, 2, 3, 4, 5))
b = set((3, 4, 5, 6, 7))

print a - b[/PHP]

Returns set([1, 2]), which are the values on set A that are not on set B.

You can repeat this with the result

[PHP]a = set((1, 2, 3, 4, 5))
b = set((3, 4, 5, 6, 7))
c = set((2, 3, 5, 6, 7))

print a - b - c[/PHP]

Returns set([1]), the only value on set A that is not in B neither C.

(Link: [Set operations]("http://docs.python.org/library/stdtypes.html#set"))

---

### Post by Can+~ on 2009-07-27
I kinda feel bad for the OP, it sucks when you go all out on coding something to realize that there was a one-line solution to it.

---

### Post by lavinog on 2009-07-28
> **Can+~ said:**
> I kinda feel bad for the OP, it sucks when you go all out on coding something to realize that there was a one-line solution to it.
EDIT: at first I didn't think your approach would work, because I was thinking that I needed to return set([1,6]), but I forgot what the original goal was.
I guess it helps to keep the problem straight...thanks

---

### Post by lavinog on 2009-07-28
I figured out my problem, I originally worked out something similar, but it wasn't working because I wasn't copying the sets:
I guess it helps to simplify the problem first.
```

s=[]
s.append( set((1, 2, 3, 4, 5)) )
s.append( set((3, 4, 5, 7)) )
s.append( set((2, 3, 5, 6, 7)) )

s2=[x.copy() for x in s] #need to copy each set not the list
for i in range(len(s)):
    for j in range(len(s)):
        if i==j:continue
        s2[i] -= s[j]
print(s2)

```

---

### Post by CptPicard on 2009-07-28
In the general case, using reduce:

```

def uniques(my_set, others):
    return reduce(lambda x,y: x-y, [my_set]+others)

```

---

### Post by lavinog on 2009-07-28
> **CptPicard said:**
> In the general case, using reduce:

```

def uniques(my_set, others):
    return reduce(lambda x,y: x-y, [my_set]+others)

```

Neat.
It looks like reduce is not standard in python3.

---

### Post by unutbu on 2009-07-28
Gah! No reduce?
	
```

from functools import reduce
```

Phew. :)

See [http://diveintopython3.org/porting-code-to-python-3-with-2to3.html#reduce](http://diveintopython3.org/porting-code-to-python-3-with-2to3.html#reduce)

---

### Post by lavinog on 2009-07-28
I updated my original example:
```

def make_unique(setdata):
    '''Remove values in each set that exist in another set'''
    data={}

    for key1 in setdata.keys():
        
        data[ key1 ] = setdata[ key1 ].copy() # make copy of set
        
        for key2 in setdata.keys():

            if key2 == key1 : continue # skip already iterated key

            # remove original set in key2 from new key1
            data[ key1 ] -= setdata[ key2 ]

    return data

```

It looks like to use the reduce method I have to iterate through with each key as my_set and all others in others.
```

def uniques(my_set, others):
    return reduce(lambda x,y: x-y, [my_set]+others)

s=[]
s.append( set((1, 2, 3, 4, 5)) )
s.append( set((3, 4, 5, 7)) )
s.append( set((2, 3, 5, 6, 7)) )

s2=[]
for a in s:
    b=s[:]
    b.remove(a)
    s2.append( uniques (a,b) )
print(s2)

```
What is the advantage to using reduce?

---

### Post by lisati on 2009-07-28
> **Can+~ said:**
> I kinda feel bad for the OP, it sucks when you go all out on coding something to realize that there was a one-line solution to it.

True: but sometimes it can be helpful to have at least a basic appreciation of the "behind the scenes" stuff. It can help immensely when troubleshooting or designing a routine which is "almost but not quite like" something that comes as standard.

---

### Post by lavinog on 2009-07-28
```

def uniques(my_set, others):
        return reduce(lambda x,y: x-y, [my_set]+others)

def make_unique_2(setdata):
    '''Remove values in each set that exist in another set'''
    data={}

    for key in setdata.keys():
        otherdata = [ setdata[ k ] for k in setdata.keys() if k != key ]
        data[ key ] = uniques( setdata[ key ] , otherdata )

    return data

```

---

