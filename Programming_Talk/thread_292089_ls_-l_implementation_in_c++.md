---
title: "ls -l implementation in c++"
date: 2006-11-03
forum: Programming Talk
---

### Post by FuzZy2006 on 2006-11-03
which is the c++ code that would do the same thing that the ls -l command does?

---

### Post by supirman on 2006-11-03
[glibc filesystem interface]("http://www.gnu.org/software/libc/manual/html_node/File-System-Interface.html#File-System-Interface")

---

### Post by amo-ej1 on 2006-11-05
- run strace ls -al
- and look at the output:

```

fstat64(1, {st_mode=S_IFCHR|0620, st_rdev=makedev(136, 0), ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7c63000
write(1, "000_0198.jpg\t      cv\t\t\t\t\t      "..., 139000_0198.jpg  

```

Prior to writing the output it did a call to 'fstat64'

- gather info on fstat:

```

e@lap:~$ whatis fstat
fstat (2)            - get file status

```

And now the most vital part:
```

man fstat 

```

And now it is only a matter of formatting. i wish everything in life was this easy ;)

---

