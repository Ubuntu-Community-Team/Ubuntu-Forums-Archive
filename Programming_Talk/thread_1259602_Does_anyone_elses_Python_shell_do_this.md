---
title: "Does anyone elses Python shell do this?"
date: 2009-09-06
forum: Programming Talk
---

### Post by filifunk on 2009-09-06
Here's what I've been doing in ipython:

```


In [17]: fcsv = open('/home/petemondejar/Desktop/tobuy.csv')

In [18]: for row in csv.DictReader(fcsv):
   ....:     print "Please buy ", row['Count'], row['Item']
   ....:     
   ....:     
Please buy  2 Milk
Please buy  12 Eggs
Please buy  5 tomatoes

In [19]: fcsv
Out[19]: <open file '/home/petemondejar/Desktop/tobuy.csv', mode 'r' at 0x9aca570>

In [20]: for row in csv.DictReader(fcsv):
   ....:     print "Please buy ", row['Count'], row['Item']
   ....:     
   ....:     

In [21]: 


```

as you can see, In [18] does exactly what I want it to do.  It prints off 'Please buy....etc.'  However, when I do the same thing over again in In[20], it doesn't print it anymore.  Why does it do this?  I wanted it to print it again.

---

### Post by bear24rw on 2009-09-06
You can try re opening the file or try setting row = None before the loop..

---

### Post by Can+~ on 2009-09-06
[PHP]fcsv.seek(0)[/PHP]

[seek]("http://docs.python.org/library/stdtypes.html#file.seek") before the second try.

---

