---
title: "What does &quot;grep&quot; do?"
date: 2008-10-12
forum: New to Ubuntu
---

### Post by bull205 on 2008-10-12
What does the command grep do?

---

### Post by cardinals_fan on 2008-10-12
It searches for things, either in a directory or in text.  The command "man grep" might be useful.

---

### Post by Sam on 2008-10-12
[http://www.panix.com/~elflord/unix/grep.html](http://www.panix.com/~elflord/unix/grep.html)

---

### Post by paris_alex on 2008-10-13
hmm.. this is a very newbie question, but in a highly enthusiatic ubuntu user community.. let's try to answer this without say 'google it' ;-)

...it basically search for text that you're interested in. for example, this command would list all the processes you have on your system. it's very hard to see the output:

> ps aux

by executing something like:

> ps aux | grep gnome

we're basically filtering the the output of "ps aux" for lines that contains the word "gnome". as for more advanced usage, yea.. you should google or man grep it. ;-)

---

