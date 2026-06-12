---
title: "Problems with Python"
date: 2009-01-25
forum: Programming Talk
---

### Post by artir on 2009-01-25
So I was writing my 1st prime finder sieve like this:

```
hasta=10
numeros=range(2,hasta+1)
lol=numeros
print numeros
for i in numeros:
    for o in numeros:
      quitar=o*i
      
      if quitar   in numeros:
        lol.remove(quitar)    

print lol
print numeros
```

Basically, the resulting primes should go to "lol", but the weird thing is that both "print lol" and "print numeros" return the same, even though I'm not doing anything to numeros but reading the i and o vars. What is that happening?

---

### Post by eightmillion on 2009-01-25
That's because when you assign one list to another, you're copying by reference. You end up with two different names that both refer to the same list. Observe:

```

In [69]: a = range(20)

In [70]: b = a

In [71]: a is b      <----------- a and b are literally the same object
Out[71]: True

In [72]: a[4]="spam" <----------- now I assign the value "spam" to a[4]

In [73]: b           <----------- b now reflects the change
Out[73]: [0, 1, 2, 3, 'spam', 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19]

```

There are many different ways to copy by value. Here's a few:
```

b = list(a)
   OR
b = a[:]
   OR
b = [ i for i in a ]
   OR
from copy import copy
b = copy(a)
   OR
from copy import deepcopy
b = deepcopy(a)

```

---

### Post by artir on 2009-01-26
Thanks!
This is what i did. Is now fully operative. 
[PHP]from copy import copy

hasta=1000
numeros=range(2,hasta+1)
lol=copy(numeros)



        
def calc():
    for x in lol:
        if (numeros[-1]**0.5)< x:
          
         if x%2==0:
            if x!=2:
                
                break
            lol.remove(x)
    for i in lol:
        
        for o in numeros:
          
          quitar=o*i
         
          
          if quitar   in lol:
           
            lol.remove(quitar)
            
            
            
            
calc()
print lol
[/PHP]

---

