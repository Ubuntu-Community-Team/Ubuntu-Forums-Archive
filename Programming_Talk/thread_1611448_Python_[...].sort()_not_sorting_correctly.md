---
title: "Python [...].sort() not sorting correctly?"
date: 2010-11-01
forum: Programming Talk
---

### Post by flyingsliverfin on 2010-11-01
i have a variable bla = [['0.01', 'x'], ['0.05', 'z'], ['0.17', 'q'], ['0.62', 'v'], ['0.63', 'j'], ['0.69', 'k'], ['1.49', 'u'], ['1.62', 'y'], ['1.65', 'r'], ['1.95', 'g'], ['16.67', 't'], ['2.00', 'e'], ['2.37', 'n'], ['2.55', 'p'], ['2.67', 'd'], ['2.71', 'l'], ['25.60', 'a'], ['3.51', 'c'], ['3.78', 'f'], ['4.37', 'm'], ['4.70', 'b'], ['6.26', 'o'], ['6.29', 'i'], ['6.66', 'w'], ['7.23', 'h'], ['7.76', 's']]

Why are the 16.67 and 25.60 sitting in the middle out of place?
is it because a '6' or '5' comes before a '.' in the sorting algorithm? If so, does it sort in order of the ASCII tables or differently?

thanks

---

### Post by jpkotta on 2010-11-01
You probably want the key= option to sort().  Even better would be to store the numbers as floats instead of strings, because it's almost always a mistake to store numbers as strings.

```
bla.sort(key=lambda x: float(x[0]))
```

---

### Post by flyingsliverfin on 2010-11-01
yea sorry i was just sorting a text file and didn't convert it to floats. if i had done that i guess the problem would have been avoided

---

