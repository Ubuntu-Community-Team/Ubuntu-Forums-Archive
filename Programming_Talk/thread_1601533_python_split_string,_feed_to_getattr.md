---
title: "python split string, feed to getattr"
date: 2010-10-20
forum: Programming Talk
---

### Post by junapp on 2010-10-20
Hi,

Using google app engine where an object has properties which are accessed through the standard dot notation.

Using an inventory system of computers as an example

item.formfactor # returns 'slim form'

If one of the properties of a model is a reference property of another model, expanding the dot notation gives the value of the related object.

item.manufacturer.name # returns 'dell'

I have a need for some generic purposes to use getattr
myProp = "formfactor"
getattr(object,myProp) # returns 'slim form' as desired.

myProp = "manufacturer.name"
getattr(object,myProp) # returns an error.

however
getattr(getattr(object,"manufacturer"),"name") # returns dell

My question is how do I manage this? I'd like to have a wrapper of some sort mygetattr which expands the prop argument to chain the getattr calls in this fashion, but can't quite seem to piece it together. Any pointers?

```

def mygetattr(obj,prop):
    # need to amend to allow a dot delimited list in prop
    return getattr(obj,prop)

```

---

### Post by junapp on 2010-10-20
This might be working.
```

def mygetattr(obj,prop):
  if len(prop) == 1:
    return getattr(obj,prop[0])
  else:
    return mygetattr(getattr(obj,prop[0]),prop[1:])

```

---

### Post by DaithiF on 2010-10-20
something like:
```
class Manufacturer(object):
    def __init__(self):
        self.name = 'dell'

class Item(object):
    def __init__(self):
        self.formfactor = 'slim form'
        self.manufacturer = Manufacturer()

def mygetattr(obj, prop):
    if '.' in prop:
        props = prop.split('.')
        child_obj = getattr(obj, props[0])
        return mygetattr(child_obj, '.'.join(props[1:]))
    else:
        return getattr(obj,prop)

if __name__ == '__main__':
    i = Item()

    props = ('formfactor', 'manufacturer.name')
    for prop in props:
        print '%s => %s' % (prop, mygetattr(i, prop))

```

```
$ python mygetattr.py
formfactor => slim form
manufacturer.name => dell

```

---

### Post by junapp on 2010-10-20
I came up with:
```

@register.filter
def mygetattrlist(obj,prop):
	
	if isinstance(prop, list):
		myprop = prop
	else:
		myprop = prop.split(".",3)

	if len(myprop) == 1:
		return getattr(obj,myprop[0])
	else:
		return mygetattrlist(getattr(obj,myprop[0]),myprop[1:])

```
But will look over what you have here. Might be just about the same sort of thing though

---

### Post by junapp on 2010-10-20
yup, going with your solution, as mine seemed to break some other functionality, needed to check for list etc, then blah blah, your's works better as a drop in replacement for my original mygetattr

Thanks!!

---

### Post by junapp on 2010-10-20
```

return mygetattr(child_obj, '.'.join(props[1:]))

```
was the line that had me defeated originally, having to pass the dot delimited list to the function in the recursive call was causing me an issue (didn't know how), so I ended up passing in the list and checking for a list.

Love the internet.

---

### Post by DaithiF on 2010-10-20
just by the way, if you're on python 2.6 or greater, then you can use the inbuilt attrgetter method of the operator module to do this for you:

```

import operator

def myattrgetter(obj, prop):
    return operator.attrgetter(prop)(obj)
```

---

### Post by junapp on 2010-10-20
> **DaithiF said:**
> ... inbuilt attrgetter method ...
perfect; thank you!

---

