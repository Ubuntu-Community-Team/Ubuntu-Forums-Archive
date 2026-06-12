---
title: "Find and replace in a file Unix Scripting"
date: 2010-05-06
forum: Programming Talk
---

### Post by hakermania on 2010-05-06
I have a file with the current path. I read the current path with 'pwd'. However this has a disadvantage: If a directory has spaces (e.g. /home/alex/Home Sweet Home) the pwd will output "/home/alex/Home Sweet Home" and no "/home/alex/Home\ Sweet\ Home". So, I want in the file to replace each space with backsplash-space ( i mean each " " with "\ " without the quotes)

Thx in advance for any replies!

---

### Post by tgm4883 on 2010-05-06
You could pipe it to sed to replace the space
```
pwd | sed 's/ /\\ /g'

```

---

### Post by hakermania on 2010-05-06
Ok thank you this worked.

---

