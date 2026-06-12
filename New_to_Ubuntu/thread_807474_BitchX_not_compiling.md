---
title: "BitchX not compiling"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by linkmaster03 on 2008-05-25
When I try to compile BitchX with 'make' (after configuring, which runs fine) these are the last some lines that come up before it stops compiling:

```
ctcp.c:1367: warning: pointer targets in passing argument 1 of ‘stripansi’ differ in signedness
ctcp.c:1368: warning: value computed is not used
ctcp.c:1369: warning: value computed is not used
ctcp.c:1371: warning: value computed is not used
ctcp.c:1423: warning: value computed is not used
ctcp.c:1424: warning: value computed is not used
ctcp.c: In function ‘BX_split_CTCP’:
ctcp.c:1662: warning: value computed is not used
ctcp.c:1663: warning: value computed is not used
make[1]: *** [ctcp.o] Error 1
make[1]: Leaving directory `/home/brad/BitchX/source'
make: *** [BitchX] Error 2
```

---

### Post by iaculallad on 2008-05-25
> **linkmaster03 said:**
> When I try to compile BitchX with 'make' (after configuring, which runs fine) these are the last some lines that come up before it stops compiling:

```
ctcp.c:1367: warning: pointer targets in passing argument 1 of ‘stripansi’ differ in signedness
ctcp.c:1368: warning: value computed is not used
ctcp.c:1369: warning: value computed is not used
ctcp.c:1371: warning: value computed is not used
ctcp.c:1423: warning: value computed is not used
ctcp.c:1424: warning: value computed is not used
ctcp.c: In function ‘BX_split_CTCP’:
ctcp.c:1662: warning: value computed is not used
ctcp.c:1663: warning: value computed is not used
make[1]: *** [ctcp.o] Error 1
make[1]: Leaving directory `/home/brad/BitchX/source'
make: *** [BitchX] Error 2
```

BithX can be found at the (Universe) repository.

Code:

> sudo apt-get update
sudo apt-get install bitchx

---

### Post by linkmaster03 on 2008-05-25
I have the universe repository enabled, but the BitchX package can't be found.

---

### Post by iaculallad on 2008-05-25
> **linkmaster03 said:**
> I have the universe repository enabled, but the BitchX package can't be found.

Try enabling Main, Multiverse, and Restricted. Or you can search/install it using the Synaptics Package Manager.

---

### Post by m_ad on 2008-05-25
bitchx isn't in the repositories anymore..

[https://lists.ubuntu.com/archives/ubuntu-motu/2007-November/002726.html](https://lists.ubuntu.com/archives/ubuntu-motu/2007-November/002726.html)

---

### Post by linkmaster03 on 2008-05-26
Thanks, I've got irssi now.

---

