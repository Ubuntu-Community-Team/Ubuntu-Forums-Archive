---
title: "Finding a comment or directive I've used in a file"
date: 2013-03-27
forum: New to Ubuntu
---

### Post by Maurices5000 on 2013-03-27
I typed a comment in a file (using "#" of course) on my linux server, but i can't remember where i put it. is there a way to find a term, word or directive (such as <Limit>) that i've used?

---

### Post by Derek Karpinski on 2013-03-27
Use grep.

```
grep -r -I 'string you're searching for' /*
```

That will search starting at '/' recursively through all files, ignoring binary files.  It will take a while.

If you remember which directory you put the file in, or the extension of the file, that will speed up the search.

For more options,

```
man grep
```

---

### Post by tgalati4 on 2013-03-27
It helps to use your initials in your comments:

# TFG 27 Mar 13  Cheesy work around, because I'm too lazy to refactor this code.
#

---

