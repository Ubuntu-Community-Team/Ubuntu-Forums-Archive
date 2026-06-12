---
title: "customization of M-compile shortcut key in emacs"
date: 2007-01-10
forum: Programming Talk
---

### Post by monkeyking on 2007-01-10
I want to compile my sourcefile from within emacs.
I have a working Makefile,
and would simply like the,
```
M-compile
```
command to be called when I press, something like
```
C-c C-c
```
So that the buffercommandline asks
```
Compile command: make -k

```
-------------------------------------------------------------
Thanks in advance.

---

### Post by boirax on 2008-06-14
Hi,

I think 
```

C-c C-c 

```
adds a comment (at least in c++ Abbrev mode)

In principle you can add to your .emacs file,

```
(global-set-key [SOME KEY YOU CHOOSE] 'compile)
```

Just choose it so that it doesn't interfere with other stuff you use.

for example I have,

```
(global-set-key [f12] 'compile)
```

in my .emacs.

---

### Post by monkeyking on 2008-08-21
Hi, that works perfectly,
thanks.

:)

---

