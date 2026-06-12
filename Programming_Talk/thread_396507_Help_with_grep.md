---
title: "Help with grep"
date: 2007-03-29
forum: Programming Talk
---

### Post by smbm on 2007-03-29
Hi

Firstly I hope I've placed this thread in the right place. If not sorry.

I need to grep a percentage out of a text file to use in conky (it is my folding at home work unit completed percentage) but can't quite figure out how to do it.

The file looks like this:
```

Current Work Unit
-----------------
Name: p1487_DPPC_DOPC_CHOL
Download time: March 21 06:33:48
Due time: August 18 06:33:48
Progress: 47%  [||||______]

```

I just need the percentage.

The nearest I have got is:

```
grep Progress: /opt/foldingathome/1/unitinfo.txt
```

Which obviously outputs whole the last line.

I've read the man page but I'm pretty new to this sort of malarkey and I can't really fathom most of it.

Can anyone give me a prod in the right direction?

Is grep the way to go? I also looked into using cat but decided to try grep first.

Thanks in advance for everyone's time.

Tom

---

### Post by Mr. C. on 2007-03-29
awk '/Progress/ {print $2}' /opt/foldingathome/1/unitinfo.txt

---

### Post by smbm on 2007-03-29
That's amazing thanks very much.

I'll read up on awk, find out what it can do.

---

### Post by Mr. C. on 2007-03-29
Youre welcome,

Bypass awk - go straight to perl.  Awk is good, as is sed, but perl provides the best of both worlds, and much more.  I'm an old-school guy, so I learned all these tools years ago.  For newbies, you can just use perl and have it all.

MrC

---

