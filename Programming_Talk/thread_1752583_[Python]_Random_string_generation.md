---
title: "[Python] Random string generation"
date: 2011-05-08
forum: Programming Talk
---

### Post by ki4jgt on 2011-05-08
How do you generate a random string in Python? Stackoverflow and a couple of other sites suggest a really long line of code to achieve this but when I plug it into Python and (Importing the modules and substituting length) I get errors (Away from console right now)

---

### Post by simeon87 on 2011-05-08
This gives pretty random strings:

```
from hashlib import sha1
from random import random
print sha1(str(random())).hexdigest()
```

---

### Post by ziekfiguur on 2011-05-08
[PHP]import string
import random
size = 20 # or whatever lenght you want your random string to be
allowed = string.ascii_letters # add any other allowed characters here
randomstring = ''.join([allowed[random.randint(0, len(allowed) - 1)] for x in xrange(size)])
print randomstring
[/PHP]
This works too, but also allows you to have other characters than only hexadecimal numbers and can be used to generate strings of any length.

---

### Post by ki4jgt on 2011-05-08
> **ziekfiguur said:**
> [PHP]import string
import random
size = 20 # or whatever lenght you want your random string to be
allowed = string.ascii_letters # add any other allowed characters here
randomstring = ''.join([allowed[random.randint(0, len(allowed) - 1)] for x in xrange(size)])
print randomstring
[/PHP]
This works too, but also allows you to have other characters than only hexadecimal numbers and can be used to generate strings of any length.

Thanks

---

