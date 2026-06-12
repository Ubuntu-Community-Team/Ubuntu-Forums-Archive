---
title: "Compare 2 files"
date: 2008-07-29
forum: New to Ubuntu
---

### Post by DBrocks on 2008-07-29
Hey guys. I am writing a BASH file that compares 2 files, and if 1 is different then the other, it sends an error message. How would I go about doing this? Thanks!

---

### Post by WRDN on 2008-07-29
The following script compares the files, and returns the word "Same" or "Different".

```
#!/bin/sh

if diff file1 file2 >/dev/null ; then
  echo Same
else
  echo Different
*exit*
fi

```

Note I have added the word "exit" in italics. This can be added if there is code after the If function that you do NOT want to run if the files are different.

---

### Post by cdtech on 2008-07-29
diff --side-by-side /file1 /file2

**P.S.**
Never mind, I'm just thinking comparing two files.

---

### Post by InfinityCircuit on 2008-07-29
For a simple script like this you can also just use cat (/usr/bin/diff might not be available if you use /usr on a separate partition):

```

#!/bin/bash

if [[ $(cat file1) == $(cat file2) ]]; then
    echo same
else
    echo diff
fi

```

---

### Post by DBrocks on 2008-07-29
THanks guys.

---

