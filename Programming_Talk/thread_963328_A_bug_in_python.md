---
title: "A bug in python?"
date: 2008-10-30
forum: Programming Talk
---

### Post by Xavieran on 2008-10-30
I'm running python 2.5.2 and I think I may have found a bug...

When I run:
```
isinstance(True,int)
```

python returns True...
it also returns true when I substitute False for True...

Is this a bug?
Or was this intended?

---

### Post by Delever on 2008-10-30
The Boolean type is a subclass of the int class so that arithmetic using a Boolean still works.

---

### Post by Xavieran on 2008-10-30
Seems a bit strange though, In my app I need to distuinguish between int and bool...

```
def opposite(x):
    '''Return the opposite of x.'''
    if x:
        if isinstance(x,bool):return False
        elif isinstance(x,int):return 0
        
    else:
        if isinstance(x,bool):return True
        elif isinstance(x,int):return 1
```

I've switched the order of ifs so it works correctly...
But it seems rather strange...:confused:

---

### Post by geirha on 2008-10-30
I don't understand why you have to distinguish between bool and int. They are both ints ...
```
>>> True+True
2

```

---

### Post by ghostdog74 on 2008-10-30
> **Xavieran said:**
> I'm running python 2.5.2 and I think I may have found a bug...

When I run:
```
isinstance(True,int)
```

python returns True...
it also returns true when I substitute False for True...

Is this a bug?
Or was this intended?

True has value of 1, False is 0. So what is wrong that you think its wrong?

---

### Post by slavik on 2008-10-30
err, shouldn't true+true be invalid in Python since it isn't duck typed?

---

### Post by Delever on 2008-10-30
> **slavik said:**
> err, shouldn't true+true be invalid in Python since it isn't duck typed?

This is good read if you are interested:

[http://www.python.org/dev/peps/pep-0285/](http://www.python.org/dev/peps/pep-0285/)

---

### Post by loell on 2008-10-30
maybe use **isnum**? or sumpin equivalent.

---

### Post by slavik on 2008-10-30
> **Delever said:**
> This is good read if you are interested:

[http://www.python.org/dev/peps/pep-0285/](http://www.python.org/dev/peps/pep-0285/)
thanks for the link ... it clears up the decision up a bit ...

---

### Post by loell on 2008-10-30
> **loell said:**
> maybe use **isnum**? or sumpin equivalent.

```
def isnum(x) :  
#     """Return true if x is a number."""  
        try :  
         return complex(x) == x  
        except Exception :  
         return False  
```

---

