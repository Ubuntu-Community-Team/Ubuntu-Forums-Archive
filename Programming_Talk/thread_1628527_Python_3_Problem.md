---
title: "Python 3 Problem"
date: 2010-11-22
forum: Programming Talk
---

### Post by timzorr on 2010-11-22
```

n = float(input("Enter the size of the list "))
i = 0
k = n - 1
numericValues = [0]
numericValues[0] = float(input("Enter list element "))
while (i < k):
    i = i + 1
    numericValues.append( float(input("Enter list element ")))

theValues = sorted(numericValues)
if len(theValues) % 2 == 1:
    print(theValues[(len(theValues)+1)/2-1])
else:
    lower = theValues[len(theValues)/2-1]
    upper = theValues[len(theValues)/2]
    print((lower + upper) / 2)
```

Im trying to find the median of a list of numbers but im getting the error code: 
```
lower = theValues[len(theValues)/2-1]
TypeError: list indices must be integers, not float
```

This error only appears in python3 because i have tested it in python 2.6.6 and it worked without any errors. :confused:

---

### Post by s3MA00RRNY on 2010-11-22
Firstly, don't use input() for input, because an evil individual could plug any python expression in there and screw up the program. Use raw_input() instead.

Second, you explicitly requested float, so of course it will convert to a float. Use int() instead.

---

### Post by timzorr on 2010-11-22
I thought input replaced raw_input in Python 3 and im looking to have an output as a float. how would i go about this ?

---

### Post by mo.reina on 2010-11-23
input did replace raw_input in python3.x

if you want to have a float as output, you can just change the last line to this

```
print((lower + upper) / 2.0)
```

this will print out a float.  you can't use a float however for list indexing, so you'll have to change your n variable to a normal integer.

---

### Post by ziekfiguur on 2010-11-23
just use ```
lower = theValues[int(len(theValues)/2-1)]
```

---

### Post by StephenF on 2010-11-23
> **timzorr said:**
> ```
lower = theValues[len(theValues)/2-1]
TypeError: list indices must be integers, not float
```

This error only appears in python3 because i have tested it in python 2.6.6 and it worked without any errors. :confused:

One of the differences between Pythons 2 and 3 is that a calculation such as 3/2 no longer equates to 1 but 1.5 which is what you would get if you had used a calculator. It is also appropriately a float.

What you need to do in your program is use // for floor division. Since the floor of 1.5 is 1 the result can and will arrive in the form of an int, provided both arguments are also ints (3.0//2 equals 1.0, a float).

Python 3's // operator behaves exactly like / does in Python 2.

---

