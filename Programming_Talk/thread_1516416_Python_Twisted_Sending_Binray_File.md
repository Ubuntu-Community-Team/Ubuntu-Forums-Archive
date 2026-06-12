---
title: "Python Twisted: Sending Binray File"
date: 2010-06-23
forum: Programming Talk
---

### Post by Chamillionaire2 on 2010-06-23
Zoinks!

But seriously, I've been sending the contents of a small text file to a client Python script, Using Twisted. And then writing it once again to a file, But when I try and send a non plain text file via the same method, I get a connection closed message, I take it because I'm not reading the file correctly?

```
binray = open("datebase.db", 'rb')
binrayr = binray.read()
self.sendLine(binrayr)
``` But of course then we get the 'Connection closed cleanly' message. Can anyone give an example of how to send such a file?

Thanks Bye.

---

