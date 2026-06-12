---
title: "ls recusively, files only with full path"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by lucasl on 2008-06-11
Hi,
How can I recursively list files only (no directories) with full the path (eg. /home/user/folder) in a way so I can process each file as one argument even if it has spaces (I think read is used for this, but not sure how)?

I'm just horrible at regex, sed and the like.

Thanks!

---

### Post by decoherence on 2008-06-11
using my home directory as an example,

```
find /home/sean -type f -printf \"%p\"\\n
```

This should give you a list of file paths under /home/sean, quoted to protect whitespace.

---

### Post by niteshifter on 2008-06-11
Hi,

```
find /home/user/folder -type f -print0 | xargs -0 <processing-cmd>
```

where <processing-cmd> is whatever command / process you wish. You're guarded against embedded newlines and whitespace in file names this way.

---

### Post by lucasl on 2008-06-11
@dechoherence
It looks like it should work when he command is run by itself, for when used in a for loop spaces make it separated still.

@niteshifter
That works brilliantly, but for some reason didn't work for vbrfix, which is what I'm trying to do.

In the end, I did some research on find and this worked for me (the goal being to run vbrfix on all my mp3s):
```
find /home/lucas/Music -type f -name *.mp3 -exec vbrfix {} {} \;
```

Thanks!

---

### Post by cariboo on 2008-06-11
You could remove the spaces in the file names using this:

```
for i in *.mp3; do mv "$i" `echo $i | tr ' ' '_'`; done 
```

Jim

---

