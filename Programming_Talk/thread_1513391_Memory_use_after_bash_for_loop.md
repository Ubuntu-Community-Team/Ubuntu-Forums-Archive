---
title: "Memory use after bash for loop"
date: 2010-06-19
forum: Programming Talk
---

### Post by lavinog on 2010-06-19
I just noticed something in bash.
If I use a for loop with {a..b}, memory is used and never freed.

For instance the following command will cause bash to use 187M of memory, and there doesn't seem to be a way to recover that memory unless you close the terminal or logout of that session.
```

for x in {1..1000000};do :;done

```

using seq seems to work better in speed and only uses 103M in this case:
```

for x in $(seq 1 1000000);do :;done

```

I understand that the list will take up this memory during the for loop, but I don't understand why it isn't released when the command completes.

---

### Post by Compyx on 2010-06-20
This issue has been reported on launchpad: [https://bugs.launchpad.net/ubuntu/+source/bash/+bug/82123]("https://bugs.launchpad.net/ubuntu/+source/bash/+bug/82123"). It seems the bash maintainers don't see this as a problem, so I don't expect this will get fixed soon. Then again, since there isn't a memory leak, just a lot of memory consumption where you wouldn't expect it, I wouldn't worry about it too much.

It appears dash does free the memory used after such a loop, so if you have scripts that use such loops, perhaps using dash for those scripts might be a 'solution'.

And to be honest: on modern hardware sporting multiple gigabytes of memory, what is 187MB anyway ;)

---

### Post by simeon87 on 2010-06-20
You seem to be arguing that it's not really a problem. I would say this is indeed a memory leak: memory is leaked when an application doesn't give (all) the memory back.. in this case, none is given back until you kill it.

---

### Post by Compyx on 2010-06-20
But it isn't really a leak, the memory is freed by bash when bash exits. Of course, it would make sense to free the memory used by a loop after the loop has finished, but there may be reasons why the bash devs don't do this, I am not familiar with the bash code base, so I really can't tell.

It could be that the memory used by the loop is kept in some kind of free list, to be reused for other operations. In that case the memory isn't wasted at all, but rather 'put aside' for future use, reducing the amount of malloc() and free() calls. 

That said, I did a lot of programming on 8-bit systems, specifically the Commodore 64, where every byte wasted was one too many, so a simple for-loop using over 100MB seems a bit 'odd'.


Edit:

I just did a quick test to see if my suspicions where correct:
```

#!/bin/bash

echo "loop 1"
for i in {1..1000000}; do :; done

echo "loop 2"
for x in {1000001..2000000}; do :; done

```
When running this script with bash, memory use shoots up (by about 190MB) during the first loop, but memory use does not increase when running the second loop. So it would appear bash does indeed use the technique I described. I also suspect bash generates a string for each loop value, which would account for the major memory usage.

Keeping strings in a free list adds some overhead to the memory used for the actual strings. Suppose we would use a simple linked list to keep track of strings that can be reused:
```

struct gc_string_t {
    char *string;              /* pointer to actual string */
    size_t length;             /* length of string */
    size_t available;          /* memory actually allocated for string */
    struct gc_string_t *next;  /* pointer to next node in list */
}

```
On a 32-bit system, this would add 16 bytes of overhead, on a 64-bit system, it would add 32 bytes of overhead, per string.
If we further assume memory for a string is allocated to the next power of two (a 5 char string causes 8 bytes to be allocated, a 9 char string causes 16 bytes to be allocated, and so on), similar to what GLib does, we can see why memory use increases the way it does.

But these are all just assumptions, I'd have to look into the bash code base to be sure.

---

