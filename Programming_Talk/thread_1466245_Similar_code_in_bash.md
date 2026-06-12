---
title: "Similar code in bash"
date: 2010-04-30
forum: Programming Talk
---

### Post by dragos2 on 2010-04-30
Is there a way to list all files and folder from a folder path with bash in a similar way ls -l
does ?

And redirect all to a file, so in short a bash equivalent to this:
```

find /folder/ -type f -print0 2>/dev/null | xargs -0 ls -l > /f1.txt

```

---

