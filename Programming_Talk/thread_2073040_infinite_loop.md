---
title: "infinite loop"
date: 2012-10-18
forum: Programming Talk
---

### Post by sunnypt on 2012-10-18
so i'm trying to make a script that asks my name right?
so i have this: 

#!/bin/bash

echo -n  "Please enter your forum name: "
read fname
if [ $fname = "quit" ]; then echo "bye! "
exit
fi
while [ $fname= ]; do
      echo "please insert at least 1 character"
done

so if i don't enter anything, it goes to an endless loop. what i want the script to do  is to go back to this part if i don't put any character there
echo -n  "Please enter your forum name: "
read fname

any help?

---

### Post by lisati on 2012-10-18
Please do not start multiple threads for the same problem.

Thread closed.

Please see the answers to your original thread here: [http://ubuntuforums.org/showthread.php?t=2073001](http://ubuntuforums.org/showthread.php?t=2073001)

---

