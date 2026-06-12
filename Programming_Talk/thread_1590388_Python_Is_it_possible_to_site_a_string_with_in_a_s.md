---
title: "Python: Is it possible to site a string with in a string?"
date: 2010-10-07
forum: Programming Talk
---

### Post by BlackRat90 on 2010-10-07
I want to be able to have a string with in a string.
```
Example:

food = ['Mexican','Italian']
Mexican = ['Tacos','Burritos']

print "My favorite food is:", food[0]

OUTPUT:

My favorite food is: ['Tacos','Burritos']


```

Is it possible to do this??

---

### Post by Queue29 on 2010-10-07
Take a look at the dict type.

[http://docs.python.org/library/stdtypes.html#dict](http://docs.python.org/library/stdtypes.html#dict)

---

### Post by epicoder on 2010-10-07
This is possible, and is called nesting. Instead of a string, you can use a variable name to include it in a list. To use your example:
[PHP]
Mexican = ['Tacos','Burritos']
food = [Mexican,'Italian']

print "My favorite food is:", food[0]
[/PHP]OUTPUT:

My favorite food is: ['Tacos', 'Burritos']

Note the lack of quotes around Mexican in the food variable.

---

### Post by nvteighen on 2010-10-08
I'd go for a dictionary here. It's much clearer and explicit and allows to do some nice things. Look at this:

```

#!/usr/bin/env python

def main():
    food = {"mexican" : ["Tacos", "Burritos"],
            "italian" : ["Pizza", "Spaghetti", "Stromboli"]}

    choice = raw_input("What's your favorite food? ")

    # choice.lower() returns your input in lowercase... that makes this program
    # case non-sensitive.
    print("Your favorite food is: %s" % food[choice.lower()])

if __name__ == "__main__": # Prevents execution when importing this module
    main()

```

A dict is like an array, but instead of accesing the items by index, you do it by key. So, using strings as keys allows you to ask for input and use the very same input as the key for the data you want.

---

