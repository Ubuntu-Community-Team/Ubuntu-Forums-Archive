---
title: "Remove hard link?"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by Kopachris on 2008-11-28
The command I'm trying to reverse is:
```

sudo ln ~/Desktop/sdcc/bin/* /usr/bin

```So,
1. Which does it look in first, /usr/bin or /usr/local/share?
2. If it looks in /usr/bin first, would I have to manually provide a file list to rm to delete all the links I don't want?

---

### Post by __Ryan__ on 2008-11-29
Where does "/usr/local/share" come into play?  Did mean "~/Desktop/sdcc/bin/*".

If this successfully executed then you should be able to remove all the files created in "~/Desktop/sdcc/bin/" and you will be fine.

---

### Post by sujoy on 2008-11-29
if ~/Desktop/sdcc/bin/ was previously empty then a simple 
rm ~/Desktop/sdcc/bin/*
would suffice

---

### Post by Kopachris on 2008-11-29
I was making a bunch of links in /usr/bin that linked to the files in ~/Desktop/sdcc/bin.  Now I'm trying to remove all of those links at the same time without removing anything else in /usr/bin.

UPDATE: There weren't as many binaries as I thought there were, so I ended up rm-ing them all one by one.  Then I downloaded sdcc's source code and made it myself.  Precompiled binaries with bad installation instructions are no match for "sudo make install".

---

