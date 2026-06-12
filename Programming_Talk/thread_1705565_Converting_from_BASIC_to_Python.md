---
title: "Converting from BASIC to Python"
date: 2011-03-12
forum: Programming Talk
---

### Post by ki4jgt on 2011-03-12
OK, I'm converting a program which is about 7 months old from BASIC to Python from [http://www.smashindex.org](http://www.smashindex.org)

Here is the code I'm having problems with:
```

import os

CAL = []
INF = []
FRE = []
MOD = []
RST = []
TIM = []
DAT = []
GOT = []

v = 2011
b = v - 1

def cls():
    os.system("clear")
    return "\n"

print "WELCOME TO SMASHINDEX LOGGER " + `v`
print
print """THIS PROGRAM IS FREE SOFTWARE: YOU CAN REDISTRIBUTE IT AND/OR MODIFY
IT UNDER THE TERMS OF THE GNU GENERAL PUBLIC LICENSE AS PUBLISHED BY
THE FREE SOFTWARE FOUNDATION, EITHER VERSION 3 OF THE LICENSE, OR
ANY LATER VERSION.

THIS PROGRAM IS DISTRIBUTED IN THE HOPE THAT IT WILL BE USEFUL
BUT WITHOUT ANY WARRANTY; WITHOUT EVEN THE IMPLIED WARRANTY OF
MERCHANTABILITY OR FITNESS FOR A PARTICULAR PURPOSE. SEE THE
GNU GENERAL PUBLIC LICENSE FOR MORE DETAILS.

YOU MAY VIEW THE GNU GENERAL PUBLIC LICENSE IN IT'S ENTIRETY BY
ENTERING '7' AT THE MAIN MENU"
"""
print "COPYRIGHT (C) " + `b` + "," + `v` + " SMASHINDEX"
print
raw_input("PRESS 'ENTER' TO CONTINUE")

a = "0"

while a != "1" or "2":
    cls()
    
    print "WELCOME TO SMASHINDEX LOGGER " + `v`
    print """
    PLEASE CHOOSE ONE OF THE FOLLOWING OPTIONS:

    1 - CREATE A LOG"
    2 - OPEN A CURRENT LOG"
    """
    a = raw_input("CHOICE: ")

```
I'm having trouble with the log open or create menu.

---

### Post by cgroza on 2011-03-12
Any errors maybe?

Your wile loop must be: ```
while a != "1" or a != "2":
```

Your loop will always evaluate True because "2" is taken as True. I realized that you probably checking a for that "2". That "2" for python is a separate evaluation, and since it is not 0 or False, it is True.

---

### Post by wmcbrine on 2011-03-12
Another way to write that would be:

```
while a not in ('1', '2'):
```

---

### Post by cgroza on 2011-03-12
> **wmcbrine said:**
> Another way to write that would be:

```
while a not in ('1', '2'):
```
Yes, this seems more cleaner.

---

