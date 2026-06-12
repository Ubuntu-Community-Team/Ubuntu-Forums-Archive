---
title: "QT4 QFile resize and other problems"
date: 2008-05-23
forum: Programming Talk
---

### Post by Odin25 on 2008-05-23
Hi,

I wrote some code that should create a file, resize it to a definite size, so that I can write QByteArray-blocks at different positions.

The first resizing worked, the file is filled with NULLs.
```

...
file.resize(1024000);
file.seek(12335);
pos = file.pos();
c_size=file.write(ba);
pos2 = file.pos();
file.close();
...
```
pos and pos2 indicate the right position

Problems/Questions:
1. after closing, the file is somehow resized (truncated) do I have to resize it every time?
2. the data seems not to be at the position it should be 
3. do I have to open the file for the resizing?

I'm stuck and would appreciate your help
Thanks

---

