---
title: "Python - Easily accessible terminal information"
date: 2007-02-08
forum: Programming Talk
---

### Post by ironfistchamp on 2007-02-08
Hey all

When programming in Python is there an easy way to get information about the terminal the program is running in. Namely the amount of characters in a row? It would be very useful to be able to get this information and make my program work to this rather than needing it to be a certain way or changing the terminal.

Any thoughts?

Thanks

Ironfistchamp

---

### Post by RHTopics on 2007-02-08
This may partially answer your question.

You can import the "os" module and from that you look at the TERM key to determine whether the user is running from the console or from a xterm session.

example:

>>> import os
>>>  os.environ['TERM']
'xterm'

There maybe other things available in the "os" module that are helpful.

---

### Post by lnostdal on 2007-02-08
run `resize' and parse the output

```

lars@ibmr52:~/programming/lisp$ resize
COLUMNS=167;
LINES=54;
export COLUMNS LINES;
lars@ibmr52:~/programming/lisp$ resize
COLUMNS=79;
LINES=21;
export COLUMNS LINES;
lars@ibmr52:~/programming/lisp$ whereis resize
resize: /usr/bin/resize /usr/X11R6/bin/resize /usr/bin/X11/resize /usr/share/man/man1/resize.1.gz

```

---

### Post by ironfistchamp on 2007-02-08
Thanks for the replies. I shall have to experiment now :) 

Ironfistchamp

---

