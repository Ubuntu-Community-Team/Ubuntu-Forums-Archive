---
title: "Time copying files in nautilus"
date: 2007-09-09
forum: Programming Talk
---

### Post by wayanwolvie on 2007-09-09
Hi,

I have problem to get the exact time Nautilus need to copy a bunch files using Nautilus from one to another folder. In terminal there is 'time' command to do similar thing. But seems that it can't work with GUI program like Nautilus. 

Can anybody suggest me how to do the timing operation in Nautilus?

---

### Post by dwhitney67 on 2007-09-09
Can you specify what you want to accomplish?  Please do not reference Nautilus or the Terminal in your statement.

This may inquiry may seem strange, but it is helpful to understand the problem without being subjected to limits (e.g. terminal, nautilus, etc.).

---

### Post by wayanwolvie on 2007-09-09
Hmm, actually I need to compare the performance of some virtual  file system, in copy operation with or without file manager (Nautilus). Nautilus is used because it is the default in Gnome. Can you help me on this?

---

### Post by dwhitney67 on 2007-09-09
I still don't quite understand your needs, but one thing I can say... using the Nautilus, or Gnome interface, will be slower than a terminal because the former requires user (operator) input.

With a terminal you can execute a script to copy files from one location (whether local or remote) to another.

Operator inputs, via the mouse, are without saying, slow.

---

### Post by CptPicard on 2007-09-09
I think what he needs is obvious -- measure the time from dropping the files to copy by mouse until the files are copied. No?

Can't say I have any great ideas besides using a stopwatch... how much accuracy do you need?

---

### Post by ghantoos on 2007-09-09
you could try to write a shel script.

an idea (very simplistic..):

```

#!/bin/bash

date
cp /path/to/file /path/to/target
date
```
then compare the the dates outputs.

cheers,

ghantoos

---

### Post by AlexThomson_NZ on 2007-09-09
ghantos, I think the OP used something similar:
```

time cp /path/to/file /path/to/target

```

Now he wants to compare it to doing the same thing via Nautilus.  I can't think of anyway besides a stopwatch, which should give you an ok idea (+-0.5s I guess)...

---

### Post by CptPicard on 2007-09-09
If there is no external way to hook into GTK's user interface events, I don't think it's doable outside of actually inserting your own timing code into that of Nautilus'... and it's probably beyond the scope of this excercise...

---

### Post by wayanwolvie on 2007-09-09
The main idea why I need to this is to get the slowing factor (how many times slower) of using file manager rather than console. The virtual file system is still under development and it is slow. And it feels even much much slower if I use nautilus.

---

### Post by AlexThomson_NZ on 2007-09-09
I think a stopwatch will be fine if you do enough work to last a couple of minutes, the loss in accuracy can be written off, as even using uS timers embedded in the code, other outside influences will probably cause just as much inaccuracy (disk/ram fragmentation, system overheads changing, etc.), so will will definitely get at least +-1s variance anyway...

---

### Post by wayanwolvie on 2007-09-10
thanks :)

---

### Post by lambros on 2007-09-10
I'm not sure, but I think Nautilus uses 'gnomevfs-copy' to do the actual copying.  So maybe you could time that instead?

```
time gnomevfs-copy <src> <dest>
```

Lambros

---

### Post by wayanwolvie on 2007-09-10
hi,
how to copy an entire folder using that command?
the commmand takes URI as it's argument. So far, I'm sucessfully copy a a file. But I can't copy a bunch of files or a directory using it. Is there any URI wildcard (something like "*" )??

---

