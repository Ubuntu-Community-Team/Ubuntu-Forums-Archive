---
title: "Quick Python Random Sort"
date: 2007-09-19
forum: Programming Talk
---

### Post by ablegreen on 2007-09-19
Hi, I'm still learning Python, but I need to know this quickly to study for this math test.

Suppose I have a list:

red
white
blue

I want to store it in a list and print it in a random order.
How do  I do this?

---

### Post by olejorgen on 2007-09-19
```

import random
list = ['red', 'white', 'blue']
random.shuffle(list)
print list

```

---

### Post by ablegreen on 2007-09-19
> **olejorgen said:**
> ```

import random
list = ['red', 'white', 'blue']
random.shuffle(list)
print list

```

Ok thanks!

---

