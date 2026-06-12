---
title: "[SOLVED] Wipe data instead of erasing it?"
date: 2008-10-17
forum: New to Ubuntu
---

### Post by slughappy1 on 2008-10-17
Is there a way to wipe data off of you hdd instead of just deleting it? I don't want to erase my entire hdd, I just want to be able to use a command, similar to ```
rm filename
```

---

### Post by saj0577 on 2008-10-17
You mean so it is unrecoverable?

If so.

```
shred filename
```

is the command you want i believe.
FOr more information
```
man shred
```


Saj

---

### Post by handydan918 on 2008-10-17
> **saj0577 said:**
> You mean so it is unrecoverable?

If so.

```
shred filename
```

is the command you want i believe.
FOr more information
```
man shred
```


Saj
I don't believe shred works on journalised filesystems like ext3....

---

### Post by Paqman on 2008-10-17
There's also a more capable package called secure-delete that can wipe free space, swap, etc.

---

### Post by slughappy1 on 2008-10-17
Well according to ```
man shred
``` It doesn't work on journaled systems

---

### Post by Paqman on 2008-10-17
Yes it does. From man shred:
> 
In the case of ext3 file systems, the above disclaimer applies (and shred is thus of limited  effectiveness) only in  data=journal mode, which journals file data in addition to just metadata.  In both the data=ordered (default) and data=writeback modes, shred works as usual.


---

