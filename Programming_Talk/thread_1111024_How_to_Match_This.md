---
title: "How to Match This?"
date: 2009-03-30
forum: Programming Talk
---

### Post by huangyingw on 2009-03-30
hello:
    I met difficulty when trying regular expression in Ubuntu. The original string is a file with the full path name:'/media/storage/primaryStorage/dvd\ disk/temp.sh', I want to use grep to match out only the file name: 'temp.sh'.
    How could I realize this? I found that, in grep, it does not support *,. [],etc.In general, the grep, and sed, seem to only support simple regular expression.

---

### Post by dwhitney67 on 2009-03-30
Try using basename.

Example:
```

basename /media/storage/primaryStorage/dvd\ disk/temp.sh

```

---

### Post by ghostdog74 on 2009-03-30
you are not very clear. you have a string "/media/storage/primaryStorage/dvd\ disk/temp.sh"  stored in a variable, and you want to get the last part of it after the last "/", ie temp.sh? 
```

# str="/media/storage/primaryStorage/dvd\ disk/temp.sh"
# echo ${str##*/}
temp.sh

```

---

### Post by huangyingw on 2009-03-30
thank you all, even with such an unclear discription.
To make it clear. 
sh file:
=================================================================
#! /bin/sh
egrep -o '[^/]+[^1234567890]*[.]jpg' /root/myproject/linux/shell/regulator/file
=================================================================
file content
=================================================================
/media/storage/aidafe03a004.jpg
=================================================================
my expecting result:
aidafe
I first need aidafe03a004.jpg, then, I want to delete the number, and .jpg post fix. So, my final target is aidafe.

---

### Post by huangyingw on 2009-03-30
while, I found this expression does not work:
egrep -o '[^/]+[^1234567890]*[.](?=jpg)' /root/myproject/linux/shell/regulator/file
It seems that (?=xxx), does not work in egrep. This is my confusion.

---

### Post by rolandrock on 2009-03-30
Don't know about egrep, you cuold try using sed.  Depends on exact filename spec but a place to start:

sed -n 's,.*/\([a-z]*\).*\.jpg,\1,p' $filename

---

### Post by ghostdog74 on 2009-03-30
```

while read line
do
 line=${line##*/}
 echo ${line%%[0-9]*jpg}
done < file

```

---

### Post by huangyingw on 2009-03-31
> **rolandrock said:**
> Don't know about egrep, you cuold try using sed.  Depends on exact filename spec but a place to start:

sed -n 's,.*/\([a-z]*\).*\.jpg,\1,p' $filename
Great, this works for my case, Thanks you.

---

### Post by huangyingw on 2009-03-31
> **ghostdog74 said:**
> ```

while read line
do
 line=${line##*/}
 echo ${line%%[0-9]*jpg}
done < file

```
Thank you a lot, though I still prefer to realize this in regular expression.

---

### Post by rolandrock on 2009-03-31
> **huangyingw said:**
> Great, this works for my case, Thanks you.

Glad I could help.  BTW, if you need to match upper and lower case text, change the 'z' to 'Z'.

---

### Post by huangyingw on 2009-03-31
> **rolandrock said:**
> Glad I could help.  BTW, if you need to match upper and lower case text, change the 'z' to 'Z'.
Hi, in fact, I only have a rough understanding at your sed expression. Could you guid me to a URL or pdf, that could give me detail introduction about sed.

---

