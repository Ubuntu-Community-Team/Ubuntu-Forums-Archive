---
title: "what does it mean to be work aligned?"
date: 2011-03-18
forum: Programming Talk
---

### Post by cybo on 2011-03-18
i can't seem to get a grasp on what it means to be word aligned? say i have an integer which is 4 bytes in length and a char which is 1 byte in length, word length in my machine is 4 bytes. what would it mean for an integer and a char (i was told it is unusual) to be word aligned?

any help is appreciated

---

### Post by Milliways on 2011-03-18
> **cybo said:**
> i can't seem to get a grasp on what it means to be word aligned? say i have an integer which is 4 bytes in length and a char which is 1 byte in length, word length in my machine is 4 bytes. what would it mean for an integer and a char (i was told it is unusual) to be word aligned?


In this case it means that characters would be stored on 4 byte boundaries in memory.
char a, b ... j [10 chars] would use 40 bytes of memory.

It would be extremely unlikely that you would use it in this case.
It can be important on some processors which perform more efficiently when data is stored on word boundaries.

You would really need to give more information about what you are trying to do.

---

### Post by schauerlich on 2011-03-18
Memory is broken up into various sized chunks, each of which can be fetched separately. At its most basic, memory is addressed at the byte level. However, it's often retrieved from memory at the word level, which just means it grabs 4 bytes at once instead of just the 1. There's also blocks and pages, but we'll ignore that for now. The reason why word alignment is important is that some structures that are larger than 1 byte might cross a word boundary, forcing you to fetch both words in order to get the whole structure.

```
word          0               1               2               3
      |               |               |               |               |
      |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |   |
byte    0   1   2   3   4   5   6   7   8   9   A   B   C   D   E   F
                  { 0 |       1       | 2 }
                      [       1       | 2     ]
```

Now, let's say you have a structure that's 6 bytes long. If you start this structure at byte 3 (curly braces), it will go up to and include byte 8. Now, to read the entire structure, you have to fetch words 0, 1 and 2 (containing bytes 0-B) just to get those 6 bytes. However, if you start at byte 4 (ie align the structure with word 1, square brackets), it will go up to byte 9, and you'll only have to fetch words 1 and 2.

---

### Post by cybo on 2011-03-18
thanks, i got it. i really appreciate it.

---

