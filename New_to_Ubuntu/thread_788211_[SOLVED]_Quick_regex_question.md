---
title: "[SOLVED] Quick regex question"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by ConMan318 on 2008-05-09
So I know that **mv filename newFilename** will rename a file.  My question is regarding renaming multiple files, and just modifying their names, not changing them completely.  For example, if I wanted to hide files by adding a period to the front but keeping their names the same otherwise.

My guess was something like (this example being to change all .ext files to hidden files):
```

mv *.ext .*.ext

```
But that doesn't work.

So what do I put in place of that second asterisk to refer to the original filename?

---

### Post by Monicker on 2008-05-09
afaik, the mv command does not understand regex.

This bash one liner will work though
```

for i in *.ext; do mv "$i" ".$i"; done;
```

---

### Post by ACJarrett on 2008-05-09
well, to rename with multiple files using wildcards you're going to need to write a simple shell script.

Edit:  Wow nice code monicker!  Beat me to figuring it out :)

---

### Post by ConMan318 on 2008-05-09
Sweet, that works.  It seems like I learn something new every day with Linux that makes me glad I switched from Windows. :)

---

