---
title: "Python Basic Function question"
date: 2011-05-20
forum: Programming Talk
---

### Post by pafoo on 2011-05-20
I (after many pain staking hours) created a basic function that takes a list as a argument and randomises it and returns the new list. I FINALLY figured out how to make it work, but I was looking for some advice on how I could of made the function more intelligent.  Any advice would be appreciated.

```


def listmix(the_list):
    import random
    first_word = random.choice(the_list)
    scrable = []
    scrable.insert(0, first_word)
    while len(scrable) != len(the_list):
        word = random.choice(the_list)
        if word not in scrable:
            scrable.append(word)
    
    
    return scrable

```

---

### Post by DaithiF on 2011-05-20
Hi, you could use the built-in shuffle method of the random module rather than coding your own.

```
random.shuffle(the_list)
```

---

### Post by cgroza on 2011-05-20
> **DaithiF said:**
> Hi, you could use the built-in shuffle method of the random module rather than coding your own.

```
random.shuffle(the_list)
```
Beat me to it.:D:P

---

### Post by Reiger on 2011-05-20
Well, to start what you are really seem to be working with is sets and not lists[*]. Additionally consider that random.choice(the_list) is likely to end up returning the same item as least once for suitably large lists when you can avoid that. This should reduce the number of iterations in the for loop required until you have the result. 

* By the by if you did intend to work with lists think about what would happen if you accidentally passed in a list like this:
```

mixed = listmix(['spam', 'spam', 'eggs', 'ham'])

```

---

### Post by pafoo on 2011-05-20
random.shuffle... your kidding me hah. Thank you. 

One question, what do you mean I was working with sets, not lists? The intent was to work with lists.

---

### Post by simeon87 on 2011-05-20
> **pafoo said:**
> random.shuffle... your kidding me hah. Thank you. 

One question, what do you mean I was working with sets, not lists? The intent was to work with lists.

Technically you are working with lists but what Reiger meant is that your function behaves as if it was a set. Your function won't work properly if a word is present multiple times in the list. That's because you are doing:
```
if word not in scrable:
``` as a condition for appending the word. This means word can only occur once.

---

### Post by StephenF on 2011-05-20
If random.shuffle did not exist...
```

import random

def listmix(seq):
    n = len(seq)
    while n:
        n -= 1
        seq.append(seq.pop(random.randint(0, n)))
    return seq

```

---

