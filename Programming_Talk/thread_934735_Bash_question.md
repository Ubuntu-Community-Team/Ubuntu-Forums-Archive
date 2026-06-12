---
title: "Bash question"
date: 2008-09-30
forum: Programming Talk
---

### Post by thesoothsayer on 2008-09-30
When we perform a "-N" test for a file using bash, does bash keep the information about the last time the file was read on a peruser basis or does it just use the last modified time of the file and compare it with the last accessed time?

---

### Post by tomchuk on 2008-09-30
From bash's test.c
```

case 'N':
      return (sh_stat (arg, &stat_buf) == 0 &&
        stat_buf.st_atime <= stat_buf.st_mtime);

```
Looks like it's using the atime and mtime.

---

### Post by thesoothsayer on 2008-10-01
Ah thanks. Where do you get the bash source from?

---

### Post by tomchuk on 2008-10-01
At [http://ftp.gnu.org/gnu/bash/](http://ftp.gnu.org/gnu/bash/) or
```

apt-get source bash

```

---

