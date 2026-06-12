---
title: "Python output manipulation"
date: 2006-08-04
forum: Programming Talk
---

### Post by NewWithoutClue on 2006-08-04
Hi.

I would ask google.. but i really don't know how.

Anyway,
So you know how wget updates it's output in 'real time' to show transfer speed and other things.. i was wondering if this were possible in Python, too.

To be a little more clear:
i would like to be able to print out 'foobar asfdasdfasdf asfdasdf asdfasdf' and change the already-displayed part of the data 'foobar' to something else.. It would be fine to remove the line.. but how do i do that? Basically i'm looking to manipulate things that are already shown to the user.

P.S:
You could be nice and show examples, but i'll settle for a good google query string.

Paul

---

### Post by dabear on 2006-08-04
1) Fiddle with the ncurses library
2) Don't know if this works on MS windows though: collect the length of output, and then send an equal amount of "\r"'s, and then new output. Th downside is that the text has to be the same length each time, or else not all chars from the last print will be removed. You could possibly append spaces or something if you need too..
[quote="ipython console"]
In [19]: print 'aaa', '\r\r\r', 'bbb'
bbb

In [20]: print 'aaa', '\r\r\r', 'bb'
bba
[/quote]

---

### Post by ifokkema on 2006-08-04
\r is a carriage return, it returns the cursor to the left of the screen allowing you to *overwrite* previously written characters. Therefor, using it just once should suffice.
\x8 is a backspace; it allows you to *delete* the last character sent to the screen. I must add that although using both work on PHP, I can't return to the previous line sent to the screen. Not sure if Python can.

HTH!

---

### Post by Pitmairen on 2006-08-05
You could maybe try something like this:
```

import time, sys

test = ["Hallo", "dette", "er", "en", "test", "haaper", "det", "funker", ":)"]
overwrite = 0
for word in test:
    sys.stdout.write("%s%s\r" % (word, " "*overwrite ))
    sys.stdout.flush()
    time.sleep(1)
    overwrite = len(word)
time.sleep(3)

```

---

