---
title: "[SOLVED] Returning TAR_FD to tar in bash script"
date: 2008-12-23
forum: Programming Talk
---

### Post by Paddy Landau on 2008-12-23
I wish to automate *tar* with multi-volume spanning. For that, I need a script.

The following link gives a script written in *sh* (using *#!/bin/sh*)
[http://www.gnu.org/software/tar/manual/html_node/Multi_002dVolume-Archives.html#SEC156](http://www.gnu.org/software/tar/manual/html_node/Multi_002dVolume-Archives.html#SEC156)

The script works, but I need to modify this script a little. However, I'm totally unfamiliar with *sh*, and I'm familiar with *bash*. Thus, I've rewritten this in bash (using *#!/bin/bash*).

But...

The *sh* script sets TAR_FD as:
```
echo ${name:-$TAR_ARCHIVE}-$TAR_VOLUME >&$TAR_FD
```The equivalent in *bash*, I thought, was:
```
TAR_FD=${NEWNAME}
```(where ${NEWNAME} contains the new name)

However, *tar* doesn't receive this new name and continues to reuse the old name.

I've also tried
```
export TAR_FD=${NEWNAME}
```without success.

How do I return TAR_FD back to *tar*?

Thanks.

---

### Post by Paddy Landau on 2008-12-24
Doh! I've answered my own question.

TAR_FD is a file descriptor. The answer is the same as for *sh*:
```
echo ${NEWNAME} >&${TAR_FD}
```

---

### Post by scorp123 on 2008-12-24
> **Paddy Landau said:**
>  The following link gives a script written in *sh* (using *#!/bin/sh*)
[http://www.gnu.org/software/tar/manual/html_node/Multi_002dVolume-Archives.html#SEC156](http://www.gnu.org/software/tar/manual/html_node/Multi_002dVolume-Archives.html#SEC156)

The script works, but I need to modify this script a little. However, I'm totally unfamiliar with *sh*, and I'm familiar with *bash*. I was under the impression that /bin/sh and /bin/bash are one and the same on Linux?

Ubuntu uses a "light-weight" version called "dash" per default, but "dash" should be 100% compatible to "bash". I have seen a few rare cases though where for some odd reason a script did not function as intended. In that case you'd have to disable "dash" and reroute "/bin/sh" to "bash" again. In a shell, please type this:
```
sudo dpkg-reconfigure dash
``` When asked if you want to use "dash" as "/bin/sh" say "No" and it will reroute it back to "bash" again. Before that change becomes active you will have to logout and login back again.

---

### Post by Paddy Landau on 2008-12-24
> **scorp123 said:**
> I was under the impression that /bin/sh and /bin/bash are one and the same on Linux?
Well, I'm not exactly an expert, so I go by the fact that they have different manuals (*man sh* and *man bash*), and that I don't understand the *sh* script.

Thanks for the ideas. I have it working now.

---

### Post by scorp123 on 2008-12-24
> **Paddy Landau said:**
> *man sh* and *man bash* For me the two open the same thing: bash's manual ...

---

### Post by Paddy Landau on 2008-12-25
> **scorp123 said:**
> For me the two open the same thing: bash's manual ...
I'm guessing that's because you did what you described:
> **scorp123 said:**
> ```
sudo dpkg-reconfigure dash
``` When asked if you want to use "dash" as "/bin/sh" say "No" and it will reroute it back to "bash" again.
My *man bash* and *man sh* are definitely different. Briefly looking at the two manuals, I notice that they look mostly the same.

---

