---
title: "Windows-1250 character set"
date: 2012-09-05
forum: Programming Talk
---

### Post by DustWolf on 2012-09-05
Hello,

I am looking for some way to (automatically) convert a file in Windows-1250 character encoding to UTF-8. Apparently while where there are many tools to handle many Windows-125x character sets, there is no support for Windows-1250. On the other hand, my VIM editor can recgotnize and display (on an UTF-8 terminal) "1250C" just fine.

Or am I missing something?

Thanks!

LP,
Jure

---

### Post by The Cog on 2012-09-05
Depends what you mean by automatically. 

Like an on-access virus scanner that converts as your application reads/writes a file? I'm not sure that's a good idea, and I wouldn't know how to do it anyway. 

A program/command/filter that will read a 1250 and write utf8 is easy to do. I don't know of an existing program, but could write one. 
Here's a python script that reads 1250 from stdin and writes utf8 to stdout:
```
#!/usr/bin/env python

import sys

while True:
    s = sys.stdin.read(1000)
    if not s:
        break
    sys.stdout.write(s.decode("cp1250").encode("utf8"))

```

---

### Post by ofnuts on 2012-09-05
> **DustWolf said:**
> Hello,

I am looking for some way to (automatically) convert a file in Windows-1250 character encoding to UTF-8. Apparently while where there are many tools to handle many Windows-125x character sets, there is no support for Windows-1250. On the other hand, my VIM editor can recgotnize and display (on an UTF-8 terminal) "1250C" just fine.

Or am I missing something?

Thanks!

LP,
Jure
The iconv command (pretty much standard on Linux) knows both WINDOWS-1250 and UTF-8 and so will convert between the two.

---

