---
title: "Command line arguments"
date: 2012-01-14
forum: Programming Talk
---

### Post by achuth on 2012-01-14
Sir,
I have read in a text book that positional-parameters (command line argument) can be from $0 through $9.
But when I tried more than $9 it is working. I used ${10},${11} and so on.  What is the maximum number of command line arguments that we can give to a shell program?

---

### Post by Bachstelze on 2012-01-15
It is shell- and platform-dependent. POSIX does not say anything about that as far as I can see. In Bash on Ubuntu the answer is "more than you will probably ever need".

---

### Post by Telengard C64 on 2012-01-15
There are other shells besides Bash, and not all of them support pp's greater than $9. Some of the tutorials you find with Google are written for older shells like **sh**.

[http://www.gnu.org/software/bash/manual/bashref.html#Major-Differences-From-The-Bourne-Shell](http://www.gnu.org/software/bash/manual/bashref.html#Major-Differences-From-The-Bourne-Shell)

---

