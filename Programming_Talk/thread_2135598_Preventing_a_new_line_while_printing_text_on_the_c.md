---
title: "Preventing a new line while printing text on the commandline"
date: 2013-04-14
forum: Programming Talk
---

### Post by checoimg on 2013-04-14
So I have this code in D :  ```
import std.stdio;
import std.c.stdlib;
void main() {
     writeln("\033c");
     exit (0);
 }
```  but the program prints a new line which is not desired in this  case. I want to prevent the new line so it prints the working  directory line only.

---

### Post by spjackson on 2013-04-14
use 'write' not 'writeln'.

---

### Post by checoimg on 2013-04-14
> **spjackson said:**
> use 'write' not 'writeln'.

Thank you ! that works perfectly.

---

### Post by Vaphell on 2013-04-14
writeln = write line
look for some other function, is there write() par chance?

oops, too late :)

---

### Post by checoimg on 2013-04-14
> **Vaphell said:**
> writeln = write line
look for some other function, is there write() par chance?

oops, too late :)

Thank you anyway!

---

