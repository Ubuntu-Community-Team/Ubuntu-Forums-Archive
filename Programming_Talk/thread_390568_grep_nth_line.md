---
title: "grep nth line"
date: 2007-03-22
forum: Programming Talk
---

### Post by monkeyking on 2007-03-22
Is there a nice unix tool to grep the nth line of a file?

thanks in advance

---

### Post by thumper on 2007-03-22
There are these wonderful inventions called pipes.

To grep the 45th line of file foo.txt for "hello"
```
$ head -45 foo.txt | tail -1 | grep hello

```

---

### Post by monkeyking on 2007-03-22
okay,
I wasn't clear enought,

I just want to "extract" the n'th line of a file.

I know I can do stuff like
```

head -n44 file > tmp1.file
head -n45 file > tmp2.file
diff tmp1.file tmp2.file > difference

```
This will give me the 45'th line but with some additional info.

---

### Post by xadder on 2007-03-22
Good old-fashioned awk is incredibly useful for these small jobs:


awk '{ if (NR==45) print $0 }'    file

Or, you can pass in n as a parameter if you want to make  a script:

#!/bin/bash
# Usage   getn  N   filename

awk '{ if(NR==n) print $0 }' n=$1 $2



the syntax is a bit cryptic, but easy to learn. $0 is the whole line. $1 would be the first
column, $2 the 2nd etc.

---

### Post by ghostdog74 on 2007-03-22
you can use sed
```

sed -n '45p' file

```

in awk
```

awk 'NR==45' file

```

---

### Post by Mojtaba-Ebrahimi on 2010-08-21
I have same problem priorly. there are many solution when your line number is a constant number. but if your line number saved in a variable use this one.

suppose your file name saved in a variable named File_Name and your favourite Line number saved in Line variable, then use this command:

cat -n $File_Name | grep "   $Line"

now you can use cut command to cut additional information added by cat command:

cat -n $File_Name | grep "   $Line" | cut -d: -f2

---

### Post by DaithiF on 2010-08-22
or just:
```
sed -n "${Line}p"
```

---

### Post by geirha on 2010-08-22
Bookmark this page [http://mywiki.wooledge.org/BashFAQ](http://mywiki.wooledge.org/BashFAQ), it answers alot of questions like this. For this question, number 11.

---

### Post by ghostdog74 on 2010-08-22
> **DaithiF said:**
> or just:
```
sed -n "${Line}p"
```

```

sed -n "${Line}{p;q}"

```

---

### Post by Chasalin on 2011-01-25
... and what if you're grepping from a file with numeric values, you want to get line numer 7, but '7' also appears in another line? (including the leading spaces...)

I think sed or awk is the way to go and head/tail is a nice trick.

> **Mojtaba-Ebrahimi said:**
> suppose your file name saved in a variable named File_Name and your favourite Line number saved in Line variable, then use this command:

cat -n $File_Name | grep "   $Line"

now you can use cut command to cut additional information added by cat command:

cat -n $File_Name | grep "   $Line" | cut -d: -f2

---

### Post by slavik on 2011-01-25
and this is an old thread and all solutions are available via google.

---

