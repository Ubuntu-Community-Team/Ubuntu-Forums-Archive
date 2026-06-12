---
title: "long lines in bash script"
date: 2011-04-04
forum: Programming Talk
---

### Post by CaptainMark on 2011-04-04
probaly a silly question but one that google seems to be failing on for me, im surprised its never come up before actually,

i have a line in a bash script, its a nested for loop and the command pipes the output of rsync to grep and then sed and etc.etc. the line is way too long, how can wrap the text to make the script more human readable without changing how it behaves?

Thanks 
Mark

---

### Post by Telengard C64 on 2011-04-04
It should be safe to break long lines at **|** (pipe) characters. I think it is also safe to break at **||** (OR operator) and **&&**.

Another possibility which I haven't tried (so don't take my word for it) is to use line continuations. Try putting a **\** (backslash escape) at the end of the long line just before you break it.

HTH

---

### Post by AlphaLexman on 2011-04-04
You could escape the 'newline' with a '\' at logical breaks...
```
for FILE in * ; do

rsync [options] | \
grep [options] | \ 
sed [options] \

done
```

---

