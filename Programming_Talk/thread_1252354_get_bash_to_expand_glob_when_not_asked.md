---
title: "get bash to expand glob when not asked"
date: 2009-08-28
forum: Programming Talk
---

### Post by PGScooter on 2009-08-28
Hi,

I would like to find a way to get bash to expand a glob, even when not asked by the particular command.

For example, I have a file named "financeStatment.cx" in my current directory but I cannot type ```
evince fina
``` and then [tab] to have bash expand it because evince only wants files that have extensions that it recognizes. However, evince opens the file just fine when I type out the whole file name.

The following does the trick:
```
evince `echo fina*`
```
But I would prefer to not have to type that much (I know... lazy :).

How can I do this?

Thanks!

---

### Post by DaithiF on 2009-08-28
Hi,
take a look at /etc/bash_completion
search for evince and you'll see the line which defines the file patterns for which evince completes.  To match all files, change that to the pattern used a few lines above that for zcmp, etc.  Or maybe you could just comment out the evince line -- no sure what the default completion would be -- hopefully it would match all files as a default.

---

### Post by PGScooter on 2009-08-28
exactly what I was looking for. Thank you DaithiF!

---

### Post by kevdog on 2009-08-28
Can you have a personal /etc/bash_completion file like in ~/.bash_completion?  Will this work?

---

### Post by DaithiF on 2009-08-29
> Can you have a personal /etc/bash_completion file like in ~/.bash_completion?  Will this work? 
sure, you would just need to add a line to your .bashrc to source that file.
Default .bashrc's have a section like this:
```
if [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
fi
```
to source the system-wide completion file, just add something similar pointing to your own ~/.bash_completion.

---

