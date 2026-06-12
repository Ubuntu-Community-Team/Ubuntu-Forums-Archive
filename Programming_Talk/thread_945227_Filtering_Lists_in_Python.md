---
title: "Filtering Lists in Python"
date: 2008-10-12
forum: Programming Talk
---

### Post by era86 on 2008-10-12
I want to remove elements from a list based on some sort of criteria comparing an element to other parts of the list.  I am trying to do this:

[PHP]
for i in list :
    for j in list :
        if j < i : ( remove j from list )
[/PHP]

I'm running into some issues of elements not being removed.  Is there a better way to do this?  Please let me know.  Thanks.

---

### Post by ghostdog74 on 2008-10-12
you must be careful when removing items from list like this.
it seems like you want to get the max number of that list? you can use max() or provide and example of what you want.

---

### Post by pp. on 2008-10-12
Removing elements from the list over which you are iterating does not seem a good idea to me.

---

### Post by ankursethi on 2008-10-12
Use the filter() function. Check out the Python docs for more info, but it works something like this :

```
list = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
filter(function(element), list)
```

Each element of the list is passed to function() once. function() is a function which returns true or false by testing each element according to the condition you specify. filter() returns the new list obtained by removing elements for which function() return false.

---

### Post by pmasiar on 2008-10-12
> **era86 said:**
> I want to remove elements from a list ...I'm running into some issues of elements not being removed.  Is there a better way to do this? 

Yes, there is 8-) 

You should never change list you are iterating through, results are undefined. You need to create another list with only items you want.

---

### Post by snova on 2008-10-12
The last time I tried modifying the list while iterating, it threw an exception.

The only way I know of to do this sort of thing would be to create a new list.

[PHP]
tmp = []
for i in list:
    for j in list: 
        if j >= i:
            tmp.append( j )
list = tmp
del tmp
[/PHP]

No doubt there are more efficient ways. Usage of the filter() function somebody mentioned might go like this:

[PHP]
def decide( tmp ):
    for i in list:
        if tmp < i:
            return False
    return True
list = filter( decide, list )
[/PHP]

---

### Post by era86 on 2008-10-13
> **ankursethi said:**
> Use the filter() function. Check out the Python docs for more info, but it works something like this :

```
list = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
filter(function(element), list)
```

Each element of the list is passed to function() once. function() is a function which returns true or false by testing each element according to the condition you specify. filter() returns the new list obtained by removing elements for which function() return false.

Didn't even know about this.  Thank you so much!

---

