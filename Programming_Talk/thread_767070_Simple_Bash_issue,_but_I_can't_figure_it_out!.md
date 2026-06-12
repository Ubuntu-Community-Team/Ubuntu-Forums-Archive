---
title: "Simple Bash issue, but I can't figure it out!"
date: 2008-04-25
forum: Programming Talk
---

### Post by EvilMarshmallow on 2008-04-25
Hey all,

I'm working on a bash script that reads data from a file using cut.  I have the whole thing working just like I want, except that my while loop never terminates!  Apparently I don't know what to compare it to if my 'cut' statement exceeds its available data.  If I do

echo `cut -s -d, -f 7 file`

and my file only has 6 fields, I get a blank space.  What can I compare to the output of cut in this case, so that when it no longer has data (my field counter exceeds the number of available fields), the loop will terminate?

---

### Post by EvilMarshmallow on 2008-04-25
Ok, finally found the problem.

cut -s -d, -f X 

is wrong in this case...

cut -d, -f X

works fine!  The while then compares the variable where the results of the above cut statement are stored like so:

while [ -n $VARIABLE ]; do ...

And my infinite loop is gone!

---

