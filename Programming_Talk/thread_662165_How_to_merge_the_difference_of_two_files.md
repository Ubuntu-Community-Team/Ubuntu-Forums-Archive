---
title: "How to merge the difference of two files?"
date: 2008-01-08
forum: Programming Talk
---

### Post by fyplinux on 2008-01-08
Suppose I have a file a, it is content is:
a,b,c

another file b, the content is:
a,b,d

I want to merge the two files to replace both of them, the final state of a and b should be:
a,b,cd

I know that diff and patch could do this, but I intend to implement such functionality by c programming. Reusing diff and patch should be fine, but I don't know how to use them by programming. I just mean to perform such a task, no matter how I do it.

Hope you could give me some idea on this topic. thanks.

---

### Post by Can+~ on 2008-01-08
The content of the files are.. words, numbers, or just letter like in the example?

It's pretty hard to know when working with textfiles, since there's a criteria of comparison, do you want each letter in the same position in both texts? each word? each paragraph?

The most straightforward way, should be to open both files and compare A and B while reading them, and output the difference, but that would imply a pretty strict comparison.

---

### Post by ghostdog74 on 2008-01-08
without any further info,
```
# join -t"," -o 1.1,1.2,1.3,2.2 file1 file2
a,b,c,b


```

---

### Post by fyplinux on 2008-01-09
> **Can+~ said:**
> The content of the files are.. words, numbers, or just letter like in the example?

It's pretty hard to know when working with textfiles, since there's a criteria of comparison, do you want each letter in the same position in both texts? each word? each paragraph?

The most straightforward way, should be to open both files and compare A and B while reading them, and output the difference, but that would imply a pretty strict comparison.

Just say the content is the text file in Ascii.

---

