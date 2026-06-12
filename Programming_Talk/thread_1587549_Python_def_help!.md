---
title: "Python def help!"
date: 2010-10-03
forum: Programming Talk
---

### Post by Qualia on 2010-10-03
I just started programming in Python about a week ago, and today I ran into this problem when trying to place a list in a function. I placed two print statements after the function so that I could check if the values were there. 

But when I ran it in IDLE, it gave me and error message saying: 
 ```
NameError: name 'ro' is not defined
```I ended up with same problem when I tried running just the other print statement (print rooms), and got the same error message

Any ideas on what I'm doing wrong?
Here is the program below:
```

# Adobe
#    a text adventure

import random # allows me to userandom integers in program

def setup():
    # set up 2D array/list for room movement
    rooms = [
        [0,2,0,3],
        [1,0,4,5],
        [0,5,0,5],
        [0,0,0,2],
        [3,0,2,0]]
    # set up other variables
    ro = 0 # set starting room to room 0(the first row in array)

setup()
print ro
print rooms

```

---

### Post by dv3500ea on 2010-10-03
'ro' and 'rooms' are local variables to the method 'setup'.

Change the program to something like this:
```

import random # allows me to userandom integers in program

def setup():
    return [
        # set up 2D array/list for room movement
        [
            [0,2,0,3],
            [1,0,4,5],
            [0,5,0,5],
            [0,0,0,2],
            [3,0,2,0]
        ],
        0 # set starting room to room 0(the first row in array)
    ]
a = setup()
print a[1]
print a[0]

```

---

### Post by Qualia on 2010-10-03
Cool, it works now! I get it now! Thanks for the help :)

---

