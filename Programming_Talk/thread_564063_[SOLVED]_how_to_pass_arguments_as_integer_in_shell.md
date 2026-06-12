---
title: "[SOLVED] how to pass arguments as integer in shell programming"
date: 2007-09-30
forum: Programming Talk
---

### Post by fyplinux on 2007-09-30
HI

I am wondering on how to pass arguments as integer in shell programming

eg.

a script can run as:
              ./script 1 2
and the script can do add operation, get the result of 1+2 is 3

It seems I cannot pass 1 and 2 as integer by defining
      x = $(( $1 )),

 i get the the following exception:
    ./script: line 6: [: x: integer expression expected



How can i solve this problem?

Thank you.

---

### Post by pheeror on 2007-09-30
try add ```
declare -i x
``` before your code

(man bash :: buildin commands :: declare)

---

