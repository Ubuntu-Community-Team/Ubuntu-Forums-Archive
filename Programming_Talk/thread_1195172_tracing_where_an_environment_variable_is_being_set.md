---
title: "tracing where an environment variable is being set"
date: 2009-06-23
forum: Programming Talk
---

### Post by bcrowell on 2009-06-23
I have an environment variable (a tex-related one called TEXMFMAIN) that's being set to an incorrect value in every bash shell. I checked  /etc/profile and /etc/bash.bashrc, and there's nothing in those that sets thie variable. To make sure it wasn't something I'd inadvertently put in one my own per-user files (e.g., ~/.bashrc), I made a new user account called glub and tested it:
```
  $ su glub
  Password:
  glub@cl-t091-011cl:/home/bcrowell$ echo $TEXMFMAIN
  /usr/local/share/texmf 
```
I also grepped through every text file in every subdirectory of /etc and /usr, and didn't turn up anything that looked like it was setting this variable.

This seems like a more general problem that people would run into in Unix, and I'm sure someone must have figured out a good, general solution for it: if an environment variable has been set, there must be some general debugging technique that would allow you to find out when it was getting set, and by what program.

Any suggestions?

TIA!

-Ben

---

### Post by geirha on 2009-06-23
> **bcrowell said:**
> 
```
  $ su glub
  Password:
  glub@cl-t091-011cl:/home/bcrowell$ echo $TEXMFMAIN
  /usr/local/share/texmf 
```


That doesn't mean it's being set for every user; the TEXMFMAIN variable was simply inherited from the parent shell in that example. Try with "su - glub" so the environment is not carried over.

Does this give any hits though?
```
grep -r TEXMFMAIN ~
```

---

### Post by bcrowell on 2009-06-23
Aha!! Thanks, geirha! I has a .bashrc left over from when I was using FreeBSD, and it was setting that variable. I hadn't realized that when I do an su, it was carrying over the environment variables. Woo hoo!!!!! :D

---

### Post by %hMa@?b&lt;C on 2009-06-23
sorry for the ot, but we have the same last name :P

---

