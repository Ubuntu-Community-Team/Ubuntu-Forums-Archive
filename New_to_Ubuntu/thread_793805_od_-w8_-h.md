---
title: "od -w8 -h"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by fmpfmpf on 2008-05-14
od -w8 -h

what is the above command for?#

tq

---

### Post by Michael.Godawski on 2008-05-14
```
OD(1)                            User Commands                           OD(1)

NAME
       od - dump files in octal and other formats

SYNOPSIS
       od [OPTION]... [FILE]...
       od [-abcdfilosx]... [FILE] [[+]OFFSET[.][b]]
       od --traditional [OPTION]... [FILE] [[+]OFFSET[.][b] [+][LABEL][.][b]]

DESCRIPTION
       Write an unambiguous representation, octal bytes by default, of FILE to
       standard output.  With more than one FILE argument, concatenate them in
       the  listed  order to form the input.  With no FILE, or when FILE is -,
       read standard input.
```

When you do not know a command just type in into the terminal:

```
man name of command
man od
```

no idea what this command does...

---

### Post by balagosa on 2008-05-14
also
```
name-of-command --help
od --help
``` 

works too

---

