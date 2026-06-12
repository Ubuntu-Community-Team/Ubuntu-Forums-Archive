---
title: "[Python] Telnet"
date: 2008-09-12
forum: Programming Talk
---

### Post by themusicwave on 2008-09-12
Hello everyone,

I am having some trouble with Pythons telnet lib.  I am trying to rewrite some old batch files we have for configuring equipment in Python.  The batch files are quirky and don't always work right so they need replaced.

My confusion is mainly with all the read methods like read_eager() read_very_eager() read_lazy(), etc.

What I need to do is send a command.  Then read the response and check for either an error or an ok. Based on that I send the next command.

Which read is best suited for that?  Does anyone have any other telnet tips using Python?

Thanks!

---

### Post by themusicwave on 2008-09-12
I think I made some major progress.

Basically, the read_very_eager() function often returns nothing.  So I put it in a loop and kept doing it until I got the expected length of characters.

Is there a better way though?

---

### Post by kpatz on 2008-09-12
More info on the telnet lib is here: [http://lfw.org/python/htmldoc/telnetlib.html](http://lfw.org/python/htmldoc/telnetlib.html)

Basically, read_very_eager() reads whatever is already available on the socket, without waiting.  So if there's no data available yet, it will return nothing.  If you want to block (wait) for a response, use read_some() or read_all().  read_some() will wait for at least one byte to become available, while read_all() waits for end-of-file and then returns everything.  This is more efficient than using read_very_eager in a loop, since no CPU is used while waiting for I/O.

If you're expecting a certain response, or one of a number of set responses, you can use expect() to read and check for specific strings/regular expressions.  Read up more in the linky above.

---

