---
title: "[SOLVED] output of two awk commands in the same line"
date: 2008-01-25
forum: Programming Talk
---

### Post by Claus7 on 2008-01-25
Hello,

I have file1 and file2. In these files I want to apply pattern1 and pattern2 respectively, and print the output of the two in a new file, file3 in the same line of this file. I want something like this :

awk ' /pattern1/ < file1 ; /pattern2/ < file2' >> file3
I do know that the ouput of each pattern in each file is only one line.

Is it possible?

Regards!

---

### Post by Claus7 on 2008-01-25
Hello,

maybe something like :
paste file1 file2 | awk  'pattern1'; 'pattern2' >> file3 ,
yet I'm still working on it...

Regards!

---

### Post by Claus7 on 2008-01-25
Hello,
with the following command :
paste file1 file2 | awk  'matches=pattern1 || matches=pattern2' >> file3

someone can search both files for the aforementioned patterns, and every time in each file one of the patterns is found (for example line 5) , then that line of this file will be printed with the same line from the other file. 

So that way the patterns I'm interested in should be on the same line.

What I would like to do is keep this "in memory" and when the other pattern is found on the other file, these two to be printed on the same line.

Any ideas?
Regards!

---

### Post by Claus7 on 2008-04-21
Hello,

it could be done as follows:

```

awk '/string1/ {print $0}' file1 > file1.tmp
awk '/string2/ {print $0}' file2 > file2.tmp
paste file1.tmp file2.tmp > file3

```

that way we use the temporary files file1.tmp and file2.tmp and after that we paste them in the new file file3. If we want to add data to this file we do 'command' >> file3 so as to append data to it.

Regards!

---

### Post by ghostdog74 on 2008-04-21
> **Claus7 said:**
> Hello,

it could be done as follows:

```

awk '/string1/ {print $0}' file1 > file1.tmp
awk '/string2/ {print $0}' file2 > file2.tmp
paste file1.tmp file2.tmp > file3

```

that way we use the temporary files file1.tmp and file2.tmp and after that we paste them in the new file file3. If we want to add data to this file we do 'command' >> file3 so as to append data to it.

Regards!

just awk will do

```

awk 'FNR==NR && /string1/{
  a[++c] = $0
  next
}
/string2/{
  b[++d] = $0
}
END {
  for ( i=1;i<=c ;i++) {
    printf "%s %s\n", a[i],b[i]
  }
}
' file1 file2

```

---

### Post by nanotube on 2008-04-22
> **ghostdog74 said:**
> just awk will do

ah, the power of awk :)

---

### Post by Claus7 on 2008-04-23
Hello!

> **ghostdog74 said:**
> just awk will do

Yup, it's working also without the 'FNR=NR &&'.

Regards!

---

