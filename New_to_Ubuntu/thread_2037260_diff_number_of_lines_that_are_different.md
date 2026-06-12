---
title: "diff number of lines that are different?"
date: 2012-08-04
forum: New to Ubuntu
---

### Post by honeybear on 2012-08-04
Hi,

I would be glad to know the difference in terms of lines that are not same?

diff file1.txt file2.txt  that would ouput 2 if two lines are different.

Any hint for the almighty command that would perform this would be appreciated if possible

thank you

---

### Post by codemaniac on 2012-08-04
> **honeybear said:**
> Hi,

I would be glad to know the difference in terms of lines that are not same?

diff file1.txt file2.txt  that would ouput 2 if two lines are different.

Any hint for the almighty command that would perform this would be appreciated if possible

thank you

diff output is actually a description of how to transform the file1.txt file into file2.txt.

Here is a explanation .
[http://lowfatlinux.com/linux-compare-files-diff.html](http://lowfatlinux.com/linux-compare-files-diff.html)

---

### Post by honeybear on 2012-08-04
```
> **codemaniac said:**
> diff output is actually a description of how to transform the file1.txt file into file2.txt.

Here is a explanation .
[http://lowfatlinux.com/linux-compare-files-diff.html](http://lowfatlinux.com/linux-compare-files-diff.html)

diff -e t.lis s.lis
15d
2a
hi there
.
```

The syntax is line number[, line number end]command [text]
where command is one one of a, c, d
. marks the end of the ed command stream

Count the number of d commands - deletes
Count the number of a commands - inserts
Count the number of c commands - changes
When there is a line range eg., 13,17a subtract 17 - 13 to get the number of lines


I still have to make it work.... man diff does not give any hint about ouputing hte number of lines

---

### Post by honeybear on 2012-08-04
Do you think that it would work? 

```
diff in.html in2.html  | egrep -c '^[<]'
```

---

### Post by codemaniac on 2012-08-04
> **honeybear said:**
> Do you think that it would work? 

```
diff in.html in2.html  | egrep -c '^[<]'
```

diff writes to standard output , hence there is no reasons you cannot do that  .

---

