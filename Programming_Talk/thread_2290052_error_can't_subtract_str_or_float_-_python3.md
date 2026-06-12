---
title: "error: can't subtract str or float - python3"
date: 2015-08-08
forum: Programming Talk
---

### Post by huff2 on 2015-08-08
I'm trying to get this piece of code to work:
```
"""
Income Tax Calculator.py
"""
tax_rate = .20
standard_deduction = 10000
dependent_deduction = 2000
standard_deduction = float(standard_deduction)
dependent_deduction = float(dependent_deduction)
grossIncome = input ("enter gross income: ")
numDependents = input ("enter number of dependents: ")
taxable_income = (grossIncome - standard_deduction) - (dependent_deduction * numDependents)
incomeTax = (taxable_income * tax_rate)
print(incomeTax)
incomeTax = round(incomeTax, 2)
print ("your income tax is: $%r" % (incomeTax))


```

I get this error:
```
>>> 
enter gross income: 737574635
enter number of dependents: 2
Traceback (most recent call last):
  File "C:\Users\John\Desktop\New folder\income tax calculator.py", line 16, in <module>
    taxable_income = (grossIncome - standard_deduction) - (dependent_deduction * numDependents)
TypeError: unsupported operand type(s) for -: 'str' and 'float'
>>> 

```

I can't figure out why. Can anybody help me?

---

### Post by kostkon on 2015-08-08
Well, either evaluate the input value, like input() in python2 does
e.g.
```
grossIncome = eval(input ("enter gross income: "))
```
but it's better to just convert it to float
e.g.
```
grossIncome = float(input ("enter gross income: "))
```

---

### Post by huff2 on 2015-08-08
Great! Thanks!

---

