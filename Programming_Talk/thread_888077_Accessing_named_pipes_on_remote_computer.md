---
title: "Accessing named pipes on remote computer"
date: 2008-08-12
forum: Programming Talk
---

### Post by VMbuseck on 2008-08-12
I have a question about the access of named pipes on remote computer:

How does it work with linux ?

On windows you have to pass a special "filename" to the open function like
\\ServerName\pipe\PipeName to open a named pipe.

---

### Post by ZylGadis on 2008-08-12
Named pipes in UNIX mean something quite different from named pipes in Windows. Look up sockets if you need Windows-like functionality.

---

