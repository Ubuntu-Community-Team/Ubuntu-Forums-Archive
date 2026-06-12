---
title: "[SOLVED] regexp for lowercasing the first letter on rename command"
date: 2007-08-17
forum: Programming Talk
---

### Post by TheApe on 2007-08-17
Hi, Friends.

I have some files which names aren`t standardized.
Some of them starts with Uppercase letter, some of them not.
They are like this.
-------------------------
fileOne.asp
FileTwo.asp
file.asp
Filen.asp
-------------------------

As I'm developing on Quanta, and it differs the case of the first letter of the file on the sorting(at the file list), I'd like to standardize them like this

-------------------------
fileOne.asp
fileTwo.asp
file.asp
filen.asp
-------------------------

I tryed the unix function "rename" on the command line
```

rename 'y/[A-Z]/[a-z]/' *

```

It works fine, excepts that it lowercases all letter, not just the first one.
I also tryed this
```

rename 's/[^A-Z]?/[a-z]/' *

```
not worked :(

Do you know the exactly regular expression to do it?

Thanks a lot!

---

### Post by rrwo on 2007-08-17
Try ```
rename 's/(.)/lc($1)/e' *
```

---

