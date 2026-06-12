---
title: "Python TextIOBase"
date: 2008-11-22
forum: Programming Talk
---

### Post by Martje_001 on 2008-11-22
Hello,
[Here](http://docs.python.org/library/io.html#text-i-o) I read about streams in Python. Now my question is: How do I setup such a stream?

Let me explain why I want this; I have developed code which creates 4 threads to split some work. To give new work to a thread and read his status you have to, somehow, stream it to a stream.

So:
```
stream.open()
Start thread 1 (which writes to stream)
Start thread 2

for i in stream.readline():
 process i
```
Could someone help me with this?

---

