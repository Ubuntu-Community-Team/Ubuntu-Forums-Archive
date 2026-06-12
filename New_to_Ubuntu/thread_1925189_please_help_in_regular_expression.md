---
title: "please help in regular expression"
date: 2012-02-14
forum: New to Ubuntu
---

### Post by jpjohnj on 2012-02-14
hi,

what is meaning of ./ 



where . and / used in linux?


if consider it is an regular expression what is the use of this?

---

### Post by lechien73 on 2012-02-14
./ is used to refer to the current directory.

For example:

```
ls /
```

Produces a directory listing for the root - top level directory

```
ls ../
```

Produces a directory listing for the directory one level above where you currently are.

```
ls ./
```

Produces a directory listing for your current directory.

./ is often used in front of a script that's in your current directory, since for security purposes you can't launch it just by typing the name (like you can in DOS, for instance).

---

### Post by cortman on 2012-02-14
In regular expressions, the period '.' is used to match a single instance of any character. Forward slash '/' is used as an expression delimiter in some regex flavors, but otherwise has no special meaning.
If you're just referring to seeing it in the terminal, lechien73 has the right explanation for that.

---

