---
title: "bash script oddity with $RANDOM returning null"
date: 2011-08-10
forum: Programming Talk
---

### Post by bsautner on 2011-08-10
This is really weird and probably has a simple fix but check this out - driving me crazy

Ubuntu 11.04 in a terminal i type

$echo $RANDOM

I get a random number as expected. 

I create a bash script ($vi script.sh): 

#!/bin/bash
echo $RANDOM

do a chmod a+x on it

run sh ./script.sh 

and i get en empty response - i.e as if $RANDOM returned a null or empty string or something. In any case where i use $RANDOM in a bash script it returns empty but it works on the command line... thoughts!? I'm missing something here.

---

### Post by sisco311 on 2011-08-10
In Ubuntu sh is s symlink to dash. ;)

---

### Post by bsautner on 2011-08-10
ohhhhh i must delete this thread out of shame. ok running my scripts without the sh works fine. Great googly moogly thank you.

---

### Post by sisco311 on 2011-08-10
No problem.

---

