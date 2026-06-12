---
title: "how to use multiple linux cut comman to display on same line, in script ?"
date: 2010-04-27
forum: Programming Talk
---

### Post by smartlogicsseo on 2010-04-27
how to use multiple linux cut comman to display on same line, in script ?
e.g ls -il | cut -f6 d:
ls - il cut -f9 -d:

The linux script output is 
filename
123

How to use cut to display on same line ?

---

### Post by beren.olvar on 2010-04-27
depending on what you want to do, you may find the "tr" command useful,
for example
```

ls -il | cut -f6 -d: |tr -d [:cntrl:]

```
will delete the control characters (tabs, new lines) from the output, so the following command will start printing in the same line. But as "ls" will output several lines, you will get a mess unless there is only one file in the directory.

maybe something like
```

ls -il | awk '{print $6, $9}'

```
will give you better results.
(look at the IFS variable of awk to change the separating field from "space" to ":" or whatever you need)

---

### Post by Elfy on 2010-04-27
[http://ubuntuforums.org/showthread.php?t=1463729](http://ubuntuforums.org/showthread.php?t=1463729)

---

