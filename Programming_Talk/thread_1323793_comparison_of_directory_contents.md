---
title: "comparison of directory contents"
date: 2009-11-12
forum: Programming Talk
---

### Post by mvalviar on 2009-11-12
I've been trying to figure this out by myself but to no avail. How do I list files in one dir that is also found on another dir. ie:

dir1              dir2
   |                 |
   +file1            +file1
   +file2            +file2
   +file3
   `file4

$<some command> dir dir2
file1
file2

---

### Post by ghostdog74 on 2009-11-12
hardcore method and assuming you are not traversing directories
```

#!/bin/bash
ls /home/path2| awk 'BEGIN{
  cmd="ls /home/path1"
  while ( (cmd|getline f)>0) {
    files[f]
  }
  close(cmd)
}
($0 in files){
 print "found: "$0
}' 


```

Of course, the more simpler method is to use diff. check its man page for usage

---

### Post by slakkie on 2009-11-12
I would go for diff:

diff -qr /dir1 /dir2

---

### Post by mvalviar on 2009-11-12
Thanks! diff -qr dir1 dir|grep differ and I got the output I was looking for.

---

