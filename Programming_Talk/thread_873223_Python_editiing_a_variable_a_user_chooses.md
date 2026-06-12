---
title: "Python editiing a variable a user chooses?"
date: 2008-07-28
forum: Programming Talk
---

### Post by jacensolo on 2008-07-28
I want have a class setup with an __init__ functions that assigns attributes to the object which the user chooses. Later, the user may want to change the attributes. I want to have an edit function that asks which attribute to edit. How can I do that without writing out a bunch of if statements?

Simple Ex:
```

def __init__(self):
     self.x = raw_input()
     self.y = raw_input()
def edit(self):
    h = raw_input("what do you want to change?")
    self.(("h?")) = raw_input(h, 'is now...')    - *I know that raw_input only takes 1 argument.*
```

---

### Post by slavik on 2008-07-28
since I know Perl, I would set up a hash (I think they are called dictionaries in Python) and have the variable be a key. :)

someone with Python knowledge should be able to show you some code to accomplish this.

---

### Post by jacensolo on 2008-07-28
> **slavik said:**
> since I know Perl, I would set up a hash (I think they are called dictionaries in Python) and have the variable be a key. :)

someone with Python knowledge should be able to show you some code to accomplish this.

Sounded good. I tried it, but couldn't figure out how to do it with the self in front of it.

Any Python users want to give me some advice? Appreciated.

---

### Post by Torajima on 2008-07-28
> Any Python users want to give me some advice? Appreciated.

Try this:

```
def __init__(self):
    self.variables = {}
    self.variables['x'] = raw_input()
    self.variables['y'] = raw_input()
def edit(self):
    h = raw_input("what do you want to change?")
    self.variables[h] = raw_input('%s is now...' %h)
```

---

### Post by days_of_ruin on 2008-07-28
Simple.For every variable you declare just add it to a dictionary
```
self.vars = {}
somvar = 10
self.vars['somvar'] = somvar
```

---

### Post by days_of_ruin on 2008-07-28
> **jacensolo said:**
> I want have a class setup with an __init__ functions that assigns attributes to the object which the user chooses. Later, the user may want to change the attributes. I want to have an edit function that asks which attribute to edit. How can I do that without writing out a bunch of if statements?

Simple Ex:
```

def __init__(self):
     self.x = raw_input()
     self.y = raw_input()
def edit(self):
    h = raw_input("what do you want to change?")
    exec("self."+h+" = raw_input(h+' is now...')")    - *Fixed*
```

That should work too;)If it doesn't its because I posted it wrong:P

---

