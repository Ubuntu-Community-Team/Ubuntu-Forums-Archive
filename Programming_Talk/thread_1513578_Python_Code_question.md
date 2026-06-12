---
title: "Python Code question"
date: 2010-06-19
forum: Programming Talk
---

### Post by MickSulley on 2010-06-19
Hi,

As part of a Python program I am developing I am reading definitions from a file and creating variables using that info. I read the data from each line in the file into id, code and desc, then - 

            if code == 'Outside':
                Outside = SenObject( id,  code,  desc)
            if code == 'DHW_Main':
                DHW_Main = SenObject( id,  code,  desc)
            if code == 'DHW_Main_Top':
                DHW_Main_Top = SenObject( id,  code,  desc)
            if code == 'DHW_Preheat':
                DHW_Preheat = SenObject( id,  code,  desc)
 
etc. There are many more than that.

Question - is there a more elegant way to do this, maybe an indirect reference something like 

while file
   variablename(code) = SenObject ( id, code, desc)

Thanks
Mick

---

### Post by Tony Flury on 2010-06-19
> **MickSulley said:**
> Hi,

As part of a Python program I am developing I am reading definitions from a file and creating variables using that info. I read the data from each line in the file into id, code and desc, then - 

            if code == 'Outside':
                Outside = SenObject( id,  code,  desc)
            if code == 'DHW_Main':
                DHW_Main = SenObject( id,  code,  desc)
            if code == 'DHW_Main_Top':
                DHW_Main_Top = SenObject( id,  code,  desc)
            if code == 'DHW_Preheat':
                DHW_Preheat = SenObject( id,  code,  desc)
 
etc. There are many more than that.

Question - is there a more elegant way to do this, maybe an indirect reference something like 

while file
   variablename(code) = SenObject ( id, code, desc)

Thanks
Mick

Firstly - when you post code it is better to use the CODE or PHP tags so that the formatting is kept (which is important in python).

I would use a dictionary here

[PHP]
vars = {}
while file:
    ...
    vars[code] = SenObject( id,  code,  desc)
[/PHP]

You can then retrieve the data using : 
[PHP]
vars["DHW_Main"]
[/PHP]

---

### Post by MickSulley on 2010-06-20
Hi Tony,

Thanks for the advice.  I am fairly new to Python and had read about dictionaries but could not really see any practical use for them.  Now I can!  

Brilliant solution, many thanks

Mick

---

### Post by StephenF on 2010-06-20
One other solution if you have a spare class lying around (and who doesn't).
```

>>> class A(object):
...     pass
... 
>>> a = A()
>>> setattr(a, "var", 12)
>>> a.var
12
>>> setattr(A, "classvar", 13)
>>> a.classvar
13

```

---

