---
title: "Text File Output"
date: 2013-06-23
forum: New to Ubuntu
---

### Post by emreergecen on 2013-06-23
Hi everyone,

I am trying to write all the folder content to a text document. To do that I use the following Shell command:

ls ./DIRECTORY > xox.txt

My question is how one can print the directory path before the names of the files? For example, if DIRECTORY contains 2 files as A and B, how can I make Shell write these files to xox.txt as:

(whole path)/A
(whole path)/B

Thanks!

---

### Post by Lars Noodén on 2013-06-23
I'm not sure that is possible with ls.

You may want to try [find](http://manpages.ubuntu.com/manpages/raring/en/man1/find.1.html), which will list the full path.

```

find /home/emreergecen/Documents

```

Be aware that find will travel recursively through all the directories it finds, if it is not told to stop.

```

find /home/emreergecen -maxdepth 1

```

---

### Post by ktat on 2013-06-23
and if you just want a specific file type...

```
find home/username/Documents/*.pdf -maxdepth 1
```

where .pdf could be any extension you like :)

---

