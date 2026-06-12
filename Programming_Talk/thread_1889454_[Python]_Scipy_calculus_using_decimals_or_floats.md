---
title: "[Python] Scipy calculus using decimals or floats?"
date: 2011-12-01
forum: Programming Talk
---

### Post by kramer65 on 2011-12-01
Hello,

I need to get the Standard Deviation from a list of numbers, which I would normally do like this (using scipy):
```
from scipy import ndimage
normal_list = [-21.50, -1.50, 27.00, -5.00, 16.00]
print(ndimage.standard_deviation(normal_list))
```
Using the [psycopg2 module]("http://initd.org/psycopg/") I now get the list from a Postgres database. This list however, is now in decimals. So I try to get the standard deviation from a list of decimals like this:
```
from scipy import ndimage
from decimal import Decimal
decimal_list = koop_koers = [Decimal('-21.50'), Decimal('-1.50'), Decimal('27.00'), Decimal('-5.00'), Decimal('16.00')]
print(ndimage.standard_deviation(decimal_list))
```
This results however, in the following error:
```
Traceback (most recent call last):
  File "rommelen.py", line 16, in <module>
    print(ndimage.standard_deviation(decimal_list))
  File "/usr/lib/python2.6/dist-packages/scipy/ndimage/measurements.py", line 174, in standard_deviation
    var = variance(input, labels, index)
  File "/usr/lib/python2.6/dist-packages/scipy/ndimage/measurements.py", line 164, in variance
    return _nd_image.statistics(input, labels, index, 2)
RuntimeError: data type not supported
```
So I guess the problem is, that scipy can't work with decimals (which I think is quite weird for a sophisticated scientific module). So I guess there are two options here:
[LIST=1]
[*]**Make scipy work with decimals.** Because I am calculating quite some detailed financial information, this would be my preferred solution (I am only a bit wary of performance, since I am working on something which in my last version which I wrote in php, took more than 20 days to finish). I wouldn't have a clue though how I would be able to do this. Anybody got any suggestions?
[*]**Get floats instead of decimals from the database.** The [psycopg2 package page]("http://packages.python.org/psycopg2/faq.html") says that "*you can register a customized adapter for PostgreSQL decimal type*" as follows:
[/LIST]
```
DEC2FLOAT = psycopg2.extensions.new_type(
    psycopg2.extensions.DECIMAL.values,
    'DEC2FLOAT',
    lambda value, curs: float(value) if value is not None else None)
psycopg2.extensions.register_type(DEC2FLOAT)
```
So I tried to implement this, by pasting this code on the top, and the getting the numbers from the database as follows:
```
normal_list.append(DEC2FLOAT([row['number_from_db']]))
```
This then results in an error saying
```
Traceback (most recent call last):
  File "rommelen.py", line 49, in <module>
    normal_list.append(DEC2FLOAT('none', [row['number_from_db']]))
  File "rommelen.py", line 4, in <lambda>
    lambda value, curs: float(value))
ValueError: invalid literal for float(): none
```
So I guess I have to do something with the "*if value is not None else None*" in the lambda function. I'm kinda lost here however since I don't really get what this actually is saying?

So to come to my questions. Does anybody have any idea how I can solve this issue by either 1) have scipy work with decimals, or 2) by converting the decimals into floats.

All tips and hints are welcome!

---

### Post by karlson on 2011-12-01
Just for my curiosity why not store "double precision" in the database?

---

### Post by kramer65 on 2011-12-01
Hmmmm, I didn't expect the solution to this problem being so simple..  #-o :roll:

Thanks for opening my eyes here!

---

