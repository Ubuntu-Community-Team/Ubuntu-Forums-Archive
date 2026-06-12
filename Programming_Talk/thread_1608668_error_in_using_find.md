---
title: "error in using find"
date: 2010-10-29
forum: Programming Talk
---

### Post by jamesbon on 2010-10-29
If I use 
```
find  ./ -name udp

```I dont get any output.(may be the file does not exist)
but if I do 
```
find  ./ -name udp*
find: paths must precede expression: udpcliserv
Usage: find [-H] [-L] [-P] [-Olevel] [-D help|tree|search|stat|rates|opt|exec] [path...] [expression]

```
So why adding a * to name is giving error

---

### Post by spjackson on 2010-10-29
> **jamesbon said:**
> If I use 
```
find  ./ -name udp

```I dont get any output.(may be the file does not exist)
but if I do 
```
find  ./ -name udp*
find: paths must precede expression: udpcliserv
Usage: find [-H] [-L] [-P] [-Olevel] [-D help|tree|search|stat|rates|opt|exec] [path...] [expression]

```So why adding a * to name is giving error
The shell tries to expand udp* before find sees it, so find could be being passed a list of files from the current directory each of which has a name beginning with udp.

In order to be sure of passing the wildcard to find, you need to escape it from the shell, i.e. one of
```
find  ./ -name "udp*"
find  ./ -name udp\*

```

---

### Post by jamesbon on 2010-10-30
Ok.

---

