---
title: "How to Setup PyQt for Ubuntu 12.10"
date: 2013-01-02
forum: Programming Talk
---

### Post by rich1939 on 2013-01-02
I have returned to Ubuntu, after having spent a year or so with Windows development and am now using a new computer and a new copy of Ubuntu v12.10. I'm not familiar with this new user interface and don't recall how to load the necessary packages to get up and running with PyQt and the Qt GUI Builder programs.

I assume I'll need to issue terminal commands to "apt get" compilers, SIP, Qt, PyQt wrappers, etc., and I can't find the necessary documentation on how to retrieve, compile, or install these. If pre-compiled versions of the necessary packages are available, please refer me to these instead.

I appreciate the Ubuntu community very much and look forward to being much more involved in the near future.

Thank you in advance,

Rich1939

---

### Post by 3v3rgr33n on 2013-01-02
I think you have to download sip and pyqt from [http://www.riverbankcomputing.com/news](http://www.riverbankcomputing.com/news) as tarballs.

I don't think you can just "apt get" them. After that run run the "configure.py" script,
```
make
``` and then ```
make install
```

---

### Post by lykwydchykyn on 2013-01-02
> **3v3rgr33n said:**
> 

I don't think you can just "apt get" them. 

Uhhh... yeah you can.
For python 2.7:
```

sudo apt-get install python-qt4

```

For python 3.x:
```

sudo apt-get install python3-pyqt4

```

For the GUI designer:
```

sudo apt-get install qt4-designer

```

---

### Post by 3v3rgr33n on 2013-01-02
Lol my bad.

---

### Post by rich1939 on 2013-01-02
> **lykwydchykyn said:**
> Uhhh... yeah you can.
For python 3.x:
```

sudo apt-get install python3-pyqt4

For the GUI designer:
sudo apt-get install qt4-designer

```

Thank you very much :D

I just installed these and will let you know if I have any further problems. I can't believe that I forgot how to install these. :o

My next problem will be how to get a compatible interface for a decent SQL database.

Thanks again.

Rich1939

---

### Post by lykwydchykyn on 2013-01-03
> **rich1939 said:**
> 
My next problem will be how to get a compatible interface for a decent SQL database.


Don't know what you consider a decent SQL database, but QT has sql interfaces for several popular ones in the repositories, including mysql, postgresql (my favorite), odbc, sqlite, and TDS (for MSSQL and Sybase).  About the only one I've dealt with that was a real pain is Oracle, thought setting up TDS is a bit tedious (no pun intended).

---

