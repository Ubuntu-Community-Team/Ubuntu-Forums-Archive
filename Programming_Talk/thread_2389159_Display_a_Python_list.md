---
title: "Display a Python list?"
date: 2018-04-12
forum: Programming Talk
---

### Post by dannyk2 on 2018-04-12
Hope someone can help me out here

I have been following a tutorial for making a list in Python as follows:

```


I opened a terminal and typed: nano shopping.py

costs = [5, 10, 15, 20, 25, 30, 35, 40, 45, 50]

def sumCart(items):
    totalCost = 0
    for x in costs:
     totalCost += x
    return totalCost

print sumCart(costs)

Now when i call the above function in a terminal using: python shopping.py
275 is displayed

But when i try to open the same file in a terminal using: python3 shopping.py
An error is displayed as followed: 

File "shopping.py", line 11
  print sumCart(costs)

```

I know that i have tried to use two different versions of Python
But would someone tell me how i might get the above function
to display in Python3 please.

---

### Post by &amp;KyT$0P# on 2018-04-12
[FONT=Courier New]print[/FONT] is a function in Python 3, you need to change it to this -
```
print(sumCart(costs))
```

---

### Post by monkeybrain20122 on 2018-04-12
why is the argument items in the first line of the function while the body refers to costs?

also you don't need the loop, just sum(costs) will give 275.

The print statement is also not needed, sum(costs) would return the sum already.

so basically your function is the same as sum() but maybe slower because of loop.

---

### Post by dannyk2 on 2018-04-13
As you both can tell, i have only just started learning Python and i do get a little confused with the Python 2 and Python 3 versions.
But i would like to thank you both for your kind help and advice. Thanks

---

