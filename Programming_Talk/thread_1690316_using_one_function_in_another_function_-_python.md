---
title: "using one function in another function - python"
date: 2011-02-18
forum: Programming Talk
---

### Post by Bigmon on 2011-02-18
I wonder if anyone can help. I am quite simply, trying to use one function within another in python but am doing something quite wrong, but am not sure what:

```

def convert_mileage(miles):
    convert_to_km = miles * 1.609344
    next = 100/convert_to_km
    next_1 = next * 4.54609188
    print (next_1)


def litres_needed(km):
    x = convert_mileage(30)
    y = (km/100)* x
    print (y)

litres_needed(150)

```

I get an error:

   y = (km/100)* x
TypeError: unsupported operand type(s) for *: 'float' and 'NoneType'

---

### Post by Arndt on 2011-02-18
> **Bigmon said:**
> I wonder if anyone can help. I am quite simply, trying to use one function within another in python but am doing something quite wrong, but am not sure what:

```

def convert_mileage(miles):
    convert_to_km = miles * 1.609344
    next = 100/convert_to_km
    next_1 = next * 4.54609188
    print (next_1)


def litres_needed(km):
    x = convert_mileage(30)
    y = (km/100)* x
    print (y)

litres_needed(150)

```

I get an error:

   y = (km/100)* x
TypeError: unsupported operand type(s) for *: 'float' and 'NoneType'

You need to do "return next_1" in the first function, otherwise it returns None.

---

### Post by Bigmon on 2011-02-18
Many thanks !!!

---

