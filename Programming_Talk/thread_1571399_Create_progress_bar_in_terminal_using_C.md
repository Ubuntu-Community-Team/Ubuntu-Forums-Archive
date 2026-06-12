---
title: "Create progress bar in terminal using C"
date: 2010-09-09
forum: Programming Talk
---

### Post by sheazar on 2010-09-09
Hi

I'm working on a C program and would like to have a progress bar to indicate how far a operation has come. When the result I've got from google indicated that ncurses should be used, but when I implemented it all overhead made the operation take twice as much time...

There must be a better alternative. Does wget use a library for it's progress bar?

Any suggestions?

EDIT: I could use escape characters but I'm sure I've heard some good argument to why you shouldn't do that...

---

### Post by Bachstelze on 2010-09-09
> **sheazar said:**
> 
Does wget use a library for it's progress bar?

No. Look at src/progress.c, it's simple enough.

---

### Post by soltanis on 2010-09-09
You have several options here. If you are transferring files, or something similar, you can take a look at the **pv** program which can update you on the progress of a file transfer (sudo apt-get install pv).

You can also do what apt-get does, if you do not require a fancy progress bar. On any reasonable terminal emulator the '\b' character will back up one space and let you overwrite the character at that position. For example, if you run this program:

```

awk 'BEGIN { print "12345\b\b67" }'

```

You will see 12367 displayed instead of 12345. apt-get uses this trick to update the percentage progress it reports to you when reading the database ("Reading database... 75%", then a little later, "Reading database... 80%").

Also, you'll need to mess with output buffering to make this work properly (i.e. turn it off, check out **setvbuf**).

You can watch this in action as you install the **pv** program and decide which one of the two you want. Also, as far as I understand, this technique only works on terminals (not on files) so if you were not attached to a terminal (there are ways to determine this) then you should not use this method.

---

### Post by sheazar on 2010-09-09
Thanks for the replies :)

The easy way out is using \r but I'd rather not, not sure why... But I will most definably look at the wget's progress.c code.

---

