---
title: "[SOLVED] Check this little chunk of Python code. What's wrong?"
date: 2008-10-19
forum: Programming Talk
---

### Post by Brain-free on 2008-10-19
I'm new to Python language and I'm doing some exercises to get more familiar with it. Part of them is making a code that passes this doctest. My problem is with the last part of the doctest, where it checks if the initial list has changed in the course of the program. It always fails, even though I'm careful not to alias the lists involved. The code is here:

```
def add_column(matrix):
    """
      >>> m = [[0, 0], [0, 0]]
      >>> add_column(m)
      [[0, 0, 0], [0, 0, 0]]
      >>> n = [[3, 2], [5, 1], [4, 7]]
      >>> add_column(n)
      [[3, 2, 0], [5, 1, 0], [4, 7, 0]]
      >>> n
      [[3, 2], [5, 1], [4, 7]]
    """
    a = matrix[:]
    for i in range(len(a)):
        a[i] += [0]
    return a

    

if __name__ == '__main__':
    import doctest
    doctest.testmod()

```

After one very frustrating hour I noticed that if I change the line "a[i] += [0]" to "a[i] = a[i] + [0]", it passes the doctest. 

So my question is this: What justifies this behavior? Since **a** isn't aliased with **matrix**, how can this happen?

---

### Post by y-lee on 2008-10-19
Hmm interesting another python gotta :)

The way i see this is you are passing a list containing lists to the function add_column. The statement a = matrix[:] copies the values of what matrix contains to a. BUT what matrix contains is references to three lists, in the case of calling add_column(n) with n = [[3, 2], [5, 1], [4, 7]]. Only the references to the three lists [3,2] and [5,1] and [4,7] are copied into a **not** the values of these list. So your statement  a[i] += [0] actually is changing these three list which are the same three list contained in n.

But if you change a[i] += [0] to a[i] =a[i]+[0]
then the new a[i] is set to a[i]+[0] which is a newly created list. and hence a ends up with all new lists and n remains unchanged.

A bit confusing but I think that is it.:)

---

### Post by BackwardsDown on 2008-10-19
y-lee:
After reading this thread I also started to tinker with this code but I could not find out what was wrong. But your explanation is very clear and sounds logical.

Can the line:
    a = matrix[:]
be rewritten so that it does make a copy of all the variables?

---

### Post by WW on 2008-10-19
> **y-lee said:**
>  Only the references to the three lists [3,2] and [5,1] and [4,7] are copied into a **not** the values of these list.
To use the Python lingo, **a** is a *shallow copy* of **matrix**.

You can use deepcopy:
```

import copy

a = copy.deepcopy(matrix)

```

---

### Post by BackwardsDown on 2008-10-19
This works ok: (edit: same solution as WW)

```
import copy

def add_column(matrix):
    """
      >>> m = [[0, 0], [0, 0]]
      >>> add_column(m)
      [[0, 0, 0], [0, 0, 0]]
      >>> n = [[3, 2], [5, 1], [4, 7]]
      >>> add_column(n)
      [[3, 2, 0], [5, 1, 0], [4, 7, 0]]
      >>> n
      [[3, 2], [5, 1], [4, 7]]
    """
    a = copy.deepcopy(matrix)
    for i in range(len(a)):
        a[i] += [0]
    return a

    

if __name__ == '__main__':
    import doctest
    doctest.testmod()
```

---

### Post by Can+~ on 2008-10-19
One of the great things about python, is that you don't need the 0..n iterator, you can do it with the __iter__ description of each object, lists included, so instead of doing an xrange or range, use:

[PHP]def add_column(matrix): #passing argument as reference
	for column in matrix: #yay, iterators.
		column.append(0) # or += [0], same thing[/PHP]

Also, this doesn't make a deepcopy, it just modifies the list in-place (like passing a pointer in C):

[PHP]x = [[1, 2],[3, 4]]
add_column(x)
print x[/PHP]

---

### Post by Brain-free on 2008-10-19
First things first, thanks for taking the time to take a look at my code. BTW, it's licensed under EULA so no guys, you can't use it for free...

> **y-lee said:**
> Hmm interesting another python gotta :)

The way i see this is you are passing a list containing lists to the function add_column. The statement a = matrix[:] copies the values of what matrix contains to a. BUT what matrix contains is references to three lists, in the case of calling add_column(n) with n = [[3, 2], [5, 1], [4, 7]]. Only the references to the three lists [3,2] and [5,1] and [4,7] are copied into a **not** the values of these list. So your statement  a[i] += [0] actually is changing these three list which are the same three list contained in n.

But if you change a[i] += [0] to a[i] =a[i]+[0]
then the new a[i] is set to a[i]+[0] which is a newly created list. and hence a ends up with all new lists and n remains unchanged.

A bit confusing but I think that is it.:)

Got it. It's one of these tiny little things that can ruin your program in the worst possible way. Thanks again for the insightful explanation.

---

