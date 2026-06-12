---
title: "print Python list ??"
date: 2011-04-24
forum: Programming Talk
---

### Post by da3klest on 2011-04-24
i am new at Python Programming 
my problem is when i print "list" it show []{}
items = [1,2,3,4,5,6,7,8,9]
when i print it has {[1,2,3,4,5,6,7,8,9]}
i wanna make it show only the number 123456789 

source Code
```

import random
items = [1,2,3,4,5,6,7,8,9,1,2,3]
random.shuffle(items)
algor = ((items[0]*13)+(items[1]*12)+(items[2]*11)+(items[3]*10)+(items[4]*9)+(items[5]*8)+(items[6]*7)+(items[7]*6)+(items[8]*5)+(items[9]*4)+(items[10]*3)+(items[11]*2))
sum = 11 - (algor % 11)
total = items[:],sum
print total

```
please solve this problem for 4 plz

sorry for my Bad english ^^'

---

### Post by MrStill on 2011-04-24
```

total = items[:],sum 

```

This is your issue. You are printing a tuple which contains the list of values and the sum. This is why your output is this:

```

([1, 3, 4, 9, 2, 8, 1, 2, 7, 3, 6, 5], 4)

```
...that is (items[:], sum). Print works on a list by including the '[' and ']' characters; this is why your numbers are surrounded by those characters. If you do not want this you may have to step through your list an construct a string to print:

```

out = ''
for num in items:
   out += str(num) + ' '
print out

```  

There may be a pretty printer for python; but I'm not sure.

---

### Post by simeon87 on 2011-04-24
You can get rid of the tuple by doing this:

```
>>> p = [1,2,3]
>>> print str(p) + " " + str(sum(p))
[1, 2, 3] 6
```

and you can get rid of the list [ ] by doing what MrStill said.

---

### Post by da3klest on 2011-04-24
thanks for MrStill & simeon87 it's work!!  :)

---

### Post by kurum! on 2011-04-24
> **MrStill said:**
> 

```

out = ''
for num in items:
   out += str(num) + ' '
print out

```There may be a pretty printer for python; but I'm not sure.

use join()

---

### Post by simeon87 on 2011-04-24
> **kurum! said:**
> use join()

That would be:

```
' '.join(map(str, items))
```

where items is the list with numbers.

---

### Post by kurum! on 2011-04-24
> **simeon87 said:**
> That would be:

```
' '.join(map(str, items))
```where items is the list with numbers.
that is correct and should be the way if one wants to live in Python land.

---

