---
title: "Parent constructor not invoked with Python"
date: 2013-01-09
forum: Programming Talk
---

### Post by vikkyhacks on 2013-01-09
I have the code

```
class A:
    def __init__(self):
        print('Class A loaded')
        
class B(A):
    def __init__(self):
        print('Class B loaded')


b = B()
```

and this produces the output, 

```
Class B loaded
```

I have more of C and Java background and in them the parent constructor is automatically invoked when the parent class is created, but why not in python. Why is the parent constructor not invoked ???

---

### Post by ofnuts on 2013-01-10
> **vikkyhacks said:**
> I have the code

```
class A:
    def __init__(self):
        print('Class A loaded')
        
class B(A):
    def __init__(self):
        print('Class B loaded')


b = B()
```and this produces the output, 

```
Class B loaded
```I have more of C and Java background and in them the parent constructor is automatically invoked when the parent class is created, but why not in python. Why is the parent constructor not invoked ???

Not in Python: [http://stackoverflow.com/questions/3782827/why-arent-pythons-superclass-init-methods-automatically-invoked](http://stackoverflow.com/questions/3782827/why-arent-pythons-superclass-init-methods-automatically-invoked)

To call your parent class initialisation: [http://stackoverflow.com/questions/2399307/python-invoke-super-constructor](http://stackoverflow.com/questions/2399307/python-invoke-super-constructor)

---

### Post by Bachstelze on 2013-01-10
> **vikkyhacks said:**
> 
I have more of C and Java background and in them the parent constructor is automatically invoked when the parent class is created, but why not in python. Why is the parent constructor not invoked ???

"constructor" in C, really?

---

### Post by vikkyhacks on 2013-01-11
> **Bachstelze said:**
> "constructor" in C c++ actually

---

### Post by MG&amp;TL on 2013-01-11
> **vikkyhacks said:**
> c++ actually

Then be more careful typing here. Bachstelze gets grumpy when people mix C and C++. ;)

---

### Post by vikkyhacks on 2013-01-12
Thanks, and apologies for the late response, I am a bit slow learner and took time for me to understand !!!

):P

---

